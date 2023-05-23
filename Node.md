# REST API and its methods

REST (Representational State Transfer) is an architectural style that provides a set of principles for building web services. In a RESTful architecture, the communication between the client and the server is done through HTTP protocols, and resources are represented as URLs (Uniform Resource Locators).

REST APIs (Application Programming Interfaces) are the implementations of the REST principles that allow different software applications to communicate with each other over a network. REST APIs use various HTTP methods to perform different actions on the resources. Here are the commonly used HTTP methods in RESTful APIs:

1. GET: The GET method is used to retrieve or read a representation of a resource. It is an idempotent operation, meaning that multiple identical requests will have the same effect as a single request. GET requests should not have any side effects on the server or the resource itself. For example, retrieving a list of users or fetching a specific user's details.

2. POST: The POST method is used to submit or create new resources on the server. It sends data to the server to be processed. Each POST request typically results in a new resource being created on the server. For example, creating a new user by sending user details in the request body.

3. PUT: The PUT method is used to update or replace an existing resource on the server. It requires sending the entire representation of the resource to be updated. If the resource does not exist, PUT can also be used to create a new resource. For example, updating a user's details by sending the modified user object.

4. PATCH: The PATCH method is used to update or modify a part of an existing resource on the server. Unlike PUT, which requires sending the entire resource representation, PATCH allows sending only the changes that need to be applied. For example, updating only the email address of a user without sending the entire user object.

5. DELETE: The DELETE method is used to remove or delete a resource on the server. It performs the deletion of the specified resource. For example, deleting a user by specifying the user ID in the request.

These HTTP methods, combined with the appropriate URLs and request payloads, allow clients to perform various operations on resources exposed by a RESTful API. The response from the server typically includes the status code, indicating the success or failure of the operation, and the representation of the requested resource (if applicable).

It's important to note that REST APIs should follow the principles of statelessness, using standard HTTP status codes and providing a consistent and uniform interface for interacting with resources.











# Callback functions

In JavaScript, a callback function is a function that is passed as an argument to another function and is invoked or called within that function. The purpose of using a callback function is to allow asynchronous or non-blocking operations, where the code can continue executing while waiting for a certain event or operation to complete.

Here's a simple example to illustrate the concept of callback functions in JavaScript:

```javascript
function processResult(result, callback) {
  // Perform some asynchronous operation
  // ...

  // Once the operation is complete, invoke the callback function
  callback(result);
}

function handleResult(data) {
  console.log('Received result:', data);
}

// Calling the function and passing the callback function as an argument
processResult('Some data', handleResult);
```

In the example above, the `processResult` function takes two parameters: `result` and `callback`. It performs some asynchronous operation (which is not shown in the example) and once it's done, it invokes the `callback` function, passing the `result` as an argument.

The `handleResult` function is defined separately and acts as the callback function. It receives the `data` argument passed from the `processResult` function and logs it to the console.

By using a callback function, we can ensure that the `handleResult` function is executed only after the asynchronous operation in `processResult` is complete. This allows us to handle the result or perform further actions with the data once it becomes available.

Callbacks are commonly used in JavaScript for handling events, making AJAX requests, working with timers, and dealing with other asynchronous operations. They provide a way to execute code in response to an event or completion of an operation without blocking the execution of other code.

# Success and Error codes

In the context of web development and APIs, error and success codes are used to indicate the outcome of a request or operation. These codes are typically returned as part of the HTTP response from the server to the client, allowing the client to understand the result of their request. Here are some common error and success codes:

1. HTTP Success Codes (2xx):
   - 200 OK: The request was successful, and the server returned the requested resource.
   - 201 Created: The request was successful, and a new resource was created as a result.
   - 204 No Content: The request was successful, but there is no content to return.

2. HTTP Redirection Codes (3xx):
   - 301 Moved Permanently: The requested resource has been permanently moved to a new URL.
   - 302 Found/Redirect: The requested resource has been temporarily moved to a different URL.
   - 304 Not Modified: The requested resource has not been modified since the last request.

3. HTTP Client Error Codes (4xx):
   - 400 Bad Request: The server cannot understand the request due to invalid syntax or parameters.
   - 401 Unauthorized: The request requires authentication or the provided credentials are invalid.
   - 403 Forbidden: The server understood the request but refuses to authorize it.
   - 404 Not Found: The requested resource could not be found on the server.
   - 405 Method Not Allowed: The requested HTTP method is not allowed for the specified resource.

4. HTTP Server Error Codes (5xx):
   - 500 Internal Server Error: A generic server error occurred, indicating an issue on the server-side.
   - 502 Bad Gateway: The server acting as a gateway or proxy received an invalid response from an upstream server.
   - 503 Service Unavailable: The server is currently unavailable or overloaded and cannot handle the request.
   - 504 Gateway Timeout: The server acting as a gateway or proxy did not receive a timely response from an upstream server.

These are just a few examples of commonly encountered HTTP status codes. Each status code provides specific information about the outcome of a request, whether it was successful, encountered an error, or requires further action. By examining the status code, the client can determine how to handle the response and take appropriate action based on the result.










# CORS

CORS stands for Cross-Origin Resource Sharing. It is a security mechanism implemented in web browsers to control access to resources (such as APIs) hosted on different domains or origins. 

In a web application, the same-origin policy is enforced by default, which means that web pages can only request resources from the same domain they originated from. However, there are scenarios where a web page from one origin needs to make requests to a different origin. CORS provides a standardized way to enable cross-origin requests while still maintaining security.

When a web page makes a cross-origin request, the browser sends an HTTP request with an "Origin" header, indicating the origin of the requesting page. The server can then respond with appropriate CORS headers that define which origins are allowed to access the requested resource.

The CORS mechanism involves the following headers:

1. Origin: The browser includes this header in the request, indicating the origin of the requesting page.

2. Access-Control-Allow-Origin: The server includes this header in the response to specify which origins are allowed to access the resource. It can be a specific origin, "*", which allows any origin, or a list of origins.

3. Access-Control-Allow-Methods: The server includes this header to specify the HTTP methods (e.g., GET, POST, PUT, DELETE) allowed for the resource.

4. Access-Control-Allow-Headers: The server includes this header to specify the custom headers that the client is allowed to include in the request.

5. Access-Control-Allow-Credentials: If the client needs to include credentials (such as cookies or HTTP authentication) in the request, the server must include this header with the value "true".

When a browser receives a response with appropriate CORS headers, it checks if the requesting origin is allowed access. If allowed, the browser allows the response to be accessed by the requesting page's JavaScript code. If not allowed, the browser blocks the response, and the JavaScript code on the requesting page cannot access the returned data.

CORS is an important security mechanism that helps prevent cross-site scripting (XSS) and cross-site request forgery (CSRF) attacks. By enforcing restrictions on cross-origin requests, it helps protect sensitive data and resources on different domains while still allowing controlled and authorized access when needed.










# Middlewares

Middlewares are components or functions that sit between the client and server in a web application. They intercept and process incoming requests and outgoing responses, performing certain operations or modifications before passing them to the next step in the application's pipeline. 

In short, middlewares act as a layer of processing logic that sits between the client and server, enabling functionalities such as request authentication, data validation, error handling, logging, and more. They provide a way to modularize and separate concerns in the application's request/response flow.









# Node single-threaded or multi-threaded

Node.js is primarily single-threaded, meaning it executes JavaScript code in a single thread. However, it leverages an event-driven, non-blocking I/O model, which allows it to handle concurrent operations efficiently. This is achieved through the use of an event loop and asynchronous callbacks, which enable Node.js to handle multiple requests concurrently without blocking the execution of other operations.









# Promises and async/await

In JavaScript, the `promise`, `async`, and `await` keywords are used to handle asynchronous operations in a more readable and manageable way. Here's a short and concise explanation of each term:

1. Promise: A `Promise` is an object representing the eventual completion (or failure) of an asynchronous operation and its resulting value. It provides a cleaner way to handle asynchronous tasks and avoid callback hell. A `Promise` can be in one of three states: pending, fulfilled, or rejected.

2. Async: The `async` keyword is used to define an asynchronous function. It allows you to write functions that implicitly return a `Promise`. Inside an `async` function, you can use the `await` keyword to pause the execution of the function until a `Promise` is fulfilled and retrieve its resolved value.

3. Await: The `await` keyword can only be used inside an `async` function. It pauses the execution of the function until the `Promise` is fulfilled and returns the resolved value. This way, you can write asynchronous code that looks and behaves more like synchronous code, making it easier to read and reason about.

Here's a simple example to demonstrate their usage:

```javascript
function fetchUser() {
  return new Promise((resolve, reject) => {
    // Simulating an asynchronous operation
    setTimeout(() => {
      const user = { name: 'John', age: 25 };
      resolve(user);
    }, 2000);
  });
}

async function getUser() {
  try {
    const user = await fetchUser();
    console.log(user);
    // Do something with the user object
  } catch (error) {
    console.log(error);
    // Handle the error
  }
}

getUser();
```

In the example above, the `fetchUser` function returns a `Promise` that resolves with a user object after a simulated delay of 2 seconds. The `getUser` function is defined as an `async` function, allowing us to use the `await` keyword to pause its execution until the `fetchUser` promise is resolved. Finally, we can handle the retrieved user object or catch any errors using a try-catch block.









# MVC

MVC stands for Model-View-Controller and is a software architectural pattern commonly used in web development. It separates the concerns of data management (Model), user interface (View), and application logic (Controller). Here's a short and concise example of how MVC works:

1. Model: The Model represents the data and business logic of the application. It encapsulates the data and provides methods to manipulate and access it. For example, in a simple to-do list application, the Model could consist of classes like Task and TaskList that manage tasks and task lists.

2. View: The View is responsible for rendering the user interface and displaying the data to the user. It receives data from the Model and presents it visually. In our to-do list application, the View could be an HTML template that displays the tasks and provides buttons for adding, editing, or deleting tasks.

3. Controller: The Controller acts as the intermediary between the Model and the View. It handles user interactions, such as button clicks or form submissions, and updates the Model or View accordingly. It contains the application logic and orchestrates the flow of data. In our example, the Controller would handle actions like adding a new task, deleting a task, or marking a task as complete.

This separation of concerns provided by MVC allows for modular development, easier maintenance, and code reusability. Each component can be developed and tested independently, making the overall application more flexible and scalable.









# ES5 vs ES6

Sure! Here's a concise side-by-side comparison of important points between ECMAScript 5 (ES5) and ECMAScript 6 (ES6), presented in a table format:

| ES5                                                    | ES6                                                      |
|--------------------------------------------------------|----------------------------------------------------------|
| Introduced in 2009                                      | Introduced in 2015                                        |
| Limited support for features like classes and modules   | Added support for classes and modules                      |
| Uses the 'var' keyword for variable declarations        | Introduced 'let' and 'const' for block-scoped variables   |
| No support for default function parameters              | Added support for default function parameters             |
| No support for arrow functions                          | Added support for arrow functions                         |
| No support for template literals (string interpolation) | Added support for template literals                       |
| No support for destructuring assignments                | Added support for destructuring assignments               |
| No support for iterators and generators                 | Added support for iterators and generators                |
| No support for Promises and async/await                 | Added support for Promises and async/await                |
| No support for modules                                  | Added support for native modules                           |

Please note that this table provides a simplified overview and there are many more features and differences between ES5 and ES6.









# CRUD

CRUD stands for Create, Read, Update, and Delete. It is a set of basic operations used in computer programming and database management to manipulate data.

- Create: It refers to the action of adding new data or records to a system or database.
- Read: It involves retrieving or accessing existing data from a system or database.
- Update: It involves modifying or changing existing data in a system or database.
- Delete: It refers to the action of removing or deleting existing data from a system or database.

These four operations form the fundamental building blocks for interacting with data in various software applications and database systems.









# Exceptions

An exception refers to a situation or condition that deviates from the norm or expected behavior. It represents an unusual circumstance that interrupts the regular flow of events or breaks established rules or patterns. Exceptions are typically handled differently than regular cases and often require special treatment or consideration.









# SOLID

The SOLID principle is a set of design principles that aim to promote software development practices that result in maintainable, modular, and extensible code. The acronym SOLID stands for:

1. Single Responsibility Principle (SRP): A class should have only one reason to change, meaning it should have a single responsibility or purpose.

2. Open-Closed Principle (OCP): Software entities (classes, modules, functions) should be open for extension but closed for modification. This principle encourages the use of abstraction and inheritance to allow new functionality to be added without modifying existing code.

3. Liskov Substitution Principle (LSP): Subtypes must be substitutable for their base types. In other words, objects of a superclass should be able to be replaced with objects of its subclasses without affecting the correctness of the program.

4. Interface Segregation Principle (ISP): Clients should not be forced to depend on interfaces they do not use. This principle suggests that interfaces should be specific to the needs of clients to avoid bloated interfaces and unnecessary dependencies.

5. Dependency Inversion Principle (DIP): High-level modules should not depend on low-level modules. Both should depend on abstractions. This principle promotes the use of dependency injection and inversion of control to decouple modules and improve flexibility.

By following these principles, developers can create code that is easier to understand, maintain, and extend, resulting in more robust and flexible software systems.









# Closure, anonymous function, hoisting

Closure: In JavaScript, closure refers to the combination of a function and its lexical environment, which allows the function to access variables from its outer scope even after the outer function has finished executing. It forms a closure around the variables it references, preserving their values.

Example of closure:

```javascript
function outerFunction() {
  var outerVariable = 'Hello';

  function innerFunction() {
    console.log(outerVariable);
  }

  return innerFunction;
}

var closure = outerFunction();
closure(); // Output: Hello
```

In the example above, the `innerFunction` is defined inside `outerFunction` and has access to the `outerVariable`. When `outerFunction` is called, it returns `innerFunction`, creating a closure. Even after `outerFunction` has finished executing, the closure retains access to `outerVariable` and can still access its value.

Anonymous function: An anonymous function is a function that is defined without a name. It is often used when a function is only needed for a specific task and does not need to be referenced elsewhere in the code.

Example of an anonymous function:

```javascript
var sum = function (a, b) {
  return a + b;
};

console.log(sum(2, 3)); // Output: 5
```

In the example above, the anonymous function is assigned to the variable `sum`. It takes two parameters `a` and `b` and returns their sum. The function is invoked using `sum(2, 3)`.

Hoisting: Hoisting is a JavaScript behavior where variable and function declarations are moved to the top of their containing scope during the compilation phase. This means that you can use variables and functions before they are declared in your code.

Example of hoisting:

```javascript
console.log(x); // Output: undefined
var x = 5;
console.log(x); // Output: 5

hoistedFunction(); // Output: "This is a hoisted function"

function hoistedFunction() {
  console.log("This is a hoisted function");
}
```

In the example above, even though the variable `x` and the function `hoistedFunction` are referenced before their actual declarations, the code still runs without errors. This is because during the compilation phase, the variable and function declarations are hoisted to the top of their respective scopes. However, only the declarations are hoisted, not the assignments or function expressions. Hence, `x` is `undefined` before it is assigned the value `5`, and `hoistedFunction` can be called before its declaration.









# ---
