# Resume-Ready Deployment Guide

## 1) Frontend on Vercel
- Import the client folder into Vercel.
- Set the build command to: `npm run build`
- Set the output directory to: `dist`
- Add this environment variable:
  - `VITE_API_BASE_URL=https://your-backend-url.onrender.com/api`

## 2) Backend on Render
- Create a new Web Service from the backend folder.
- Use:
  - Build Command: `npm install && npm run build`
  - Start Command: `npm run start`
- Add the same environment variables from backend/.env.example.
- Important values:
  - `NODE_ENV=production`
  - `PORT=8000` (or let Render assign it)
  - `FRONTEND_ORIGIN=https://your-frontend-url.vercel.app`
  - `FRONTEND_GOOGLE_CALLBACK_URL=https://your-frontend-url.vercel.app/google/callback`

## 3) Google OAuth
If Google login must work in production, add these redirect URIs in Google Cloud Console:
- `http://localhost:8000/api/auth/google/callback`
- `https://your-backend-url.onrender.com/api/auth/google/callback`
- `https://your-frontend-url.vercel.app/google/callback`

## 4) Notes
- Vercel alone is not enough for this app because the backend, database, and auth sessions need a separate host.
- For a resume demo, this split deployment is the simplest reliable setup.
