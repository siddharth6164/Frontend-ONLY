# Interview

| Column 1 | Column 2 | Column 3 | Column 4 | Column 5 |
|----------|----------|----------|----------|----------|
|[BOM and DOM](#bom-and-dom)|[Callback Function](#callback-function)|[Callback Hell](#callback-hell)|[call(), apply(), bind()](#call-apply-bind)|[Closure](#closure)|
|[Controlled and Uncontrolled Components](#controlled-and-uncontrolled-components)|[Cookie, Local Storage, Session Storage](#cookie-local-storage-session-storage)|[Currying Function](#currying-function)|[Deep Copy & Shallow Copy](#deep-copy-and-shallow-copy)|[ES6](#es6)|
|[Event Capturing, Event Bubbling](#event-capturing-event-bubbling)|[event.preventDefault()](#eventpreventdefault)|[Event Loop](#event-loop)| [Higher Order Function](#higher-order-function)|[Hoisting](#hoisting)|
|[Immediately Invoked Function Expression (IIFE)](#immediately-invoked-function-expressioniife)|[Lexical Scope](#lexical-scope)|[Map, forEach, Filter, Reduce](#map-foreach-filter-reduce)|[Memoization](#memoization)|[Null, Undefined, NaN](#null-undefined-nan)|
|[Promise](#promise)|[Pure Function and Impure Function](#pure-function-and-impure-function)|[Rest Parameter and Spread Operator](#rest-parameter-and-spread-operatar)|[Scope in JS](#scope-in-js)|[Slice and Splice](#slice-and-splice)|
|[TDZ (Temporal Dead Zone)](#tdztemporal-dead-zone)|[This](#this)|[Var vs Let vs Const](#var-vs-let-vs-const)|[== and ===](#-and-)|[Block and Non-Block](#block-and-non-block)|
||||[async/await](#asyncawait)|[Synchronous and Asynchronous](#synchronous-and-asynchronous)|


---
## Closure 
Closure is created when a child function to keep the enviroment of the parents scope even after the parents function has already executed.
```js
function parents() {
  let count = 0;   // this lexical scope
  function child() {
    count++;
    console.log(count);
  }
  return child;
}

const counter = parents();
counter(); // 1
counter(); // 2
```

[⬆ Back to Top](#Interview)

## Lexical Scope
Inner function to access variable from their outer function.
```js
function outer() {
  var outerVar = "I'm in the outer function";
  return function inner() {
    console.log(outerVar); // Can access outerVar because it's lexically inside the outer function's scope
  };
}

const innerFunc = outer();
innerFunc(); // Logs "I'm in the outer function"
```

[⬆ Back to Top](#Interview)
## Deep Copy and Shallow Copy
##### Deep Copy
Create a new object and  recursively copies all nested object ensuring that the original and the copy are completely independed.
```js
// 1. JSON.parse(JSON.stringify())
const obj = { a: 1, b: { c: 2 } };
const deepCopy = JSON.parse(JSON.stringify(obj));
deepCopy.b.c = 99;
console.log(obj.b.c); // 2 (unchanged)
```
```js
// 2. Manual recursive deep copy
function deepCopy(obj) {
  if (obj === null || typeof obj !== "object"){
    return obj;
  }
  const copy = Array.isArray(obj) ? [] : {};
  for (let key in obj) {
    copy[key] = deepCopy(obj[key]);
  }
  return copy;
}

const original = {a: 1,b: { c: 2}};
const cloned = deepCopy(original);
cloned.b.c = 99;
console.log(original.b.c);      // 2 (unchanged)
console.log(cloned.b.c);        // 99
```

##### Shallow Copy
Create a new object but copies references to original, nested object means change to nested object offect both original and copy.
```js
// 1. Spread operator (...) 
const obj = { a: 1, b: { c: 2 } }; 
const shallowCopy = { ...obj }; 
shallowCopy.b.c = 100; 
console.log(obj.b.c); // 100 (changed!) 
```
```js
// 2. Object.assign() 
const obj = { a: 1, b: { c: 2 } }; 
const shallowCopy = Object.assign({}, obj); 
shallowCopy.b.c = 99; 
console.log(obj.b.c); // 99 (changed!)
```

[⬆ Back to Top](#Interview)

## Hoisting
Hoisting is a JS mechanism where variable and function declarations are moved to the top of their contaning scope during the compilation phase. This allows variable and functions to be used before they are declared in the code. ``` var ``` are hoisted to the top of their scope and initialized with undefined. ``` let ``` and ``` const ``` are also hoisted, but they are not initialized, accessing them before declaration result in a ``` ReferenceError ``` due to the ``` Temporal Dead Zone ``` .
```js
// 1. var declarations(with var)
console.log(x); // undefined
var x = 5;
console.log(x); // 5
```
```js
// 2. Function Declarations
greet(); // "Hello!"
function greet() {
  console.log("Hello!");
}
```

```js
// 3. let and const Declarations
console.log(a); // ReferenceError: Cannot access 'a' before initialization
let a = 10;
```

[⬆ Back to Top](#Interview)

## Immediately Invoked Function Expression(IIFE)
Immediately Invoked Function Expression. It is function expression that return immediately after it is defined.
```js
// 1. Basic IIFE
(function () {
  console.log("IIFE executed!");
})();
```
```js
// 2. IIFE with Arrow Function
((Parameters) => {
  console.log("Arrow function IIFE executed!");
})(Parameters);
```

[⬆ Back to Top](#Interview)

## Var vs Let vs Const
``` var ``` is function scoped. It decloration is hoisted means you can refer to variable before it's line of declartion but it's value will be undefined until assignment you can also re-declare and re-assign it.

``` let ``` **and** ``` const ``` both are block scoped. They are also hoisted, but you can't access them before the declaration , so it show the ``` Reference Error ``` because if the Temporal Dead Zone. ``` let ``` allow re-assignement but not re-declaration in same block. ``` const ``` can not allow re-assignement and re-declaration.

[⬆ Back to Top](#Interview)

## == and ===
``` == ``` is loose equality operatior. It compares two value after doing type coericon, means if the operands are of different types it will try to convert them to a common type before comparing 
```js
console.log("0"==0) // true
```

``` === ``` is the strict equality operator. It check both value and type.
```js
console.log("0"==0) // fasle
```

[⬆ Back to Top](#Interview)

## Map, forEach, Filter, Reduce
``` map ``` create a new array by appling a function to each element. return a new array with modified values.
```js 
const numbers = [1, 2, 3, 4, 5];
const squaredNumbers = numbers.map(num => num * num);
console.log(squaredNumbers);  // Output: [1, 4, 9, 16, 25]
```

``` forEach() ```  is used to iterate over array elements and execute a function for each element without returning a new array.
```js
const fruits = ["apple", "banana", "mango"];
fruits.forEach((fruit, index) => {
  console.log(index, fruit);
});
```

``` filter ``` create a new array with elements  that pass a condition. return filtered array.
```js
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const oddNumbers = numbers.filter(num => num % 2 !== 0);
console.log(oddNumbers);  // Output: [1, 3, 5, 7, 9]
```

``` reduce ``` reducer an array to a single value by appling a function. return final accumulated value.
```js
const numbers = [1, 2, 3, 4, 5];
const sum = numbers.reduce((acc, num) => acc + num, 0);
console.log(sum);  // Output: 15
```

[⬆ Back to Top](#Interview)

## ES6
- ``` let ``` and ``` const ```
- Arrow function
- Template titeals ``` ` ```
- De-structring
- Rest and Spread operator
- Promises
- classes
- Modules
- ``` map ``` and ``` set ```

[⬆ Back to Top](#Interview)
## BOM and DOM
##### BOM
The BOM represents the browser environment, allowing JavaScript to interact with the browser outside the webpage content.

- Browser window
- URL
- Navigation
- Browser history
- Screen information
- Timers

##### DOM
The DOM represents the structure of an HTML document as a tree of objects. JavaScript uses the DOM to access, modify, add, or delete HTML elements, CSS styles,Attributes ,Events (click, input, submit, etc.).

### Common DOM objects & methods

- getElementById()
- getElementsByClassName()
- querySelector()
- createElement()
- appendChild()
- addEventListener()
  
[⬆ Back to Top](#Interview)

## Higher Order Function
A function that takes one or more functions as arguments or return a function. It controls the execution of the callback funtion.
##### Example-> map(), filter(), reduce(), forEach()
#### Why use HOF   

| Code reusability | Cleaner & modular code | Functional programming style | Avoid repetition |
|------------------|------------------------|------------------------------|------------------|

```js
function multiplier(a) {
  return function (b) {
    return a + b;
  };
}
const double = multiplier(2);
console.log(double(5)); // 7
```

[⬆ Back to Top](#Interview)

## Controlled and Uncontrolled Components
``` Controlled ``` components is form element(like input, textarea, select) whose value is controlled by React state. Like ``` Form ``` values are handled and controlled using the useState hook.
  #### Cons of Controlled conponents
  - Re-renders on every change
    
``` Uncontrolled ``` components lets the DOM handle the form data, not React state. so Data is stored in the DOM. 

  - Data is stored in the DOM
  - You access it using a ``` ref ```
  #### Cons of Uncontrolled conponents
  - less control over input

[⬆ Back to Top](#Interview)

## Promise
``` Promises ``` in JS to handle asynchronous operations in a cleaner, safer, and more readable way.

3 states in promises:
1. Pending -> operation is still runnig
2. Fulfilled -> operation completed successfully
3. Rejected -> operation failed

so we handle the result using
``` .then() ``` ``` .catch() ``` ``` .finally() ```
```js
const myPromise = new Promise((resolve, reject) => {
  let success = true;
  if (success) {
    resolve("Operation successful!");
  } else {
    reject("Operation failed!");
  }
});

myPromise
  .then(result => {
    console.log(result);
  })
  .catch(error => {
    console.error(error);
  })
  .finally(() => {
    console.log("Done");
  });

````

##### we are use in
- Fetching data from a server
- Reading files
- Waiting for a timer
- Database operations

##### - Promises are return a object. 
##### - Promises are take 2 paramerters: ``` resolve ``` and ``` reject ```

##### asyns-await
if we are use asyncs await it is return ``` Promises ```
```js
async function example() {
  try {
    const result = await wait;
    console.log(result);
  } catch (error) {
    console.error(error);
  }
}
example();
```

[⬆ Back to Top](#Interview)

## Slice and Splice
both are array methods

``` slice() ``` extracts part of an array and returns a new array and does NOT change the original array.
```js
//array.slice(start_index, end_index)
let arr = [1, 2, 3, 4, 5];
let result = arr.slice(1, 4);

console.log(result); // [2, 3, 4]
console.log(arr);    // [1, 2, 3, 4, 5] (unchanged)
```

``` splice() ``` add, remove, or replace elements and changes the original array.
```js
//array.splice(start, deleteCount, item1, item2, ...)

// remove
let arr = [1, 2, 3, 4, 5];
let removed = arr.splice(1, 2);
console.log(removed); // [2, 3]
console.log(arr);     // [1, 4, 5]

// add
let arr = [1, 2, 3];
arr.splice(1, 0, "a", "b");
console.log(arr); // [1, "a", "b", 2, 3]

//replace
let arr = [1, 2, 3, 4];
arr.splice(2, 1, "x");
console.log(arr); // [1, 2, "x", 4]
```

[⬆ Back to Top](#Interview)

## Currying Function
``` Currying function ``` multiple arguments is transformed into a series of functions that each take one argument at a time.
```js
function add(a) {
  return function (b) {
    return function (c) {
      return a + b + c;
    };
  };
}
add(1)(2)(3); // 6
```

[⬆ Back to Top](#Interview)

## Pure Function and Impure Function
``` Pure function ``` given the same inputs, a pure function will always return the same output, and it does not modify any external state or data.
```js
function add(a, b) {
  return a + b;
}
// add(2, 3) will always return 5
```

``` Impure function ``` menas does not always give the same output for the same input or that causes side effects.
```js
let x = 10;
function add(y) {
  return x + y;
}
```
- Result changes if x changes
- Same input does not always give same output

[⬆ Back to Top](#Interview)
## TDZ(Temporal Dead Zone)
``` Temporal Dead Zone ``` is the time between the block start and variable declaration where accessing a ```let``` and ```const``` variable results in a Refference Error.
```js
    console.log(counter1); // Output: undefined (due to var hoisting)
    console.log(counter2); // Throws ReferenceError (TDZ for let)
    var counter1 = 1;
    let counter2 = 2;
```

[⬆ Back to Top](#Interview)

## Memoization
Memoization in JS optimization technique that stores the results of expensive function calls and reuses them when the same input occur again. This reduces the number of computation by caching the result.
#### Real-world examples
- Fibonacci
- API response caching means saving the result of an API call so the next time the same request is made, you return the saved data instead of calling the API again
  
[⬆ Back to Top](#Interview)

## Scope in JS
1. Global Scope
2. Function scope
3. Block scope
4. Lexical scope
5. Modular scope

[⬆ Back to Top](#Interview)

## Cookie, Local Storage, Session Storage
```Cookie``` Small pieces of data stored in the browser and sent to the server with every request.
Key features:
- Size limit: ~4 KB
- Can have expiration time
- Automatically sent with HTTP requests
- Used for authentication, sessions

```Local-storage``` Stores data permanently in the browser (until manually cleared).
Key features:

- Size limit: ~5–10 MB
- Data persists even after browser is closed
- Client-side only
- Stores data as strings

```Session-storage``` Stores data for one browser tab/session only.
Key features:

- Size limit: ~5 MB
- Data cleared when tab is closed
- Client-side only
- Not shared between tabs

###### Security Notes
- Never store passwords in any of them
- Use HttpOnly cookies for auth tokens
- Use HTTPS for secure cookies

[⬆ Back to Top](#Interview)

## Callback Function
A callback function is a function passed into another function as an argument. This function is invoked inside the outer function to complete an action. like-> ```setTimeout()```
```js
function greet(name, callback) {
  console.log("Hello " + name);
  callback();
}
function sayBye() {
  console.log("Bye!");
}
greet("Alex", sayBye);
```
[⬆ Back to Top](#Interview)
## Callback hell
Callback hell is many callbacks nested inside each other, making code hard to read and maintain.
###### avoid callback hell -> 1. Use Promises 2. Use async / await
```js
setTimeout(() => {
  console.log("Step 1");
  setTimeout(() => {
    console.log("Step 2");
    setTimeout(() => {
      console.log("Step 3");
    }, 1000);
  }, 1000);
}, 1000);
```
[⬆ Back to Top](#Interview)
## Null, Undefined, NaN
```null``` value represents but not a value, not a object. It is known as empty value/object.

```undefined``` variable are declare but not assign a value.

```NaN``` 
- "NOT A NUMBER" and type is number
- if ```NaN```==```NaN``` or ```NaN```===```NaN``` are ```False```, 
- If we are check the NaN use ```isNaN()``` function, so it return  ```Ture```

[⬆ Back to Top](#Interview)

## this
```this``` keyword refers to the object it belongs to,

[⬆ Back to Top](#Interview)

## call(), apply(), bind()
- ```call()``` method invokes a function immediately, allowing you to specify the value of this and pass arguments individually.

```js
function_Name.call(thisArg, arg1,arg2,....)
```
###### Example
```js
function greet(city, country) {
  console.log(this.name + " from " + city + ", " + country);
}
const person = { name: "Alex" };
greet.call(person, "Paris", "France");
```

- ```apply()``` method is similar to call(), but it takes the function arguments as an array.

```js
func.apply(thisArg, [arg1,arg2,arg3,...])
```
###### Example
```js
var employee1 = { firstName: "John", lastName: "Rodson" };
var employee2 = { firstName: "Jimmy", lastName: "Baily" };

function invite(greeting1, greeting2) {
  console.log(
    greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2
  );
}

invite.apply(employee1, ["Hello", "How are you?"]); // Hello John Rodson, How are you?
invite.apply(employee2, ["Hello", "How are you?"]); // Hello Jimmy Baily, How are you?
```

- ```bind()``` method is used to fix the value of ```this``` for a function and return a ```new function```. It does not execute the function immediately.
```js
const newFunction = originalFunction.bind(thisArg, arg1, arg2, ...);
```
```js
function greet(city) {
  console.log(this.name + " from " + city);
}
const person = { name: "Alex" };
const greetAlex = greet.bind(person, "Paris"); // function are store in greetAlex

greetAlex(); // function all called
```
[⬆ Back to Top](#Interview)
## Rest parameter and Spread operatar
```Rest Parameter(...)```
- it provides an improved way to handling the parameter of a function ,used in function parameter.
```js
function a(...num){}
a(1,2,3,4)
```

```Spread Operatar```
- Spread the elements of an array or object.
- Used for copying, merging or passing value.
```js
let arr = [1,2,3];
let newarr = [...arr,4,5];
console.log(newarr); 
```

[⬆ Back to Top](#Interview)

## Event capturing, Event bubbling
```event capturing``` means the event starts from the root and goes downward to the target element. Top -> Bottom
```html
<div id="parent">
  Parent
  <button id="child">Child</button>
</div>
```
```js
document.getElementById("parent").addEventListener("click",() => {
  console.log("Parent clicked");
},true);

document.getElementById("child").addEventListener("click", () => {
  console.log("Child clicked");
});
```

```event bubbling``` means the event starts from the target element and goes upward to its parents. Bottom -> Top
```html
<div id="parent">
  Parent
  <button id="child">Child</button>
</div>
```
```js
document.getElementById("parent").addEventListener("click", () => {
  console.log("Parent clicked");
});

document.getElementById("child").addEventListener("click", () => {
  console.log("Child clicked");
});
```

[⬆ Back to Top](#Interview)
## event.preventdefault()
```event.preventDefault()``` is a JavaScript method used to stop the browser’s default behavior for an event.

**1. Prevent a form from submitting ->** 
By default, submitting a form reloads the page. 
➡️ He page does not reload, so you can handle the form use event.preventDefault().
**2. Stop a link from opening ->**
Clicking a link normally navigates to another page.
➡️ The browser doesn’t follow the link.

[⬆ Back to Top](#Interview)

## event loop
The event loop lets JavaScript handle async code by coordinating the call stack, task queues, and microtasks.
```text
+----------------+        +-----------------------------+
|   Call Stack   | -----> |   Web APIs                  |
|                |        | (setTimeout, fetch, events) |
+----------------+        +-----------------------------+
        ^                           |
        |                           v
+----------------+        +-----------------------------+
|   Event Loop   | <----- |   Task Queue (Macrotask) 2  |
+----------------+        +-----------------------------+
          ^              
          |               +-----------------------------+
          ----------------|   Microtask Queue        1   |
                          |   (Promises, queueMicrotask) |
                          +-----------------------------+


```
[⬆ Back to Top](#Interview)

## Block and Non-Block
```Non-Block``` 
  - Non-blocking code is code that does not stop execution while task is running. It does not block the main thread and allow others operation to continue.
  - The result of the task is handled later using --> callback, promises, asyn/await, or functions like setTimeout.
```js
  console.log("Start");
  setTimeout(()=>{console.log("Middle")},2000);
  console.log("End");
  // Output--> 1. Start 2. End 3. Middle
```


```Blocking```
  - Blocking code is code that stops the execution of the program until the current task is finished. The next line of code cannot run until the blocking operation completes.
  - It blocks the main thread and executes synchronously like that 

```js
  console.log("Start");
  function a(){
    console.log("Middle")
  } 
  a()
  console.log("End");
  // Output--> 1. Start 2. Middle 3. End
```
[⬆ Back to Top](#Interview)

## Synchronous and Asynchronous
```Synchronous```
  - Synchronous code executes line by line where each task must complete before next the start.
    
```Asynchronous```
  - Asynchronous code allows tasks to run independently, so the program does not wait for a task to finish before moving to next line like setTimeout

[⬆ Back to Top](#Interview)

## async/await
  ```async``` make a function return a promise
  
  ```await``` pauses the execution until the promise is resolved
  
```js
async function getData() {
  let response = await fetch("https://api.example.com/data");
  let data = await response.json();
  console.log(data);
}
```

why use async/await->
 - avoid long ```.then()``` chains
 - easier error handling using ```try...chatch```
   
<hr>

[⬆ Back to Top](#Interview)

## input output question
#### Question1.
```js
 [..."John Resig"];
```
#### Question2.
```js
const obj = {a:1};
obj.a = 2;
console.log(obj);
```
#### Question3.
```js
console.log("0"+1);
console.log(1+1+"0");
```
[⬆ Back to Top](#Interview)
