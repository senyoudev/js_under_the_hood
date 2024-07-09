# Nodejs Specifies

## Event-Driven Architecture

By event-driven architecture, we mean that the flow of the program is determined by events such as user actions, sensor outputs, or messages from other programs. In Node.js, this is achieved using events and callbacks.

For example, when a user clicks a button on a web page, an event is triggered, and a callback function is executed in response to that event. This allows the program to respond to user actions in a non-blocking way.

```javascript
const EventEmitter = require('events'); // Import the EventEmitter class, which is a built-in module in Node.js
const myEmitter = new EventEmitter();
myEmitter.on('event', () => console.log('Event occurred!')); // 'event' is the event name, for example, 'click', 'submit', etc.
myEmitter.emit('event');
```

In this example, we create an `EventEmitter` object and attach a callback function to the `event` event. When we call `emit('event')`, the callback function is executed.

## Streams and Buffers

Streams are objects that let you read data from a source or write data to a destination in a continuous manner. They are used to process large amounts of data efficiently without loading the entire data into memory. They exist in other programming languages as well such as Java, etc.

Buffers are temporary storage areas in memory that hold data while it is being transferred from one place to another. They are used to store raw binary data and are commonly used with streams. They are useful because they minimize the number of read and write operations that are too expensive.

```javascript
const fs = require('fs');
const readStream = fs.createReadStream('input.txt');
const writeStream = fs.createWriteStream('output.txt');
readStream.pipe(writeStream);
```

In this example, we create a read stream from an input file and a write stream to an output file. We then use the `pipe` method to transfer data from the read stream to the write stream. and buffers are used to store the data while it is being transferred.

maybe you are asking where the buffers are used ? the buffers are used in the background to store the data while it is being transferred from the read stream to the write stream, so it kind of an automatic process that you don't have to worry about.

note : 
- `piping` is chaining streams together, where the output of one stream is the input to another stream.
- There are four fundamental stream types in Node.js: `Readable`, `Writable`, `Duplex`, and `Transform`.
    - `Readable`: Used for reading data.
    - `Writable`: Used for writing data.
    - `Duplex`: Used for reading and writing data.
    - `Transform`: Used for modifying data as it is read or written.

Example of `Duplex` stream:

```javascript
const { Duplex } = require('stream');
const duplexStream = new Duplex({
  write(chunk, encoding, callback) {
    console.log(chunk.toString());
    callback();
  },
  read(size) {
    this.push('Hello, ');
    this.push('world!');
    this.push(null);
  }
});

duplexStream.pipe(process.stdout);
```

In this example, we create a `Duplex` stream that can both read and write data. When we write data to the stream, it logs the data to the console. When we read data from the stream, it pushes the data 'Hello, ' and 'world!' to the stream.

Example of `Transform` stream:

```javascript
const { Transform } = require('stream');
const transformStream = new Transform({
  transform(chunk, encoding, callback) {
    this.push(chunk.toString().toUpperCase());
    callback();
  }
});

transformStream.pipe(process.stdout);
transformStream.write('hello, ');
transformStream.write('world!');
transformStream.end();
```

In this example, we create a `Transform` stream that modifies the data as it is read or written. When we write data to the stream, it transforms the data to uppercase and pushes it to the stream.

## File System Operations

Node.js provides a built-in module called `fs` that allows you to work with the file system on your computer. You can use this module to read and write files, create directories, and perform other file system operations.

```javascript
const fs = require('fs');
// Read a file
fs.readFile('file.txt', 'utf8', (err, data) => {
  if (err) throw err;
  console.log(data);
});

// Write to a file
fs.writeFile('file.txt', 'Hello, world!', (err) => {
  if (err) throw err;
  console.log('File written!');
});

// Create a directory
fs.mkdir('new-directory', (err) => {
  if (err) throw err;
  console.log('Directory created!');
});
```

## Child Processes

Node.js allows you to run shell commands or other executables as child processes. This is useful for running tasks that are not natively supported by Node.js or for running tasks in parallel.

```javascript
const { exec } = require('child_process');
// Run a shell command that lists the files in the current directory
exec('ls', (err, stdout, stderr) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log(stdout);
});
```

## Clustering

Clustering is a way to scale Node.js applications by creating multiple instances of the application that can run on different CPU cores. This allows the application to handle more requests and utilize the full processing power of the server.

```javascript
const cluster = require('cluster');
const http = require('http');
const numCPUs = require('os').cpus().length;


if (cluster.isMaster) {
  console.log(`Master ${process.pid} is running`);

  // Fork workers
  for (let i = 0; i < numCPUs; i++) {
    cluster.fork();
  }

  cluster.on('exit', (worker, code, signal) => {
    console.log(`Worker ${worker.process.pid} died`);
  });
} else {
  http.createServer((req, res) => {
    res.writeHead(200);
    res.end('Hello, world!');
  }).listen(8000);

  console.log(`Worker ${process.pid} started`);
}
```

In this example, we create a master process that forks multiple worker processes, each of which runs an HTTP server. This allows the application to handle more requests by utilizing the full processing power of the server.

