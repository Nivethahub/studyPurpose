- Nested function's scope
- Closures
- Currying
- This keyword
- Prototype
- Prototype inheritance
- Class
- Iterables and Iterations
- Generators
- Asynchronous

**Scope**:
-Block scope:
Variables which is declared inside a pair of curly braces cannot be accessed outside the block
```js
if(true){
const i = 10
}
console.log(i) //which is not accessible, i is initailized and assigned the value in the block and it is not outside the block, but it can be accessible inside the if block.
```

-Function scope:
Variables which is declared inside function is accessible only inside the function and any nested fn but not from the outside.

```js

function calculateArea(length, width) {
  // 'area' is a local variable with function scope
  const area = length * width; 
  console.log("Inside function: Area is", area); // Accessible here
}

calculateArea(5, 10); // Calls the function

 console.log(area); // This would cause a ReferenceError: area is not defined
```
-Global scope:
Variable can be accessed from any where ie.) Inside or outside the block or function.

***Nested Function Scope***:
```js
let a=10
function outfunction(){
let b =20
function infunction(){
let c=30
console.log(a,b,c)
}
infunction()
}
outfunction()
```

- Nested function has the access to the variable which is declared its own scope and as well as declared in the outer scope.

- When the js has nested function, js first access the innermost function and moves to outer layer until it reaches the end.
  
*Lexical scope:*
It is a function which is defined in another function and it has all the access to variable or function defined in the parent function.

***Closure***:

A function bundled with **its function and along with its lexical scope** is known as closure.
A closure is the combination of a function bundled together with references to its surrounding state. Closures are created every time a function is created, at function creation time.

```js
function outer(){
let counter = 0
function inner(){
counter++
console.log(counter)
}
return inner
}
let data = outer()
data()
```
Ipo naa outer function ah invoke pani oru variable ahset pani antha variable ah invoke pani vita parent function return panidum inner function oodatha outer pathi na details athuku theriyathu outer () gets removed. 
Let data = outer () 

ithu varikum function dhan return aai irukum
Data ()
But  antha variable ah invoke panum bothu returned function result kudukum epadi na sila scopes data vanthu antha return statement ooda irukum athula return aana function la scopes la parent scope edhu nu athunala find panika mudiyum like closure

![[Pasted image 20250724111843.png]]
Hoisting is a js by which we can access the variables and function even before it is initailized
Var can be only access like this in hoisting as a variable.
```js
console.log(k) //this is hoisting var k is not initailized with value and it is stored in a global scope with the value undefined
var k=10
```

Temporal Dead zone:
The time period between the hoisting and the value initailized is called temporal dead zone

```js
console.log(d)//hoisted the variable d which is in separte scope
let d=5// to the value is initailized, in this line end duration is said to be temporal dead zone
console.log(d)
```

TypeError:

Syntax Error: 

***Currying***:----
A process in functional programming in which we transform a function with multiple arguments into a sequence of nesting function sthat take one arguments at a time
Function f (a, b, c) is transform to f (a)(b)(cl)

***this***:---
```js
const person={
name:"nivetha"
sayMyname: function(){
console.log(`my name is ${this.name}`)
}
}
person.sayMyname()
```
Implicit binding rule:
A function which is invoked with the dot notation then the object on the left side belongs or able to access to the this keyword

Explicit binding rule:
```js
const person={
name:"nivetha"
}

function sayName(){
console.log(`my name is ${this.name}`)}

sayName.call(person)
```

New binding:
We can invoke a function with new keyword

```js
function Person(name){
this.name = name}

const p1= new Person("nivetha")
const p2= new Person("nivethaaa")
```

Person function is know as constructor where we can create multiple function. When we invoke a function with new keyword, js will create a new empty object with the this keyword reference

***Prototype***:

For each and every creation of function or objects, etc inour code. Js engine will creates its own internal object which consists of default properties and links to our function\objects\array and that object we can able to access by using chaining (. Operator). 

Whenever we create object, js engine automatically without letting you know attaches your object to hidden properties & functions. Arr.__proto__
Protochaining:

When the object\array has a prototype 


***Asynchronous***:
+ Timeouts and intervals
+ Callbacks
+ Promises
+ async await
+ Eventloop
  
1) What and why async Javascript?
Javascript is a synchronous, blocking and single threaded language.
Synchroronous:
  If we have 2 functions which log message to the console, code executes top to down with only one line at a given time
  Blocking:
  No matter how long the previous process takes, the subsequesnt processess won't kick off until the previous one is completed.
  Single-threaded:
  It a process that code can use to run a task. Each thread can do only one task at  a time, only one thread main thread.
  
  *Timeouts and Intervals*:
Traditional methods to run code asynchronously
SetTimeout ()

SetTimeout () function executes a particular block of code once after a specified time has elapsed
SetTimeout (function, duration, param 1,...)
```js
function greet(){
console.log("hi")}
setTimeout(greet,2000)//logs after 2 seconds
```

Once SetTimeout is called we have to cancel it for sometime.
To clear the SetTimeout, use the clearTimeout () method passing in the identifier returned by SetTimeout as a parameter
```js
const timeoutvar = setTimeout(greet,2000)
clearTimeout(timeoutvar) //cancellation of settimeout
```
  
  SetInterval ():
  This function runs repeatedly the same code over and over again at regular intervals.
  ```js
  SetInterval(dunction,duration,params...)
  ```
  
  To cancel the setInterval
  We use clearInterval () as same as clearTimeout ()
  
*Callbacks*:

Functions are first class objects

*Eventloop*:
