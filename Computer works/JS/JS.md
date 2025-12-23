Essential concepts:
- Data types & variables (`let`, `const`, `var`)- Functions (declaration, expression, arrow)
- Array & object methods (`map`, `filter`, `reduce`)
- DOM manipulation (`querySelector`, `addEventListener`)
- Event bubbling & delegation
- ES6+ features (destructuring, spread/rest, template literals)
- Promises, async/await
- Error handling (`try/catch`)
- Closures, hoisting, scope
- Modules (`import`, `export`)
- LocalStorage, sessionStorage

DOM:
  Document object model , this one has all the html tags
  If we print document
  It gives the full html code
  QuerySelector:
  
  ***GetelementById:***
  If we need to filter a specific element.
  If it has the Id, 
  With the help of id it returns the element it is called getelementById

  Id irunthuchu na postive result kudukum
  Id mismatch means null nu kudukum
  
  **Let element = document. GetelementById ("head")**
  To filter the tag element fully
  
  **Let element = document. GetelementById ("head")**
  **Element. TextContent;**
  Returns only the text datas
  
  To add some value in that:
  **Let element = document. GetelementById ("head")**
  **Element. TextContent += "Youtube"**
  
  Return code. Io youtube

To add some tag in that:
**Let element = document. GetelementById ("head")**
Element. InnerHML = "<p> html new lement</p>"

Can able to add class name in that tag:
**Let element = document. GetelementById ("head")**
Element. ClassName = "bodyclass"

To change the colour:
**Let element = document. GetelementById ("head")**
Element. ClassName = "bodyclass"
Element. Style. Colour = "red"
Element. Style. Background = "blue"


  ***GetelementbyTagName:***
  Return all the tagsname in array format based on the respective parameters
  
  ***QuerySelector***
  Oru tag ooda first element ah kudukurathu QuerySelector
  
  Dynamic element ah creation:
  Const para = Document. Createelement ("tagname")
  Para. TextContent="creating a paragraph tag for the dynamic purpose"
  
  Append:
  Element. Append (para)
  Ithu kudutha website screen la visible aaguma
  At the end the website la
  Element. Preapend (para)
  Preapend panna starting for the website la show aagum
