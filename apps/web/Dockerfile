# Build stage
FROM oven/bun:1 AS build
WORKDIR /app

COPY package.json bun.lock* ./
COPY apps/web/package.json ./apps/web/
RUN bun install --filter web

COPY apps/web ./apps/web
WORKDIR /app/apps/web
RUN bun run build

# Serve stage
FROM nginx:alpine
COPY --from=build /app/apps/web/dist /usr/share/nginx/html
COPY apps/web/nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
