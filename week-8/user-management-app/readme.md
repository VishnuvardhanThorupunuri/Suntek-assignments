# User Management Application (Full-Stack)

A complete full-stack web application for managing user profiles, featuring a fast and modern Single Page Application (SPA) frontend and a secure, validation-guarded backend API with MongoDB database persistence.

---

## Project Purpose

The primary purpose of this application is to demonstrate a fully integrated, scalable, and responsive user profile management portal. Users can seamlessly create accounts, query registered users, view profile cards, and navigate the application dashboard. The project features strict form validations on the client side, robust constraints on the server side (such as duplicate checks and data schema integrity), and reliable MongoDB database integration.

---

## Architectural Overview

The application is split into two modular layers to ensure a clean separation of concerns:

1.  **Frontend Client (Single Page Application):** Powered by React, Vite, and React Router. It handles all visual rendering, user interaction, routing, and form state validations before querying the server. Styled fully with Tailwind CSS v4.
2.  **Backend API Service (REST Server):** Powered by Node.js, Express, and MongoDB (via Mongoose). It exposes standard API routes under `/user-api`, coordinates database connections, validates requests, enforces business logic constraints, and serves uniform JSON payloads.

---

## Key Features

### Frontend Client
*   **Vite Dev Server:** Extremely fast page reloads and hot module updates (HMR).
*   **React Router Integration:** Instantaneous routing transitions between Home, Users List, Add User, and User Profile pages.
*   **React Hook Form Validations:** Strict client-side checks for email syntax, required fields, date formats, and mobile numbers.
*   **Tailwind CSS v4 Layouts:** Modern, clean, glassmorphic-inspired design built with pure utility-first styling for complete viewport responsiveness.
*   **Dynamic Data Binding:** Connects to the backend REST API to render up-to-date user records dynamically.

### Backend API
*   **Node.js & Express Router:** Clean, modularized router endpoints managing HTTP actions.
*   **Mongoose ODM Validation:** DB schema-level protection with typed fields and automatic timestamp audit attributes (`createdAt`, `updatedAt`).
*   **Email Uniqueness Constraint:** Prevents multi-account registration for identical email addresses.
*   **CORS Protection:** Configured cross-origin sharing rules to securely accept client requests.
*   **Global Handling of Errors:** Catch-all middlewares to format error messages, prevent system crashes, and clean logs.

---

## Directory Structure

```text
user-management-app/
├── backend/            # Node.js + Express + MongoDB Backend Service
│   ├── models/         # Mongoose DB models
│   ├── .env            # Environment database secrets
│   ├── index.js        # Server execution entrypoint
│   └── package.json    # Backend project configs
├── frontend/           # React + Vite + Tailwind Client Application
│   ├── public/         # Static global assets
│   ├── src/            # Application components, routing, and styling
│   │   ├── components/ # Header, Footer, Layout, Home, AddUser, UserList, User
│   │   ├── App.jsx     # Route controller
│   │   └── main.jsx    # Client entry point
│   ├── package.json    # Frontend project configs
│   └── vite.config.js  # Vite settings
└── README.md           # Master documentation (This file)
```

---

## System Configuration and Installation

Follow these steps to run both the frontend and the backend locally:

### 1. Prerequisites
Ensure you have the following installed on your machine:
*   [Node.js](https://nodejs.org/) (v18+ recommended)
*   A running [MongoDB Instance](https://www.mongodb.com/) (either a local installation or a cloud MongoDB Atlas cluster URI)

### 2. Backend API Setup
1.  Navigate into the `backend` folder:
    ```bash
    cd backend
    ```
2.  Install the required dependencies:
    ```bash
    npm install
    ```
3.  Configure the environment secrets. Create a `.env` file in the `backend/` directory:
    ```env
    PORT=5000
    MONGODB_URI=your_mongodb_connection_string
    ```
4.  Launch the backend service:
    ```bash
    node index.js
    ```
    *The API will start running at `http://localhost:5000`.*

### 3. Frontend Client Setup
1.  Open a new terminal window and navigate into the `frontend` folder:
    ```bash
    cd frontend
    ```
2.  Install the required client dependencies:
    ```bash
    npm install
    ```
3.  Start the local development server:
    ```bash
    npm run dev
    ```
    *The frontend web client will start running at `http://localhost:5173`.*

---

## Technology Stack Summary

| Layer | Technologies & Libraries |
| :--- | :--- |
| **Frontend** | React 19, Vite 7, Tailwind CSS v4, React Router 7, React Hook Form 7 |
| **Backend** | Node.js, Express 5, MongoDB, Mongoose 9, dotenv, cors |
