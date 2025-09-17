# ---- Build Stage ----
FROM node:20-alpine AS builder

# Set working directory
WORKDIR /src

# Install dependencies (only package.json + lock first for caching)
COPY package*.json ./
RUN npm install

# Copy the rest of the application
COPY . .

# ---- Run Stage ----
FROM node:20-alpine

WORKDIR /src

# Copy node_modules and source from builder
COPY --from=builder /src /src

# Expose port 3000
EXPOSE 3000

# Run in dev mode
CMD ["npm", "run", "dev"]
