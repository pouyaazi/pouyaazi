# Public

## What is Garbage Collection?
Garbage Collection (GC) is the process of **automatically reclaiming memory** that is no longer in use by a program. It helps prevent **memory leaks** and optimizes memory usage without requiring manual memory management.

---

### How Does Garbage Collection Work?
Garbage collectors typically follow these steps:

1. **Mark:** Identify objects that are still in use (reachable).  
2. **Sweep:** Remove objects that are no longer referenced.  
3. **Compact (optional):** Rearrange memory to avoid fragmentation.

---

### Garbage Collection in Different Languages
- **JavaScript (V8 Engine):** Uses a **Mark-and-Sweep** algorithm.
- **Python:** Uses **Reference Counting** and **Cyclic Garbage Collection**.
- **Java:** Uses **Generational Garbage Collection** (Young, Old, and PermGen/Metaspace).
- **C++:** No automatic garbage collection; developers must manage memory manually.

---

### Pros & Cons of Garbage Collection

✅ **Pros:**  
- Reduces memory leaks.  
- Improves developer productivity.  
- Handles memory allocation dynamically.  

❌ **Cons:**  
- Adds overhead to performance.  
- Not deterministic (GC runs unpredictably).  
- May cause application pauses (Stop-the-World events).  

---

### Example: Garbage Collection in JavaScript
JavaScript uses a **Mark-and-Sweep** algorithm for garbage collection:

```javascript
function demoGC() {
    let obj = { name: "Garbage Collection Example" };
    console.log(obj); // Object is reachable

    obj = null; // Now eligible for garbage collection
}
demoGC();
```

```python
import gc

class Demo:
    def __del__(self):
        print("Object is being deleted")

obj = Demo()
del obj  # Now eligible for garbage collection
gc.collect()  # Manually trigger garbage collection
```

# SOLID Principles - Employment Questions & Answers

## 1. What is SOLID in software engineering?
**Answer:**
SOLID is an acronym representing five design principles in object-oriented programming that make software more maintainable and scalable:
- **S**: Single Responsibility Principle
- **O**: Open/Closed Principle
- **L**: Liskov Substitution Principle
- **I**: Interface Segregation Principle
- **D**: Dependency Inversion Principle

---

## 2. What is the Single Responsibility Principle (SRP)?
**Answer:**
A class should have **only one reason to change**, meaning it should have only one job or responsibility.

✅ **Example (Bad):**
```python
class Report:
    def calculate(self):
        pass

    def print_report(self):
        pass  # violates SRP
```

✅ **Example (Good):**
```python
class Report:
    def calculate(self):
        pass

class ReportPrinter:
    def print_report(self, report):
        pass
```

---

## 3. What is the Open/Closed Principle (OCP)?
**Answer:**
Software entities (classes, modules, functions) should be **open for extension but closed for modification**. This means behavior can be extended without modifying existing code.

✅ **Example:**
Use inheritance or interfaces to add new functionality.
```python
class Shape:
    def area(self):
        pass

class Circle(Shape):
    def area(self):
        return 3.14 * r * r
```

---

## 4. What is the Liskov Substitution Principle (LSP)?
**Answer:**
Objects of a superclass should be replaceable with objects of a subclass **without affecting the correctness** of the program.

✅ **Example:**
```python
class Bird:
    def fly(self):
        pass

class Sparrow(Bird):
    def fly(self):
        print("Flying")

# Good: Sparrow can be used wherever Bird is expected.
```

❌ **Bad Example:**
If a subclass throws an error when a method of the base class is used (e.g., Penguin not being able to fly), it violates LSP.

---

## 5. What is the Interface Segregation Principle (ISP)?
**Answer:**
Clients should **not be forced to depend on interfaces they do not use**. It's better to have many small, specific interfaces than one large, general-purpose one.

✅ **Example (Good):**
```python
class Printer:
    def print(self): pass

class Scanner:
    def scan(self): pass
```

❌ **Bad Example:**
```python
class MultiFunctionMachine:
    def print(self): pass
    def scan(self): pass
    def fax(self): pass

# Not all clients need fax()
```

---

## 6. What is the Dependency Inversion Principle (DIP)?
**Answer:**
High-level modules should **not depend on low-level modules**. Both should depend on **abstractions**.
Abstractions should not depend on details. Details should depend on abstractions.

✅ **Example:**
```python
class Keyboard:
    def get_input(self):
        pass

class WindowsMachine:
    def __init__(self, keyboard: Keyboard):
        self.keyboard = keyboard
```
Here, `WindowsMachine` depends on an abstraction `Keyboard`, not a concrete implementation.

---

## 7. Why are SOLID principles important in real-world software development?
**Answer:**
- Improves **code maintainability** and **readability**
- Enhances **scalability** and **testability**
- Reduces the risk of introducing bugs
- Makes **refactoring** easier and safer

---

## 8. Can SOLID principles be applied in functional programming?
**Answer:**
Yes, while SOLID is rooted in OOP, many of the ideas like single responsibility and dependency inversion translate well to functional programming, albeit in a different form (e.g., using pure functions and dependency injection).

---

## 9. How does SRP help in unit testing?
**Answer:**
When a class has only one responsibility, its behavior is easier to test in isolation because it doesn't have side-effects or unrelated functionalities.

---

## 10. What happens when SOLID principles are not followed?
**Answer:**
- The code becomes **tightly coupled**
- Difficult to **extend** or **maintain**
- Harder to **test**
- Higher chance of introducing **bugs** during changes


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


# Next.js

## 1. What is Next.js?

**Answer:**
Next.js is a React framework that enables **server-side rendering (SSR)**, **static site generation (SSG)**, and other performance optimizations for React applications.

---

## 2. What are the key features of Next.js?

**Answer:**
- **Hybrid Rendering** – Supports both **SSG** and **SSR**.
- **API Routes** – Built-in backend functionality.
- **Automatic Code Splitting** – Optimizes loading performance.
- **Image Optimization** – Uses the `next/image` component.
- **Incremental Static Regeneration (ISR)** – Updates static content without redeploying.
- **Fast Refresh** – Improved development experience with hot reloading.
- **Built-in CSS & Sass Support** – Supports global and module styles.

---

## 3. What is the difference between SSR and SSG in Next.js?

**Answer:**
| Feature | SSR (Server-Side Rendering) | SSG (Static Site Generation) |
|---------|---------------------------|----------------------------|
| When is HTML generated? | At request time (runtime) | At build time |
| Performance | Slower due to real-time rendering | Faster as pre-rendered |
| Use Case | Dynamic content (e.g., user dashboards) | Static content (e.g., blogs) |

Example:
```js
// SSR Example
export async function getServerSideProps() {
  return { props: { time: new Date().toISOString() } };
}
```
```js
// SSG Example
export async function getStaticProps() {
  return { props: { data: await fetchData() } };
}
```

---

## 4. What is Incremental Static Regeneration (ISR)?

**Answer:**
ISR allows static pages to be **updated after deployment** without rebuilding the entire site.

Example:
```js
export async function getStaticProps() {
  return {
    props: { data: await fetchData() },
    revalidate: 10, // Regenerate page every 10 seconds
  };
}
```

---

## 5. How do API routes work in Next.js?

**Answer:**
Next.js allows creating backend API endpoints inside the `pages/api` directory.

Example:
```js
export default function handler(req, res) {
  res.status(200).json({ message: 'Hello from Next.js API' });
}
```

---

## 6. What is the difference between `getStaticProps`, `getServerSideProps`, and `getInitialProps`?

**Answer:**
| Function | When does it run? | Use Case |
|----------|----------------|----------|
| `getStaticProps` | At build time | Static content (e.g., blogs) |
| `getServerSideProps` | On each request | Dynamic content (e.g., dashboards) |
| `getInitialProps` | On both server & client | Deprecated, use `getServerSideProps` instead |

---

## 7. How does routing work in Next.js?

**Answer:**
Next.js uses a **file-based routing system**, where the file structure in `pages/` determines the routes.

Example:
```
pages/
  index.js -> '/'
  about.js -> '/about'
  blog/[id].js -> '/blog/:id'
```

Dynamic routes:
```js
// pages/blog/[id].js
import { useRouter } from 'next/router';
export default function BlogPost() {
  const router = useRouter();
  return <h1>Blog ID: {router.query.id}</h1>;
}
```

---

## 8. How does Next.js handle CSS?

**Answer:**
Next.js supports:
- **Global CSS** (`styles/global.css`)
- **CSS Modules** (`Component.module.css`)
- **Sass/SCSS Support** (`styles/global.scss`)
- **Styled Components** (via third-party libraries)

Example:
```css
/* styles/Home.module.css */
.title {
  color: blue;
}
```
```js
import styles from './Home.module.css';
export default function Home() {
  return <h1 className={styles.title}>Hello Next.js</h1>;
}
```

---

## 9. How to handle redirects in Next.js?

**Answer:**
Redirects are configured in `next.config.js`.

Example:
```js
module.exports = {
  async redirects() {
    return [{
      source: '/old-page',
      destination: '/new-page',
      permanent: true,
    }];
  },
};
```

---

## 10. What are middleware functions in Next.js?

**Answer:**
Middleware functions in Next.js **intercept requests** before reaching API routes or pages.

Example:
```js
// middleware.ts
import { NextResponse } from 'next/server';
export function middleware(req) {
  if (!req.cookies.token) {
    return NextResponse.redirect('/login');
  }
}
```

---

## 11. How does Next.js optimize images?

**Answer:**
Next.js provides the `next/image` component for automatic image optimization.

Example:
```js
import Image from 'next/image';
<Image src="/image.jpg" width={500} height={300} alt="Optimized Image" />
```

---

## 12. How do you deploy a Next.js app?

**Answer:**
- **Vercel** (recommended): `vercel deploy`
- **Static Export**: `next build && next export`
- **Custom Server**: Deploy using Node.js and Express.

Example:
```sh
npm run build
npm start
```

---

## 13. How do you enable environment variables in Next.js?

**Answer:**
Create a `.env.local` file:
```
NEXT_PUBLIC_API_URL=https://api.example.com
```
Access it in your code:
```js
const apiUrl = process.env.NEXT_PUBLIC_API_URL;
```

---

## 14. What is the difference between `next/link` and `next/router`?

**Answer:**
- `next/link` – Used for client-side navigation.
- `next/router` – Provides programmatic navigation.

Example:
```js
import Link from 'next/link';
<Link href="/about">Go to About</Link>;
```
```js
import { useRouter } from 'next/router';
const router = useRouter();
router.push('/dashboard');
```

---

## 15. How do you handle authentication in Next.js?

**Answer:**
- Use **NextAuth.js** for easy OAuth & JWT authentication.
- Implement **JWT-based authentication** using API routes.

Example:
```js
import { getSession } from 'next-auth/react';
export async function getServerSideProps(context) {
  const session = await getSession(context);
  if (!session) return { redirect: { destination: '/login', permanent: false } };
  return { props: { user: session.user } };
}
```


# Docker

## 1. What is Docker?
**Answer:**
Docker is an open-source platform that enables developers to automate the deployment, scaling, and management of applications using containerization.

---

## 2. What is a Docker Container?
**Answer:**
A Docker container is a lightweight, standalone, executable package that includes everything needed to run an application: code, runtime, libraries, and dependencies.

---

## 3. What is a Docker Image?
**Answer:**
A Docker image is a read-only template used to create containers. It contains application code, libraries, dependencies, and configuration files.

---

## 4. What is the difference between a Docker Image and a Container?
**Answer:**
- **Image**: A template with the application and dependencies.
- **Container**: A running instance of an image.

---

## 5. How do you create and run a Docker container?
**Answer:**
```sh
docker build -t myapp .  # Build image
docker run -d -p 8080:80 myapp  # Run container
```

---

## 6. What is a Dockerfile?
**Answer:**
A Dockerfile is a script containing instructions to automate the creation of Docker images.

Example:
```dockerfile
FROM node:16
WORKDIR /app
COPY . .
RUN npm install
CMD ["node", "server.js"]
```

---

## 7. What is the difference between `CMD` and `ENTRYPOINT`?
**Answer:**
- **CMD**: Provides default commands that can be overridden.
- **ENTRYPOINT**: Defines a fixed command that always runs.

Example:
```dockerfile
ENTRYPOINT ["python", "app.py"]
```

---

## 8. What is a Docker Volume?
**Answer:**
A Docker volume is used to persist data outside a container’s lifecycle.

Example:
```sh
docker volume create mydata
docker run -v mydata:/app/data myapp
```

---

## 9. What are Docker Networks?
**Answer:**
Docker networking enables communication between containers.
- **Bridge** (default)
- **Host**
- **None**
- **Overlay**

Example:
```sh
docker network create mynetwork
docker network connect mynetwork mycontainer
```

---

## 10. What is Docker Compose?
**Answer:**
Docker Compose is a tool for defining and running multi-container applications.

Example `docker-compose.yml`:
```yaml
version: '3'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
```

Start with:
```sh
docker-compose up -d
```

---

## 11. What is the difference between Docker and Virtual Machines?
**Answer:**
- **VMs**: Require a full OS per instance.
- **Docker**: Uses a shared OS kernel, making it more lightweight and efficient.

---

## 12. What is a Multi-Stage Build in Docker?
**Answer:**
A multi-stage build helps reduce image size by using intermediate containers.

Example:
```dockerfile
FROM golang:alpine AS builder
WORKDIR /app
COPY . .
RUN go build -o main .

FROM alpine
COPY --from=builder /app/main /app/main
CMD ["/app/main"]
```

---

## 13. What is Docker Swarm?
**Answer:**
Docker Swarm is Docker’s native clustering and orchestration tool for managing a cluster of Docker nodes.

Example:
```sh
docker swarm init
docker service create --replicas 3 -p 80:80 nginx
```

---

## 14. How do you inspect a running Docker container?
**Answer:**
```sh
docker ps  # List running containers
docker inspect <container_id>  # Get detailed info
docker logs <container_id>  # View logs
docker exec -it <container_id> /bin/sh  # Access shell
```

---

## 15. What is the difference between `docker stop`, `docker kill`, and `docker rm`?
**Answer:**
- **docker stop**: Gracefully stops a container.
- **docker kill**: Forces a container to stop immediately.
- **docker rm**: Removes a stopped container.

Example:
```sh
docker stop mycontainer
docker kill mycontainer
docker rm mycontainer
```

---

## 16. What are some security best practices for Docker?
**Answer:**
- Use minimal base images (e.g., `alpine` instead of `ubuntu`).
- Avoid running containers as root.
- Regularly scan images for vulnerabilities (`docker scan`).
- Restrict container privileges using AppArmor or SELinux.

---

## 17. How do you clean up unused Docker resources?
**Answer:**
```sh
docker system prune -a  # Remove unused images, containers, and networks
docker volume prune  # Remove unused volumes
```

---

## 18. What is Docker BuildKit?
**Answer:**
BuildKit improves the speed and security of Docker builds.

Enable it with:
```sh
export DOCKER_BUILDKIT=1
docker build .
```

---

## 19. How do you push a Docker image to Docker Hub?
**Answer:**
```sh
docker login -u myusername -p mypassword
docker tag myapp myusername/myapp:v1
docker push myusername/myapp:v1
```

---

## 20. What is the difference between `ADD` and `COPY` in Dockerfile?
**Answer:**
- **COPY**: Copies files from the local system to the container.
- **ADD**: Like `COPY`, but also allows remote URL fetching and file extraction.

Example:
```dockerfile
COPY myfile.txt /app/
ADD archive.tar.gz /app/
```


# Nginx

## 1. What is Nginx?
**Answer:**
Nginx is a high-performance web server, reverse proxy, and load balancer used to handle HTTP and other network protocols efficiently.

---

## 2. What are the key features of Nginx?
**Answer:**
- Reverse proxy with caching
- Load balancing
- FastCGI, SCGI, and uWSGI support
- TLS/SSL termination
- Static file serving
- WebSockets support

---

## 3. What is the difference between Apache and Nginx?
**Answer:**
| Feature       | Apache            | Nginx               |
|--------------|------------------|--------------------|
| Process Model | Multi-threaded (mpm_prefork) | Event-driven, asynchronous |
| Performance  | Slower for high concurrency | Handles many connections efficiently |
| Configuration | .htaccess per directory | Single configuration file |
| Static Content | Slower | Faster |

---

## 4. How do you install Nginx on Linux?
**Answer:**
```sh
sudo apt update
sudo apt install nginx -y
```
To start and enable:
```sh
sudo systemctl start nginx
sudo systemctl enable nginx
```

---

## 5. How do you check the status of Nginx?
**Answer:**
```sh
sudo systemctl status nginx
```
Or test the configuration:
```sh
nginx -t
```

---

## 6. What is the default configuration file for Nginx?
**Answer:**
The default configuration file is located at:
```sh
/etc/nginx/nginx.conf
```

---

## 7. How do you restart Nginx?
**Answer:**
```sh
sudo systemctl restart nginx
```

---

## 8. What is an Nginx reverse proxy?
**Answer:**
A reverse proxy forwards client requests to backend servers, providing load balancing, caching, and security features.

Example configuration:
```nginx
server {
    listen 80;
    location / {
        proxy_pass http://backend_server;
        proxy_set_header Host $host;
    }
}
```

---

## 9. How do you configure Nginx as a load balancer?
**Answer:**
Example configuration:
```nginx
upstream backend {
    server server1.example.com;
    server server2.example.com;
}

server {
    listen 80;
    location / {
        proxy_pass http://backend;
    }
}
```

---

## 10. How do you enable HTTPS in Nginx?
**Answer:**
Use SSL certificates with the following configuration:
```nginx
server {
    listen 443 ssl;
    server_name example.com;
    ssl_certificate /etc/ssl/certs/example.crt;
    ssl_certificate_key /etc/ssl/private/example.key;
}
```

---

## 11. How do you redirect HTTP to HTTPS in Nginx?
**Answer:**
```nginx
server {
    listen 80;
    server_name example.com;
    return 301 https://$host$request_uri;
}
```

---

## 12. How do you serve static files with Nginx?
**Answer:**
```nginx
server {
    listen 80;
    root /var/www/html;
    index index.html;
}
```

---

## 13. What is Nginx caching?
**Answer:**
Nginx caching stores static responses to improve performance. Example:
```nginx
location / {
    proxy_cache my_cache;
    proxy_pass http://backend;
}
```

---

## 14. How do you block an IP in Nginx?
**Answer:**
```nginx
server {
    deny 192.168.1.1;
}
```

---

## 15. How do you set up basic authentication in Nginx?
**Answer:**
```nginx
location /secure {
    auth_basic "Restricted";
    auth_basic_user_file /etc/nginx/.htpasswd;
}
```
Generate password file:
```sh
echo "user:$(openssl passwd -crypt password)" | sudo tee -a /etc/nginx/.htpasswd
```

---

## 16. How do you enable gzip compression in Nginx?
**Answer:**
```nginx
gzip on;
gzip_types text/plain application/json;
```

---

## 17. How do you monitor Nginx logs?
**Answer:**
```sh
tail -f /var/log/nginx/access.log
```

---

## 18. What is a 502 Bad Gateway error in Nginx?
**Answer:**
This occurs when the backend server is unreachable. Check:
- Backend server status
- `proxy_pass` configuration

---

## 19. How do you configure Nginx with PHP?
**Answer:**
```nginx
server {
    location ~ \.php$ {
        fastcgi_pass unix:/run/php/php7.4-fpm.sock;
        include fastcgi_params;
    }
}
```

---

## 20. How do you optimize Nginx performance?
**Answer:**
- Enable caching
- Use gzip compression
- Optimize worker processes (`worker_processes auto;`)
- Load balance traffic


# Kubernetes

## 1. What is Kubernetes?
**Answer:**
Kubernetes (K8s) is an open-source container orchestration platform for managing containerized applications across multiple hosts, providing automation, scaling, and management.

---

## 2. What are the main components of Kubernetes architecture?
**Answer:**
- **Master Node:** API Server, Controller Manager, Scheduler, etcd
- **Worker Nodes:** Kubelet, Kube Proxy, Container Runtime (Docker, CRI-O)
- **Pods:** Smallest deployable units in Kubernetes

---

## 3. What is a Pod in Kubernetes?
**Answer:**
A Pod is the smallest deployable unit in Kubernetes that contains one or more containers sharing networking and storage.

---

## 4. What is a ReplicaSet?
**Answer:**
A ReplicaSet ensures a specified number of pod replicas are running at all times.
```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: my-replicaset
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-container
        image: nginx
```

---

## 5. What is a Deployment in Kubernetes?
**Answer:**
A Deployment manages ReplicaSets and provides rollout, rollback, and scaling of applications.
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-container
        image: nginx
```

---

## 6. What is a Service in Kubernetes?
**Answer:**
A Service exposes a set of Pods as a network service.
```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app: my-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
```

---

## 7. What are the types of Kubernetes Services?
**Answer:**
- **ClusterIP:** Default, accessible within the cluster
- **NodePort:** Exposes the service on a static port on each node
- **LoadBalancer:** Provisions an external load balancer
- **ExternalName:** Maps to an external domain

---

## 8. What is a ConfigMap in Kubernetes?
**Answer:**
A ConfigMap is used to store non-confidential configuration data.
```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: my-config
  data:
    database_url: "mongodb://db:27017"
```

---

## 9. What is a Secret in Kubernetes?
**Answer:**
A Secret is used to store confidential information like passwords and API keys.
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: my-secret
  type: Opaque
  data:
    password: cGFzc3dvcmQ=
```

---

## 10. What is a Persistent Volume (PV)?
**Answer:**
A Persistent Volume provides long-term storage for Pods.
```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: my-pv
spec:
  capacity:
    storage: 1Gi
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain
```

---

## 11. What is a Persistent Volume Claim (PVC)?
**Answer:**
A PVC requests storage from a Persistent Volume.
```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: my-pvc
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
```

---

## 12. How do you scale a Deployment in Kubernetes?
**Answer:**
Using `kubectl scale`:
```sh
kubectl scale deployment my-deployment --replicas=5
```
Or by updating the Deployment YAML.

---

## 13. What is a DaemonSet in Kubernetes?
**Answer:**
A DaemonSet ensures a Pod runs on every node in the cluster.
```yaml
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: my-daemonset
spec:
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-container
        image: busybox
```

---

## 14. What is an Ingress in Kubernetes?
**Answer:**
An Ingress manages external access to services inside the cluster using HTTP/HTTPS.
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: my-ingress
spec:
  rules:
  - host: example.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: my-service
            port:
              number: 80
```

---

## 15. How do you check the logs of a running Pod?
**Answer:**
```sh
kubectl logs my-pod
```
For a specific container in a pod:
```sh
kubectl logs my-pod -c my-container
```

---

## 16. How do you troubleshoot a failing pod?
**Answer:**
- Check pod status: `kubectl get pods`
- Describe the pod: `kubectl describe pod my-pod`
- View logs: `kubectl logs my-pod`
- Access container shell: `kubectl exec -it my-pod -- /bin/sh`

---

## 17. What is a Horizontal Pod Autoscaler (HPA)?
**Answer:**
HPA automatically scales the number of pods based on CPU/memory usage.
```sh
kubectl autoscale deployment my-deployment --cpu-percent=50 --min=2 --max=10
```

---

## 18. What is a StatefulSet?
**Answer:**
StatefulSets are used for stateful applications where each pod has a unique identity.
```yaml
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: my-statefulset
spec:
  serviceName: my-service
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-container
        image: nginx
```

---

## 19. What is Helm in Kubernetes?
**Answer:**
Helm is a package manager for Kubernetes that simplifies application deployment using charts.

---

## 20. How do you delete a Kubernetes resource?
**Answer:**
```sh
kubectl delete pod my-pod
kubectl delete deployment my-deployment
kubectl delete service my-service
```

# MinIO

## 1. What is MinIO?
**Answer:**
MinIO is a high-performance, open-source object storage system compatible with Amazon S3, designed for cloud-native environments, AI/ML workloads, and large-scale data storage.

---

## 2. How is MinIO different from AWS S3?
**Answer:**
- MinIO is self-hosted, whereas AWS S3 is a managed service.
- MinIO provides better performance for on-premise and edge deployments.
- MinIO is open-source and can be deployed on any infrastructure.

---

## 3. What are the key features of MinIO?
**Answer:**
- Amazon S3 API compatibility
- High availability with distributed deployment
- Erasure coding for data protection
- Encryption at rest and in transit
- Multi-tenancy support
- Lambda compute functionality

---

## 4. How do you install MinIO?
**Answer:**
```sh
wget https://dl.min.io/server/minio/release/linux-amd64/minio
chmod +x minio
sudo mv minio /usr/local/bin/
```
Or using Docker:
```sh
docker run -p 9000:9000 -p 9001:9001 --name minio \
  -e "MINIO_ROOT_USER=admin" -e "MINIO_ROOT_PASSWORD=password" \
  quay.io/minio/minio server /data --console-address ":9001"
```

---

## 5. What is Erasure Coding in MinIO?
**Answer:**
Erasure coding is a data protection technique that splits data into multiple shards, adding parity information to recover lost data without full replication.

---

## 6. How do you create a bucket in MinIO?
**Answer:**
Using the MinIO Client (mc):
```sh
mc alias set myminio http://localhost:9000 admin password
mc mb myminio/my-bucket
```

---

## 7. How do you upload a file to MinIO?
**Answer:**
```sh
mc alias set myminio http://localhost:9000 admin password
mc cp myfile.txt myminio/my-bucket/
```

---

## 8. How do you configure MinIO for high availability?
**Answer:**
MinIO can be deployed in distributed mode:
```sh
docker run -p 9000:9000 -p 9001:9001 --name minio \
  -e "MINIO_ROOT_USER=admin" -e "MINIO_ROOT_PASSWORD=password" \
  minio/minio server http://server{1...4}/data
```
This setup requires at least 4 nodes.

---

## 9. How do you enable MinIO encryption?
**Answer:**
MinIO supports SSE (Server-Side Encryption):
```sh
export MINIO_KMS_SECRET_KEY="my-secret-key"
minio server /data
```

---

## 10. How do you list all buckets in MinIO?
**Answer:**
```sh
mc ls myminio
```

---

## 11. How do you delete an object in MinIO?
**Answer:**
```sh
mc rm myminio/my-bucket/myfile.txt
```

---

## 12. How do you enable versioning in MinIO?
**Answer:**
```sh
mc version enable myminio/my-bucket
```

---

## 13. What is the MinIO Console?
**Answer:**
MinIO Console is a web-based UI for managing MinIO deployments, available at `http://localhost:9001`.

---

## 14. How do you set bucket policies in MinIO?
**Answer:**
```sh
mc policy set public myminio/my-bucket
```

---

## 15. How do you monitor MinIO?
**Answer:**
MinIO provides Prometheus-compatible metrics at `http://localhost:9000/minio/v2/metrics/cluster`.

---

## 16. How do you integrate MinIO with Kubernetes?
**Answer:**
Using MinIO Operator:
```sh
kubectl apply -k github.com/minio/operator/
```

---

## 17. What is MinIO Gateway?
**Answer:**
MinIO Gateway allows using MinIO as a caching layer for external storage like AWS S3 or NAS.

---

## 18. How do you use MinIO with Terraform?
**Answer:**
```hcl
provider "aws" {
  access_key = "admin"
  secret_key = "password"
  endpoint   = "http://localhost:9000"
  region     = "us-east-1"
  s3_force_path_style = true
}
```

---

## 19. What authentication methods does MinIO support?
**Answer:**
- Access keys
- JWT-based authentication
- LDAP/Active Directory integration

---

## 20. How do you delete a bucket in MinIO?
**Answer:**
```sh
mc rb --force myminio/my-bucket
```



# Design Patterns

## 1. What are Design Patterns?
**Answer:**
Design patterns are reusable solutions to common software design problems. They provide a standardized approach to solving recurring issues in software development.

---

## 2. What are the main categories of Design Patterns?
**Answer:**
Design patterns are categorized into three main types:
- **Creational Patterns**: Deal with object creation mechanisms (e.g., Singleton, Factory, Builder, Prototype, Abstract Factory).
- **Structural Patterns**: Deal with object composition (e.g., Adapter, Bridge, Composite, Decorator, Facade, Proxy, Flyweight).
- **Behavioral Patterns**: Focus on communication between objects (e.g., Observer, Strategy, Command, Chain of Responsibility, State, Template Method, Mediator, Memento, Visitor).

---

## 3. Explain the Singleton Pattern.
**Answer:**
The Singleton pattern ensures that a class has only one instance and provides a global point of access to it.

**Example in JavaScript:**
```js
class Singleton {
  constructor() {
    if (!Singleton.instance) {
      Singleton.instance = this;
    }
    return Singleton.instance;
  }
}
const instance1 = new Singleton();
const instance2 = new Singleton();
console.log(instance1 === instance2); // true
```

---

## 4. What is the Factory Method Pattern?
**Answer:**
The Factory Method pattern provides an interface for creating objects but allows subclasses to alter the type of objects that will be created.

**Example:**
```js
class Factory {
  static create(type) {
    if (type === 'A') return new ProductA();
    if (type === 'B') return new ProductB();
  }
}
```

---

## 5. What is the Observer Pattern?
**Answer:**
The Observer pattern defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified automatically.

**Example:**
```js
class Subject {
  constructor() {
    this.observers = [];
  }
  addObserver(observer) { this.observers.push(observer); }
  notifyObservers() { this.observers.forEach(o => o.update()); }
}
class Observer {
  update() { console.log('State updated!'); }
}
```

---

## 6. What is the Strategy Pattern?
**Answer:**
The Strategy pattern defines a family of algorithms, encapsulates each one, and makes them interchangeable.

**Example:**
```js
class StrategyA {
  execute() { console.log('Executing strategy A'); }
}
class StrategyB {
  execute() { console.log('Executing strategy B'); }
}
class Context {
  setStrategy(strategy) { this.strategy = strategy; }
  executeStrategy() { this.strategy.execute(); }
}
```

---

## 7. What is the Decorator Pattern?
**Answer:**
The Decorator pattern dynamically adds responsibilities to objects without modifying their existing code.

**Example:**
```js
class Coffee {
  cost() { return 5; }
}
class MilkDecorator {
  constructor(coffee) { this.coffee = coffee; }
  cost() { return this.coffee.cost() + 2; }
}
```

---

## 8. What is the Adapter Pattern?
**Answer:**
The Adapter pattern allows incompatible interfaces to work together.

**Example:**
```js
class OldSystem {
  oldMethod() { return 'Old system method'; }
}
class Adapter {
  constructor(oldSystem) { this.oldSystem = oldSystem; }
  newMethod() { return this.oldSystem.oldMethod(); }
}
```

---

## 9. What is the Proxy Pattern?
**Answer:**
The Proxy pattern provides a surrogate or placeholder for another object to control access to it.

**Example:**
```js
class RealSubject {
  request() { console.log('Real request'); }
}
class Proxy {
  constructor(realSubject) { this.realSubject = realSubject; }
  request() { console.log('Proxy in action'); this.realSubject.request(); }
}
```

---

## 10. What is the Command Pattern?
**Answer:**
The Command pattern encapsulates a request as an object, allowing parameterization of clients with different requests.

**Example:**
```js
class Command {
  execute() {}
}
class LightOnCommand extends Command {
  execute() { console.log('Light turned on'); }
}
```

---

## 11. What is the Template Method Pattern?
**Answer:**
The Template Method pattern defines the skeleton of an algorithm, deferring steps to subclasses.

**Example:**
```js
class AbstractClass {
  templateMethod() { this.step1(); this.step2(); }
  step1() {}
  step2() {}
}
class ConcreteClass extends AbstractClass {
  step1() { console.log('Step 1 implemented'); }
}
```

---

## 12. What is the Facade Pattern?
**Answer:**
The Facade pattern provides a simplified interface to a complex subsystem.

**Example:**
```js
class Subsystem {
  operation() { console.log('Subsystem operation'); }
}
class Facade {
  constructor() { this.subsystem = new Subsystem(); }
  operation() { this.subsystem.operation(); }
}
```

---

## 13. What is the Chain of Responsibility Pattern?
**Answer:**
The Chain of Responsibility pattern passes a request along a chain of handlers.

**Example:**
```js
class Handler {
  setNext(handler) { this.nextHandler = handler; }
  handle(request) { if (this.nextHandler) this.nextHandler.handle(request); }
}
```

---

## 14. What is the Flyweight Pattern?
**Answer:**
The Flyweight pattern minimizes memory usage by sharing as much data as possible between similar objects.

**Example:**
```js
class Flyweight {
  operation() { console.log('Flyweight operation'); }
}
class FlyweightFactory {
  constructor() { this.flyweights = {}; }
  getFlyweight(key) {
    if (!this.flyweights[key]) {
      this.flyweights[key] = new Flyweight();
    }
    return this.flyweights[key];
  }
}
```

---

## 15. What is the State Pattern?
**Answer:**
The State pattern allows an object to alter its behavior when its internal state changes.

**Example:**
```js
class State {
  handle() {}
}
class ConcreteStateA extends State {
  handle() { console.log('State A'); }
}
class Context {
  setState(state) { this.state = state; }
  request() { this.state.handle(); }
}
```







# Python

## 1. What are Python’s key features?
**Answer:**
- Easy to learn and read
- Interpreted language
- Dynamically typed
- Supports multiple programming paradigms (OOP, functional, procedural)
- Extensive standard library
- Open-source and community-driven
- Cross-platform compatibility

---

## 2. What is the difference between Python 2 and Python 3?
**Answer:**
- Python 3 has improved Unicode support.
- Print statement is replaced with `print()` function.
- Integer division returns a float by default.
- Iterators behave differently (`range()` in Python 3 returns an iterator instead of a list).

---

## 3. What are Python’s built-in data types?
**Answer:**
- **Numeric types:** `int`, `float`, `complex`
- **Sequence types:** `list`, `tuple`, `range`
- **Set types:** `set`, `frozenset`
- **Mapping types:** `dict`
- **Boolean type:** `bool`
- **Binary types:** `bytes`, `bytearray`, `memoryview`

---

## 4. What is the difference between a list and a tuple?
**Answer:**
- **List:** Mutable, can be modified, slower, defined using `[]`.
- **Tuple:** Immutable, faster, defined using `()`.

**Example:**
```python
my_list = [1, 2, 3]
my_tuple = (1, 2, 3)
```

---

## 5. What are Python’s mutable and immutable data types?
**Answer:**
- **Mutable:** `list`, `dict`, `set`, `bytearray`
- **Immutable:** `int`, `float`, `bool`, `str`, `tuple`, `frozenset`

---

## 6. What is a lambda function?
**Answer:**
A lambda function is an anonymous function defined using the `lambda` keyword.

**Example:**
```python
square = lambda x: x ** 2
print(square(5))  # Output: 25
```

---

## 7. What is the difference between `deepcopy()` and `copy()`?
**Answer:**
- **`copy.copy()`**: Creates a shallow copy (references nested objects instead of copying them).
- **`copy.deepcopy()`**: Creates a deep copy (recursively copies all nested objects).

---

## 8. What is Python’s `self` keyword?
**Answer:**
The `self` keyword represents the instance of the class and is used to access class attributes and methods.

**Example:**
```python
class Example:
    def __init__(self, value):
        self.value = value
    def show(self):
        print(self.value)
```

---

## 9. What is Python’s `__init__` method?
**Answer:**
The `__init__` method is the constructor method in Python, executed when an object is created.

**Example:**
```python
class Person:
    def __init__(self, name):
        self.name = name
```

---

## 10. What are Python’s magic methods?
**Answer:**
Magic methods (dunder methods) are special methods with double underscores, such as:
- `__init__` (constructor)
- `__str__` (string representation)
- `__len__` (length)
- `__getitem__` (indexing)
- `__setattr__` (attribute setting)

---

## 11. What is the difference between `is` and `==` in Python?
**Answer:**
- `is`: Compares object identity (memory location).
- `==`: Compares values.

**Example:**
```python
x = [1, 2, 3]
y = x
z = [1, 2, 3]
print(x is y)  # True
print(x == z)  # True
print(x is z)  # False
```

---

## 12. What are Python’s decorators?
**Answer:**
Decorators are functions that modify the behavior of other functions.

**Example:**
```python
def decorator(func):
    def wrapper():
        print("Before function execution")
        func()
        print("After function execution")
    return wrapper

@decorator
def say_hello():
    print("Hello!")

say_hello()
```

---

## 13. How does Python manage memory?
**Answer:**
- Uses automatic garbage collection.
- Reference counting and cyclic garbage collection.
- Objects are stored in private heap space.

---

## 14. What is the difference between a generator and an iterator?
**Answer:**
- **Iterator**: An object that implements `__iter__()` and `__next__()` methods.
- **Generator**: A function that yields values using `yield` and retains state.

**Example of a generator:**
```python
def my_generator():
    yield 1
    yield 2
    yield 3
```

---

## 15. What is multithreading in Python? Does Python support true multithreading?
**Answer:**
- Python has a `threading` module for multithreading.
- Due to the Global Interpreter Lock (GIL), Python does not support true parallel threads for CPU-bound tasks but works well for I/O-bound tasks.

---

## 16. What is a Python module and package?
**Answer:**
- **Module:** A `.py` file containing Python code.
- **Package:** A directory containing multiple modules, with an `__init__.py` file.

---

## 17. How do you handle exceptions in Python?
**Answer:**
Using `try-except` blocks.

**Example:**
```python
try:
    x = 1 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")
```

---

## 18. What is the difference between `@staticmethod`, `@classmethod`, and instance methods?
**Answer:**
- **Instance method:** Works on instance data (default method).
- **Class method (`@classmethod`)**: Works with class attributes, takes `cls` as a parameter.
- **Static method (`@staticmethod`)**: Does not depend on instance or class attributes.

---

## 19. What is the difference between `del`, `remove()`, and `pop()`?
**Answer:**
- `del`: Deletes a variable or index.
- `remove()`: Removes an element by value.
- `pop()`: Removes an element by index and returns it.

---

## 20. What is a virtual environment in Python?
**Answer:**
A virtual environment is an isolated Python environment where dependencies are managed separately for different projects.

**Example:**
```sh
python -m venv myenv
source myenv/bin/activate  # (Linux/macOS)
myenv\Scripts\activate  # (Windows)
```



# FastAPI

## 1. What is FastAPI?
**Answer:**
FastAPI is a modern, high-performance web framework for building APIs with Python 3. It is based on Starlette and Pydantic and is known for its speed, automatic interactive documentation, and ease of use.

---

## 2. What are the key features of FastAPI?
**Answer:**
- Asynchronous support with `async` and `await`.
- Automatic generation of OpenAPI and Swagger documentation.
- Data validation using Pydantic.
- Dependency injection system.
- High performance, similar to Node.js and Go.
- Type hints for request parameters.

---

## 3. How do you install FastAPI and run a server?
**Answer:**
```sh
pip install fastapi uvicorn
```
Then, create a simple FastAPI app:
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello, FastAPI!"}
```
Run it using Uvicorn:
```sh
uvicorn main:app --reload
```

---

## 4. What is Uvicorn, and why is it used with FastAPI?
**Answer:**
Uvicorn is an ASGI (Asynchronous Server Gateway Interface) server that runs FastAPI applications. It is used because it provides high-performance, asynchronous capabilities required for FastAPI apps.

---

## 5. How do you define query parameters in FastAPI?
**Answer:**
```python
@app.get("/items/")
def read_item(name: str, quantity: int = 1):
    return {"name": name, "quantity": quantity}
```

**Example request:** `GET /items/?name=apple&quantity=5`

---

## 6. How do you define path parameters in FastAPI?
**Answer:**
```python
@app.get("/items/{item_id}")
def read_item(item_id: int):
    return {"item_id": item_id}
```
**Example request:** `GET /items/10`

---

## 7. How does FastAPI handle request body parsing?
**Answer:**
FastAPI uses Pydantic models for request body validation.
```python
from pydantic import BaseModel

class Item(BaseModel):
    name: str
    price: float
    in_stock: bool

@app.post("/items/")
def create_item(item: Item):
    return {"message": "Item created", "item": item}
```
---

## 8. How do you add middleware in FastAPI?
**Answer:**
```python
from fastapi.middleware.cors import CORSMiddleware

app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)
```

---

## 9. How do you handle dependencies in FastAPI?
**Answer:**
```python
from fastapi import Depends

def common_parameters(q: str = None):
    return {"q": q}

@app.get("/search/")
def search(params: dict = Depends(common_parameters)):
    return params
```

---

## 10. How does FastAPI support authentication and authorization?
**Answer:**
FastAPI supports OAuth2, JWT, and API keys for authentication. Example using OAuth2:
```python
from fastapi.security import OAuth2PasswordBearer

oauth2_scheme = OAuth2PasswordBearer(tokenUrl="token")

@app.get("/users/me")
def read_users_me(token: str = Depends(oauth2_scheme)):
    return {"token": token}
```

---

## 11. How do you use background tasks in FastAPI?
**Answer:**
```python
from fastapi import BackgroundTasks

def send_email(email: str):
    print(f"Sending email to {email}")

@app.post("/send-email/")
def request_email(email: str, background_tasks: BackgroundTasks):
    background_tasks.add_task(send_email, email)
    return {"message": "Email will be sent in the background"}
```

---

## 12. How do you add API documentation in FastAPI?
**Answer:**
FastAPI automatically generates OpenAPI documentation, accessible at:
- **Swagger UI:** `http://127.0.0.1:8000/docs`
- **ReDoc UI:** `http://127.0.0.1:8000/redoc`

---

## 13. What are some real-world use cases of FastAPI?
**Answer:**
- Building RESTful APIs.
- Microservices.
- AI and ML model deployment.
- WebSockets and real-time applications.

---

## 14. What is the difference between FastAPI and Flask?
**Answer:**
| Feature      | FastAPI | Flask |
|-------------|--------|-------|
| Performance | Fast   | Slower |
| Async Support | Yes | No (by default) |
| Type Hints | Yes | No |
| Documentation | Auto-generated | Manual |

---

## 15. How do you handle file uploads in FastAPI?
**Answer:**
```python
from fastapi import File, UploadFile

@app.post("/upload/")
def upload_file(file: UploadFile = File(...)):
    return {"filename": file.filename}
```

---

## 16. How do you connect FastAPI with databases?
**Answer:**
Using SQLAlchemy:
```python
from sqlalchemy import create_engine
DATABASE_URL = "sqlite:///./test.db"
engine = create_engine(DATABASE_URL)
```
FastAPI also supports async ORMs like Tortoise-ORM.

---

## 17. How do you structure a FastAPI project?
**Answer:**
A common structure:
```
project/
│── main.py
│── models.py
│── schemas.py
│── routes/
│   ├── users.py
│   ├── items.py
│── database.py
│── config.py
```

---

## 18. How does FastAPI handle response models?
**Answer:**
```python
from pydantic import BaseModel

class ItemResponse(BaseModel):
    name: str
    price: float

@app.get("/items/{item_id}", response_model=ItemResponse)
def get_item(item_id: int):
    return {"name": "Laptop", "price": 1200.00}
```

---

## 19. How do you add logging in FastAPI?
**Answer:**
```python
import logging
logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)
logger.info("Application started")
```

---

## 20. How do you deploy a FastAPI app?
**Answer:**
- Using **Uvicorn**:
  ```sh
  uvicorn main:app --host 0.0.0.0 --port 8000 --workers 4
  ```
- Using **Docker**:
  ```dockerfile
  FROM python:3.9
  WORKDIR /app
  COPY . .
  RUN pip install fastapi uvicorn
  CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
  ```







