# NIVAAS Installation Guide

> ⚠️ **Note:** NIVAAS is currently in prototype stage. This guide describes the planned installation process for the full implementation.

---

## Prerequisites

| Requirement | Version |
|-------------|---------|
| Node.js | 18.x or higher |
| npm / yarn | Latest |
| PostgreSQL | 14.x or higher |
| Redis | 6.x or higher (optional, for caching) |
| Google Maps API Key | — |

---

## Environment Variables

Create a `.env` file in the project root:

```env
# Database
DATABASE_URL=postgresql://user:password@localhost:5432/nivaas

# Redis (optional)
REDIS_URL=redis://localhost:6379

# Google Maps
GOOGLE_MAPS_API_KEY=your_api_key_here

# JWT
JWT_SECRET=your_jwt_secret_here
JWT_EXPIRY=7d

# File Storage (S3 or local)
STORAGE_TYPE=local
STORAGE_PATH=./uploads

# Server
PORT=3000
NODE_ENV=development
```

---

## Quick Start

```bash
# Clone repository
git clone https://github.com/your-org/nivaas.git
cd nivaas

# Install dependencies
npm install

# Run database migrations
npm run db:migrate

# Seed development data (optional)
npm run db:seed

# Start development server
npm run dev
```

---

## Docker (Planned)

```bash
docker-compose up -d
```

---

## API Documentation

Once running, API docs will be available at:

- Swagger UI: `http://localhost:3000/api-docs`
- OpenAPI spec: `http://localhost:3000/api-docs.json`

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Database connection failed | Check PostgreSQL is running; verify DATABASE_URL |
| Maps not loading | Ensure GOOGLE_MAPS_API_KEY is set and has Maps JavaScript API enabled |
| CORS errors | Add frontend origin to CORS whitelist in backend config |
