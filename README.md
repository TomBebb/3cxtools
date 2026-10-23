# 3cxtools

Monorepo using **Bun** workspaces with a demo **Elysia** server and **Vue 3 + Vite** frontend.

Docker-ready for local development and production-like runs.

## Structure

```
.
├── apps
│   ├── server     # Elysia + Bun API
│   └── web        # Vue 3 + Vite frontend
├── docker-compose.yml
├── package.json
└── README.md
```

## Prerequisites

- [Bun](https://bun.sh) (latest)
- Docker & Docker Compose (optional, for containerised runs)

## Local Development

```bash
# Install all workspace dependencies
bun install

# Run both apps
bun run dev

# Or individually
bun run dev:server   # http://localhost:3000
bun run dev:web      # http://localhost:5173
```

## Docker

```bash
docker compose up --build
```

- Frontend: http://localhost:5173
- Backend: http://localhost:3000

## Features

- Bun workspaces monorepo
- Elysia server (Hello endpoint + CORS)
- Vue 3 frontend that calls the backend
- Multi-service Docker Compose setup
