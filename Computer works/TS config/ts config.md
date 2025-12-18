File setup:

	npm init -y

Install express and mongoose:

	npm install express mongoose

Install TypeScript and Node. Js types:

	npm install typescript ts-node @types/node @types/express --save-dev

Install typescript config file:

	npx tsc --init

Nodemon:

Npm install nodemon ts-node --save-dev


Package. Json:
{
  "scripts": {
    "start": "nodemon --exec ts-node file. Ts"
  }
}


Or 
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "nodemon --exec tsx src/main.ts"
  },

Tsconfig. Json:

```
{
  "compilerOptions": {
    "target": "ESNext",
    "module": "ESNext",
    "moduleResolution": "bundler",
    "noEmit": true,
    "esModuleInterop": true, 
    "typeRoots": ["node_modules/@types"],
    "types": ["node"],                    
    "forceConsistentCasingInFileNames": true,
    "strict": true,
    "skipLibCheck": true
  }
}
```