# Closures


## What is a closure?

A closure is a function that has access to its own scope, the outer function's scope, and the global scope. In other words, a closure gives you access to an outer function's scope from an inner function.

Here's an example:

```javascript
function outerFunction() {
  const outerVariable = 'I am from the outer function';

  function innerFunction() {
    console.log(outerVariable);
  }

  return innerFunction;
}

const innerFunc = outerFunction();
innerFunc(); // I am from the outer function
```

In this example, the `innerFunction` has access to the `outerVariable` from the `outerFunction`. This is possible because the `innerFunction` is a closure.

## How Closures Work ?

When a function is defined inside another function, the inner function has access to the outer function's variables. This is because the inner function has access to the scope in which it was created, even after the outer function has finished executing.

### Lexical Scope

Closures are possible because of lexical scoping in JavaScript. Lexical scoping means that the scope of a variable is determined by its position within the source code. In other words, a variable defined in an outer function is available to an inner function even after the outer function has finished executing.

```javascript
function init() {
  var name = "Mozilla"; // name is a local variable created by init
  function displayName() {
    // displayName() is the inner function, that forms the closure
    console.log(name); // use variable declared in the parent function
  }
  displayName();
}
init();
```

### Scoping With let and const

Traditionally (before ES6), JavaScript only had two kinds of scopes: function scope and global scope. Variables declared with var are either function-scoped or global-scoped, depending on whether they are declared within a function or outside a function. This can be tricky, because blocks with curly braces do not create scopes:

```javascript
if (Math.random() > 0.5) {
  var x = 1;
} else {
  var x = 2;
}
console.log(x);
```

For people from other languages (e.g. C, Java) where blocks create scopes, the above code should throw an error on the console.log line, because we are outside the scope of x in either block. However, because blocks don't create scopes for var, the var statements here actually create a global variable. 

In ES6, JavaScript introduced the let and const declarations, which, among other things like temporal dead zones, allow you to create block-scoped variables.

```javascript
if (Math.random() > 0.5) {
  const x = 1;
} else {
  const x = 2;
}
console.log(x); // ReferenceError: x is not defined
```

I already mentionned `let` and `const` in the ES6 features section, but it's important to mention them here because they are crucial for understanding closures in modern JavaScript.