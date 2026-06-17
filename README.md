# Chat Bot

> Intelligent Communication Automation — starting with Telegram

Chat Bot automates client communication for businesses. Originally designed for WhatsApp and Instagram, we're launching with **Telegram** as our primary messaging channel, with a roadmap to add WhatsApp, Instagram, and Facebook once Meta API access is secured.

---

## The Problem

- Businesses waste 3–5 hours daily on manual reminders, follow-ups, and updates
- Inconsistent messaging damages brand voice and causes errors
- Missed appointments from no automated reminders → lost revenue
- Irregular social media presence without scheduled content

## The Solution

One platform to automate all client communication. Chat Bot handles:

| Module | Description |
|--------|-------------|
| **Telegram Bot** | Automated messaging, broadcasting, group management |
| **Smart Reminders** | Upload client data via CSV, custom templates, timed triggers |
| **AI Auto-Responder** | Answers FAQs, escalates to human, learns from interactions |
| **Content Scheduler** | Schedule posts and broadcasts (Telegram channels) |
| **Analytics Dashboard** | Web-based dashboard, real-time status, engagement reports |
| **Client Data Manager** | Role-based access, encrypted storage, GDPR-aligned policies |

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| **Backend** | Python, FastAPI |
| **Frontend** | React.js, HTML5, CSS3, JavaScript |
| **Database** | PostgreSQL |
| **Messaging** | Telegram Bot API (python-telegram-bot) |
| **API** | REST APIs |
| **Version Control** | Git + GitHub |
| **Tools** | VS Code, Postman, Docker |
| **Deployment** | Linux VPS / Cloud Platform |

---

## Project Structure

```
chat-bot/
├── backend/
│   ├── app/
│   │   ├── api/              # FastAPI routes
│   │   ├── bot/              # Telegram bot handlers
│   │   ├── core/             # Config, auth, middleware
│   │   ├── models/           # Database models
│   │   ├── schemas/          # Pydantic schemas
│   │   ├── services/         # Business logic
│   │   └── utils/            # Helpers
│   ├── migrations/           # Alembic migrations
│   ├── tests/
│   ├── requirements.txt
│   └── Dockerfile
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/         # API client
│   │   ├── hooks/
│   │   └── utils/
│   ├── package.json
│   └── Dockerfile
├── docs/
│   ├── architecture.md
│   ├── api.md
│   └── deployment.md
├── .github/
│   └── workflows/            # CI/CD pipelines
├── BUILDPLAN.md
├── README.md
└── docker-compose.yml
```

---

## Team Roles

| Role | Members | Responsibilities |
|------|---------|-----------------|
| **Project Manager / Team Lead** | 1 | Planning, task allocation, progress tracking, risk management |
| **Backend Developers** | 2 | API development, bot logic, database, deployment |
| **Frontend Developers** | 2 | Dashboard UI, user experience, API integration |

---

## Quick Start

### Prerequisites

- Python 3.11+
- Node.js 18+
- PostgreSQL 15+
- Docker (optional)

### Backend Setup

```bash
cd backend
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# Configure environment
cp .env.example .env
# Edit .env with your database and Telegram bot token

# Run migrations
alembic upgrade head

# Start server
uvicorn app.main:app --reload
```

### Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

---

## Git Workflow

Per our project management standards:

1. **Feature branches** — create from `main`: `feature/<name>`
2. **Pull Requests** — required before merging to `main`
3. **Code reviews** — every PR must be reviewed by at least 1 team member
4. **Commit messages** — clear, descriptive, conventional format

```
feat: add Telegram reminder scheduler
fix: correct timezone handling in CSV import
docs: update API endpoint documentation
```

---

## Sprint Cadence

We follow **Agile Scrum** with **2-week sprints**. See [BUILDPLAN.md](./BUILDPLAN.md) for the full roadmap.

---

## License

Project undertaken by Web Developers Student Group.

---

## Contact

Built with ❤️ for businesses that value their time.