# User Management App - Frontend Client

A modern, fast, and responsive Single Page Application (SPA) web client built with React and Vite, styled using Tailwind CSS v4. It serves as the interactive dashboard for the User Management System.

---

## Purpose

The primary purpose of this frontend application is to provide an intuitive, user-friendly, and responsive user interface for managing profiles. It allows administrators and users to register new accounts via validation-guarded forms, view a comprehensive listing of registered users, search/filter user profiles, and navigate through a unified portal. It interacts with the Express REST backend API to perform real-time data synchronizations.

---

## Key Features

*   **Fast Development with Vite:** Built on Vite for near-instantaneous Hot Module Replacement (HMR) and highly optimized production asset bundling.
*   **Client-Side SPA Routing:** Integrated with React Router to provide fluid, instantaneous page transitions without browser page reloads.
*   **Validation-Guarded Form Handling:** Powered by React Hook Form to ensure smooth user creation workflows with strict client-side validation rules (correct email pattern, required fields, date formats, and mobile lengths).
*   **Dynamic Data Fetching & Listing:** Connects to the backend REST API to fetch, render, and display list data of registered profiles in a clear user grid.
*   **Responsive Styling:** Built using Tailwind CSS v4 to provide a fully responsive, pixel-perfect, and modern UI that scales beautifully from mobile viewports to large desktop monitors.
*   **Component-Driven Architecture:** Clean codebase organization utilizing reusable layout wrappers, distinct visual components, and structural routing.
*   **State-of-the-Art Typography & Layout:** Designed with semantic HTML tags, accessible headers, a distinct navbar brand, and sticky footers for a polished user experience.

---

## Directory Structure

```text
frontend/
├── public/             # Static public assets
├── src/
│   ├── assets/         # App images, logos, and global SVGs
│   ├── components/     # Functional React components
│   │   ├── AddUser.jsx    # Validation-guarded user creation form page
│   │   ├── UserList.jsx   # Grid and list view of registered profiles
│   │   ├── User.jsx       # Individual user profile card/view
│   │   ├── Home.jsx       # Portal landing and dashboard page
│   │   ├── Header.jsx     # Navigation bar with responsive links
│   │   ├── Footer.jsx     # Bottom copyright information bar
│   │   └── RootLayout.jsx # Common layout shell rendering children views
│   ├── App.css         # Custom layout overrides
│   ├── App.jsx         # Router path declarations and main layout mount
│   ├── index.css       # Tailwind directives and utility classes
│   └── main.jsx        # App entry point, DOM render wrapper
├── index.html          # HTML entry shell
├── package.json        # Project metadata, dev configurations, and dependencies
├── vite.config.js      # Vite compilation configurations
└── eslint.config.js    # ESLint style guidance rules and setups
```

---

## Technical Specifications & Stack

*   **Core Library:** React 19
*   **Build Tool & Dev Server:** Vite 7
*   **Styling Engine:** Tailwind CSS v4
*   **Routing Framework:** React Router 7
*   **Form Management:** React Hook Form 7
*   **Code Linter:** ESLint 9

---

## Getting Started

Follow these steps to run the frontend application locally:

### 1. Prerequisites
Ensure you have Node.js (v18+ recommended) installed on your system.

### 2. Install Dependencies
Navigate to the frontend directory and install the necessary package files:
```bash
cd frontend
npm install
```

### 3. Start the Development Server
Launch the local development server:
```bash
npm run dev
```

By default, Vite will start the dev server at:
*   [http://localhost:5173](http://localhost:5173)

### 4. Build for Production
To compile and build optimal static production assets:
```bash
npm run build
```
This output is saved to the `/dist` directory, ready to be deployed to a static hosting provider.
