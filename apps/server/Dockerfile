FROM oven/bun:1 AS base
WORKDIR /app

# Install dependencies (workspace-aware)
COPY package.json bun.lock* ./
COPY apps/server/package.json ./apps/server/
RUN bun install --filter server --production

# Copy source
COPY apps/server ./apps/server

WORKDIR /app/apps/server
ENV NODE_ENV=production
EXPOSE 3000

CMD ["bun", "run", "src/index.ts"]
