# User & Role Management Single Page Application (SPA)

> **Software Internship Coding Challenge Submission**  
> A full-stack, enterprise-grade User & Role Management application built with Angular 22, Node.js, Express.js, and TypeScript, styled using a premium **Deep Navy + Warm Gold** visual theme.

---

## 📋 Project Overview

This project is a single-page web application demonstrating client-side Angular architecture, role-based access control (RBAC), and RESTful API integration with a Node.js Express backend.

The application allows system administrators and general users to interact with a centralized user directory. It features robust form validation, dynamic role checking, status indicators, and responsive layouts designed for mobile, tablet, and desktop environments.

---

## ✨ Features

- **Enterprise Deep Navy + Warm Gold Theme**: Custom CSS design system with smooth micro-interactions, gold hover glows, and glassmorphic elevated surface cards.
- **Role-Based UI & Access Control (RBAC)**:
  - **Admin**: Full read, write, create, update, and delete (CRUD) permissions across the entire directory.
  - **General User**: Read-only directory access with protected views and administrative controls automatically hidden.
- **RESTful API Integration**: Synchronized with a Node.js / Express backend writing directly to a local JSON data source (`users.json`).
- **Form Validation & Real-time Feedback**: Includes ID duplication detection, field validation, password toggles, and toast alerts.
- **Interactive Search & Filtering**: Multi-field search across ID, Name, Role, Email, and Department, plus role-specific dropdown filtering.
- **Reusable Component Architecture**: Built with modular components (Login, Dashboard, User Management, User Form Modal, Confirmation Dialog, Toast Alerts).
- **Session Persistence**: Stores current session user details in `localStorage` and enforces route security via Angular `AuthGuard` and `AdminGuard`.

---

## 🛠️ Technology Stack

- **Frontend**:
  - Angular 22 (Standalone Component Architecture)
  - TypeScript
  - HTML5 & CSS3 (Custom Variables, Animations & Responsive Grid)
  - RxJS (Reactive Data Streams)
  - Angular Router & Reactive Forms
- **Backend**:
  - Node.js
  - Express.js (REST API Router & Controllers)
  - TypeScript / `tsx`
  - Local JSON persistence (`server/data/users.json`)

---

## 🏛️ Application Architecture

```
Angular Frontend (Port 4200)
       │
       ▼
   ApiService & AuthService
       │
   HttpClient / Dev Proxy (/api)
       │
       ▼
Node.js Express Server (Port 3000)
       │
       ├─► Controllers (user.controller.ts)
       ├─► Routes (user.routes.ts)
       └─► Data Storage (users.json)
```

---

## 👥 User Roles & Access Control Matrix

| Feature / Action | General User | Admin |
| :--- | :---: | :---: |
| Log in to portal | ✅ | ✅ |
| View Dashboard overview & metrics | ✅ | ✅ |
| View Users Directory | ✅ | ✅ |
| Search & Filter Users | ✅ | ✅ |
| Add New User | ❌ *(Hidden & Guarded)* | ✅ |
| Edit Existing User | ❌ *(Hidden & Guarded)* | ✅ |
| Delete User | ❌ *(Hidden & Guarded)* | ✅ |

---

## 🔑 Dummy Login Credentials

For quick evaluation, use the credentials below or click the **Demo Quick Fill** buttons on the login page:

| Role | User ID | Password | Role Dropdown Selection |
| :--- | :---: | :---: | :--- |
| **General User** | `101` | `user123` | `General User` |
| **Admin** | `103` | `admin123` | `Admin` |

---

## 📡 REST API Endpoints

All endpoints are hosted at `http://localhost:3000/api` (proxied via `/api` in development):

| HTTP Method | Endpoint | Description | Status Code |
| :--- | :--- | :--- | :---: |
| `POST` | `/api/auth/login` | Validate user credentials and return user profile | `200` / `401` |
| `GET` | `/api/users` | Retrieve all users (supports optional `?q=search` filter) | `200` |
| `GET` | `/api/users/:id` | Retrieve single user details by ID | `200` / `404` |
| `POST` | `/api/users` | Create a new user record | `201` / `400` |
| `PUT` | `/api/users/:id` | Update an existing user record | `200` / `404` |
| `DELETE` | `/api/users/:id` | Delete a user record by ID | `200` / `404` |
| `GET` | `/api/health` | Health check endpoint | `200` |

---

## 📂 Folder Structure

```
MployCheck-internship/
├── proxy.conf.json            # Angular dev proxy forwarding /api -> localhost:3000
├── angular.json               # Angular CLI configuration
├── package.json               # Workspace dependencies & npm scripts
├── README.md                  # Project documentation
│
├── server/                    # Node.js Express REST API
│   ├── app.ts                 # Express app initialization & server entry
│   ├── controllers/
│   │   └── user.controller.ts # CRUD logic & authentication logic
│   ├── routes/
│   │   └── user.routes.ts     # Express router definition
│   ├── models/
│   │   └── user.model.ts      # TypeScript interfaces for server
│   └── data/
│       └── users.json         # Local JSON database
│
└── src/                       # Angular Frontend Application
    ├── index.html             # HTML entry point with Inter font & Deep Navy bg
    ├── styles.css             # Global Deep Navy + Warm Gold CSS design system
    └── app/
        ├── app.ts             # Root component with toast container & router outlet
        ├── app.config.ts      # Application config (providers, routing, HttpClient)
        ├── app.routes.ts      # Route definitions & guards
        ├── components/
        │   ├── login/         # Login component & quick demo helper
        │   ├── dashboard/     # Header, Sidebar, Stats overview & navigation
        │   ├── user-management/# Responsive user directory table & actions
        │   ├── user-form/     # Add/Edit modal dialog with reactive form
        │   ├── confirm-modal/ # Reusable action confirmation dialog
        │   └── toast/         # Floating toast alert notifications
        ├── guards/
        │   ├── auth.guard.ts  # Session authentication guard
        │   └── admin.guard.ts # Admin privilege guard
        ├── models/
        │   └── user.model.ts  # Frontend user & toast interfaces
        └── services/
            ├── api.service.ts  # HttpClient service for Express REST API
            ├── auth.service.ts # Authentication & session management service
            └── toast.service.ts# Global toast notification service
```

---

## 🚀 Installation & Running Instructions

### Prerequisites
- **Node.js**: v18.0.0 or higher
- **npm**: v9.0.0 or higher

### Step 1: Install Dependencies
Open a terminal in the project root directory and run:
```bash
npm install
```

### Step 2: Run Frontend & Backend Concurrently
To start both the Node.js Express REST API server and the Angular dev server together with a single command:
```bash
npm start
```

This will run:
- **Node.js Express Server**: `http://localhost:3000`
- **Angular App**: `http://localhost:4200`

### Step 3: Run Frontend or Backend Separately (Optional)
If you prefer running them in separate terminal windows:

- **Backend REST Server**:
  ```bash
  npm run start:backend
  ```
- **Frontend Angular App**:
  ```bash
  npm run start:frontend
  ```

Access the application in your browser at: **`http://localhost:4200`**

---

## 🖼️ Application Preview & Screenshots

The application adheres strictly to the **Deep Navy + Warm Gold** visual design guidelines:

1. **Login Screen**: Glassmorphic dark card with shield logo, password toggle, role dropdown, and quick fill chips for `101` (User) and `103` (Admin).
2. **Dashboard Overview**: Summary stats cards featuring Total Users, General Users, Admins, and Active User Role with Warm Gold highlight cards.
3. **User Directory**: Responsive data grid with role badges (Gold for Admin, Muted Navy for General User), search bar, and action buttons (`Edit` / `Delete` for Admins only).
4. **Add/Edit Modal**: Dark navy overlay with warm gold primary buttons and field validation.

---

## 🚀 Future Improvements

- JWT / OAuth2 token authentication for enhanced session security.
- MongoDB / PostgreSQL database connector replacing local JSON file persistence.
- User activity audit log tracking modifications and administrative actions.
- Multi-language (i18n) localization support.
