# Core Concepts

## 'this' keyword

'this' keyword refers to the object that is executing the current function.

if a function is called as a method of an object, 'this' refers to the object.

```javascript
const person = {
  name: 'John',
  greet() {
    console.log(`Hello, my name is ${this.name}`);
  }
};

person.greet(); // Hello, my name is John
```

If a function is called as a standalone function, 'this' refers to the global object.(window in the browser, global in Node.js)

```javascript
function greet() {
  console.log(`Hello, my name is ${this.name}`);
}

greet(); // Hello, my name is undefined
```

To avoid this behavior, you can use the 'bind' method to explicitly set the value of 'this'.

```javascript
function greet() {
  console.log(`Hello, my name is ${this.name}`);
}

const person = {
  name: 'John'
};

const greetPerson = greet.bind(person);
greetPerson(); // Hello, my name is John
```


## Prototypes and Prototypal Inheritance


People always says that everything in JavaScript is an object. and this has a lot to do with prototypes.

### Prototype

Every JavaScript object has a prototype. A prototype is also an object.

When you access a property on an object, JavaScript will first look for that property on the object itself. If it doesn't find it, it will look for the property on the object's prototype. If it doesn't find it there, it will look for the property on the prototype's prototype, and so on.

Example:

Let's take the example of an array and sorting it.

```javascript
const numbers = [1, 3, 2];
numbers.sort(); // [1, 2, 3]
```

In this example, the `sort` method is not defined on the `numbers` array itself. It is defined on the `Array.prototype`. When you call `numbers.sort()`, JavaScript looks for the `sort` method on the `numbers` array. Since it doesn't find it, it looks for the `sort` method on the `Array.prototype` and finds it there.

we can put our own methods on the prototype of an object.

```javascript
function Person(name) {
  this.name = name;
}

Person.prototype.greet = function() {
  console.log(`Hello, my name is ${this.name}`);
};

const john = new Person('John');
john.greet(); // Hello, my name is John
```

In this example, we define a `Person` constructor function that takes a `name` parameter and assigns it to the `name` property of the object. We then add a `greet` method to the `Person.prototype` object. When we create a new `Person` object and call the `greet` method on it, JavaScript first looks for the `greet` method on the `john` object. Since it doesn't find it there, it looks for the `greet` method on the `Person.prototype` object and finds it there.

### Prototypal Inheritance

Prototype inheritance in javascript is the linking of prototypes of a parent object to a child object to share and utilize the properties of a parent class using a child class.

Example:

```javascript
// Creating a parent object as a prototype
const parent = {
  greet: function() {
    console.log(`Hello from the parent`);
  }
};

// Creating a child object
const child = {
  name: 'Child Object'
};

// Performing prototype inheritance
child.__proto__ = parent;

// Accessing the method from the parent prototype
child.greet(); // Outputs: Hello from the parent 
```

In this example, we have a parent object with a `greet` method. We then create a child object and set its prototype to the parent object. This allows the child object to access the `greet` method from the parent object.


