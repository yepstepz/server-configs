# Use the official Bun image
FROM oven/bun:latest

# Set the working directory
WORKDIR /app

# Copy the application code into the image
COPY webmentions-server /app

# Install dependencies
RUN bun install --production

# Expose the port your server runs on
# EXPOSE 3000

# Deal with Prisma
RUN bun run prisma db push
RUN bun run prisma db pull
RUN bun run prisma generate

# Command to start the application
CMD ["bun", "run", "src/server/index.js"]
