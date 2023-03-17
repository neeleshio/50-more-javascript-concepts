<div align="center">
  <h1>50 More Javascript Concepts</h1>
  
  <p><b>JavaScript</b> is a lightweight, Just-in-time compiled, Synchronous Single threaded, Loosly typed programming language.</p>
  
  <img src="https://miro.medium.com/max/3200/1*i8-u-V8LTTbQwTeUwLI_BQ.gif" alt="JS-banner">
</div>

<br>

# Let's go :)

51. [Event loop](#51-Event-loop)
52. [Web APIs](#52-Web-APIs)
53. [Callback Queue](#53-Callback-Queue)
54. [Microtask Queue](#54-Microtask-Queue)
55. [Starvation of callbacks](#55-Starvation-of-callbacks)
56. [JavaScript Runtime Environment](#56-JavaScript-Runtime-Environment)
57. [JS Engine](#57-JS-Engine)
58. [Just-in-time compilation](#58-Just-in-time-compilation)
59. [Concurrency model](#59-Concurrency-model)
60. [Functional Programing](#60-Functional-Programing)
61. [DRY](#61-DRY)
62. [Higher order functions](#62-Higher-order-functions)
63. [Prototype chain](#63-Prototype-chain)
64. [Uses of prototype]()
65. [Call, Apply, Bind]()
66. [Promises]()
68. [Async/await]()
69. [Callback hell]()
70. [Imports & dynamic imports]()
71. [Polyfills]()
72. [Currying]()
73. [Coercion]()
74. [Event Bubbling & Event Capturing (trikkling)]()
75. [Event delegation]()
76. [Debouncing & Throtling]()
77. [Objects]()
78. [Rest & spread operators]()
79. [Destructuring]()
80. [Deep copy & shallow copy]()
81. [Array methods & their Big(O)]()
82. [for in vs for of loops]()
83. [map() vs forEach()]()
84. [map() vs reduce() vs filter()]()
85. [Sort vs Numeric sort]()
86. [Map vs Objects vs Sets]()
87. [WeakMap vs WeakSets]()
88. [Memoization]()
89. [Object freeze vs seal vs preventExtension]()
90. [Numeric Seperator]()
91. [DOM APIs]()
92. [Fetch vs Axios]()
93. [Mutation Observer]()
94. [Browser storages]()
95. [Cookies vs Localstorage]()
96. [SessionStorage & CacheStorage]()
97. [Iterators & Generators]()
98. [XSS attack (cross site scripting)]()
99. [CSRF attack]()
100. [ClickJacking]()
101. [CSP (content security policy)]()
102. [Service workers]()

## 51. Event loop
The event loop is a constantly running process that monitors both the `callback queue` and the `call stack`. It is responsible for both pushing the callbacks to callback queue & pulling back the callbacks to the call stack once call stack is free.

If the call stack is not empty, the event loop waits until it is empty and places the next function from the callback queue to the call stack.

#### In case of event listeners:
It first registers the event listeners & attaches the click event & callback function will be in the web APIs. when we click that button the cb pushed first into callback queue & then into call stack.

## 52. Web APIs
When writing code for the Web, there are a large number of Web APIs available.

Some examples:
1. DOM
2. Fetch
3. setTimeout
4. Console
5. Intersection Observer
6. Service Workers
7. Geolocation etc.

## 53. Callback Queue
This is where your asynchronous code gets pushed to, and waits for the execution.

It follows the queue(FIFO) data structure to maintain the correct sequence in which all operations should be sent for execution.

## 54. Microtask Queue
Microtask is also a queue but have more `priority` than callback queue.

All callback functions those comes through promises & Mutation observers are `Microtasks`.

```javascript
console.log('start')
setTimeout(() => {
  console.log('CB setTimeout')
}, 1000)
fetch('https://api.netflix.com').then(() => {
  console.log('CB Fetch')
})
console.log('end')

// start
// end
// CB Fetch       ---> high priority microtask
// CB setTimeout  ---> second priority async task
```

## 55. Starvation of callbacks
When CBs inside microtask queue creates another microtask & if this goes on creating more microtasks then the task waiting in the callback queue doen't get a chance to get executed, this is Starvation of callbacks.

## 56. JavaScript Runtime Environment


## 57. JS Engine


## 58. Just-in-time compilation


## 59. Concurrency model
Concurrency means the fact of two or more events or circumstances happening or existing at the same time.

Javscript is a `single threaded` language so how can we achieve concurrency then? It can be achieved with the help of `event loop`. JavaScript has a concurrency model based on an "event loop".

Event loop is responsible for executing the code, collecting and processing events, and executing queued sub-tasks.

## 60. Functional Programing
One of the most famous programming paradigms is `object-oriented programming`.

Functional programming is a `paradigm` of building computer programs using expressions and functions without mutating state and data.

1. Don’t mutate data.
2. Use pure functions: fixed output for fixed inputs, and no side effects.
3. Use expressions and declarations.
4. Reusability through Higher order functions(HOC).

By respecting these restrictions, functional programming aims to write code that is clearer to understand and more bug resistant.

## 61. DRY
There’s a principle in programming called DRY, or Don’t Repeat Yourself.

DRY code is easy to change, because you only have to make any change in one place.

```javascript
 let chips = ['corn', 'pita', 'potato', 'tortilla'];

  // non DRY code
  console.log(chips[0]);
  console.log(chips[1]);
  console.log(chips[2]);

  // DRY code
  for (let i = 0; i < chips.length; i++) {
    console.log(chips[i]);
  }
```

## 62. Higher order functions
A “higher-order function” is a function that accepts functions as parameters and/or returns a function.

An example is the map method. The `map()` method creates a new array by calling the callback function provided as an argument on every element in the input array. The `map()` method will take every returned value from the callback function and creates a new array using those values.

## 63. Prototype chain
When it comes to `inheritance`, JavaScript only has one construct: objects.

Each object has a private property which holds a link to another object called its prototype. That prototype object has a prototype of its own, and so on until an object is reached with `null` as its prototype. or,

Every object in JavaScript has a built-in property, which is called its prototype. The prototype is itself an object, so the prototype will have its own prototype, making what's called a prototype chain. The chain ends when we reach a prototype that has null for its own prototype.

By definition, `null` has no prototype, and acts as the final link in this prototype chain.

Characteristics:
1. All objects in JavaScript have a prototype. An object’s prototype is also considered to be an object.
2. All the prototypes are linked to together, so we can call JS a OLOO - Object linked to other objects.
3. Most grandparent is the Capital O Object.
4. Prototype is always attached to the functions, but dunder proto attaches to the objects.

As we know we can create object with the function. If we use new keyword then itwill be an object.
```javascript
let myFunc = function(){}  // function
let myObj = new myFunc  // object

console.log(myObj) // myObj{}  
```

## 64. Uses of prototype.
1. Reduces memory usage.
2. Resuability.

```javascript
String.prototype.isMe = 'Neelesh'
// Now every string will have access to isMe method.
console.log(isMe) // 'Neelesh'

let x = 'abc';
console.log(x.isMe) // 'Neelesh' --> becoz x is a string.
```

## 65. Call, Apply, Bind
All the 3 are predefined methods/functions used to set the `this` keyword independent of how a function is called.

With these, an object can use a method belonging to another object.

```javascript
let obj = {
  name: 'Neelesh'
}

function printName(city) {
  console.log(this.name + ' ' + 'from' + ' ' + city)
}

printName() // undefined

// with call
printName.call(obj, 'ckm') // 'Neelesh from ckm'
```
So, what happens is, by default the context of 'this' is pointing to the lexical environment of the printName function i.e, the global space. So to change that we use call method with a first argument as the object which we need. Behind the scene it just puts the printName function inside the passed object, now 'this' points to the object itself.

`Apply` is also similar to the call function. The only difference is that in apply you can pass an array as an argument list.

```javascript
let obj = {
  name: 'Neelesh'
}

function printName(city, college) {
  console.log(this.name + ' ' + 'from' + ' ' + city + ',' + college)
}

// with call
printName.apply(obj, ['ckm', 'ait']) // 'Neelesh from ckm, ait'
```

`Bind` is a method/function that helps you create another function that you can execute later with the new context of `this` that is provided.

## 66. Promises
The Promise object represents the eventual completion (or failure) of an asynchronous operation and its resulting value.

3 stages of a Promise:

pending: initial state, neither fulfilled nor rejected.
fulfilled: meaning that the operation was completed successfully.
rejected: meaning that the operation failed.

