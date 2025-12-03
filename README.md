# Room Booking – Frontend Service (React + TypeScript)

This repository contains the **frontend microservice** of the Room Booking Platform.  
It is a production-oriented React + TypeScript application served via **Nginx** inside Docker.

The frontend communicates with the backend API (running in its own container) through the environment variable:  
`VITE_API_BASE_URL`

---

## 🚀 How to Run (Docker)

To build and start the frontend container:

```bash
docker compose up -d --build
```

This will:

- Build the React app (Vite)
- Rewrite API URLs using the `VITE_API_BASE_URL` build-time argument
- Serve the compiled app through **Nginx**
- Expose it locally at:

```
http://localhost:4173
```

---

## 🧩 Environment Configuration

API base URL is passed during the Docker build process using:

```yaml
args:
  VITE_API_BASE_URL: "http://localhost:4000/api"
```

Inside the app, API calls use:

```ts
import.meta.env.VITE_API_BASE_URL
```

---

## 📁 Project Structure

```
frontend/
├── src/
│   ├── auth/           # Auth context + API wrapper
│   ├── components/     # UI components
│   ├── pages/          # Login, Register, Rooms, MyBookings
│   ├── styles/         # Minimal styles
│   └── main.tsx        # App entry (React Router)
├── public/             # Static assets
├── Dockerfile          # Builds app + serves via Nginx
├── nginx.conf          # SPA routing + static file serving
└── docker-compose.yml  # Frontend container config
```

---

## 🧪 Local Development (Without Docker)

If you want to run the frontend directly:

```bash
npm install
npm run dev
```

Navigate to:

```
http://localhost:5173
```

Make sure the backend (`http://localhost:4000`) is running.

---

## 🎯 Features

- Login & Register  
- Room search (location, dates, capacity)  
- Booking flow  
- My bookings dashboard  
- Token-aware UI (auto-logout on expired token)  
- Clean micro-frontend architecture  
