#  Premium Multi-Role Blog Platform Frontend

Welcome to the frontend application of the **Multi-Role Blog Platform**. This is a cutting-edge, fast, and fully responsive Single-Page Application (SPA) built using **React 19**, **Vite**, **Tailwind CSS v4**, and **Zustand**. It provides a sleek, modern visual interface for our readers, authors, and administrators.

---

##  Purpose & Overview

The primary purpose of this frontend is to deliver a beautiful, intuitive, and interactive user experience for content publishing and community engagement. It bridges the gap between our secure backend APIs and our three primary user roles:

1.  **Readers (Users):** A clean interface to search, browse, read, and comment on published articles.
2.  **Creators (Authors):** A distraction-free dashboard to draft, edit, organize, and toggle the visibility of their portfolio.
3.  **Moderators (Admins):** A powerful moderation cockpit to oversee system-wide content and restrict or allow access by blocking or unblocking users.

---

##  Key Features

###  1. Modern Design & Tailwind CSS v4
*   **Tailwind CSS v4 Engine:** Leveraging the latest CSS-in-JS compilation for ultra-fast, modular styling.
*   **Fully Responsive Layouts:** Optimized for all viewports, from mobile screens to extra-large desktop setups.
*   **Micro-Animations & Visual Cues:** Equipped with smooth hover states, transitions, active navigation states, and interactive feedback mechanisms.

###  2. Dynamic Role-Based User Experience
*   **Smart Routing:** Programmatically redirects and displays custom views depending on the logged-in role (`USER`, `AUTHOR`, `ADMIN`).
*   **Conditional Header & Navigation:** Displays relevant quick-action buttons (like "Add Article" for authors or "My Dashboard" for users) based on session states.

###  3. Form Management & State Persistence
*   **Validations via React Hook Form:** Keeps validation errors localized and performance optimal for inputs like sign-ups, logins, and comment boxes.
*   **Zustand Global State Management:** Centralized auth and platform-wide states (`useAuth`) synchronizing seamlessly with the server.
*   **Session Continuity:** Uses persistent browser storage (`localStorage`) to maintain user login states even after page refreshes.

###  4. Author & Admin Interactive Dashboards
*   **Author Control Panel:** Direct interface to perform CRUD actions on personal articles, complete with edit prompts and soft-delete/restore toggles.
*   **Admin Control Cockpit:** Direct interactive management cards to monitor authors, toggle account bans, and browse all published system content.

---

##  Project Structure

```text
frontend/
├── public/                 # Static assets (favicons, logos, public icons)
├── src/
│   ├── assets/             # Global visual resources (illustrations, SVGs, etc.)
│   ├── components/         # Reusable presentation & core view components
│   │   ├── AddArticle.jsx      # Author writing and drafting form
│   │   ├── AdminDashboard.jsx  # Admin moderation & user control console
│   │   ├── AuthorDashboard.jsx # Author personal article lists & edit portals
│   │   ├── Footer.jsx          # Dynamic copyright & links footer
│   │   ├── Header.jsx          # Smart responsive role-based navigation bar
│   │   ├── Home.jsx            # Dynamic platform landing page
│   │   ├── Layout.jsx          # Master layout wrapper (Header + main child pages + Footer)
│   │   ├── Login.jsx           # Unified credential sign-in page with role selector
│   │   ├── Register.jsx        # Account registration form with profile image url support
│   │   └── UserDashboard.jsx   # Readers article dashboard & commenting feed
│   ├── stores/             # Global state definitions
│   │   └── GlobleStore.js      # Zustand store coordinating authentication & APIs
│   ├── App.css             # Root stylesheet overrides
│   ├── App.jsx             # React Router DOM configuration and route trees
│   ├── index.css           # Tailwind CSS directives importing design elements
│   └── main.jsx            # Application bootstrap file
├── eslint.config.js        # Strict code styling and lint rules
├── index.html              # Core single-page entry template
├── package.json            # Front-end packages, scripts, & dependencies
└── vite.config.js          # Vite configurations + Tailwind CSS engine compilation
```

---

## ⚡ Technology Stack

| Technology | Purpose | Description |
| :--- | :--- | :--- |
| **React 19** | Core Library | Leverages rendering performance and cleaner component states. |
| **Vite** | Build Tool | Lightning-fast bundler with Hot Module Replacement (HMR). |
| **Tailwind CSS v4** | Styles | State-of-the-art styling framework with modern color presets. |
| **React Router v7** | Routing | Manages client-side route transitions and layout nesting. |
| **Zustand** | State | Lightweight, high-performance global state manager. |
| **Axios** | HTTP Client | Communicates with the backend server securely. |
| **React Hook Form** | Form Engine | Provides robust, performant form validations. |
| **React Hot Toast** | Notifications | Toast notifications for sign-up, login, and error responses. |

---

##  Screen Navigation Flow

```text
               ┌───────────────┐
               │  Landing /    │
               │   Home Page   │
               └───────┬───────┘
                       │
             ┌─────────┴─────────┐
             ▼                   ▼
      ┌─────────────┐     ┌─────────────┐
      │  Register   │     │    Login    │
      └──────┬──────┘     └──────┬──────┘
             │                   │
             └─────────┬─────────┘
                       │
             Authenticated Dashboard?
                       │
        ┌──────────────┼──────────────┐
        ▼              ▼              ▼
 ┌─────────────┐┌─────────────┐┌─────────────┐
 │    User     ││   Author    ││    Admin    │
 │  Dashboard  ││  Dashboard  ││  Dashboard  │
 └─────────────┘└──────┬──────┘└─────────────┘
                       │
                       ▼
                ┌─────────────┐
                │ Add Article │
                │    Form     │
                └─────────────┘
```

---

##  Development Configuration

All requests to the backend server must target the correct base URL. By default, API calls are directed to:

*   **API Base URL:** `http://localhost:3000` (Make sure your backend server is up and listening on this port).
*   **Local Web Server Port:** `http://localhost:5173` (Vite's default client URL).

---

##  Setup & Run Instructions

To install local modules and host the client application:

1.  **Navigate to the frontend folder:**
    ```bash
    cd frontend
    ```

2.  **Install dependencies:**
    ```bash
    npm install
    ```

3.  **Run the local development server:**
    ```bash
    npm run dev
    ```

After running `npm run dev`, Vite will open the local development environment. Navigate to `http://localhost:5173` in your browser.

---

##  Building for Production

To optimize and bundle the application assets for production deployments:

1.  **Execute the compiler script:**
    ```bash
    npm run build
    ```
    *This creates a highly-optimized, static `dist/` directory ready for deployment on platforms like Netlify, Vercel, or AWS S3.*

2.  **Preview the production build locally:**
    ```bash
    npm run preview
    ```
