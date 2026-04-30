# NyayaSakhi-Docs
documentation and live URLs for the project NyayaSakhi
# Nyaya Sakhi — Backend

AI-powered legal aid platform for Indian women. Voice-first kiosk support in 11 Indian languages.

## Live App (Vercel)

- Main URL: https://nyaya-sakhi.vercel.app
- Citizen app: https://nyaya-sakhi.vercel.app/get-help
- Volunteer login: https://nyaya-sakhi.vercel.app/volunteer/login

## Quick Start

```bash
# 1. Create virtual environment
python -m venv venv
source venv/bin/activate   # Linux/Mac
# venv\Scripts\activate    # Windows

# 2. Install dependencies
pip install -r requirements.txt

# 3. Set up PostgreSQL
# Create database: nyaya_sakhi

# 4. Configure environment
# Edit .env with your API keys (Gemini, Bhashini, Twilio)

# 5. Run server
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

## API Docs

- Swagger UI: http://localhost:8000/docs
- ReDoc: http://localhost:8000/redoc

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| **Users** | | |
| POST | `/api/v1/users/register` | Register citizen |
| POST | `/api/v1/users/login` | Login (phone + password) |
| GET | `/api/v1/users/me` | Get profile |
| PATCH | `/api/v1/users/me` | Update profile |
| POST | `/api/v1/users/cases` | File a case (text) |
| GET | `/api/v1/users/cases` | List my cases |
| GET | `/api/v1/users/cases/{id}` | Get case detail |
| **Kiosk** | | |
| POST | `/api/v1/kiosk/voice` | Full voice pipeline |
| POST | `/api/v1/kiosk/voice/followup` | Follow-up on case |
| POST | `/api/v1/kiosk/tts` | Text-to-speech |
| POST | `/api/v1/kiosk/translate` | Translate text |
| **Volunteers** | | |
| POST | `/api/v1/volunteers/register` | Register volunteer |
| POST | `/api/v1/volunteers/login` | Volunteer login |
| GET | `/api/v1/volunteers/me` | Volunteer profile |
| PATCH | `/api/v1/volunteers/me` | Update profile |
| GET | `/api/v1/volunteers/cases` | List assigned cases |
| PATCH | `/api/v1/volunteers/cases/{id}` | Update case status |
| **Admin** | | |
| GET | `/api/v1/admin/dashboard` | Analytics dashboard |
| GET | `/api/v1/admin/cases` | List all cases |
| GET | `/api/v1/admin/cases/{id}` | Get any case |
| PATCH | `/api/v1/admin/cases/{id}` | Update/assign case |
| POST | `/api/v1/admin/cases/{id}/escalate` | Escalate case |
| GET | `/api/v1/admin/volunteers` | List volunteers |
| POST | `/api/v1/admin/volunteers/{id}/approve` | Approve volunteer |
| POST | `/api/v1/admin/volunteers/{id}/suspend` | Suspend volunteer |
| GET | `/api/v1/admin/users` | List all users |

## Tech Stack

- **FastAPI** — async web framework
- **PostgreSQL + SQLAlchemy** — async ORM
- **Groq AI** — AI legal guidance
- **savaram** — Indian language STT / TTS / Translation
- **Twilio** — SMS notifications
- **JWT** — authentication

## Running Tests

```bash
pytest app/tests/ -v
```
