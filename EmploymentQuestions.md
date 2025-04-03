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

















