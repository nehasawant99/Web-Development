# API Development — Complete Notes

## 1. What is an API?

**API = Application Programming Interface**

An API is a defined interface that allows **one software system to communicate with another software system**.

It defines:

* What can be requested
* How the request should be sent
* What data can be provided
* What response will be returned
* What errors can occur
* What authentication/authorization is required

### Simple concept

```text
Client
   │
   │ Request
   ▼
  API
   │
   ▼
Backend / Business Logic
   │
   ▼
Database
   │
   ▼
Backend
   │
   │ Response
   ▼
  API
   │
   ▼
Client
```

---

# 2. Real-World Analogy

Think of an API as a **waiter in a restaurant**.

```text
Customer
   │
   │ Order
   ▼
Waiter (API)
   │
   ▼
Kitchen (Backend)
   │
   ▼
Food / Result
   │
   ▼
Waiter
   │
   ▼
Customer
```

The customer doesn't enter the kitchen and directly interact with it.

Similarly, a frontend shouldn't directly manipulate the production database.

---

# 3. Why Do We Need APIs?

Without an API, an application could become tightly coupled:

```text
Frontend
   ↓
Database
```

This creates problems because the frontend would need to know:

* Database structure
* Database connection details
* Queries
* Business rules
* Security rules

A better architecture is:

```text
Frontend
   ↓
API
   ↓
Business Logic
   ↓
Database
```

### Benefits

* Separation of responsibilities
* Better security
* Reusable backend
* Easier maintenance
* Multiple clients can use the same backend
* Easier integration with external services
* Better scalability

---

# 4. API Request and Response

Every API interaction generally follows:

```text
CLIENT
   │
   │ HTTP REQUEST
   ▼
SERVER
   │
   │ HTTP RESPONSE
   ▼
CLIENT
```

### Request

A request tells the server what the client wants.

Example:

```http
GET /api/products
```

### Response

The server returns data or information about the operation.

Example:

```json
[
  {
    "id": 1,
    "name": "Apple",
    "price": 120
  },
  {
    "id": 2,
    "name": "Milk",
    "price": 60
  }
]
```

---

# 5. Components of an API Request

An HTTP request can contain:

## Method

```text
GET
POST
PUT
PATCH
DELETE
```

## URL / Endpoint

```text
/api/products
```

## Headers

Additional request information.

Example:

```http
Content-Type: application/json
Authorization: Bearer <token>
```

## Body

Data sent to the server.

Example:

```json
{
  "name": "Apple",
  "price": 120
}
```

Not every HTTP request requires a body.

---

# 6. HTTP Methods

HTTP methods describe the operation being requested.

| Method | Purpose                     |
| ------ | --------------------------- |
| GET    | Retrieve data               |
| POST   | Create data                 |
| PUT    | Replace/update a resource   |
| PATCH  | Partially update a resource |
| DELETE | Delete a resource           |

### GET

```http
GET /api/products
```

Meaning:

> Give me the products.

### POST

```http
POST /api/products
```

```json
{
  "name": "Apple",
  "price": 120
}
```

Meaning:

> Create a new product.

### PUT

```http
PUT /api/products/10
```

Usually used to replace/update the resource.

### PATCH

```http
PATCH /api/products/10
```

Used when only part of the resource needs to change.

### DELETE

```http
DELETE /api/products/10
```

Meaning:

> Delete product 10.

---

# 7. What is an Endpoint?

An **endpoint** is a specific URL through which an API exposes an operation.

Example:

```text
GET    /api/products
GET    /api/products/10
POST   /api/products
PUT    /api/products/10
DELETE /api/products/10
```

These are different API endpoints/operations.

Conceptually:

```text
API
│
├── /products
│     ├── GET
│     └── POST
│
└── /products/{id}
      ├── GET
      ├── PUT
      ├── PATCH
      └── DELETE
```

---

# 8. What is JSON?

**JSON = JavaScript Object Notation**

JSON is a common format used to exchange structured data between applications.

Example:

```json
{
  "id": 101,
  "name": "Milk",
  "price": 60
}
```

An API can return JSON to:

* Web applications
* Mobile applications
* Desktop applications
* Other backend services

---

# 9. API Is NOT the Database

A common beginner misconception is:

```text
API = Database
```

This is incorrect.

A better architecture is:

```text
API
 ↓
Controller
 ↓
Service / Business Logic
 ↓
Data Access
 ↓
Database
```

The API provides controlled access to application functionality and data.

---

# 10. Business Logic

An API shouldn't blindly insert client data into the database.

For example:

```json
{
  "productId": 15,
  "quantity": -100
}
```

The backend should validate it.

Possible flow:

```text
Request
   ↓
Authentication
   ↓
Validation
   ↓
Check Product
   ↓
Check Stock
   ↓
Apply Business Rules
   ↓
Calculate Price
   ↓
Save Data
   ↓
Response
```

This logic is part of the application's business layer.

---

# 11. HTTP Status Codes

APIs communicate the result of a request using HTTP status codes.

| Code | Meaning                                |
| ---- | -------------------------------------- |
| 200  | OK / successful request                |
| 201  | Created                                |
| 204  | Success with no response body          |
| 400  | Bad Request                            |
| 401  | Unauthorized / authentication required |
| 403  | Forbidden                              |
| 404  | Resource not found                     |
| 409  | Conflict                               |
| 500  | Internal Server Error                  |

Example:

```http
HTTP/1.1 404 Not Found
```

The frontend can use the status code to determine how to handle the result.

---

# 12. Authentication vs Authorization

These are different concepts.

### Authentication

> **Who are you?**

Example:

```text
Login
 ↓
Username/password
 ↓
Authentication
 ↓
Token
```

### Authorization

> **What are you allowed to do?**

Example:

```text
Authenticated User
       ↓
Can access own orders?       YES
Can delete another user?     NO
Can access admin panel?      NO
```

---

# 13. JWT Authentication

A common API authentication approach is **JWT (JSON Web Token)**.

Basic flow:

```text
User
 ↓
POST /api/auth/login
 ↓
Server verifies credentials
 ↓
JWT generated
 ↓
Client receives token
 ↓
Client sends token with requests
```

Example:

```http
Authorization: Bearer <token>
```

The server validates the token before allowing protected operations.

---

# 14. REST API

**REST = Representational State Transfer**

REST is an architectural style commonly used for web APIs.

REST APIs generally work with **resources**.

Example:

```text
/products
/users
/orders
/payments
/cart
```

Example operations:

```http
GET    /api/products
POST   /api/products
GET    /api/products/10
PUT    /api/products/10
DELETE /api/products/10
```

The URL identifies the resource and the HTTP method describes the operation.

---

# 15. API vs Website

A website commonly returns HTML:

```html
<h1>Milk</h1>
<p>₹60</p>
```

An API commonly returns structured data:

```json
{
  "name": "Milk",
  "price": 60
}
```

Simplified:

```text
Website
   ↓
UI / HTML

API
   ↓
Data / Services
```

Modern applications can use both.

---

# 16. API and Frontend

One backend API can support multiple clients.

```text
                 API
                  │
       ┌──────────┼──────────┐
       ↓          ↓          ↓
    Website    Mobile     Admin
    App        App        Dashboard
```

This allows different frontend applications to reuse the same backend functionality.

---

# 17. Third-Party APIs

Applications often communicate with external services through APIs.

Examples include:

```text
Application
     │
     ├── Payment API
     │
     ├── Email API
     │
     ├── SMS API
     │
     ├── Maps API
     │
     └── Authentication API
```

Instead of building every service from scratch, applications integrate existing services.

---

# 18. Real-World Order Example

Consider a grocery application.

The user clicks:

**Place Order**

The frontend might send:

```http
POST /api/orders
```

Request:

```json
{
  "items": [
    {
      "productId": 5,
      "quantity": 2
    },
    {
      "productId": 8,
      "quantity": 1
    }
  ],
  "addressId": 3
}
```

Production flow:

```text
POST /api/orders
       ↓
Authenticate User
       ↓
Validate Request
       ↓
Check Products
       ↓
Check Inventory
       ↓
Calculate Total
       ↓
Create Order
       ↓
Create Order Items
       ↓
Process Payment
       ↓
Update Inventory
       ↓
Save Transaction
       ↓
Return Response
```

Response:

```json
{
  "orderId": 152,
  "status": "Pending",
  "total": 540
}
```

---

# 19. Production API Architecture

A simple production-style architecture might look like:

```text
                    CLIENTS
                       │
          ┌────────────┼────────────┐
          ↓            ↓            ↓
       Website       Mobile       Admin
          │            │            │
          └────────────┼────────────┘
                       ↓
                  API Gateway
                       │
        ┌──────────────┼──────────────┐
        ↓              ↓              ↓
   Product API     Order API      Payment API
        ↓              ↓              ↓
   Product DB      Order DB      Payment Service
```

Large systems may use multiple services instead of one monolithic backend.

---

# 20. API Gateway

An API Gateway can act as a central entry point for client requests.

```text
Client
  ↓
API Gateway
  ↓
 ┌──────────────┬──────────────┐
 ↓              ↓              ↓
User Service  Order Service  Product Service
```

It can handle responsibilities such as:

* Routing
* Authentication
* Rate limiting
* Request filtering
* Monitoring
* Load distribution

---

# 21. API Scalability

Production applications can receive thousands or millions of requests.

A common architecture is:

```text
                  Load Balancer
                       │
          ┌────────────┼────────────┐
          ↓            ↓            ↓
       API #1        API #2        API #3
          │            │            │
          └────────────┼────────────┘
                       ↓
                     Cache
                       ↓
                   Database
```

If one API server fails:

```text
API #1 ❌
   ↓
Load Balancer
   ↓
API #2 / API #3
```

This helps improve availability.

---

# 22. API Security

APIs are exposed to clients and therefore require strong security.

Important API security concepts:

* Authentication
* Authorization
* Input validation
* HTTPS
* JWT
* OAuth
* API keys
* Rate limiting
* CORS
* Secure error handling
* Logging
* Access control
* Data protection

Example problem:

```http
GET /api/users/101
```

If User A changes the ID to:

```http
GET /api/users/102
```

and can access User B's information, the API has an access-control vulnerability.

Therefore API security is an important cybersecurity area.

---

# 23. API Monitoring

Production APIs need monitoring.

Important metrics include:

```text
Request count
Response time
Error rate
CPU usage
Memory usage
Database latency
Authentication failures
Failed requests
```

Example:

```text
/api/orders

Requests:       85,000
Average latency: 120 ms
Error rate:       0.8%
```

If the error rate suddenly increases:

```text
0.8%
 ↓
15%
```

the engineering team investigates.

---

# 24. API Logging

Logs help developers and security teams understand what happened.

Example:

```text
2026-08-31 11:30:15
POST /api/orders
UserId: 152
Status: 201
ResponseTime: 180ms
```

Logs can help investigate:

* Application failures
* Performance issues
* Authentication failures
* Suspicious activity
* API abuse

---

# 25. API Testing

APIs should be tested independently.

Common tools include:

* Postman
* Swagger / OpenAPI
* curl
* Automated integration tests
* Unit tests

Example:

```text
POST /api/products
        ↓
Send JSON
        ↓
Check status code
        ↓
Check response
        ↓
Check database
```

---

# 26. Swagger / OpenAPI

Swagger/OpenAPI provides API documentation and an interactive interface.

It can show:

```text
GET    /api/products
POST   /api/products
GET    /api/products/{id}
PUT    /api/products/{id}
DELETE /api/products/{id}
```

Developers can understand and test an API without reading the entire source code.

---

# 27. API Versioning

Production APIs may evolve over time.

Instead of suddenly breaking existing clients:

```text
/api/products
```

a company may use:

```text
/api/v1/products
/api/v2/products
```

This allows older applications to continue working while newer clients use the updated API.

---

# 28. API in a Full-Stack Project

A professional web application can look like:

```text
                 FRONTEND
              Razor / React
                    │
                    ↓
                 REST API
                    │
              ┌─────┴─────┐
              ↓           ↓
         Controllers   Middleware
              │
              ↓
           Services
              │
              ↓
        Business Logic
              │
              ↓
          EF Core / ORM
              │
              ↓
          SQL Server
```

Supporting infrastructure:

```text
Authentication
Logging
Validation
Swagger
Testing
Docker
Caching
Monitoring
CI/CD
```

---

# 29. API in FreshMart

For a grocery application such as **FreshMart**, meaningful APIs could include:

### Products

```http
GET    /api/products
GET    /api/products/{id}
POST   /api/products
PUT    /api/products/{id}
DELETE /api/products/{id}
```

### Cart

```http
GET    /api/cart
POST   /api/cart/items
PUT    /api/cart/items/{id}
DELETE /api/cart/items/{id}
```

### Orders

```http
POST /api/orders
GET  /api/orders
GET  /api/orders/{id}
```

### Payments

```http
POST /api/payments
GET  /api/payments/{id}
```

### Authentication

```http
POST /api/auth/register
POST /api/auth/login
```

The goal isn't to create hundreds of endpoints.

The goal is to create **meaningful APIs representing real application operations**.

---

# 30. Real Production Role of APIs

API development is not simply:

> "Creating GET and POST endpoints."

In production, APIs act as the controlled communication layer between:

```text
Users
 ↓
Frontend
 ↓
API
 ↓
Business Logic
 ↓
Database
```

and between:

```text
Service A
   ↕
 API
   ↕
Service B
```

They are responsible for exposing application functionality while handling:

* Security
* Validation
* Authentication
* Authorization
* Business operations
* Data exchange
* Error handling
* Monitoring
* Scalability
* Integration

---

# 31. API Development Learning Path

A practical learning sequence:

```text
1. HTTP
   ↓
2. Request / Response
   ↓
3. HTTP Methods
   ↓
4. Status Codes
   ↓
5. JSON
   ↓
6. REST
   ↓
7. CRUD
   ↓
8. ASP.NET Core Web API
   ↓
9. Controllers
   ↓
10. DTOs
   ↓
11. Services
   ↓
12. Entity Framework Core
   ↓
13. SQL Server
   ↓
14. Authentication / JWT
   ↓
15. Authorization
   ↓
16. Validation
   ↓
17. Error Handling
   ↓
18. Swagger / OpenAPI
   ↓
19. Postman
   ↓
20. Logging
   ↓
21. API Security
   ↓
22. Docker
   ↓
23. Deployment
   ↓
24. Monitoring & Scaling
```

---

# 32. Key Concepts to Remember

### API

> Interface that allows software components to communicate.

### Endpoint

> A specific API URL through which an operation is exposed.

### Request

> Information sent by the client to the server.

### Response

> Information returned by the server to the client.

### REST

> Architectural style commonly used to design web APIs around resources and HTTP operations.

### JSON

> Common structured data format used for API communication.

### Authentication

> Determines who the user is.

### Authorization

> Determines what the user is allowed to do.

### Status Code

> Indicates the result of an HTTP request.

### Business Logic

> Rules that determine how the application should behave.

---

# 33. The Mental Model

The most important thing to remember:

```text
                CLIENT
                  │
                  │ HTTP
                  ▼
                 API
                  │
       ┌──────────┼──────────┐
       ↓          ↓          ↓
   Security   Validation   Routing
                  │
                  ▼
           Business Logic
                  │
                  ▼
             Data Access
                  │
                  ▼
              DATABASE
```

An API is therefore **not just a URL**.

It is a **contract and controlled interface for accessing application functionality and data**.

---

# 34. Why API Knowledge Matters for Developers

API knowledge is valuable because modern applications depend heavily on communication between systems.

A developer who understands APIs can work on:

* Frontend + backend applications
* Backend services
* Mobile backends
* Microservices
* Payment integrations
* Authentication systems
* Cloud applications
* Third-party integrations
* API security
* Distributed systems

For a portfolio project, demonstrating:

```text
REST API
+
Authentication
+
Database
+
Validation
+
Error Handling
+
Swagger
+
Testing
+
Docker
```

shows significantly more backend understanding than simply creating static pages.

---
## Diagram 


<img width="1344" height="736" alt="D8ZUOJ7q6nB5tEj4zr2S6dNVSKXQElNUIXEBLIm3may-w6mR6ZqLZydnfPWGUhmSwIM63ZnfwQm92qzYSKEARxPy6tji416OsmALK2JdBrLJ4g0b2zDObgRcZfDI7Bfafew9lFIaAISd8FoRoiwmd27pw9nZ9RVgaEiI0t0S6c3qTi1lDWwPX3B7H7H_pKPD" src="https://github.com/user-attachments/assets/247c5611-d999-48fb-ac90-0516c0b953a2" />


<img width="1600" height="921" alt="LQIG3zoL5xXgHdQXwqCy8Qr6EXp4U8SAStVJMVoXxglkZckdRljv9q5ALDZS60Tl8XAES6Y3K0GNloIhi7meCrRO36TXRHEDkFCGfYVEIpByFd97bH_5qTnpMN5fiPfo2B4lolF1dlk5bBpsMGYeJHKzegPb5Fjh7WJh3kt9Er_5iB1GHPaM9XvQt4R6Wkcv" src="https://github.com/user-attachments/assets/dcf5382a-23e8-4d83-871d-d5d21b4faeac" />



## Final Summary

```text
API
│
├── Communication
├── Request / Response
├── HTTP
├── REST
├── JSON
├── CRUD
├── Authentication
├── Authorization
├── Validation
├── Business Logic
├── Database Access
├── Security
├── Testing
├── Documentation
├── Logging
├── Monitoring
├── Scalability
└── Integration
```

### One-line definition

> **An API is a controlled interface that allows software systems to communicate and access functionality or data through defined rules, requests, responses, and security controls.**
