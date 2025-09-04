# 📦 Inventory Management System

A modern inventory management application built with Next.js 15, React 19, and Tailwind CSS v4.

## 🚀 Features

- **Modern UI**: Built with Tailwind CSS v4 and responsive design
- **Clean Architecture**: Next.js 15 with App Router
- **Production Ready**: Optimized for performance and deployment
- **Docker Support**: Full Docker integration with Docker Desktop
- **TypeScript**: Full type safety throughout the application

## 🐳 Docker Usage (Recommended)

For the easiest setup, use Docker Desktop:

```bash
git clone https://github.com/MahaKoala/NicksInvClient.git
cd NicksInvClient
git checkout docker-ready
docker-compose up --build
```

**📖 See [DOCKER.md](./DOCKER.md) for complete Docker setup guide**

## 💻 Local Development

If you prefer to run locally without Docker:

### Prerequisites
- Node.js 18+ 
- npm or yarn

### Setup
```bash
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) to view the application.

## 🌟 Available Branches

- **`main`** - Full-featured UI with advanced components
- **`tailwind-v4-minimal-fix`** - Minimal UI with core Tailwind v4 fixes only
- **`docker-ready`** - Docker-optimized version (this branch)

## 🏗️ Tech Stack

- **Framework**: Next.js 15 with App Router
- **UI**: React 19 + Tailwind CSS v4
- **Language**: TypeScript
- **Styling**: tw-colors plugin for theming
- **Container**: Docker + Docker Compose
- **Build**: Standalone output for optimal Docker deployment

## 📁 Project Structure

```
src/
├── app/
│   ├── api/health/         # Health check endpoint
│   ├── dashboard/          # Dashboard pages
│   ├── globals.css         # Global styles with Tailwind
│   ├── layout.tsx          # Root layout
│   └── page.tsx            # Home page
└── components/             # Reusable components
```

## 🚢 Deployment

### Docker (Recommended)
See [DOCKER.md](./DOCKER.md) for complete Docker deployment guide.

### Vercel
```bash
npm run build
# Deploy to Vercel
```

### Other Platforms
The application builds to a standalone Next.js app, making it compatible with:
- AWS ECS/Fargate
- Google Cloud Run
- Azure Container Instances
- Any Docker-compatible platform

## 🔧 Configuration

The application is configured with:
- ✅ Tailwind CSS v4 with PostCSS
- ✅ TypeScript strict mode
- ✅ ESLint configuration
- ✅ Docker multi-stage builds
- ✅ Health check endpoints
- ✅ Hydration mismatch fixes

## 📄 License

This project is open source and available under the MIT License.
