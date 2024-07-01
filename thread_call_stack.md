# Thread & Call Stack

The thread and call stack are essential components of a JavaScript runtime environment.

## Thread Of Execution

- JavaScript is single-threaded, meaning it can only execute one task at a time.
- The thread of execution refers to the sequence of operations that are executed by the JavaScript engine.
- Single sequential flow of control. which means that only one operation can be executed at a time.
- Javascript is synchronous language with asynchronous capabilities.
- A thread has a call stack and memory.

## Call Stack

- The call stack is a data structure that stores information about the active subroutines of a program. I mean, it stores the execution context of the program.
- Stack of functions to be executed.(LIFO)
- Manages the execution context of the program.

Example:

```javascript
function greet() {
  return "Hello!";
}

function welcome() {
  return "Welcome!";
}

function main() {
  const message1 = greet();
  const message2 = welcome();
  console.log(message1, message2);
}

main();
```

Initial state:
1. [main()] The program starts by calling main(), which is pushed onto the call stack.
2. Inside main(), calling greet(): main() calls greet(), so greet() is pushed on top of the stack.
3. greet() returns: greet() completes and returns "Hello!". It's popped off the stack.
4. Inside main(), calling welcome(): main() now calls welcome(), which is pushed onto the stack.
5. welcome() returns: welcome() completes and returns "Welcome!". It's popped off the stack.
6. main() completes: [] main() logs the messages and completes. It's popped off the stack.
7. Final state: [] The call stack is empty, and the program ends.

