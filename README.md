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
74. [Event delegation]()
75. [Event Bubbling & Event Capturing (trikkling)]()
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
The runtime environment is what makes JavaScript code work, and in a browser it consists of the JS engine, a lot of Web APIs, a callback queue and the event loop.

The runtime environment in a browser is very different from that of Node.js. These differences are primarily at the implementation level, so most of the above concepts are still relevant like console, setTimeout etc. & localStorage, window object could be different.

## 57. JS Engine
A JS engine is a part of JS Runtime env which is a software component that executes JavaScript code.

The purpose of the JavaScript engine is to translate `source code` that developers write into machine code that allows a computer to perform specific tasks.

The first JavaScript engines were mere `interpreters`, but all relevant modern engines use `just-in-time` compilation for improved performance. JavaScript engines are typically developed by web browser vendors, and every major browser has one.

`Spidermonkey` was the first JS engine.

## 58. Just-in-time compilation vs Compiler vs Interpreter
All the three are programs that convert the Source Code (high-level language) into machine codes.

#### Compilation / Compiler:
1. Entire code is converted into machine code at once & written to a binary file that can be executed by browser or system.
2. Faster execution.
3. Debugging is slightly difficult.
4. C, C++, C#, etc are programming languages that are compiler-based.

#### Interpreter
1. It runs through the source code & executes it line by line or one statement at a time.
2. Slower execution.
3. Highly useful in debugging.
4. Python, Ruby, Perl, SNOBOL, MATLAB, etc are programming languages that are interpreter-based.

#### 3. JIT compilation
1. In JIT not all the code is converted into machine code first a part of the code that is necessary will be converted into machine code then if a method or functionality called is not in machine then that will be turned into machine code... it reduces burden on the CPU.
2. As the machine code will be generated on run time....the JIT compiler will produce machine code that is optimised for running machine's CPU architecture.
3. Because of the time it takes to load and compile bytecode, there is a startup delay in the initial execution of an application.

![image](https://user-images.githubusercontent.com/56342160/230608066-057f7d0d-3d65-48fc-97da-e7527f51894a.png)

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

```javascript
const createOrder = () => {
    setTimeout(() => {
        console.log('ID123')
    }, 4000)
}

createOrder(() => {
    console.log('placed') ---> callback function
})

// placed (after 4sec)
```

```javascript
const promise = new Promise((resolve, reject) {
  if(true) {
     resolve('success')
  } else {
     reject(new Error('failed'))
  }
})

promise.then(res => res)
       .catch(e => console.error(e))
```

## 67. Async/await
Just a most delegent way to handle promises.

The async and await keywords enable asynchronous, promise-based behavior to be written in a cleaner style, avoiding the need to explicitly configure `promise chains`.

```javascript
async function init() {
  await createPost() { console.log('created') }
  getPosts();
}
```
So here we are waiting for createPost to resolve before calling getPosts.

fetch:
```javascript
const res = await fetch(url);
const data = await res.json();
console.log(data)
```

## 68. Callback hell
The phenomenon which happens when we nest multiple callbacks within a function.

Callback hell generally refers to an ineffective way of writing code asynchronously. It is an anti-pattern that is often called the “pyramid of doom”.

```javascript
getArticles(20, (user) => {
  console.log("Fetch articles", user);
  getUserData(user.username, (name) => {
    console.log(name);
    getAddress(name, (item) => {
      console.log(item);
      // this goes on and on...
    }
})
```

## 69. Imports & dynamic imports
#### Static import:
1. Import entire module's content:
```javascript
import * as myModule from '../../';
```

2. Import single export:
```javascript
import { singleExport } from '../../';
```

3. Run the global scope of the module:
```javascript
import '/module/../...';
```

### Dynamic imports:
1. we can’t import conditionally or at run-time:
```javascript
if(...) {
  import ...; // Error, not allowed!
}

{
  import ...; // Error, we can't put import in any block
}
```

2. We can use async await to import.
```javascript
(async() => {
  if(something is true) {
    await import (modulePath)
  }
})()
```

## 70. Polyfills
A polyfill is a piece of code that implements the features that you expect the browser to support natively.

A polyfill is a piece of code (usually JavaScript on the Web) used to provide modern functionality on older browsers that do not natively support it.

In polyfilling, one write code to get a similar functionality as provided in other JS version.

## 71. Currying
Currying is an advanced technique of working with functions. It’s used not only in JavaScript, but in other languages as well.

It transforms a function with multiple arguments into a nested series of functions, each taking a single argument.  or,\
Currying is when you break down a function that takes `multiple arguments` into a series of functions that takes only one argument.

#### Uses:
1. Currying helps you avoid passing the same variable again and again.
2. It helps you create a higher order function.

We can curry our function in 2 ways:
1. Use binding function.
2. Using concept of clousers.

```javascript
let multiply = function(x, y) {
   return x * y;
}

let multiplyByTwo = multiply.bind(this, 2);
multiplyByTwo(5) // 10

let multiplyByThree = multiply.bind(this, 3);
multiplyByTwo(10) // 30
```

Using clousers:
```javascript
let multiply = function(x) {
  return function(y) {
    console.log(x * y)
  }
}

let multiplyByTwo = multiply(2)
multiplyByTwo(5) // 10
```

## 72. Coercion
Type coersion referes to the process of automatic or implicit conversion of values from one data type ro another.

Includes conversions from Number to String, String to Number, Boolean to Number etc. when different types of operators are applied.

1. When we use addition operator (+):
```javascript
const a = '5'
const b = 5

a + b => '5' + 5  =>  '55' (string) 
```
So when a string or non-string value is added to a string, it always converts non-string value to string implicitly (automatic).

2. Operators like [ - , * , / , % ]:
```javascript
'5' - 5 // 0
5 * '5' // 25
true / 2 // 0.5 => true coerced to 1
'true' * '5' // NaN
true / '2' // 0.5 => true becomes 1 & '2' becomes number.

3. Equality operator.
Used to compare the values irrespective of their type.

So this is done by Coercing. This is done by coercing a non-number data type to a Number.
```javascript
'10' == 10 // true
true == 1 // true
true == 'true' // false ==> string 'true' becomes NaN.
```

## 73. Event delegation
Event delegation is basically a `design pattern` to handle events effectively.

The idea is that if we have a lot of elements handled in a similar way, then instead of assigning a handler to each of them – we put a single handler on their common ancestor.

In the handler we get event.target to see where the event actually happened and handle it.


## 74. Event Bubbling and Event Capturing (trikkling)
`Bubbling` is a type of propogation where the event first triggers on the innermost target element & then successively triggers on the ancestors of the target element in the same nesting hiererchy till it reaches the outermost DOM element or document object.

```javascript
elem.addEventListener("click", e => alert(`Bubbling: ${elem.tagName}`));
```

```javascript
to stop bubbling, use event.stopPropogation()
```

`Event capturing` starts from the top element to the target element.

We need to pass true to enable the capturing.
```javascript
 elem.addEventListener("click", e => fn(), true);
```

## 75. Debouncing and Throtling
As developers, we follow various techniques to enhance application performance and provide a better user experience. For example, debouncing and throttling are two simple, yet powerful techniques we can use in JavaScript applications to improve performance.

`Debouncing and throttling` are two techniques that limit when and how often a function is called or simply, limiting the function calls.

In `debouncing`, we call the attached function when there is a certain time difference b/w 2 events like keystrokes, mouseclicks etc.

<img src="https://raw.githubusercontent.com/neeleshio/stock-images/master/Group%202.png"/>

```javascript
function debounce(callback, delay = 1000) {
  let time;

  return (...args) => {
    clearTimeout(time);
    time = setTimeout(() => {
      callback(...args);
    }, delay);
  };
}
```

In `throttling`, no matter how many times the user fires the event, the attached function will be executed only once in a given time interval.

<img src="https://github.com/neeleshio/stock-images/blob/master/Group%204.png"/>

```javascript
function throttle(callback, delay = 1000) {
  let shouldWait = false;

  return (...args) => {
    if (shouldWait) return;

    callback(...args);
    shouldWait = true;
    setTimeout(() => {
      shouldWait = false;
    }, delay);
  };
}
```

## 76. Objects
All javascript values except primitives are Objects.

#### Creating objects:
1. By object literal
```javascript
const person = { }  --> this creates a person object
```

2. With new keyword
```javascript
const person = new Object() 
```

3. Object.create()
```javascript
const person = Object.create(null) // object with no properties
```

4. Object constructor
```javascript
function person(id, name){  
  this.id = id;  
  this.name = name;
}

const person1 = new person(1, 'neelesh') // { id: 1, name: 'neelesh' }
```

#### Other object methods:

1. Object.assign()
The Object.assign() copies all enumerable and own properties from the source objects to the target object. It returns the target object.

```javascript
let widget = {
    color: 'red'
};

let clonedWidget = Object.assign({}, widget) // { color: 'red' } --> new object
```

2. Object.entries()
This method returns an array with arrays of the key, value pairs.

3. Object.keys()
This method returns an array of a given object's own property names.

4. Object.values()
This method returns an array of values.

## 77. Rest and Spread operators
`Spread` operator takes in an iterable or an array & expands/spreads it into indivisual elements.

```javascript
const arr = [1, 2, 3, 4]

console.log(...arr) // 1 2 3 4
```
The spread operator is commonly used to make shallow copies of JS object (Objects & Arrays).

`Rest` operator allows us to call a function with any number of arguments & then access those excess arguments as an array. or,\

When the spread operator is used as a parameter, it is known as the rest parameter. This allows a funtion to accept an indefinite number of arguments as an array.

```javascript
function calculate(...args){
    let sum = 0;
    for(let i of input){
        sum+=i;
    }
    return sum;
}

calculate(1,2,3,4,5); //15  
```

## 78. Destructuring
Destructuring Assignment is a JavaScript expression that allows to unpack values from arrays, or properties from objects, into distinct variables. Destructuring makes it easy to extract only what is needed.

```javascript
// objects
const user = {
  name: "John",
  age: 30
};

const { name, age } = user
name // 'John'
```

```javascript
// array
const colors = ['#ffffff', '#000000', 'e0e0e0'];

const [white, black, grey] = colors
white // '#ffffff'
```

## 79. Shallow copy and Deep copy
`Shallow copy` doesn't creates a new copy but it just oints to the address of the original JS object, meaning its just the reference.

```javascript
const employee = {
  id: '1234',
  name: 'Jack'
}

const employeeCopy = employee // shallow copy

employeeCopy.id = '9999'

console.log(employee) // { id: '9999', name: 'Jack' }
```

`Deep copy` creates a new copy of the JS object, meaning it creates/allocates the memory to the copy. So both the objects are independent to each other.

#### Methods for deep copy:
1. Use spread operator:

```javascript
const person = {
  name: 'Neelesh',
  age: 25
}

let copiedPerson = { ...person } // deep copy
```

2. Object.assign:

```javascript
const person = {
  name: 'Neelesh',
  age: 25
}

let copiedPerson = Object.assign({}, person)
```

But if we have a nested object them assign & spread acts same as shallow copy, so use below JSON method for nested objects.

```javascript
const person = {
  name: 'Neelesh',
  age: 25,
  place: {
    city: 'CKM',
    state: 'KA',
    country: 'IN'
  }
}

let deepClone = JSON.parse(JSON.stringify(person))
```

## 80. Array methods and their Big(O)
1. **Push & Pop** (end): Adding & Removing elements at the `end` of the array.\
BigO: O(1) 

2. **Shift & Unshift** (start): Adding & Removing elements at the `start` of the array. It has to reindex the array.\
BigO: O(n)

3. **Splice**: method to add, remove or replace array elements.\
BigO: O(1) \
`Splice` overwrites/mutates the original array.

```javascript
<--- Add --->
const fruits = ['apple', 'orange', 'jackfruit']
//arr.splice(positionIndex, 0, 'element') ===> 0 is to add elements
fruits.splice(0, 0, 'onion') // ['onion', 'apple', 'orange', 'jackfruit']

<--- Remove --->
const fruits = ['apple', 'orange', 'jackfruit']
//arr.splice(fromIndex, noOfItems)
fruits.splice(0, 1) // ['orange', 'jackfruit']

<--- Replace --->
const fruits = ['apple', 'orange', 'jackfruit']
//arr.splice(positionIndex, noOfItemsToDlt, 'element') ===> number of elements to delete needs not to be the same as the number of elements to insert.
fruits.splice(0, 0, 'onion') // ['onion', 'apple', 'orange', 'jackfruit']
```

4. **Slice**: method to remove array elements.\
BigO: O(1) \
`Slice` doesn't mutates the original array, it creates a new array.

5. **indexOf**: \
BigO: O(n) \
returns the position of the first occurence of a specified value in an array or string.

```javascript
const arr = ['one', 'two', 'three']
arr.indexOf('three') // 2
arr.indexOf('four') // -1
```

## 81. for in vs for of loops
`for..of` allows you to go through the elements of an iterable one at a time. It gives you the actual values directly, without concerning yourself with properties or keys. And doesn't work on Objects but only on Arrays.

```javascript
const arr = [5, 6, 7, 8]

for(const val of arr) {
  console.log(val) // 5, 6, 7, 8
}
```

`for...in` is used to examine the properties of an object, including those inherited from its parent object. It provides the property keys, allowing you to access the corresponding values if necessary.

```javascript
const arr = [5, 6, 7, 8]

for(const key in arr) {
  console.log(key) // 0, 1, 2, 3
}

const obj = {
  name: 'Neel',
  age: 25,
  city: 'CKM'
}

for(const key in obj) {
  console.log(key) // 'name', 'age', 'city'
  console.log(obj[key]) // 'Neel', 25, 'CKM'
}
```

## 82. map() vs forEach()
#### forEach():
1. Used to loop through the elements of an array.
2. Returns “undefined“.
3. forEach is faster than map and filter.
4. forEach() throws away return values and always returns undefined.
5. forEach() will allow a callback function to mutate the current array.
6. forEach() may be preferable when you’re not trying to change the data in your array, but instead want to just do something with it — like saving it to a database or logging it out:
7. Not recommended inside JSX becoz it doesn't return anything.

```javascript
const arr = [1, 2, 3, 4, 5]
arr.forEach(x => x * x) // undefined
```

#### map():
1. Used to transform the elements of an array.
2. Returns an entirely new array.
3. Slower than forEach.
4. map() allocates memory and stores return values.
5. map() will instead return a new array.
6. map() might be preferable when changing or altering data. Not only is it faster but it returns a new Array. This means we can do cool things like chaining on other methods ( map(), filter(), reduce(), etc.).
7. Recommended inside JSX.

```javascript
const arr = [1, 2, 3, 4, 5]
arr.map(x => x * x) // [1, 4, 9, 16, 25]
```

## 83. filter() vs reduce()
#### filter() 
filter outs the unwanted elements.

```javascript
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

function checkEven(number) {
  if (number % 2 == 0) return true;
  return false;
}

numbers.filter(checkEven) // [ 2, 4, 6, 8, 10 ]
```

#### reduce() 
reduce() method is used to reduce the array to a single value.

```javascript
arr.reduce((previousValue, currentValue) => {
    return previousValue + currentValue;
}, initialValue);
```

If we omit the initialvalue, then by default it will consider the first element of the array.

```javascript
let shoppingCart = [
  { price: 500 },
  { price: 10 },
  { price: 20 },
];

shoppingCart.reduce((previousValue, currentValue) => {
   return previousValue + currentValue['price']
}, 0)

// 530
```

## 84. Alphabetical sort vs Numeric sort
The sort() sorts the elements of an array. The sort() overwrites the original array.

The sort() sorts the elements as `strings` in alphabetical and ascending order.

```javascript
const numArr = [5, 2, 41, 87, 10, 13, 61]
numArr.sort() // [10, 11, 13, 14, 17,  2,  5]

const stringArr = ['cat', 'plane', 'swim', 'ant']
stringArr.sort() // ['ant', 'cat', 'plane', 'swim']
```

To sort numerically:
```javascript
const points = [40, 100, 1, 5, 25, 10];

points.sort((a, b) => {
  return a - b           --> ascending order
});
// [1, 5, 10, 25, 40, 100]

points.sort((a, b) => {
  return b - a           --> decending order
});
// [100, 40, 25, 10, 5, 1]
```

## 85. Map vs Objects vs Sets

| Object                         |    Map                        |             Set                |
|--------------------------------|-------------------------------|--------------------------------|
| 1. In Object, the data-type of the key-field is restricted to integer, strings, and symbols. | 1. In Map, the key-field can be of any data-type (integer, an array, even an object!) | 1. A Set is a special type collection – “set of values” (without keys), where each value may occur only once |
| 2. In objects, order of elements are not always guaranteed. | 2. In the Map, the original order of elements is preserved. | 2. In Set, the original order of elements is preserved.|
| 3. Object is not directly iterable, we must convert them to an array to iterate using keys(), entries(), values() or for..in loop | 3. Map is directly iterable using for..of loop or forEach | 3. Same as Map |
| 4. Object has its own methods | 4. Map and Set both have similar methods; these include .has(), .get(), .delete(), and .size(). | 4. Map and Set both have similar methods; these include .has(), .get(), .delete(), and .size(). |

```javascript
// Object
const obj = new Object()
obj.name = 'neelesh'
```
```javascript
// Map
const map = new Map()
map.set('name', 'neelesh')
```
```javascript
// Set
const set = new Set()
set.add('neelesh')
```

## 86. WeakMap vs WeakSets
WeakMap is Map-like collection that allows only objects as keys and removes them together with associated value once they become inaccessible by other means.

```javascript
let weakMap = new WeakMap();

let obj = {};

weakMap.set(obj, "ok"); // works fine (object key)

// can't use a string as the key
weakMap.set("test", "Whoops"); // Error, because "test" is not an object
```

WeakSet is Set-like collection that stores only objects and removes them once they become inaccessible by other means.
```javascript
let visitedSet = new WeakSet();

let john = { name: "John" };
let pete = { name: "Pete" };
let mary = { name: "Mary" };

visitedSet.add(john); // John visited us
visitedSet.add(pete); // Then Pete
visitedSet.add(mary); // John again

john = null;

console.log(visitedSet.has(john)); // false
// visitedSet will be cleaned automatically
```

## 87. Memoization
Memoization is a technique for speeding up applications by caching the results of expensive function calls and returning them when the same inputs are used again.

**Memoized function should be a pure function.**
We don't have to memoize the HTTP calls as the browser itself will cache that.

## 88. Object freeze vs seal vs preventExtension
These methods used to make objects immutable.

#### Object.seal():
It prevents add/remove properties.

```javascript
const fruit = {
  name: 'apple',
  properties: {
    color: 'red'
  }
}

Object.seal(fruit)
Object.isSealed(fruit)

* Add/Remove:
fruit.fresh = true // won't work
delete fruit.name // won't work

delete fruit.properties.color // works becoz nested prop
fruit.properties.fresh = true // works becoz nested prop

* Modify:
fruit.name = 'orange' // works
```

#### Object.freeze():
1. This also prevents add/remove properties.
2. It also prevents modifying any existing props.

```javascript
const profile = {
  name: 'Neelesh',
  address: {
    city: 'CKM'
  }
}

Object.freeze(profile)
Object.isFrozen(profile) // true

* Modfify a props:
profile.name = 'shetty' (won't work)

profile.address.city = 'Banglore' // works becoz it's nested props.

* Add/Remove:
profile.age = 24 // won't work
delete profile.name // won't work
```

#### Object.preventExtensions
This only prevents adding new props.

```javascript
profile.age = 24 // won't work
profile.name = 'something' // works
delete profile.name // works
```

## 89. Numeric Seperator
The numeric separator allows you to create a visual separation between groups of digits by using underscores (_) as separators.

```javascript
// without numeric seperator
const budget = 1000000000;

// with numeric seperator
const budget = 1_000_000_000;

let amount = 120_201_123.05; // 120201123.05
let expense = 123_450; // 123450
let fee = 12345_00; // 1234500

const max = 9_223_372_036_854_775_807n; // BigInt
```

## 90. Fetch vs Axios

|                   Axios                             |                        Fetch                            |
|-----------------------------------------------------|---------------------------------------------------------|
| 1. Axios is a stand-alone third party package that can be easily installed.  | 1. Fetch is built into most modern browsers; no installation is required.
| 2. Axios enjoys built-in XSRF protection. | 2. Fetch does not.
| 3. Axios performs automatic transforms of JSON data. | 3. We have to manually transform JSON data using response.json().
| 4. Axios allows cancelling request and request timeout. | 4. Fetch does not.
| 5. Axios has the ability to intercept HTTP requests. | 5. Fetch does not.
| 6. Axios has wide browser support. | 6. Fetch has less support than axios.


## 91. Browser storages
#### 1. localStorage API:
1. Unlike with cookies, we don't need to send the info on every HTTP request back & forth.
2. The data is stored across sessions, never shared with the server.
3. Storage is limited to ~5MB.
4. Can save only UTF-16 strings, we must make sure to convert data to strings before saving it into localStorage.
5. Data can only be destroyed by manually clearing the storage or with javascript code.
6. We can encrypt data for more security.
7. localStorage is synchronous, meaning each operation called would only execute one after the other.

```javascript
localStorage.setItem('key', 'value')
localStorage.getItem('key')
localStorage.removeItem('key')
localStorage.clear() // clears all key values.
```

#### 2. sessionStorage API:
Same as localStoarge, but the data will get deleted once we close the tab.

#### 3. Cookies:
1. They are small text files that are placed on users computer by a website.
2. They hold a very small data at a max. capacity of 4kb.
3. They can only store strings.
4. They mostly store login info, page visits etc.
5. It’s the only storage that is shared with the server.
6. We have to keep our cookies small to maintain a decent request size.

**Session cookies**: \
1. Do not have expiry data, they are stored as long as browser tab is open.
2. This type of cookies mostly common for banking website.

**Persistent cookies**: \
1. Have an expiry date.
2. Stored in user's disk until the expiration date.

#### 4. IndexedDB API:
1. IndexedDB is a modern storage solution in the browser.
2. It can store a significant amount of structured data — even files, and blobs.
3. Like every database, IndexedDB indexes the data for running queries efficiently. 
4. It’s more complex to use IndexedDB. We have to create a database, tables, and use transactions. So, localForge package is recomended.

## 92. CacheStorage
Provides a master directory of all the named caches that can be accessed by a ServiceWorker or other type of worker or window scope (you're not limited to only using it with service workers).

The Cache Storage API opens up a whole new range of possibilities, by giving developers complete control over the contents of the cache.

## 93. Iterators and Generators
### Iterators:
The ‘for...of loop’ can create a loop over any iterable object (Arrays, Set, Maps, Strings).

Plain objects are not iterable and hence the 'for...of' uses the Symbol.iterator.

The Symbol.iterator is a special-purpose symbol made especially for accessing an object's internal iterator. So, you could use it to retrieve a function that iterates over an array object.

```javascript
const arr = [1, 2, 3, 4, 5]
const iterators = arr[Symbol.iterator]()

iterators.next() // {value: 1, done: false}
iterators.next() // {value: 2, done: false}
.
.
iterators.next() // {value: undefined, done: true}
```

1. An iterator is an object that can access one item at a time from a collection while keeping track of its current position.
2. It just requires that you have a method called next() to move to the next item to be a valid iterator
3. The result of next() is always an object with two properties – value & done.

### Generators:
Generators are a special type of function in JavaScript that can pause and resume state. A Generator function returns an iterator, which can be used to stop the function in the middle, do something, and then resume it whenever. 

Generator functions/yield and Async functions/await can both be used to write asynchronous code that 'waits'.

#### Advantages of Generators:
1. Lazy Evaluation: This is an evaluation model that delays the evaluation of an expression until its value is needed.
2. Memory Efficient: A direct outcome of Lazy Evaluation is that generators are memory efficient.

```javascript
function* gen() {
  yield 1;
  yield 2;
  yield 3;
}

const g = gen();

g.next(); // { value: 1, done: false }
g.next(); // { value: 2, done: false }
g.return(); // { value: undefined, done: true } // return keyword will cause the loop to exit on the iteration.
```

#### Applications:
Quite a few libraries use generators, such as Mobx-State-Tree or Redux-Saga etc.

#### Unique ID generator:
```javascript
function* idGenerator() {
  let i = 0;
  while (true) {
    yield i++;
  }
}

const ids = idGenerator();

console.log(ids.next().value); // 0
console.log(ids.next().value); // 1
console.log(ids.next().value); // 2
.
.
console.log(ids.next().value); // n
```

## 94. XSS attack (cross site scripting)
Cross-site Scripting (XSS) is a client-side code injection attack. The attacker aims to execute malicious scripts in a web browser of the victim by including malicious code in a legitimate web page or web application.

#### Characteristics:
1. Vulnerable vehicles that are commonly used for Cross-site Scripting attacks are forums, message boards, and web pages that allow comments.
2. A web page or web application is vulnerable to XSS if it uses unsanitized user input in the output that it generates.
3. Cross-site Scripting may also be used to deface a website instead of targeting the user. The attacker can use injected scripts to change the content of the website or even redirect the browser to another web page, for example, one that contains malicious code.
4. Malicious JavaScript has access to all the objects that the rest of the web page has access to. This includes access to the user’s cookies. Cookies are often used to store session tokens. If an attacker can obtain a user’s session cookie, they can impersonate that user, perform actions on behalf of the user, and gain access to the user’s sensitive data.

#### How to prevent
1. To keep yourself safe from XSS, you must `sanitize` your input. Your application code should never output data received as input directly to the browser without checking it for malicious code.
2. Use an appropriate `escaping/encoding technique` depending on where user input is to be used: HTML escape, JavaScript escape, CSS escape, URL escape, etc. Use existing libraries for escaping, don’t write your own unless absolutely necessary.
3. Set the `HttpOnly flag` for cookies. If you do, such cookies will not be accessible via client-side JavaScript.
4. Use a `Content Security Policy` (CSP). CSP is an HTTP response header that lets you declare the dynamic resources that are allowed to load depending on the request source.

## 95. SQL Injection
SQL injection is a code injection technique that might destroy your database. SQL injection is the placement of malicious code in SQL statements, via web page input.

It generally allows an attacker to view data that they are not normally able to retrieve. This might include data belonging to other users, or any other data that the application itself is able to access.

A successful SQL injection attack can result in unauthorized access to sensitive data, such as passwords, credit card details, or personal user information. In some cases, an attacker can obtain a persistent backdoor into an organization's systems, leading to a long-term compromise that can go unnoticed for an extended period.

SQL also lets you alter data in a database and add new data. For example, in a financial application, an attacker could use SQL Injection to alter balances, void transactions, or transfer money to their account.

#### How to prevent:
1. The only sure way to prevent SQL Injection attacks is input validation and parametrized queries including prepared statements. 
2. The application code should never use the input directly. The developer must sanitize all input, not only just web form inputs such as login forms. 
3. They must remove potential malicious code elements such as single quotes. 
4. It is also a good idea to turn off the visibility of database errors on your production sites. Database errors can be used with SQL Injection to gain information about your database.

## 96. CSRF attack
Cross-Site Request Forgery (CSRF) is an attack that forces authenticated users to submit a request to a Web application against which they are currently authenticated.

A CSRF attack targets Web applications failing to differentiate between valid requests and forged requests controlled by attacker. There are many ways for an attacker to try and exploit the CSRF vulnerability.

#### How to prevent:
1. Use anti-CSRF tokens: Anti-CSRF tokens are considered the most effective method of protecting against CSRF.
2. Use SameSite cookies: Set the SameSite attribute of your cookies to Strict. If this would break your web application functionality, set the SameSite attribute to Lax but never to None. Not all browsers support SameSite cookies yet, but most do. Use this attribute as additional protection along with anti-CSRF tokens.

## 97. ClickJacking
Clickjacking is an attack that fools users into thinking they are clicking on one thing when they are actually clicking on another.

Clickjacking is an attack that tricks a user into clicking a webpage element which is invisible or disguised as another element. This can cause users to unwittingly download malware, visit malicious web pages, provide credentials or sensitive information, transfer money, or purchase products online.

#### How to prevent:
1. Preventing the browser from loading the page in frame using the X-Frame-Options or Content Security Policy (frame-ancestors) HTTP headers.
2. Preventing session cookies from being included when the page is loaded in a frame using the SameSite cookie attribute.
3. Implementing JavaScript code in the page to attempt to prevent it being loaded in a frame (known as a "frame-buster").
4. The frame-ancestors directive can be used in a Content-Security-Policy HTTP response header to indicate whether or not a browser should be allowed to render a page in a <frame> or <iframe>. Sites can use this to avoid Clickjacking attacks by ensuring that their content is not embedded into other sites.

Note that these mechanisms are all independent of each other, and where possible more than one of them should be implemented in order to provide defense in depth.


## 98. CSP (Content Security Policy)
Content Security Policy (CSP) is an added layer of security that helps to detect and mitigate certain types of attacks, including Cross-Site Scripting (XSS) and data injection attacks. 

These attacks are used for everything from data theft, to site defacement, to malware distribution.

To enable CSP, a response needs to include an HTTP response header called Content-Security-Policy with a value containing the policy. The policy itself consists of one or more directives, separated by semicolons.

## 99. Service Workers
A service worker is a script that runs independently in the browser background. On the user side, it can intercept its network requests and decide what to load (fetch).

#### Characteristics:
1. Service workers mainly serve features like background sync, push notifications and they are commonly used for ’offline first’ applications.
2. The service worker lifecycle is completely separate from the web page. It’s a programmable network proxy, which is terminated when it’s not used and restarted when it’s next needed.
3. Service workers require the use of HTTPS connection. Before deployment, the workers does work under the localhost server.
4. A service worker is run in a worker context: it therefore has no DOM access, and runs on a different thread to the main JavaScript that powers your app.
5. It is non-blocking. It is designed to be fully async; as a consequence, APIs such as synchronous XHR and Web Storage can't be used inside a service worker.
6. Service workers make heavy use of promises, as generally they will wait for responses to come through, after which they will respond with a success or failure action.

A service worker is first registered using the `ServiceWorkerContainer.register()` method.

## 100. PWAs
Progressive Web Apps (PWAs) are applications that you build by using web technologies, and that can be installed and can run on all devices, from one codebase.

PWAs provide native-like experiences to your users on supporting devices.

PWAs uses service workers, manifests, and other web-platform features in combination with progressive enhancement to give users an experience on par with native apps.

#### Benefits of PWAs:
1. They function just like normal Native Apps.
2. They're built with common web technologies.
3. They work offline unlike other sites.
4. They are discoverable via search engine.
5. The updates are independent, you don't need to visit the play store for an update.
6. They are responsive and work with many different screen sizes.
7. They are easily installable.
8. Low maintenance cost.
