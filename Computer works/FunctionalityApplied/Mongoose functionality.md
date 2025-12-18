Normal Schema:
```
import { model, Schema, Document, Types } from "mongoose";
export interface Amenity extends Document {
  parentType: "spot" | "view" | "plot";
  parentId: Types.ObjectId;
  name: string;
  type?: string;
  position: { x: number; y: number };
  image: string;
  image360?: string;
}
const AmenitySchema = new Schema({
  parentType: { type: String, enum: ["spot", "view", "plot"], required: true },
  parentId: { type: Schema.Types.ObjectId, required: true },
  name: { type: String },
  type: { type: String, enum: ["normal", "runway"], default: "normal" },
  position: { x: Number, y: Number },
  image: { type: String },
  image360: { type: String },
});
const AmenityModel = model<Amenity>("Amenity", AmenitySchema);
export default AmenityModel;
```

Connection:
```import mongoose from "mongoose";
import dotenv from "dotenv";
import { Client } from "minio";
dotenv.config();
const db = async (): Promise<void> => {
  try {
    const uri = process.env.MONGO_URI;
    if (!uri) {
      throw new Error("MONGO_URI is not defined in .env file");
    }
    await mongoose.connect(uri);
    console.log("Connected to db");
  } catch (error: any) {
    console.error("Error connecting to DB:", error.message);
  }
};
export { db };
```


Organization Based Schema:
```
import { Document, Schema } from "mongoose";
import MainModel from "../../connect/mongoose";
import { User } from "../Auth/userAuthModel";
import { Project } from "../Project/project-model";
import { Version } from "../Version/versionModel";
interface ICommonBase {
  type: string;
}
interface IPointsConveyor extends ICommonBase {
  points?: {
    Uuid: string;
    position: [number, number, number];
    rotation: [number, number, number];
  }[];
}
interface IPoint extends ICommonBase {
  point?: {
    Uuid: string;
    position: [number, number, number];
    rotation: [number, number, number];
  };
}
export interface AssetData extends Document {
  userId: User["_id"];
  projectId: Project["_id"];
  versionId: Version["_id"];
  modelUuid: string;
  assetId: string;
  modelName: string;
  isLocked: boolean;
  type: string;
  subType: "manual" | "automatic" | "semiAutomatic";
  isVisible: boolean;
  isArchive: false;
  position: [number, number, number];
  scale: [number, number, number];
  rotation: [number, number, number];
  speed: number | string;
  eventData: IPoint | IPointsConveyor;
  isCollidable: boolean;
  opacity: number;
}

const assetDataSchema: Schema = new Schema({
  userId: { type: Schema.Types.ObjectId, ref: "User" },
  projectId: { type: Schema.Types.ObjectId, ref: "Project" },
  versionId: { type: Schema.Types.ObjectId, ref: "Version" },
  isArchive: { type: Boolean, default: false },
  modelUuid: { type: String },
  assetId: { type: String },
  modelName: { type: String },
  type: { type: String },
  subType: { type: String, enum: ["manual", "automatic", "semiAutomatic"] },
  position: { type: Array },
  scale: { type: Array },
  rotation: { type: Array },
  speed: { type: Schema.Types.Mixed },
  isLocked: { type: Boolean },
  isVisible: { type: Boolean },
  eventData: {
    type: Schema.Types.Mixed,
  },
  opacity: { type: Number },
  isCollidable: { type: Boolean },
});

const assetModel = (db: string) => {
  return MainModel(db, "Assets", assetDataSchema, "Assets");
};
export default assetModel;

```

Connection:
```
import mongoose, { Schema, Connection, Model } from "mongoose";
interface ConnectionCache {
  [key: string]: Connection;
}
const connections: ConnectionCache = {};
const MainModel = <T>(
  db: string,
  modelName: string,
  schema: Schema<T>,
  collectionName: string
): Model<T> => {
  const db1_url = `${process.env.MONGO_URI}${db}`;
  const authOptions = {
    user: process.env.MONGO_USER,
    pass: process.env.MONGO_PASSWORD,
    authSource: process.env.MONGO_AUTH_DB || "admin",
    maxPoolSize: 50,
  };
  if (connections[db]) {
    return connections[db].model<T>(modelName, schema, collectionName);
  }
  try {
    const db1 = mongoose.createConnection(db1_url, authOptions);

    connections[db] = db1;

    db1.on("connected", () => {
      console.log(`Connected to MongoDB database: ${db}`);
    });
    db1.on("error", (err) => {
      console.error(
        `MongoDB connection error for database ${db}:`,
        err.message
      );
    });
    return db1.model<T>(modelName, schema, collectionName);
  } catch (error) {
    console.error("Database connection error:", (error as Error).message);
    throw error;
  }
};
export default MainModel;
```


Populate Handling:

```
//single
.populate({
        path: "createdBy",
        model: AuthModel(organization),
        select: "userName",
      });
//multiple
.populate([
        {
          path: "createdBy",
          model: AuthModel(organization),
          select: "userName",
        },
        {
          path: "comments.userId",
          model: AuthModel(organization),
          select: "userName",
        },
      ]);
```

Pagination:
Curse based pagination:
```
import { Request, Response } from "express";
import mongoose,{Connection} from "mongoose";
import { GridFSBucket } from "mongodb";
import ModelSchema from "../model/Model.ts";


//GridFSBucket
let gfsBucket: GridFSBucket | undefined;

mongoose.connection.on("connected", () => {
  if (mongoose.connection.db) {
    gfsBucket = new mongoose.mongo.GridFSBucket(mongoose.connection.db, {
      bucketName: "models",
    });
    // console.log("GridFSBucket initialized");
  } else {
    console.error(
      "Failed to initialize GridFSBucket: Database connection is undefined."
    );
  }
});

//Cursed pagination
export const CursorDatas = async (req: Request, res: Response) => {
  try {
      const { limit, cursor } = req.query;
      const limitNumber = parseInt(limit as string) || 10;
  
      const query: any = {};
      if (cursor) {
        query._id = { $gt: cursor };
      }
      const categoryLists = await ModelSchema.find(query)
      .sort({ _id: 1 }) // Sort in ascending order 
      .limit(limitNumber);
    const db = mongoose.connection.db;
    if (!db) {
      return res.status(500).json({ message: "Database not connected" });
    }
    const enrichedAssets = await Promise.all(
      categoryLists.map(async (asset: any) => {
        const file = await db
          .collection("models.files")
          .findOne({ filename: asset.filename });

        return {
          modelfileID: file?._id || null,
          ...asset.toObject(),
        };
      })
    );
    const hasNextPage = categoryLists.length === limitNumber;

    const nextCursor = hasNextPage
      ? categoryLists[categoryLists.length - 1]._id
      : null;

    return res.status(200).json({
      items: enrichedAssets,
      nextCursor, // Pass this to fetch the next page
      hasNextPage,
    });
   } catch (error) {
    console.error("Error retrieving assets:", error);
    res.status(500).json({ error: "Failed to retrieve assets." });
  }
};

//download file:
export const DownloadFile = async (req: Request, res: Response) => {
  try {
    const filename = req.params.filename.split(".")[0];
    // Find the document in ModelSchema using the filename
    const findFilename = await ModelSchema.findOne({ filename });

    if (!findFilename) {
      // console.log("No document found with the provided filename");
      return res.status(404).json({ message: "File not found" });
    }
    if (!gfsBucket) {
      return res
        .status(500)
        .json({ message: "GridFSBucket is not initialized yet." });
    }
    const downloadStream = gfsBucket.openDownloadStreamByName(filename);
    // res.setHeader("Content-Type", "image/jpeg");  // Assuming it's a JPEG file
    // res.setHeader("Content-Disposition", `attachment; filename="${filename}"`);
    res.setHeader("Content-Type", "model/gltf+json");
    res.setHeader(
      "Content-Disposition",
      `attachment; filename="${filename}.gltf"`
    );
    downloadStream.on("error", (error: any) => {
      return res.status(500).json({ message: "File not found" });
    });
    downloadStream.pipe(res);
  } catch (error: any) {
    return res
      .status(500)
      .json({ message: "Server error", error: error.message });
  }
};
export default DownloadFile;
```

Search:
```
const { searchName } = req.query;
    const findModalName = await ModelSchema.find({
      filename: { $regex: `^${searchName}`, $options: "i" }, // 'i' makes it case-insensitive
    })
```