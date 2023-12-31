<html>
<body>
<!--StartFragment--><google-sheets-html-origin><style type="text/css"><!--td {border: 1px solid #cccccc;}br {mso-data-placement:same-cell;}--></style>

Term | Description | Example
-- | -- | --
Array | A built-in JavaScript object that stores a collection of values. | const numbers = [1, 2, 3, 4, 5];
Arrow Function | A concise way to write functions in JavaScript using the => syntax. | const add = (a, b) => a + b;
Async/Await | A feature in JavaScript that simplifies working with asynchronous code using keywords async and await. | async function fetchData() { const response = await fetch('https://api.example.com/data'); const data = await response.json(); return data; }
Closures | A feature in JavaScript where a function remembers the scope in which it was created, even when executed elsewhere. | function outer() { const outerVar = 10; function inner() { console.log(outerVar); } return inner; } const closure = outer(); closure();
Callback | A function passed as an argument to another function to be executed later, often used for asynchronous operations. | function fetchData(callback) { // Fetch data from server callback(data); } fetchData(function(data) { console.log(data); });
Classes | A blueprint for creating objects in JavaScript, introduced in ECMAScript 2015 (ES6). | class Person { constructor(name) { this.name = name; } greet() { console.log(`Hello, my name is ${this.name}.`); } } const person = new Person('Alice'); person.greet();
DOM | Document Object Model, a programming interface for web documents that represents the structure of a webpage. | const element = document.getElementById('myElement');
ES6 (ECMAScript 2015) | The sixth version of the ECMAScript standard, introducing significant improvements and new features to JavaScript. | const name = 'Alice'; let greeting = `Hello, ${name}!`;
Event | An action or occurrence that can be detected and responded to in JavaScript, such as user interactions or system events. | button.addEventListener('click', () => { console.log('Button clicked!'); });
Function | A block of code that can be defined and invoked to perform a specific task in JavaScript. | function add(a, b) { return a + b; }
Hoisting | A behavior in JavaScript where variable and function declarations are moved to the top of their containing scope during compilation. | console.log(x); var x = 5;
JSON | JavaScript Object Notation, a lightweight data interchange format that is easy for humans to read and write, and easy for machines to parse and generate. | const person = { "name": "Alice", "age": 30 };
Promise | An object representing a value that might be available now, in the future, or never in JavaScript, often used for asynchronous operations. | const fetchData = () => new Promise((resolve, reject) => { fetch('https://api.example.com/data') .then(response => response.json()) .then(data => resolve(data)) .catch(error => reject(error)); });
Prototype | An object that serves as a base for other objects, allowing them to inherit properties and methods in JavaScript. | function Person(name) { this.name = name; } Person.prototype.greet = function() { console.log(`Hello, my name is ${this.name}.`); }; const person = new Person('Alice'); person.greet();
Scope | The context in which a variable or function is accessible in JavaScript, often determined by where it is defined. | function foo() { var x = 10; console.log(x); } foo(); console.log(x); // Error: x is not defined
Strict Mode | A mode in JavaScript that enforces stricter parsing and error handling, reducing some silent errors and making debugging easier. | use strict';
This | A keyword in JavaScript that refers to the current execution context, often used within functions and methods. | const person = { name: 'Alice', greet() { console.log(`Hello, my name is ${this.name}.`); } }; person.greet();
Type Coercion | The automatic conversion of values from one data type to another in JavaScript. | const sum = 5 + '10'; // '510'
typeof | An operator in JavaScript used to determine the data type of a value. | typeof 42; // 'number'
Undefined | A value in JavaScript that represents the absence of a value or uninitialized variables. | let x; console.log(x); // undefined
Var | A keyword used to declare variables in JavaScript, with function scope or global scope, often leading to unintended issues. | if (true) { var x = 5; } console.log(x); // 5
Let | A keyword introduced in ES6 to declare variables with block scope in JavaScript. | if (true) { let x = 5; } console.log(x); // Error: x is not defined
Const | A keyword introduced in ES6 to declare constants with block scope in JavaScript. | const PI = 3.14159;
Callback Hell | A situation in JavaScript where nested callbacks create complex and hard-to-read code, often encountered in asynchronous operations. | getData(function(data) { processData(data, function(result) { displayResult(result); }); });
Destructuring | A feature in JavaScript that allows you to unpack values from arrays or objects into distinct variables. | const numbers = [1, 2, 3]; const [a, b, c] = numbers;
Spread Operator | A syntax in JavaScript that allows you to spread elements of an iterable (like an array) into places where multiple elements are expected. | const array = [1, 2, 3]; const newArray = [...array, 4, 5];
Template Literal | A feature in JavaScript that allows you to create strings using backticks (`) and interpolate variables using ${}. | const name = 'Alice'; const greeting = `Hello, ${name}!`;
Rest Parameter | A feature in JavaScript that allows you to gather multiple function arguments into a single array parameter. | function sum(...numbers) { return numbers.reduce((acc, curr) => acc + curr, 0); }
Map | A built-in JavaScript object that stores key-value pairs, where keys can be of any type. | const myMap = new Map(); myMap.set('name', 'Alice'); console.log(myMap.get('name'));
Set | A built-in JavaScript object that stores unique values of any type, providing an easy way to remove duplicates from an array. | const mySet = new Set([1, 2, 2, 3, 4, 4, 5]); console.log([...mySet]);
For...of Loop | A loop introduced in ES6 that iterates over iterable objects (arrays, strings, maps, sets, etc.) in JavaScript. | const numbers = [1, 2, 3, 4, 5]; for (const num of numbers) { console.log(num); }
Promises chaining | A technique in JavaScript where multiple asynchronous operations are chained together using promises to achieve sequential execution. | fetchData() .then(data => processData(data)) .then(result => displayResult(result)) .catch(error => handleError(error));
Fetch API | A modern JavaScript API for making network requests, providing a simpler and more flexible alternative to XMLHttpRequest. | fetch('https://api.example.com/data') .then(response => response.json()) .then(data => console.log(data)) .catch(error => console.error(error));
Async Functions | A feature in JavaScript that simplifies writing asynchronous code by allowing the use of await inside functions marked with the async keyword. | async function fetchData() { const response = await fetch('https://api.example.com/data'); const data = await response.json(); return data; }
Generator Function | A special type of function in JavaScript that can pause and resume its execution, producing an iterator for generating a sequence of values. | function* generateNumbers() { yield 1; yield 2; yield 3; } const numbers = generateNumbers(); console.log(numbers.next().value);
IIFE (Immediately Invoked Function Expression) | A design pattern in JavaScript where a function is defined and executed immediately after its creation. | (function() { console.log('IIFE executed!'); })();
Module | A mechanism in JavaScript to encapsulate code and prevent global namespace pollution, often achieved using the export and import statements. | export function add(a, b) { return a + b; } import { add } from './math';
Web APIs | Interfaces provided by web browsers that allow JavaScript to interact with the browser environment, including DOM manipulation and network requests. | document.getElementById('myElement').addEventListener('click', () => { console.log('Element clicked!'); });

<!--EndFragment-->
</body>
</html>
