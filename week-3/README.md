# Week 3: Node.js, Express, MongoDB, and Mongoose Backend Development

Welcome to the Week 3 workspace. This repository contains projects, practical demonstrations, and documentation detailing server-side application development using Node.js, Express, and MongoDB (via the Mongoose ODM). It covers standard REST API design, advanced MongoDB commands, schema definition with robust validation, subdocument management, security with bcryptjs, and JSON Web Token (JWT) authentication handled via secure HttpOnly cookies.

---

## Workspace Structure

The workspace consists of the following projects and directories:

*   **Anurag-Blog-App-Backend**: An Express-based backend for a multi-role blog application (Users, Authors, and Admins) featuring Mongoose schema design with timestamps and embedded subdocuments for article comments.
*   **E-Commerce_Backend**: An e-commerce backend demonstrating user shopping carts utilizing embedded schemas and Mongoose populate queries to expand references.
*   **MongoDB_31_01_26**: A reference guide outlining fundamental MongoDB CLI commands, database CRUD operations, and key array/field update operators.
*   **backend-demo-2**: A comprehensive demonstration of RESTful APIs, Mongoose data validations, secure password hashing using bcryptjs, JWT authentication stored in HttpOnly cookies, route protection middleware, and global Express error handling.

---

## Detailed Project Breakdown

### 1. Anurag-Blog-App-Backend

This project provides the backend service layer for a blog application. It is designed around modular routers and robust schema modeling for users and articles.

#### Key Features
*   **Role-Based Modeling**: Implements a User model with role-based segregation (`USER`, `AUTHOR`, `ADMIN`).
*   **Timestamps & Strict Validations**: Enforces schema rules using `strict: "throw"` to prevent unmapped fields from being saved, along with automatic Mongoose `timestamps` creation.
*   **Embedded Comments**: Demonstrates embedded schema relationships by storing a list of comments directly inside the Article model as a subdocument array.
*   **Modular Routing**: Separates application logic into distinct router files for Admin, Author, and User APIs.

#### Core Models & Schemas
*   **User Schema** (`models/UserModel.js`):
    *   `firstName` (String, required)
    *   `lastName` (String)
    *   `email` (String, required)
    *   `password` (String, required)
    *   `profileImageURL` (String)
    *   `role` (String, enum: `["AUTHOR", "USER", "ADMIN"]`, required)
    *   `isActive` (Boolean, default: `true`)
*   **Article Schema** (`models/ArticleModel.js`):
    *   `author` (Mongoose ObjectId, ref: `user`, required)
    *   `title` (String, required)
    *   `category` (String, required)
    *   `content` (String, required)
    *   `comments` (Array of `userCommentSchema`)
    *   `isActive` (Boolean, default: `true`)

---

### 2. E-Commerce_Backend

An e-commerce API highlighting user cart relationships and Mongoose populate concepts.

#### Key Features
*   **Cart Subdocuments**: The user schema includes a nested `cartSchema` containing product references (`ObjectId`) and product quantity.
*   **MongoDB Update Operators**: Utilizes the `$push` operator in the cart update route to dynamically add items.
*   **Population**: Utilizes Mongoose `.populate()` in the retrieval route to dynamically substitute the product `ObjectId` inside the cart with the actual `productName` and `price` details from the Product collection.

#### Endpoints
*   `POST /user-api/users`: Validates input and creates a new user with a hashed password.
*   `PUT /user-api/user-cart/user-id/:uid/product-id/:pid`: Adds a specific product to a user's cart array.
*   `GET /user-api/users/:uid`: Retrieves user information and populates the cart items.
*   `POST /product-api/products`: Adds a new product (with brand and price validations) to the database.

---

### 3. MongoDB_31_01_26 (CLI Cheat Sheet)

This folder contains a reference guide for essential MongoDB command-line operations and query operators.

#### Database and Collection Administration
```javascript
// Switch or create a database
use db-name

// List available databases
show databases

// Explicitly create a new collection
db.createCollection(collection-name)
```

#### Document CRUD Operations
*   `updateOne(condition, update)`: Updates a single document matching the filter criteria.
*   `updateMany(condition, update)`: Updates all documents matching the filter criteria.
*   `findOne(condition)`: Finds and returns a single document.
*   `findMany(condition)`: Finds and returns multiple matching documents.
*   `deleteOne()` / `deleteMany()`: Removes single or multiple matching documents from a collection.

#### Array & Field Operators
*   `$all`: Matches arrays that contain all the specified elements.
*   `$set`: Replaces the value of a field with a specified value.
*   `$push`: Appends a specified value to an array.
*   `$addToSet`: Adds a value to an array only if the value does not already exist (prevents duplicates).
*   `$pop`: Removes the first (using `-1`) or last (using `1`) element of an array.
*   `$pull`: Removes all instances of a value from an array matching a specific condition.

---

### 4. backend-demo-2

A comprehensive, production-ready demonstration showcasing schema constraints, secure password management, cookie-based sessions, JWT validation, and error management.

#### Key Features
*   **Schema Validations**: Implements Mongoose validation constraints on both Users and Products:
    *   *Username*: Required, minimum length 4, maximum length 6.
    *   *Age*: Required, must be between 18 and 25.
    *   *Product Name & Brand*: Minimum length 2, maximum length 6.
*   **Secure Password Hashing**: Uses `bcryptjs` with salt rounds of 12 to encrypt passwords prior to database insertion.
*   **JWT & HttpOnly Cookies**: Generates a JSON Web Token on successful login and stores it as an `httpOnly` cookie. This mitigates XSS risks by preventing client-side scripts from reading the token.
*   **Route Protection Middleware**: Uses custom middleware (`verifyToken`) that parses the cookie, extracts the token, verifies it, and grants or denies access to protected routes.
*   **Centralized Error & 404 Handlers**: Uses a global Express error-handling middleware that catches synchronous and asynchronous failures, and includes a fallback handler for undefined endpoints (404).

#### Authentication Workflow Diagram
```
Client                      Express Server                      MongoDB
  |                               |                                |
  |--- POST /user-api/auth ------>|                                |
  |    (username & password)      |--- Find user ----------------->|
  |                               |<-- Return hashed password -----|
  |                               |                                |
  |                               |--- Compare passwords (bcrypt)  |
  |                               |--- Generate JWT token          |
  |                               |--- Set HttpOnly Cookie         |
  |<-- 200 OK (Login Success) ----|                                |
  |                               |                                |
```

---

## Installation and Setup

To run any of the Express backends locally, follow these instructions:

### Prerequisites
*   Node.js installed on your machine.
*   MongoDB local instance running or a MongoDB Atlas URI.

### Instructions

1.  **Navigate into the desired project directory**:
    ```bash
    cd Anurag-Blog-App-Backend
    # OR
    cd E-Commerce_Backend
    # OR
    cd backend-demo-2
    ```

2.  **Install dependencies**:
    ```bash
    npm install
    ```

3.  **Configure environment variables** (for projects utilizing `.env`, such as `Anurag-Blog-App-Backend`):
    *   Create a `.env` file in the root of the project directory.
    *   Provide the required variables, e.g.:
        ```env
        PORT=4000
        DB_URL=mongodb://localhost:27017/your_db_name
        ```

4.  **Start the server**:
    ```bash
    # For development (using nodemon if configured)
    npm run dev
    
    # Or standard execution
    node server.js
    ```
