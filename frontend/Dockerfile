# Build stage
FROM node:20-slim as builder

# Set working directory
WORKDIR /app

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm ci

# Copy project files
COPY . .

# Build the project
RUN npm run build

# Production stage - just create a directory with the built files
FROM scratch

# Copy built files from builder stage
COPY --from=builder /app/dist /dist
