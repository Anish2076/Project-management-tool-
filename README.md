# Teamflow — Project Management Tool

A full-stack team project board with accounts, project membership, assigned tasks, comments, inbox notifications, and live board updates.

## website  link 
http://localhost:5173


## Requirements

- Node.js 22.13 or newer (the app uses Node's built-in SQLite module)
- npm

## Run locally

1. Copy `.env.example` to `.env`. Set `JWT_SECRET` to a unique random string at least 24 characters long. The local development server uses a development-only fallback when the variable is omitted; production will refuse to start without it.
2. Install dependencies with `npm install`.
3. Start the API and Vite development server with `npm run dev`.
4. Open `http://localhost:5173`, create an account, and create a project.

In Windows PowerShell, use `npm.cmd` instead of `npm` if script execution policy blocks `npm.ps1`.

The API listens on port 4000 by default, and SQLite creates its database at `server/data/gather.db`. To use a different API port or database path, set `PORT` or `DATABASE_FILE` in `.env`. Set `CLIENT_ORIGIN` to the frontend origin when it is not `http://localhost:5173`.

## Features

- Secure registration and login with bcrypt password hashes and expiring JWTs; profile settings let users update their name, email, and password.
- User-owned projects, project membership, and email-based invitations for registered accounts.
- Task cards with descriptions, status, priority, due dates, and project-member assignments.
- Task conversations with comments.
- Authenticated Socket.IO updates for project boards and assignment/comment/member notifications in an inbox.
- SQLite persistence, foreign-key constraints, input validation, and project membership authorization.

For a production deployment, use HTTPS, configure a strong secret and the correct client origin, and put the Vite-built `dist` assets behind a static web server or CDN.

## Scripts

- `npm run dev` — run frontend and API in watch/development mode.
- `npm run build` — type-check and build the frontend.
- `npm start` — run the API (serve the built frontend separately).
