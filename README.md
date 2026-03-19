# AI Interview Assistant

A real-time interview assistant that listens to questions and delivers AI-powered answers with voice synthesis. Upload your resume and job description for context-aware responses.

## Features

- **Real-time speech recognition** — Listen to interview questions (Deepgram integration)
- **AI-powered responses** — OpenAI integration for intelligent answers
- **Voice synthesis** — Text-to-speech for responses
- **Document upload** — Resume and job description (PDF, Word, plain text)
- **Context-aware** — Responses tailored to your uploaded documents
- **Modern UI** — React + Vite + Tailwind CSS

## Quick start with Docker

**Prerequisites:** [Docker](https://docs.docker.com/get-docker/) and [Docker Compose](https://docs.docker.com/compose/install/).

```bash
# Build and start both backend and frontend
docker compose up -d --build

# Open the app
# Frontend: http://localhost:5173
# Backend API: http://localhost:3000
```

**Optional — API keys:** Create a `.env` file in the project root and uncomment the `env_file: .env` line in `docker-compose.yml`, then add:

```env
OPENAI_API_KEY=your_openai_key
DEEPGRAM_API_KEY=your_deepgram_key
```

Restart: `docker compose up -d`.

**Stop:**

```bash
docker compose down
```

## Local development

**Prerequisites:** Node.js 20+, npm.

### Backend

```bash
cd backend
npm install
# Create .env with OPENAI_API_KEY, DEEPGRAM_API_KEY, etc. (see backend/src/config/env.ts)
npm run dev
```

Runs at **http://localhost:3000**.

### Frontend

```bash
cd frontend
npm install
# Optional: .env.local with VITE_OPENAI_API_KEY, VITE_API_BASE_URL=http://localhost:3000
npm run dev
```

Runs at **http://localhost:5173**.

The frontend uses `VITE_API_BASE_URL` (default `http://localhost:3000`) for API and Socket.IO.

## Environment variables

| Variable | Where | Description |
|----------|--------|-------------|
| `PORT` | Backend | Server port (default `3000`) |
| `OPENAI_API_KEY` | Backend | OpenAI API key |
| `DEEPGRAM_API_KEY` | Backend | Deepgram API key for speech recognition |
| `ALLOWED_ORIGINS` | Backend | CORS origins (default `*`) |
| `VITE_API_BASE_URL` | Frontend (build) | Backend URL (default `http://localhost:3000`) |
| `VITE_OPENAI_API_KEY` | Frontend | Optional; can also configure in UI |

See `backend/src/config/env.ts` for full backend env schema.

## Project structure

```
AI-Interview-Copilot/
├── backend/                 # Node + Express + Socket.IO
│   ├── src/
│   │   ├── app.ts
│   │   ├── server.ts
│   │   ├── config/
│   │   ├── controllers/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── sockets/         # Deepgram & OpenAI sockets
│   │   └── utils/
│   └── Dockerfile
├── frontend/                # React + Vite + Tailwind
│   ├── src/
│   │   ├── components/
│   │   ├── hooks/
│   │   ├── services/
│   │   └── utils/
│   ├── Dockerfile
│   └── README.md            # Detailed frontend docs & architecture
├── docker-compose.yml
└── README.md
```

For component architecture, hooks, and usage details, see [frontend/README.md](frontend/README.md).

## Usage

1. **Configure API keys** — In the app or via env (OpenAI, optional Deepgram).
2. **Upload documents** — Resume and job description for personalized answers.
3. **Start listening** — Use the microphone to capture questions.
4. **Get responses** — AI answers and optional text-to-speech.

## License

MIT — use freely for interview preparation.
