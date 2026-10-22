# Kalakaar AI

Kalakaar AI helps artisans turn Punjabi product descriptions into English marketing content. The project includes a React frontend and a Flask API for account, conversation, image, and audio features.

## Tech stack

- Frontend: React, TypeScript, Vite, Tailwind CSS
- Backend: Python 3.11, Flask, SQLAlchemy

## Prerequisites

- Node.js and npm
- Python 3.11
- API credentials for any optional Google Cloud, Gemini, Groq, translation, or Clipdrop features you want to use

## Run locally

### Backend

From the repository root, create and activate a virtual environment, install the backend dependencies, and start Flask:

```powershell
cd backend
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
python app.py
```

The API listens at `http://127.0.0.1:5001`. Its health endpoint is `http://127.0.0.1:5001/api/health`.

The backend loads environment variables from a `.env` file. Create `backend/.env` for local configuration; do not commit credentials. Depending on the features you use, configure:

| Variable | Used for |
| --- | --- |
| `SECRET_KEY` | Flask session signing |
| `DATABASE_URL` | Database connection; SQLite is used when unset |
| `GEMINI_API_KEY` | Gemini content generation |
| `GROQ_API_KEY` | Groq-powered generation |
| `TRANSLATION_API_KEY` | Translation |
| `CLIPDROP_API_KEY` | Image enhancement |
| `GOOGLE_APPLICATION_CREDENTIALS_JSON` | Google Cloud Speech and Text-to-Speech credentials |

Google Cloud credentials can also be supplied as a local `backend/credentials.json` file. Keep credential files private.

### Frontend

In a second terminal, from the repository root:

```powershell
cd frontend
npm ci
npm run dev
```

Open [http://localhost:8080](http://localhost:8080).

Some frontend pages currently use a deployed API URL, while the standard studio page uses `http://127.0.0.1:5001/api`. To test a page against your local backend, update that page's `API_BASE_URL` in `frontend/src/pages` as needed.

## Build and lint

Run these commands from `frontend`:

```powershell
npm run build
npm run lint
```

## API endpoints

- `GET /api/health` — service health
- `GET /api/platforms` — supported platforms
- `POST /api/signup` and `POST /api/login` — account operations
- `POST /api/conversation/start` and `POST /api/conversation/respond` — product conversation
- `POST /api/conversation/generate` — generate content from a conversation
- `POST /api/upload_image` and `POST /api/enhance-image` — image operations

## Project layout

```text
backend/   Flask API and Python dependencies
frontend/  React/Vite application
```
