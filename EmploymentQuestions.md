# Git

## 1. What is Git?

**Answer:**
Git is a distributed version control system (VCS) that allows multiple developers to collaborate on a project by tracking changes in the source code.

---

## 2. What are the key features of Git?

**Answer:**
- **Distributed Development** – Each developer has a full copy of the repository.
- **Branching and Merging** – Enables easy creation and merging of branches.
- **Version Control** – Keeps track of all changes and revisions.
- **Lightweight and Fast** – Uses efficient algorithms for tracking changes.
- **Staging Area** – Allows selective staging of changes before committing.

---

## 3. What is the difference between Git and GitHub?

**Answer:**
- **Git** is a version control system.
- **GitHub** is a web-based platform for hosting and collaborating on Git repositories.

Other alternatives to GitHub include GitLab and Bitbucket.

---

## 4. Explain the basic Git workflow.

**Answer:**
1. `git clone <repo-url>` – Clone a remote repository.
2. `git checkout -b <branch-name>` – Create and switch to a new branch.
3. `git add <file>` – Stage changes.
4. `git commit -m "message"` – Commit changes.
5. `git push origin <branch-name>` – Push changes to the remote repository.

---

## 5. What is the difference between `git pull` and `git fetch`?

**Answer:**
- `git pull` – Fetches changes from the remote repository and automatically merges them into the current branch.
- `git fetch` – Only downloads changes without merging them.

---

## 6. What is a Git branch?

**Answer:**
A branch in Git is a separate line of development. It allows developers to work on features independently without affecting the main branch.

Commands:
```sh
git branch <branch-name> # Create a new branch
git checkout <branch-name> # Switch to a branch
git merge <branch-name> # Merge a branch into the current branch
git branch -d <branch-name> # Delete a branch
```

---

## 7. What is the difference between `git merge` and `git rebase`?

**Answer:**
- **`git merge`** – Combines two branches by creating a merge commit.
- **`git rebase`** – Reapplies commits from one branch onto another in a linear fashion.

Example:
```sh
git checkout feature-branch
git rebase main
```

---

## 8. How do you resolve merge conflicts in Git?

**Answer:**
1. Run `git status` to see conflicted files.
2. Open the conflicting files and manually resolve issues.
3. Use `git add <file>` to mark conflicts as resolved.
4. Commit the changes using `git commit`.

---

## 9. How do you undo changes in Git?

**Answer:**
- `git checkout -- <file>` – Discard uncommitted changes.
- `git reset HEAD <file>` – Unstage a file.
- `git reset --hard HEAD` – Reset to the last committed state.
- `git revert <commit-hash>` – Create a new commit that undoes a previous commit.

---

## 10. What is the `.gitignore` file?

**Answer:**
A `.gitignore` file specifies files and directories that Git should ignore.

Example:
```
node_modules/
.env
.DS_Store
```

---

## 11. What is a Git tag?

**Answer:**
Tags are used to mark specific points in history, such as releases.

Commands:
```sh
git tag v1.0.0 # Create a tag
git tag # List tags
git push origin v1.0.0 # Push a tag to remote repository
```

---

## 12. What is Git stash?

**Answer:**
`git stash` temporarily saves changes that are not ready to be committed.

Commands:
```sh
git stash # Stash changes
git stash list # View stashed changes
git stash pop # Apply stashed changes
```

---

## 13. What is Git cherry-pick?

**Answer:**
`git cherry-pick <commit-hash>` applies a specific commit from one branch to another.

Example:
```sh
git cherry-pick abc123
```

---

## 14. What is the difference between `git reset` and `git revert`?

**Answer:**
- `git reset` – Moves the branch pointer and can remove commits.
- `git revert` – Creates a new commit that undoes changes from a previous commit.

Example:
```sh
git reset --hard HEAD~1 # Remove last commit
git revert HEAD # Create a new commit undoing last commit
```

---

## 15. How do you delete a remote branch?

**Answer:**
```sh
git push origin --delete <branch-name>
```


# JavaScript

## 1. What is JavaScript?

**Answer:**
JavaScript is a high-level, interpreted programming language used primarily for web development. It enables dynamic content, interactivity, and asynchronous operations in web pages.

---

## 2. What are the key features of JavaScript?

**Answer:**
- **Lightweight and Interpreted** – Runs in the browser without needing compilation.
- **Dynamic Typing** – Variable types are determined at runtime.
- **Prototype-Based Inheritance** – Objects inherit directly from other objects.
- **Asynchronous and Event-Driven** – Supports non-blocking code execution.
- **Functional Programming Support** – Functions are first-class citizens.

---

## 3. What are the different data types in JavaScript?

**Answer:**
JavaScript has **primitive** and **non-primitive (reference)** data types.

### Primitive Types:
- `String` – Represents text (e.g., `'Hello'`).
- `Number` – Represents numbers (e.g., `42`, `3.14`).
- `Boolean` – Represents `true` or `false`.
- `Null` – Represents an empty or unknown value.
- `Undefined` – A variable that has been declared but not assigned a value.
- `Symbol` – A unique and immutable identifier (ES6+).
- `BigInt` – Large integers (e.g., `123n`).

### Non-Primitive Types:
- `Object` – Collection of key-value pairs.
- `Array` – Ordered list of values.
- `Function` – Reusable block of code.

---

## 4. Explain `let`, `const`, and `var` in JavaScript.

**Answer:**
| Keyword | Scope | Hoisting | Reassignable | Mutable |
|---------|------|---------|-------------|---------|
| `var` | Function-scoped | Hoisted (initialized as `undefined`) | ✅ Yes | ✅ Yes |
| `let` | Block-scoped | Hoisted (not initialized) | ✅ Yes | ✅ Yes |
| `const` | Block-scoped | Hoisted (not initialized) | ❌ No | ✅ Yes (for objects & arrays) |

Example:
```js
var a = 10; // Function-scoped
let b = 20; // Block-scoped
const c = 30; // Cannot be reassigned
```

---

## 5. What is the difference between `==` and `===`?

**Answer:**
- `==` (Equality Operator) checks **value only**, allowing type coercion.
- `===` (Strict Equality Operator) checks **both value and type**.

Example:
```js
console.log(5 == '5');  // true (type coercion happens)
console.log(5 === '5'); // false (different types)
```

---

## 6. What are closures in JavaScript?

**Answer:**
A closure is a function that **remembers the variables from its outer scope**, even after the outer function has finished executing.

Example:
```js
function outerFunction(x) {
  return function innerFunction(y) {
    return x + y;
  };
}

const add5 = outerFunction(5);
console.log(add5(3)); // 8
```

---

## 7. What is the difference between `null` and `undefined`?

**Answer:**
- `null` – A variable explicitly set to "no value".
- `undefined` – A variable that has been declared but not assigned a value.

Example:
```js
let a;
console.log(a); // undefined
let b = null;
console.log(b); // null
```

---

## 8. What is an Immediately Invoked Function Expression (IIFE)?

**Answer:**
An IIFE is a function that runs immediately after it is defined.

Example:
```js
(function() {
  console.log('Executed immediately!');
})();
```

---

## 9. What is the event loop in JavaScript?

**Answer:**
The event loop is a mechanism that handles asynchronous operations in JavaScript, ensuring non-blocking execution.

---

## 10. Explain `call()`, `apply()`, and `bind()`.

**Answer:**
- `call()` – Calls a function with a specific `this` value and arguments passed individually.
- `apply()` – Calls a function with a specific `this` value and arguments as an array.
- `bind()` – Returns a new function with a bound `this` value.

Example:
```js
const person = { name: 'John' };
function greet(age) {
  console.log(`Hello, my name is ${this.name} and I am ${age} years old.`);
}

greet.call(person, 30); // Call

greet.apply(person, [30]); // Apply

const boundGreet = greet.bind(person);
boundGreet(30); // Bind
```

---

## 11. What are promises in JavaScript?

**Answer:**
A promise is an object representing the **eventual completion or failure** of an asynchronous operation.

Example:
```js
const myPromise = new Promise((resolve, reject) => {
  setTimeout(() => resolve('Success!'), 1000);
});

myPromise.then(result => console.log(result));
```

---

## 12. What is `async/await`?

**Answer:**
`async/await` simplifies handling promises in an asynchronous function.

Example:
```js
async function fetchData() {
  let response = await fetch('https://api.example.com/data');
  let data = await response.json();
  console.log(data);
}
fetchData();
```

---

## 13. What are ES6 classes in JavaScript?

**Answer:**
ES6 introduced class syntax to create objects and handle inheritance more cleanly.

Example:
```js
class Person {
  constructor(name) {
    this.name = name;
  }
  greet() {
    console.log(`Hello, my name is ${this.name}`);
  }
}

const person1 = new Person('Alice');
person1.greet();
```

---

## 14. What are the different types of JavaScript errors?

**Answer:**
- **SyntaxError** – Incorrect syntax (e.g., missing brackets).
- **ReferenceError** – Accessing an undefined variable.
- **TypeError** – Performing an invalid operation on a variable.
- **RangeError** – Using an invalid range (e.g., `new Array(-1)`).

Example:
```js
console.log(x); // ReferenceError: x is not defined
```

---

## 15. What is the difference between `map()`, `filter()`, and `reduce()`?

**Answer:**
- `map()` – Transforms an array by applying a function to each element.
- `filter()` – Returns an array of elements that meet a condition.
- `reduce()` – Aggregates array values into a single value.

Example:
```js
const numbers = [1, 2, 3, 4, 5];
console.log(numbers.map(x => x * 2)); // [2, 4, 6, 8, 10]
console.log(numbers.filter(x => x % 2 === 0)); // [2, 4]
console.log(numbers.reduce((sum, x) => sum + x, 0)); // 15
```

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



# Nestjs

## 1. What is NestJS?

**Answer:**  
NestJS is a progressive Node.js framework for building efficient, scalable, and maintainable server-side applications. It is built on top of Express.js (or Fastify) and follows a modular architecture, leveraging TypeScript by default.


## 2. What are the core features of NestJS?

**Answer:**
- **Modular Architecture**: Applications are organized into modules.
- **Dependency Injection (DI)**: Built-in support for DI using providers.
- **Decorators & Metadata**: Uses TypeScript decorators to define components.
- **Middleware Support**: Supports Express and Fastify middleware.
- **Built-in Support for WebSockets and Microservices**.
- **Powerful CLI**: Automates code generation and development tasks.


## 3. What is a module in NestJS?

**Answer:**
A **module** in NestJS is a class decorated with `@Module()` that organizes related components, services, and controllers together.

Example:
```typescript
import { Module } from '@nestjs/common';
import { UsersController } from './users.controller';
import { UsersService } from './users.service';

@Module({
  controllers: [UsersController],
  providers: [UsersService],
})
export class UsersModule {}
```


## 4. What is a controller in NestJS?

**Answer:**
Controllers in NestJS handle incoming HTTP requests and define endpoints using decorators like `@Get()`, `@Post()`, etc.

Example:
```typescript
import { Controller, Get } from '@nestjs/common';

@Controller('users')
export class UsersController {
  @Get()
  getAllUsers() {
    return ['John', 'Jane', 'Doe'];
  }
}
```


## 5. What is a service in NestJS?

**Answer:**
A **service** in NestJS is a provider that contains business logic and interacts with the database or external APIs. It is injected into controllers using Dependency Injection.

Example:
```typescript
import { Injectable } from '@nestjs/common';

@Injectable()
export class UsersService {
  getUsers() {
    return ['John', 'Jane', 'Doe'];
  }
}
```


## 6. What is Dependency Injection (DI) in NestJS?

**Answer:**
DI is a design pattern where dependencies are injected instead of being created manually. NestJS uses DI to manage the lifecycle of services efficiently.

Example:
```typescript
import { Injectable } from '@nestjs/common';

@Injectable()
export class UsersService {
  getUsers() {
    return ['John', 'Jane', 'Doe'];
  }
}
```

Injecting service into a controller:
```typescript
@Controller('users')
export class UsersController {
  constructor(private readonly usersService: UsersService) {}
  
  @Get()
  getAllUsers() {
    return this.usersService.getUsers();
  }
}
```


## 7. How does NestJS handle middleware?

**Answer:**
Middleware in NestJS is a function that runs before a request reaches the controller. It is useful for logging, authentication, and request transformations.

Example:
```typescript
import { Injectable, NestMiddleware } from '@nestjs/common';
import { Request, Response, NextFunction } from 'express';

@Injectable()
export class LoggerMiddleware implements NestMiddleware {
  use(req: Request, res: Response, next: NextFunction) {
    console.log(`Request... ${req.method} ${req.url}`);
    next();
  }
}
```

Registering middleware in the module:
```typescript
import { Module, MiddlewareConsumer, NestModule } from '@nestjs/common';
@Module({})
export class AppModule implements NestModule {
  configure(consumer: MiddlewareConsumer) {
    consumer.apply(LoggerMiddleware).forRoutes('*');
  }
}
```


## 8. What are Pipes in NestJS?

**Answer:**
Pipes are used for **data transformation** and **validation** in NestJS. They can be applied at the method level, controller level, or globally.

Example using `ValidationPipe`:
```typescript
import { PipeTransform, Injectable, ArgumentMetadata, BadRequestException } from '@nestjs/common';

@Injectable()
export class ParseIntPipe implements PipeTransform {
  transform(value: any, metadata: ArgumentMetadata) {
    const val = parseInt(value, 10);
    if (isNaN(val)) {
      throw new BadRequestException('Validation failed');
    }
    return val;
  }
}
```

Using in a controller:
```typescript
@Get(':id')
findOne(@Param('id', new ParseIntPipe()) id: number) {
  return `User with ID ${id}`;
}
```


## 9. What are Interceptors in NestJS?

**Answer:**
Interceptors in NestJS are used to modify request/response objects before they reach the controller or before they are sent to the client.

Example:
```typescript
import { CallHandler, ExecutionContext, Injectable, NestInterceptor } from '@nestjs/common';
import { Observable } from 'rxjs';
import { map } from 'rxjs/operators';

@Injectable()
export class TransformInterceptor implements NestInterceptor {
  intercept(context: ExecutionContext, next: CallHandler): Observable<any> {
    return next.handle().pipe(map(data => ({ data })));
  }
}
```

Applying globally:
```typescript
app.useGlobalInterceptors(new TransformInterceptor());
```


## 10. What is the difference between Guards and Middleware in NestJS?

**Answer:**
| Feature | Middleware | Guards |
|---------|-----------|--------|
| Execution Timing | Runs before controller | Runs before route execution |
| Purpose | Modify requests (e.g., logging) | Handle authentication & authorization |
| Scope | Applies globally or to specific routes | Specific to routes |

Example of a **Guard**:
```typescript
import { Injectable, CanActivate, ExecutionContext } from '@nestjs/common';
@Injectable()
export class AuthGuard implements CanActivate {
  canActivate(context: ExecutionContext): boolean {
    const request = context.switchToHttp().getRequest();
    return request.headers.authorization === 'valid-token';
  }
}
```

Applying to a route:
```typescript
@Get()
@UseGuards(AuthGuard)
findAll() {
  return 'Protected Route';
}
```

## 11. What databases does NestJS support?

**Answer:**
NestJS supports multiple databases through ORMs such as:
- TypeORM (SQL databases)
- Sequelize (SQL databases)
- Prisma (Modern ORM for SQL databases)
- Mongoose (MongoDB)
- MikroORM (NoSQL and SQL support)

Example with TypeORM:
```typescript
import { Entity, PrimaryGeneratedColumn, Column } from 'typeorm';
@Entity()
export class User {
  @PrimaryGeneratedColumn()
  id: number;

  @Column()
  name: string;
}
```

# React

## 1. What is React?

**Answer:**
React is an open-source JavaScript library used for building user interfaces, especially single-page applications. It allows developers to create reusable UI components and efficiently update the UI using a virtual DOM.

---

## 2. What are the key features of React?

**Answer:**
- **JSX (JavaScript XML):** A syntax extension for JavaScript that allows writing HTML inside JS.
- **Virtual DOM:** Improves performance by updating only changed parts of the actual DOM.
- **Component-Based Architecture:** Applications are built using reusable components.
- **One-Way Data Binding:** Ensures unidirectional data flow.
- **Hooks:** Allow function components to use state and lifecycle methods.
- **React Router:** Enables navigation without full page reloads.

---

## 3. What is JSX?

**Answer:**
JSX is a syntax extension for JavaScript that allows writing HTML-like code inside JavaScript.

Example:
```jsx
const element = <h1>Hello, World!</h1>;
```
JSX is compiled into JavaScript using Babel before execution.

---

## 4. What is the Virtual DOM?

**Answer:**
The Virtual DOM is a lightweight representation of the real DOM. React updates the Virtual DOM first, compares it with the previous version (diffing), and then updates only the changed parts in the real DOM (reconciliation), improving performance.

---

## 5. What are components in React?

**Answer:**
Components are the building blocks of a React application. They can be **functional** or **class-based**.

Example of a Functional Component:
```jsx
function Welcome() {
  return <h1>Hello, React!</h1>;
}
```
Example of a Class Component:
```jsx
class Welcome extends React.Component {
  render() {
    return <h1>Hello, React!</h1>;
  }
}
```

---

## 6. What is the difference between functional and class components?

| Feature | Functional Component | Class Component |
|---------|---------------------|----------------|
| Syntax | Function-based | ES6 class-based |
| State | Uses `useState` Hook | Uses `this.state` |
| Lifecycle Methods | Uses `useEffect` Hook | Uses `componentDidMount`, `componentDidUpdate`, etc. |
| Performance | More optimized | Less optimized |

Example of a functional component with Hooks:
```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

---

## 7. What are props in React?

**Answer:**
Props (short for "properties") are used to pass data from parent to child components.

Example:
```jsx
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

<Greeting name="John" />
```

---

## 8. What is state in React?

**Answer:**
State is an object that stores a component's dynamic data and determines its behavior.

Example using `useState` Hook:
```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

---

## 9. What are React Hooks?

**Answer:**
Hooks are functions that allow functional components to use state and lifecycle features.

Common Hooks:
- `useState` – Manages state in functional components.
- `useEffect` – Performs side effects in function components.
- `useContext` – Provides a way to pass data deeply without prop drilling.
- `useRef` – Provides access to DOM elements or persistent values.
- `useReducer` – An alternative to `useState` for complex state logic.

Example using `useEffect`:
```jsx
import React, { useState, useEffect } from 'react';

function Timer() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      setCount(prevCount => prevCount + 1);
    }, 1000);
    return () => clearInterval(interval);
  }, []);

  return <p>Timer: {count} seconds</p>;
}
```

---

## 10. What is React Router?

**Answer:**
React Router is a library for handling navigation in React applications.

Example:
```jsx
import { BrowserRouter as Router, Route, Switch, Link } from 'react-router-dom';

function App() {
  return (
    <Router>
      <nav>
        <Link to="/">Home</Link>
        <Link to="/about">About</Link>
      </nav>
      <Switch>
        <Route exact path="/" component={Home} />
        <Route path="/about" component={About} />
      </Switch>
    </Router>
  );
}
```

---

## 11. What is Redux?

**Answer:**
Redux is a state management library used for managing global state in large applications.

Example setup:
```jsx
import { createStore } from 'redux';

const initialState = { count: 0 };

function reducer(state = initialState, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    default:
      return state;
  }
}

const store = createStore(reducer);
```

---

## 12. What are Higher-Order Components (HOC)?

**Answer:**
A Higher-Order Component (HOC) is a function that takes a component and returns a new component with additional functionality.

Example:
```jsx
function withLogger(WrappedComponent) {
  return function EnhancedComponent(props) {
    console.log('Rendering', WrappedComponent.name);
    return <WrappedComponent {...props} />;
  };
}
```

Usage:
```jsx
const EnhancedComponent = withLogger(MyComponent);
```
















