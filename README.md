# SkillNest Frontend

SkillNest Frontend is the client application for the SkillNest full-stack learning platform. It provides the user-facing experience for browsing courses, enrolling in programs, managing a student dashboard, and accessing admin features through a React single-page application.

This repository is designed to work with the backend API at:
https://github.com/anuraggusain-04/skillnest-backend

## Overview

SkillNest is an online learning and course-management platform built around a simple flow:

- learners browse and search published courses
- users register or log in to access protected functionality
- authenticated students can enroll in courses and view their enrolled learning list
- admins can create, edit, and delete course entries from the admin dashboard
- user profiles can be updated from the dashboard experience

This frontend is implemented with React, React Router, and Axios, using Create React App as the build and development setup.

## Verified features

The following features are implemented in the current source code and are therefore documented as active:

- landing page with course discovery and search
- registration and login UI flows
- JWT-based authentication stored in local storage via AuthContext
- protected route handling through authenticated state
- public course listing and course detail pages
- course enrollment flow for authenticated users
- enrolled-courses view in the dashboard
- profile editing and persistence for authenticated users
- admin dashboard for managing courses

## Tech stack

- React
- React Router DOM
- Axios for API requests
- Create React App
- JavaScript / JSX
- Local storage for session persistence

## Frontend and backend architecture

The frontend is a client-side application that sends HTTP requests to the backend API. The backend exposes REST endpoints for authentication, user data, course content, categories, and admin-only management operations.

Typical flow:

1. User logs in or registers in the frontend.
2. The frontend stores the JWT and user object in local storage.
3. Authorization headers are sent on API calls to protected endpoints.
4. The backend validates the token and role, then returns the requested data.

This repository depends on the backend API being available for its API-driven features.

## Screenshots

No screenshots are included in the repository at this time. If you want to add visuals for the product later, a good set would include:

- home page hero and course search
- login/register flow
- course listing and detail views
- student dashboard
- admin dashboard

## Prerequisites

Before running the frontend locally, make sure you have:

- Node.js installed
- npm installed
- a working backend API running locally or remotely

## Local setup

1. Clone the repository:

```bash
git clone https://github.com/anuraggusain-04/skillnest-frontend.git
cd skillnest-frontend
```

2. Install dependencies:

```bash
npm install
```

3. Start the development server:

```bash
npm start
```

The application will run with the default CRA dev server on:

- http://localhost:3000

## Environment configuration

The current source code in this repository is not yet fully using a configurable environment variable for the backend base URL. The application still contains hardcoded backend URLs in multiple UI pages, so the safer current setup is to run the local backend on the default development URL:

- http://localhost:5000

Recommended future configuration:

```bash
REACT_APP_API_BASE_URL=http://localhost:5000
```

This should be used in a `.env` file in the frontend project root. The repository does not currently show a fully implemented environment-variable based API setup, so any such configuration should be added in a minimal, explicit way and validated before relying on it in production.

## Production build

To create a production build:

```bash
npm run build
```

This produces the optimized build output in the `build/` directory.

## Project structure

```text
skillnest-frontend/
├── public/
├── src/
│   ├── components/
│   │   └── Navbar.js
│   ├── context/
│   │   └── AuthContext.js
│   ├── pages/
│   │   ├── AdminDashboard.js
│   │   ├── CourseDetail.js
│   │   ├── Courses.js
│   │   ├── Dashboard.js
│   │   ├── Home.js
│   │   └── Login.js
│   ├── App.js
│   ├── App.css
│   ├── index.css
│   ├── index.js
│   ├── logo.svg
│   ├── reportWebVitals.js
│   └── setupTests.js
├── .gitignore
├── package.json
├── package-lock.json
├── README.md
└── public/
```

## Related backend repository

- https://github.com/anuraggusain-04/skillnest-backend

## Development notes

- Authentication state is persisted in local storage.
- Most API calls are made through Axios with the backend URL defined in the page code or expected local default.
- The application expects the backend service to be available and correctly configured.

## Troubleshooting

### API calls fail

Check that the backend server is running and that the MongoDB connection is healthy.

### Login/register flow is not working

Verify that the backend authentication routes are available and that the JWT secret is configured on the backend.

### Blank or broken pages after startup

Check the browser console for runtime errors and confirm that the frontend dependencies were installed successfully.

### Production build issues

Ensure the local Node/npm version is compatible with the Create React App setup used by the project.

## Contribution guidance

Contributions are welcome as long as they remain consistent with the project’s architecture:

- keep the React pages and API logic clearly separated
- avoid hardcoding production backends into client-side code without explicit configuration
- keep authentication flows secure and consistent with the backend contract
- document any new routes or API payloads in the repository documentation

## Important note about verification

This README was prepared from the actual repository source and package manifests inspected in the project. The setup commands listed here have not been runtime-verified in this environment, so local execution should be validated on a working developer machine before relying on them for deployment or production use.
