# GIT
- **Cherry-pick**: is a Git command that allows you to **select a specific commit** from one branch and apply it to another branch. This is useful when you want to pick certain changes without merging the entire branch.
- **Git Merge**: Creates a new "merge commit" that combines the histories of both branches. Best for collaborative workflows where you want to keep the full history of branches.
- **Git Rebase**: Moves (reapplies) commits from one branch to another, rewriting the commit history. No merge commits are created. Best for creating a clean, linear history, but use with caution on shared branches to avoid rewriting public history.


# Nodejs
## 1. What is Node.js?
Node.js is a JavaScript runtime built on Chrome's V8 JavaScript engine. It is designed to build scalable network applications and allows for running JavaScript on the server side. It is event-driven, non-blocking, and uses a single-threaded event loop to handle multiple requests.

## 2. What is the event loop in Node.js?
The event loop is a core part of Node.js's asynchronous behavior. It allows Node.js to perform non-blocking I/O operations by placing tasks on a queue and handling them one at a time. It allows Node.js to process requests without waiting for I/O operations to complete.

## 3. What are the main features of Node.js?
- **Single-threaded**: Uses a single thread for handling multiple requests.
- **Non-blocking I/O**: Asynchronous I/O operations that do not block the execution thread.
- **Fast execution**: Built on the V8 JavaScript engine for high performance.
- **Scalability**: Suitable for handling high levels of concurrency.
- **Cross-platform**: Runs on multiple platforms, such as Windows, Linux, and macOS.

## 4. What is the difference between `require` and `import` in Node.js?

## 5. How does Node.js handle asynchronous operations?
Node.js handles asynchronous operations using callbacks, promises, and async/await. It uses an event-driven, non-blocking model. When an I/O operation is initiated, Node.js delegates it to the system kernel and continues processing other tasks, only notifying the program when the operation is complete.

## 6. What is the difference between process.nextTick(), setImmediate(), and setTimeout()?
- **process.nextTick()**: Executes the callback function immediately after the current operation completes and before the event loop continues.
- **setImmediate()**: Executes the callback function on the next iteration of the event loop.
- **setTimeout()**: Executes the callback after the specified time, allowing other operations in the event loop to be executed before it.

## 7. Explain the concept of middleware in Express.js.
Middleware functions in Express.js are functions that have access to the request, response, and the next middleware in the application’s request-response cycle. Middleware can modify the request or response objects, end the request-response cycle, or call the next middleware function.



## 8. How can you handle errors in Node.js?
Errors in Node.js can be handled in the following ways:

- Using try-catch blocks for synchronous code.

- Using callback functions with an error-first convention (callback(err, result)).

- Using Promises with .catch() to handle errors in asynchronous code.

- Using async/await and try-catch for more readable error handling.

## 10. What is the role of package.json in a Node.js project?
The package.json file is a key component of a Node.js project. It contains metadata about the project, such as the project's name, version, dependencies, scripts, and other configuration options. It is essential for managing dependencies and scripts for the project.


## 11. What is a callback function in Node.js?
A callback function is a function passed as an argument to another function, to be executed after the completion of that function. In Node.js, callbacks are commonly used for handling asynchronous operations, such as I/O tasks

## 12. What is the purpose of the EventEmitter class in Node.js?
The EventEmitter class in Node.js allows objects to emit events and listen for events. It provides methods like .on(), .emit(), and .once() to manage event-driven programming. It is commonly used for handling asynchronous events like HTTP requests.

## 13. What is the difference between __dirname and __filename?

- __dirname: Represents the directory name of the current module.
- __filename: Represents the full file path of the current module.


## 14. What are Streams in Node.js?
Streams in Node.js are objects that enable reading or writing data sequentially. They allow for efficient handling of large volumes of data. There are four types of streams:

- Readable streams (e.g., fs.createReadStream)
- Writable streams (e.g., fs.createWriteStream)
- Duplex streams (e.g., TCP sockets)
- Transform streams (e.g., zlib)


## 15. What is the use of cluster module in Node.js?
The cluster module in Node.js is used to spawn multiple child processes (workers) to take advantage of multi-core systems. It helps in distributing the load across multiple CPU cores, improving the performance of Node.js applications that handle high concurrency.

## 16. What is the difference between fs.readFile() and fs.createReadStream()?

- fs.readFile(): Reads the entire file into memory before returning the data. Suitable for small files.
- fs.createReadStream(): Reads the file in chunks and streams it, allowing for handling large files without loading everything into memory.

## 17. What is a promise in Node.js?
A Promise is an object representing the eventual completion (or failure) of an asynchronous operation. It allows handling asynchronous code more elegantly compared to callbacks by chaining .then() for success and .catch() for error handling.

## 18. What is npm in Node.js?
npm (Node Package Manager) is the default package manager for Node.js. It is used to install, manage, and share packages (libraries or modules) within a Node.js application. It also helps in managing dependencies and scripts.

## 19. How can you improve performance in a Node.js application?


- Use async/await and Promises to avoid blocking operations.
- Optimize I/O operations by using streams.
- Use cluster to leverage multi-core processors.
- Profile and debug with tools like Node.js Profiler and Chrome DevTools.
- Minimize the use of global variables to reduce memory footprint.

## 20. What is the purpose of npm install --save and npm install --save-dev?

- **--save**: Adds the package to the dependencies section in package.json. This is for packages required in production.
- **--save-dev**: Adds the package to the devDependencies section in package.json. This is for packages required only in the development environment (e.g., testing libraries).




















