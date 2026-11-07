# Hoo-Bank client (owned fork)

React 19/Vite 7 frontend in the Skill-Aura-Official fork of [SIYA1104/Hoo-Bank](https://github.com/SIYA1104/Hoo-Bank). The upstream project and contributors retain their attribution. This documentation changes only the owned fork, not upstream.

The client contains home, registration, login and dashboard views for a banking-style demonstration. It is not evidence of regulated banking, real money movement or production readiness.

## Local setup

Use Node.js 22.12+ and npm. From `Client`:

```sh
npm ci
npm run dev
```

Vite normally serves `http://localhost:5173`; inspect the printed URL. `src/ApiUri.js` currently sets the API to `http://localhost:8000/api/v1`. It is a source constant, not an environment-variable override. A separately configured `Server` process must match it; server CORS currently permits localhost:5173 only.

The server needs MongoDB, `MONGODB_URI` and `ACCESS_TOKEN_SECRET` supplied privately. Its default port is `8000`, matching the client API constant. If you set `PORT`, update the client API origin to match. Startup scripts preload `.env`, while index.js additionally looks for `./env`. Registration and login require backend and reCAPTCHA configuration for the intended domain. Use test data for verification.

## Checks and limits

```sh
npm run build
npm run lint
npm run preview
```

The package has no automated test script. These frontend checks do not verify backend authentication, transaction behavior or security. MongoDB, reCAPTCHA and authenticated dashboard operations were not exercised in this documentation review. A default Vite preview uses port 4173 and is not a production server; the backend's fixed CORS policy may need a reviewed change for that origin.

If login fails, verify backend health, the fixed API origin and cookie/CORS behavior. Do not reset existing accounts to make a test pass. No root licence file exists in the reviewed fork; this README does not invent or change a licence. Existing package notices remain unchanged.

## Documentation review checks (2026-11-07)

Client build and lint passed on Node 24.3.0. The server entry point passed a syntax check after correcting its default port. Backend workflows remain unverified.
