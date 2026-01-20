# ApplyEase - Local Setup Complete! 🎉

## Quick Start Guide

### Prerequisites (✅ INSTALLED)
- ✅ PostgreSQL 17 with pgvector
- ✅ Python 3.14
- ✅ Node.js v22
- ✅ Ollama with llama3.1:8b model
- ✅ All dependencies installed

---

## Starting ApplyEase

### 1. Start Backend (Terminal 1)
```bash
cd /Users/mamjed/Documents/GitHub/ApplyEase/applyease-backend
source .venv/bin/activate
export PATH="/opt/homebrew/opt/postgresql@17/bin:$PATH"
export LLM_PROVIDER=ollama
export LLM_MODEL=llama3.1:8b
uvicorn app:app --reload --port 8000
```

The backend will be available at: **http://localhost:8000**

### 2. Start Frontend (Terminal 2)
```bash
cd /Users/mamjed/Documents/GitHub/ApplyEase/frontend
npm start
```

The frontend will open automatically at: **http://localhost:3000**

### 3. Load Chrome Extension
1. Open Chrome and go to: `chrome://extensions`
2. Enable "Developer mode" (toggle in top right)
3. Click "Load unpacked"
4. Select: `/Users/mamjed/Documents/GitHub/ApplyEase`
5. The extension is now loaded!

---

## First Time Setup

### 1. Sign Up
1. Go to http://localhost:3000
2. Click "Sign Up"
3. Enter your details
4. You'll be automatically logged in

### 2. Upload Your Resume
1. Go to Dashboard
2. Click "Upload Resume"
3. Select your PDF resume
4. Fill in your profile details (name, email, phone, location)
5. Click "Save"

### 3. Test the Extension
1. Go to any job posting (LinkedIn, Indeed, etc.)
2. You should see a "Resume Match: X%" widget in the bottom-right
3. Click the widget or extension icon to see matching/missing keywords
4. Click "Auto Fill" to fill the application form

---

## Features

### Dashboard
- Upload and manage your resume
- View match statistics
- Quick actions

### Job Tracker
- Track applications (Saved → Applied → Interview → Offer → Rejected)
- Drag and drop between stages
- Board and list views

### Resume Builder
- Structured resume sections
- Generate tailored CV for specific jobs
- PDF export

### Cover Letters
- Generate AI-powered cover letters
- Template-based letters
- Save and download history

### Extension Features
- Auto-fill application forms
- Resume matching with keywords
- Generate custom answers to questions (using local LLM)
- Auto-track applications
- Upload resume automatically

---

## Environment Variables (Optional)

Create `.env` file in `applyease-backend/`:
``bash
# Database (defaults work for local setup)
PGHOST=localhost
PGPORT=5432
PGDATABASE=applyease

# JWT (default is fine for local)
JWT_KEY=dev-secret
JWT_EXPIRES_IN_MIN=60

# LLM Configuration
LLM_PROVIDER=ollama
LLM_MODEL=llama3.1:8b
OLLAMA_HOST=http://localhost:11434
```

---

## Troubleshooting

### Backend won't start
- Make sure PostgreSQL is running: `brew services list`
- If not: `brew services start postgresql@17`
- Check database exists: `psql applyease -c "SELECT 1;"`

### Frontend won't start
- Delete `node_modules` and reinstall:
  ```bash
  cd frontend
  rm -rf node_modules package-lock.json
  npm install
  ```

### Extension not working
- Check if backend is running: `curl http://localhost:8000/healthz`
- Check if frontend is running: `curl http://localhost:3000`
- Reload extension: Chrome → Extensions → Click reload icon

### LLM not responding
- Check Ollama is running: `ollama list`
- If model not found: `ollama pull llama3.1:8b`
- Test: `ollama run llama3.1:8b "Hello"`

---

## Stopping Services

```bash
# Stop backend: Ctrl+C in Terminal 1
# Stop frontend: Ctrl+C in Terminal 2
# Stop PostgreSQL (optional): brew services stop postgresql@17
```

---

## API Endpoints

- Health check: http://localhost:8000/healthz
- API docs: http://localhost:8000/docs (FastAPI Swagger UI)
- Signup: POST http://localhost:8000/signup
- Login: POST http://localhost:8000/login

---

## Need Help?

- Check logs in terminal windows
- Review README.md for detailed documentation
- Backend logs show all API requests
- Frontend console (F12) shows extension communication

---

**Enjoy ApplyEase! 🚀**
