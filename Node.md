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
