#  User Management App - Backend API

A lightweight, robust, and production-ready REST API built with **Node.js**, **Express**, and **MongoDB** (via **Mongoose**) to serve as the backend layer for the User Management System.

---

##  Purpose

The primary purpose of this backend service is to provide secure, structured, and efficient data persistence and retrieval capabilities for managing user profiles. It implements standard CRUD operations, enforces strict schema-level validation, checks for data uniqueness, and exposes reliable API endpoints for consumption by client-side applications.

---

##  Key Features

*   ** Node.js & Express REST API:** Powered by Node.js and the Express framework for standard-compliant HTTP routing, fast request processing, and high scalability.
*   ** MongoDB & Mongoose Integration:** Seamless connection to a MongoDB database using Mongoose ODM, utilizing structured models with automated schema validations.
*   ** Email Uniqueness Enforcement:** Active duplicate checking before user creation to prevent multiple sign-ups under the same email address.
*   ** Automated Schema Validation:** Enforces presence constraints for fields (`name`, `email`, `dateOfBirth`, `mobileNumber`) before persisting to the database.
*   ** Automatic Timestamps:** Built-in auditing functionality that automatically tracks and records user creation (`createdAt`) and update (`updatedAt`) times.
*   ** Cross-Origin Resource Sharing (CORS):** Pre-configured CORS middleware to allow seamless requests from frontend applications running on other domains.
*   ** Environment-Based Configuration:** Fully decoupled secrets and system configuration using `.env` files via the `dotenv` package.
*   ** Global Error Handling Middleware:** Graceful error catching and response formatting across the entire app stack, ensuring clean error logs and uniform JSON responses.

---

##  Directory Structure

```text
backend/
├── models/
│   └── User.js         # Mongoose schema and model definition for User profiles
├── .env                # Local environment secrets and port configurations
├── index.js            # Express server initialization, DB connection, routing, and middleware
├── package.json        # Project metadata and dependency mappings
└── package-lock.json   # Exact dependency resolution locks
```

---

##  API Documentation

All routes are mounted under the base path `/user-api`.

###  1. Get All Users
*   **Endpoint:** `/user-api/users`
*   **Method:** `GET`
*   **Description:** Retrieves a list of all registered users in the database.
*   **Response (Success - 200 OK):**
    ```json
    {
      "message": "Users fetched successfully",
      "payload": [
        {
          "_id": "64bf99b2...",
          "name": "Jane Doe",
          "email": "jane@example.com",
          "dateOfBirth": "1995-04-12",
          "mobileNumber": "+1234567890",
          "createdAt": "2026-05-26T10:00:00.000Z",
          "updatedAt": "2026-05-26T10:00:00.000Z",
          "__v": 0
        }
      ]
    }
    ```

###  2. Create a New User
*   **Endpoint:** `/user-api/users`
*   **Method:** `POST`
*   **Description:** Creates a new user profile in the database.
*   **Headers:** `Content-Type: application/json`
*   **Request Body:**
    ```json
    {
      "name": "John Doe",
      "email": "john@example.com",
      "dateOfBirth": "1990-01-01",
      "mobileNumber": "+1987654321"
    }
    ```
*   **Response (Success - 201 Created):**
    ```json
    {
      "message": "User created successfully",
      "payload": {
        "_id": "64bf9a20...",
        "name": "John Doe",
        "email": "john@example.com",
        "dateOfBirth": "1990-01-01",
        "mobileNumber": "+1987654321",
        "createdAt": "2026-05-26T10:05:00.000Z",
        "updatedAt": "2026-05-26T10:05:00.000Z",
        "__v": 0
      }
    }
    ```
*   **Response (Conflict - 400 Bad Request):**
    ```json
    {
      "message": "User with this email already exists"
    }
    ```

---

##  Technology Stack

*   **Runtime Environment:** Node.js
*   **Web Framework:** Express.js (v5.2.x)
*   **Database Management:** MongoDB & Mongoose (v9.6.x)
*   **Environment Manager:** dotenv (v17.4.x)
*   **CORS Handler:** cors (v2.8.x)

---

##  Getting Started

Follow these steps to run the backend server locally:

### 1. Prerequisites
Ensure you have [Node.js](https://nodejs.org/) (v16+ recommended) and a running [MongoDB instance](https://www.mongodb.com/) (local or MongoDB Atlas cloud URI) configured.

### 2. Install Dependencies
Navigate to the backend directory and run:
```bash
cd backend
npm install
```

### 3. Environment Setup
Create a `.env` file in the root of your `backend` directory (if it does not exist) and configure the environment variables:
```env
PORT=5000
MONGODB_URI=your_mongodb_connection_string
```

### 4. Run the Server
Launch the server in node runtime:
```bash
node index.js
```

You should see the following logs on startup:
```text
Attempting to connect to MongoDB...
Server is running on port 5000
Connected to MongoDB
Database Host: ...
```
