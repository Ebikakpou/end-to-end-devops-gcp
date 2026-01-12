# Use official Node.js lightweight image
FROM node:18-alpine

# Set working directory inside container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json first
# This allows Docker to cache dependencies
COPY app/package*.json ./

# Install dependencies
RUN npm install --production

# Copy application source code
COPY app/ .

# Expose application port
EXPOSE 3000

# Health check for Docker
HEALTHCHECK --interval=30s --timeout=5s --start-period=10s --retries=3 \
  CMD wget --no-verbose --tries=1 --spider http://localhost:3000/health || exit 1

# Start the application
CMD ["npm", "start"]
