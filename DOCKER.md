# 🐳 Docker Guide for Inventory Management App

This guide will help you run the Inventory Management application using Docker Desktop on Windows, macOS, or Linux.

## Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop/) installed and running
- Git (to clone the repository)

## Quick Start

### Option 1: Using Docker Compose (Recommended)

1. **Clone the repository:**
   ```bash
   git clone https://github.com/MahaKoala/NicksInvClient.git
   cd NicksInvClient
   git checkout docker-ready
   ```

2. **Build and run with Docker Compose:**
   ```bash
   docker-compose up --build
   ```

3. **Access the application:**
   - Open your browser and go to: http://localhost:3000
   - The app will be running in production mode

4. **Stop the application:**
   ```bash
   docker-compose down
   ```

### Option 2: Using Docker Commands Directly

1. **Build the Docker image:**
   ```bash
   docker build -t inventory-app .
   ```

2. **Run the container:**
   ```bash
   docker run -p 3000:3000 inventory-app
   ```

3. **Access the application:**
   - Open your browser and go to: http://localhost:3000

## Development Mode

To run the application in development mode with hot reload:

```bash
docker-compose --profile dev up inventory-app-dev --build
```

This will:
- Run the app in development mode
- Enable hot reload for code changes
- Make the app available at: http://localhost:3001

## Docker Desktop Integration

### Viewing Containers
1. Open Docker Desktop
2. Go to the "Containers" tab
3. You'll see your `nicksinvclient` containers running

### Container Management
- **Start/Stop:** Use the play/pause buttons in Docker Desktop
- **View logs:** Click on the container name to see real-time logs
- **Terminal access:** Click "CLI" to open a terminal inside the container

### Health Check
The application includes a health check endpoint:
- **URL:** http://localhost:3000/api/health
- **Response:** JSON with status, timestamp, and service info

## Available Scripts in Docker

When running the container, these scripts are available:

```bash
# Production build (used in Dockerfile)
npm run build

# Start production server
npm start

# Development server (used in dev compose service)
npm run dev

# Linting
npm run lint
```

## Environment Variables

You can customize the application using environment variables:

```bash
# Example with custom port
docker run -p 8080:8080 -e PORT=8080 inventory-app
```

Common environment variables:
- `PORT`: Server port (default: 3000)
- `NODE_ENV`: Environment mode (production/development)
- `NEXT_TELEMETRY_DISABLED`: Disable Next.js telemetry (1 to disable)

## Troubleshooting

### Port Already in Use
If port 3000 is busy, use a different port:
```bash
docker run -p 8080:3000 inventory-app
# Then access at http://localhost:8080
```

### Build Issues
If you encounter build issues:
1. Clear Docker cache: `docker system prune -a`
2. Rebuild without cache: `docker-compose build --no-cache`

### Container Won't Start
1. Check Docker Desktop is running
2. Verify no other service is using port 3000
3. Check container logs in Docker Desktop

## Docker Commands Reference

### Basic Commands
```bash
# Build image
docker build -t inventory-app .

# Run container
docker run -d -p 3000:3000 --name inventory inventory-app

# Stop container
docker stop inventory

# Remove container
docker rm inventory

# View logs
docker logs inventory

# Shell into container
docker exec -it inventory /bin/sh
```

### Docker Compose Commands
```bash
# Start services
docker-compose up

# Start in background
docker-compose up -d

# Build and start
docker-compose up --build

# Stop services
docker-compose down

# View logs
docker-compose logs

# Start specific service
docker-compose up inventory-app
```

## Production Deployment

This Docker setup is production-ready and includes:
- ✅ Multi-stage build for optimal image size
- ✅ Non-root user for security
- ✅ Standalone output for better performance
- ✅ Health checks for monitoring
- ✅ Proper layer caching for faster builds

For production deployment, consider:
- Using a reverse proxy (nginx)
- Setting up SSL/TLS certificates
- Configuring environment-specific variables
- Setting up monitoring and logging

## File Structure

```
📁 Project Root
├── 🐳 Dockerfile              # Multi-stage production build
├── 🐳 docker-compose.yml      # Docker Compose configuration
├── 🚫 .dockerignore           # Files to exclude from Docker build
├── 📖 DOCKER.md              # This documentation
└── 📂 src/
    └── app/api/health/        # Health check endpoint
```

## Need Help?

- **Docker Desktop:** Check the official Docker Desktop documentation
- **Next.js Docker:** Visit [Next.js Docker documentation](https://nextjs.org/docs/deployment#docker-image)
- **Issues:** Check container logs in Docker Desktop for error details
