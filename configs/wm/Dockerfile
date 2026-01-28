FROM oven/bun:1.3.6

WORKDIR /app

# 1) Copy only dependency manifests first (better layer caching)
COPY webmentions-server/package.json ./package.json
# bun.lockb may or may not exist; keep the wildcard pattern
COPY webmentions-server/bun.lockb* ./

# 2) Install production dependencies
RUN bun install --production --frozen-lockfile

# 3) Copy the rest of the app
COPY webmentions-server/ ./

# 4) Prisma client generation (expects prisma to be runnable via `bun run prisma`)
RUN bun run prisma generate

# 5) Run the server
CMD ["bun", "run", "src/server/index.js"]
