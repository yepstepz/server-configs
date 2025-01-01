# Use the official Bun image
FROM oven/bun:latest

# Set the working directory
WORKDIR /app

ARG PROJECT_PATH

# Copy the application code into the image
COPY ${PROJECT_PATH} /app

# Install dependencies
RUN bun install --production

# Expose the port your server runs on
EXPOSE 3000

# Command to start the application
CMD ["bun", "run", "src/server/index.js"]
