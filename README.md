# Training & Placement Management System (TnP Cell)

> A full-stack training and placement management system with a Node.js/Express backend and a React (Vite) frontend.

## Project Structure

- `tnp_cell_backend/` — Backend API (Node.js, Express, MongoDB)
- `tnp_cell_frontend/` — Frontend (React, Vite, Tailwind, shadcn/ui)

## Overview

This repository contains two main apps:

- Backend: REST API for authentication, students, companies, trainings, placements, highlights, and applications.
- Frontend: React SPA that consumes the backend API and provides admin and student views.

## Tech Stack

- Backend: Node.js, Express, Mongoose, JWT, bcrypt, dotenv
- Frontend: React, Vite, Tailwind CSS, React Router, Axios

## Prerequisites

- Node.js (v16+ recommended)
- npm or pnpm (or bun for the frontend if preferred)
- MongoDB instance (local or Atlas)

## Backend — Quick Start

1. Open a terminal in `tnp_cell_backend`.
2. Install dependencies:

```bash
cd tnp_cell_backend
npm install
```

3. Create a `.env` file in `tnp_cell_backend` with these variables:

- `MONGO_URI` — MongoDB connection string
- `PORT` — Port to run the server (default: `5000` expected in `server.js`)
- `JWT_SECRET` — Secret for signing JWTs
- `JWT_EXPIRE` — JWT expiry (e.g. `1d`)
- `JWT_COOKIE_EXPIRE` — Cookie expiry in days

4. Run the server:

```bash
npm run dev    # uses nodemon
# or
npm start      # production
```

Backend scripts (from `package.json`):

- `start` — `node server.js`
- `dev` — `nodemon server.js`

Key backend config files:

- `config/database.js` — connects using `process.env.MONGO_URI`
- `config/jwt.js` — reads `JWT_SECRET`, `JWT_EXPIRE`, `JWT_COOKIE_EXPIRE`

## Frontend — Quick Start

1. Open a terminal in `tnp_cell_frontend`.
2. Install dependencies:

```bash
cd tnp_cell_frontend
npm install
```

3. Update frontend API base URL (if needed) in `src/api/axios.js` to point to the running backend.

4. Run the dev server:

```bash
npm run dev
```

Frontend scripts (from `package.json`):

- `dev` — `vite` (development server)
- `build` — `vite build` (production build)
- `preview` — `vite preview`
- `test` — `vitest run`

## Environment & Configuration

- Backend expects the MongoDB URI and JWT environment variables (see section above).
- Frontend may require an API base URL; check `src/api/axios.js` and the `AuthContext` for how auth tokens are stored.

## API Endpoints (high level)

The backend organizes routes under `/routes/` — notable modules:

- Authentication: `routes/authRoutes.js` — login, signup, logout
- Students: `routes/studentRoutes.js`
- Companies: `routes/companyRoutes.js`
- Trainings: `routes/trainingRoutes.js`
- Placements: `routes/placementRoutes.js`
- Applications & Highlights: corresponding routes/controllers

Start the backend and inspect `controllers/` to see exact endpoints and expected request bodies.

## Development Tips

- Use Postman or similar to test backend endpoints while developing frontend features.
- Enable CORS in backend if frontend runs on a different origin (backend already includes `cors` dependency).
- Use `nodemon` for backend auto-reload during development (`npm run dev`).

## Contributing

1. Fork the repo and create a feature branch.
2. Run both backend and frontend locally and ensure endpoints work.
3. Open a PR describing changes and testing steps.

## Troubleshooting

- MongoDB connection errors: verify `MONGO_URI` and network/Atlas IP whitelist.
- JWT/auth issues: confirm `JWT_SECRET` and expiry values in `.env`.

---

If you want, I can also:

- Add a `.env.example` file for both backend and frontend
- Generate a concise API reference (endpoints + payloads)
- Add setup scripts to make running both apps easier (concurrently/docker)

README created at project root.
