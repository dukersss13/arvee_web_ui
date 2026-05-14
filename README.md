# arvee_web_ui

Standalone web frontend for ArVee, separated from the backend repository.

## Backend Connection

This frontend connects to the deployed backend API at:

- `https://arvee-backend-5hqe7uiuka-uc.a.run.app`

You can override this at runtime by setting localStorage key `arveeApiBaseUrl`.

Example in browser console:

```js
localStorage.setItem("arveeApiBaseUrl", "https://your-backend-url")
location.reload()
```

## Auth

The backend currently expects authenticated requests.

This UI sends:

- `Authorization: Bearer <token>` when `localStorage.arveeAuthToken` exists
- `X-User-Id: <email>` when `localStorage.arveeUserEmail` exists

Set from browser console:

```js
localStorage.setItem("arveeAuthToken", "<token-from-/api/auth/login>")
localStorage.setItem("arveeUserEmail", "you@example.com")
location.reload()
```

## Run Locally

Because this is a static app, serve files with any static server.

### Option 1: Python

```bash
cd arvee_web_ui
python3 -m http.server 8080
```

Then open `http://localhost:8080`.

### Option 2: VS Code Live Server

Open the folder and run Live Server on `index.html`.

## Required Backend CORS

Backend must allow the frontend origin in `ARVEE_CORS_ORIGINS`.

Example:

```bash
ARVEE_CORS_ORIGINS=http://localhost:8080,https://your-frontend-domain
```
