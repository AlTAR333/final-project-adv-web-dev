# Student Records API — Node.js (Express + SQLite)
A lightweight and secure REST API for managing student records, built with Express, a layered architecture (Controllers -> Services -> Models), SQLite persistence, and API-key authentication.

## Requirements
- Node.js 18+
- npm

## Installation
```bash
npm init -y
npm install express sql.js dotenv
npm install -D nodemon
```

Create a .env file from .env.example and configure:
```
API_KEY=your-strong-random-value
PORT=3000
NODE_ENV=development
DATABASE_URL=./database.sqlite
```

## Running the API
Development (auto-reload):
```bash
npm run dev
```
Production-style run:
```bash
npm start
```

## Endpoints
### Public Endpoints
- GET / — Welcome message + route list
- GET /health — Basic health check

### Protected Endpoints
Authentication via one of the headers:
- X-API-Key: <key>
- Authorization: Bearer <key>

Available routes:
- GET /users — Retrieve all users
- GET /users/:id — Retrieve a user by ID
- POST /users — Create a user
   ```json
   { "name": "Alice", "email": "a@ex.com" }
   ```
- PUT /users/:id — Update a user
- DELETE /users/:id — Remove a user

## Curl Examples
### List users
```bash
curl -H "X-API-Key: $API_KEY" http://localhost:3000/users
```
### Create a user
```bash
curl -X POST -H "Content-Type: application/json" \
     -H "X-API-Key: $API_KEY" \
     -d '{"name":"Eve","email":"eve@example.com"}' \
     http://localhost:3000/users
```

## Additional Notes
- In development, the database auto-seeds 4 users if the file is empty.
- `.env` and SQLite DB files are included in .gitignore.
- Deployable to Render:
   - Set environment variables in the dashboard
   - Mount a persistent volume for the SQLite file

---

# Quick Start (TL;DR)

1. Install:
```bash
npm init -y
npm install express sql.js dotenv
npm install -D nodemon
```

2. Add the project files.

3. Create `.env` and set a strong `API_KEY`.

4. Run:
```bash
npm run dev
```

5. Test:
```bash
curl -H "X-API-Key: yourkey" http://localhost:3000/users
```
