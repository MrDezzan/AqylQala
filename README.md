<h1 align="center">AqylQala</h1>
<p align="center"><b>Digital sovereignty platform for Almaty.</b><br>An intelligent city management ecosystem powered by a local, self-hosted AI model.</p>

<p align="center">
  <img src="https://img.shields.io/badge/React-18-61DAFB?style=flat-square&logo=react&logoColor=black" alt="React">
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript">
  <img src="https://img.shields.io/badge/Express-000000?style=flat-square&logo=express&logoColor=white" alt="Express">
  <img src="https://img.shields.io/badge/Prisma-2D3748?style=flat-square&logo=prisma&logoColor=white" alt="Prisma">
  <img src="https://img.shields.io/badge/PostgreSQL-316192?style=flat-square&logo=postgresql&logoColor=white" alt="PostgreSQL">
  <img src="https://img.shields.io/badge/Ollama-local%20AI-000000?style=flat-square" alt="Ollama">
</p>

<p align="center"><a href="https://canva.link/7tadsufvum8infk">Project presentation</a></p>

---

AqylQala is a Gov-Tech platform that acts as a bridge between Almaty residents and the city administration. It addresses the challenge of responding to urban issues efficiently, using a **fully local, self-hosted AI model** to analyze reports, validate submissions, and support administrative decision-making.

---

## Key Capabilities

### For Citizens
- **Interactive Reporting**: Pin city issues on a map with photo evidence.
- **AI Validation**: Reports are checked instantly by the local AI model, giving citizens immediate feedback on submission status.
- **Transparency**: Real-time status tracking ("In progress", "Resolved") with full history.

### For City Administration
- **Analytics Dashboard**: Heatmaps and activity graphs showing issue density and a "social tension index" by district.
- **Report Engine**: Generates official DOCX/XLSX reports ready for city leadership.
- **Access Control & Audit**: Admin panel for managing staff access, with a full audit log of every status change and action.

### Integration
- **Telegram Web App (TWA)** support for citizen-side access.

---

## Why a Local AI Model

Unlike solutions built on external APIs (OpenAI, Google), AqylQala runs a **local model via Ollama**. All data processing happens on the server — sensitive municipal and citizen data never leaves the infrastructure and is never used to train third-party models. This was a deliberate architectural choice for a government-facing system, not just a cost-saving measure.

---

## Tech Stack

**Frontend**
- React 18 + Vite
- Tailwind CSS
- Leaflet with custom layers (clustering, traffic overlays)
- Framer Motion for UI transitions

**Backend**
- Node.js + Express (TypeScript)
- Prisma ORM
- Local AI model (Ollama) for text analysis and validation
- DOCX/XLSX generation service for official reporting

---

## Architecture Notes

- **Aggregation Layer design**: Services like environmental monitoring (AQI) and the urban news feed are built as swappable data-aggregation layers. Connecting real IoT sensors or live RSS feeds only requires updating the backend's data-fetching logic — the frontend stays fully decoupled.
- **Security**: JWT-based Role-Based Access Control (citizen / official / admin), bcrypt password hashing, Helmet.js for HTTP header security, strict CORS policy.
- **API design**: RESTful CRUD across all resources with standard HTTP methods.

---

## Project structure

```
backend/
  src/routes/      auth, problems, ai, environmental, news, logs, users
  src/services/    AI validation, DOCX/XLSX report generation
  src/middleware/  JWT and role checks
  prisma/          schema and seed data
frontend/
  src/             React app: map, citizen reports, admin dashboard
docker-compose.yml PostgreSQL and Redis for local development
```

## Getting Started

You need Node.js 16+, Docker (for PostgreSQL and Redis) and [Ollama](https://ollama.com) for the local model.

```bash
# PostgreSQL and Redis
docker compose up -d
```

### Backend
```bash
cd backend
cp .env.example .env      # set DATABASE_URL, JWT_SECRET, OLLAMA_URL
npm install
npm run db:push
npm run seed
npm run dev
```

### Frontend
```bash
cd frontend
cp .env.example .env      # set VITE_API_URL and your TomTom API key
npm install
npm run dev
```
