# Deployment Guide

## Deploying on Vercel

1. Install Vercel CLI:
   ```powershell
npm i -g vercel
```
2. Login:
   ```powershell
vercel login
```
3. Deploy the server and client separately:
   - `cd server` and `vercel`
   - `cd ../client` and `vercel`

## Environment Variables

Set the following variables in your hosting provider:
- `MONGODB_URI`
- `JWT_SECRET`
- `CLOUDINARY_CLOUD_NAME`
- `CLOUDINARY_API_KEY`
- `CLOUDINARY_API_SECRET`
- `VITE_BACKEND_URL`

## Production Notes

- Use HTTPS endpoints for backend and frontend.
- Keep secrets out of source control.
- Enable CORS only for allowed origins.
