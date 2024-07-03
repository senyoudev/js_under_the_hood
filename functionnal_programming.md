# Functionnal Programming

Functional programming is a programming paradigm. It is a declarative type of programming style.

By declarative, we mean that we tell the computer what we want to do, and it figures out how to do it.

The other type of programming is imperative programming, where we tell the computer how to do something. as example, in imperative programming, we use loops to iterate over an array, while in declarative programming, we use the `map` function. or in imperative programming, we use `if` statements to check conditions, while in declarative programming, we use the `filter` function.

Functional programming is based on the following principles:

1. **Higher-order functions**: 

Higher-order functions are functions that take other functions as arguments or return functions as results. They enable you to abstract over actions, not just values.

Example:

```javascript
const map = (fn, arr) => arra.map(fn);
const addOne = x => x + 1;
const numbers = [1, 2, 3];
console.log(map(addOne, numbers)); // [2, 3, 4]
```

2. **Pure functions**:

Pure functions are functions that have no side effects and return the same output for the same input. They are deterministic and easy to test.

Example:

```javascript
const add = (a, b) => a + b;

console.log(add(1, 2)); // 3

// The add function is a pure function because it returns the same output for the same input.

// Impure function
let result = 0;
const add = (a, b) => {
  result = a + b;
  return result;
};

console.log(add(1, 2)); // 3
console.log(result); // 3
// The add function is an impure function because it has side effects (modifying the result variable).
```

3. **Immutability**:

Immutability means that once a value is created, it cannot be changed. This makes it easier to reason about the code and prevents bugs caused by mutable state.

Example:

```javascript
const numbers = [1, 2, 3];
const newNumbers = [...numbers, 4];

console.log(numbers); // [1, 2, 3]
console.log(newNumbers); // [1, 2, 3, 4]
```

4. **Function composition**:

Function composition is the process of combining two or more functions to produce a new function. It allows you to break down complex problems into simpler parts.

Example:

```javascript
const add = x => x + 1;
const multiply = x => x * 2;

const addAndMultiply = x => multiply(add(x));

console.log(addAndMultiply(2)); // 6
```

