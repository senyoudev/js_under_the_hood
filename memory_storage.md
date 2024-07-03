# Memory Storage

Low level languages like C require manual memory management, which can lead to memory leaks and segmentation faults if not handled properly. In contrast, high level languages like JavaScript have automatic memory management, which simplifies the process for developers.

The process of memory management is called garbage collection.


## Primitive vs Reference Types

In JavaScript, variables can store two types of values: primitive and reference.

### Primitive Types

Primitive types are stored directly in memory and have a fixed size. They include:

- **Number**: Represents numeric values.
- **String**: Represents textual data.
- **Boolean**: Represents true or false values.
- **Undefined**: Represents the absence of a value.
- **Null**: Represents the intentional absence of a value.
- **Symbol**: Represents a unique value.
- **BigInt**: Represents large integers.

```javascript
let num = 42; // Number
let str = 'Hello'; // String
let bool = true; // Boolean
let undef = undefined; // Undefined
let n = null; // Null
let sym = Symbol('foo'); // Symbol
let bigInt = 9007199254740991n; // BigInt
```

Those primitive types are stored in the call stack.


### Reference Types

Reference types are stored as references to memory locations. They include:

- **Object**: Represents a collection of key-value pairs.
- **Array**: Represents a list of elements.
- **Function**: Represents a reusable block of code.
- **Date**: Represents a date and time.
- **RegExp**: Represents a regular expression.

```javascript
let obj = { key: 'value' }; // Object
let arr = [1, 2, 3]; // Array
let func = function() {}; // Function
let date = new Date(); // Date
let regex = /pattern/; // RegExp
```

Those reference types are stored in the heap memory.

## Stack vs Heap

![Stack vs Heap](image.png)

This image illustrates how JavaScript handles primitive types (stored in the Stack) and reference types (stored in the Heap) in memory.

1. Primitive types (strings and numbers) are stored directly in the Stack:
   - `name` with value 'John'
   - `age` with value 30
   - `newName` with value 'Jonathan'

2. The object `person` is stored in the Heap, with its reference stored in the Stack.

3. `newPerson` is a new variable that references the same object as `person` in the Heap.

4. When `newPerson.name` is changed to 'Bradley', it affects the original object in the Heap.

5. Changing `newName` to 'Jonathan' doesn't affect the original `name` variable, as strings are primitive types.

6. The final `console.log(person.name)` outputs 'Bradley' because both `person` and `newPerson` reference the same object in the Heap, which was modified.

```javascript
let name = 'John'; // Stack
let age = 30; // Stack
let newName = name; // Stack

let person = { name: 'John' }; // Heap (object) + Stack (reference to the object in the Heap)
let newPerson = person; // Stack (reference to the object in the Heap)

newPerson.name = 'Bradley'; // Heap
```


