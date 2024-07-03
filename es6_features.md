# Es6 Features

## 1. let and const

`let` and `const` are block-scoped variables introduced in ES6. `let` allows you to declare variables that are limited in scope to the block, statement, or expression on which it is used. `const` is a read-only reference to a value that cannot be reassigned.

```javascript
let x = 10;
const y = 20;
x = 15; // Allowed
y = 25; // TypeError: Assignment to constant variable
```

## 2. Arrow Functions

Arrow functions are a more concise way of writing function expressions. They have a shorter syntax compared to regular functions and do not have their own `this`, `arguments`, `super`, or `new.target`.

```javascript
// Regular function
function add(a, b) {
  return a + b;
}

// Arrow function
const add = (a, b) => a + b;
```

The difference between arrow functions and regular functions is the handling of `this`. Arrow functions do not have their own `this` value, so they inherit the `this` value from the enclosing lexical context.(which means the value of `this` inside an arrow function is the same as the value of `this` outside the function).

## 3. Template Literals

Template literals are string literals allowing embedded expressions. They are enclosed by the backtick character (` `) instead of double or single quotes.

```javascript
let name = 'John';
let greeting = `Hello, ${name}!`;
console.log(greeting); // Hello, John!
```

## 4. Destructuring Assignment

Destructuring assignment allows you to extract values from arrays or objects and assign them to variables in a more concise way.

```javascript
// Array destructuring
const numbers = [1, 2, 3];
const [a, b, c] = numbers;
console.log(a, b, c); // 1 2 3

// Object destructuring
const person = { name: 'John', age: 30 };
const { name, age } = person;
console.log(name, age); // John 30
```

## 5. Rest and Spread Operators

The rest and spread operators were introduced in ES6. The rest operator (`...`) allows you to represent an indefinite number of arguments as an array. The spread operator (`...`) allows you to expand an array into individual elements.

```javascript
// Rest operator
function sum(...numbers) {
  return numbers.reduce((acc, val) => acc + val, 0);
}

console.log(sum(1, 2, 3)); // 6

// Spread operator
const numbers = [1, 2, 3];
console.log(...numbers, 4, 5); // 1 2 3 4 5
```

## 6. Default Parameters

Default parameters allow you to initialize a function with default values if no value or `undefined` is passed.

```javascript
function greet(name = 'John') {
  console.log(`Hello, ${name}!`);
}

greet(); // Hello, John!

greet('Alice'); // Hello, Alice!
```

## 7. Classes and Inheritance

ES6 introduced class syntax to create classes in JavaScript. Classes are a template for creating objects and can have constructors, methods, and inheritance.

```javascript
class Person {
  constructor(name) {
    this.name = name;
  }

  greet() {
    console.log(`Hello, my name is ${this.name}`);
  }
}

const john = new Person('John');
john.greet(); // Hello, my name is John
```

## 8. Promises and Async/Await

Promises are a way to handle asynchronous operations in JavaScript. They represent a value that may be available now, in the future, or never. Async/await is a modern way to work with asynchronous code in JavaScript.

```javascript
// Promises
function fetchData() {
  return fetch('https://api.example.com/data')
    .then(response => response.json())
    .catch(error => console.error(error));
}

fetchData()
  .then(data => console.log(data));
  .catch(error => console.error(error));

// async & await
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    return data;
  } catch (error) {
    console.error(error);
  }
}

await fetchData();
```

## 9. Modules

Modules are a way to organize code in separate files. ES6 introduced a standard for working with modules using the `import` and `export` keywords.

```javascript
// math.js
export const sum = (a, b) => a + b;
export const subtract = (a, b) => a - b;

// app.js
import { sum, subtract } from './math.js';

console.log(sum(5, 3)); // 8

console.log(subtract(5, 3)); // 2
```


Other than `import/export`, ES6 also have another way which is `modules.exports/require` which is used in Node.js.

```javascript
// math.js
module.exports = {
  sum: (a, b) => a + b,
  subtract: (a, b) => a - b
};

// app.js
const { sum, subtract } = require('./math.js');

console.log(sum(5, 3)); // 8

console.log(subtract(5, 3)); // 2
```




