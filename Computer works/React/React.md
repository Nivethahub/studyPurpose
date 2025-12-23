Essential concepts:
- JSX syntax- Components (functional & class)
- Props & State
- useEffect, useState hooks
- Conditional rendering
- List rendering with keys
- Forms & controlled components
- Lifting state up
- Component lifecycle (class-based)
- Routing with React Router
- Context API & useContext
- Custom hooks
- Error boundaries
- Performance optimization (memo, lazy loading)
  
  Why are these 2 external libraries for React?
  https://unpkg.com/supersimpledev/react-dom.js"
  https://unpkg.com/supersimpledev/react.js
  
  React can be used in different places
  Websites, mobile apps
  
  1. React = shared features which is for both website and mobile apps
  2. ReactDOM = features specific to websites
Using react to create websites:
= load React(react external libraries)& ReactDOM (externala libraries)

Using react to create mobile apps:
= load React & ReactNative

Helps us create website easier:
 const container = document.querySelector(".js-container");
      ReactDOM.createRoot(container).render(
        "Welcome to SuperSimpleDev React Course"
      );

Decode:
1. Firstly we use document.querySelector to get an html element from the website and put it in an js
   
   Queryselector
   Return the first element from the respective tag
   
   Js-container div data is stored in the variable container
2. ReactDOM. CreateRoot () =  sets up react
   To create react we have to give the html element so we give the container varaible
   Everything we create with react is displayed with that inisde js-container (which is a html element)
   Why it is inside means?
   React seams to be isolated and organized so acts like inside the html element
3. Render:
   Render is a react feature to display the things in website
   
   What is babel?
   Babel is a javascript compiler
   Translate other languages into javascript
   Why do we need babel here?
   When using react, we don't use normal javascript.
   We use an enhanced version of Javascript = JSX
   JSX = Javascript XML
    =  same as javascript, but we can write HTML directly in our javascript code
    
    <script type="text/babel">
        const button = <button>hello button</button>
      const container = document.querySelector(".js-container");
      ReactDOM.createRoot(container).render(
        "Welcome to SuperSimpleDev React Course"
      );
    </script>
    
    Inside the script we can use only javascript code
    But here, we create button variable and created button html tags and text in that
    This is the Javascript but we can write html directly in our code
    
    But we can actually use this normal javascript as well. We can use the DOM also.
    When using React, we use JSX instead of normal Javascript. Because JSX is simpler
    
    Problem with JSX:
    Our web broswer doesn't understand JSX.
    It understand only normal javascript.
    Inorder to use JSX we need to translate it into Javascript.
    To do that we use the babel external libraries
    
    TO use babel we need 2 steps:
    First loadj the external library of babel
    Translate it to Js
    Give the script element an attribute type = "text/babel"
   
   
   COMPONENTS:
   Componenets = a piece of the website
   When building websites:
   - It's better to split up the website into pieces.
   - So we can work on a small pieces of the website at a time
     
     First Component
