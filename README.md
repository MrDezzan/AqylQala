# AqylQala — Digital Sovereignty Platform for Almaty

### Intelligent city management ecosystem powered by a local AI model

**Live Demo:** https://canva.link/7tadsufvum8infk

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

## Getting Started

### Backend
```bash
cd backend
npm install
npm run db:push
npm run seed
npm run dev
