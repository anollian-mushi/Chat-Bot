# Chat Bot — Build Plan

> **Project Classification:** Medium-to-Large Project (3–6 months)  
> **Methodology:** Agile Scrum (2-week sprints)  
> **Team Size:** 4 members (1 PM/Lead, 2 Backend, 2 Frontend)  
> **Primary Channel:** Telegram (MVP) → WhatsApp/Instagram (Phase 2)

---

## 1. Project Lifecycle Overview

Following the Web Developers Group PM standards (WDG-PM-STD-001), we'll execute across 7 phases:

```
Initiation → Planning → Design → Development → Testing → Deployment → Closure
```

Development itself runs in **6 sprints** (12 weeks), with Testing & Deployment integrated into each sprint.

---

## 2. Sprint Roadmap

### Sprint 0 — Foundation (Week 0)
**Duration:** 3 days (pre-sprint setup)

| Task | Owner | Deliverable |
|------|-------|-------------|
| Repository setup & branch protection | Lead | GitHub repo configured |
| Project environment setup (VS Code, Docker, etc.) | All | Dev environments ready |
| Telegram Bot token acquisition | Backend 1 | Bot registered with @BotFather |
| Database schema design | Backend 2 | ERD diagram |
| UI/UX wireframes (Dashboard) | Frontend 1 | Figma/mockup screens |
| Project backlog creation | Lead | Product Backlog in GitHub Projects |

---

### Sprint 1 — Core Backend & Bot Foundation (Weeks 1–2)
**Goal:** Telegram bot connects and responds. Dashboard skeleton is live.

**Backend Tasks:**
- [ ] Initialize FastAPI project structure
- [ ] Set up PostgreSQL with Alembic migrations
- [ ] Implement Telegram bot connection (`python-telegram-bot`)
- [ ] Create `/start`, `/help`, and basic echo commands
- [ ] Implement user/chat model and database persistence
- [ ] Set up Docker Compose (backend + db)

**Frontend Tasks:**
- [ ] Initialize React project with Vite
- [ ] Set up routing (React Router)
- [ ] Create login page UI (placeholder auth)
- [ ] Build Dashboard layout shell (sidebar + header + content area)
- [ ] Connect frontend to backend health endpoint

**Sprint Review:** Demo a Telegram bot that responds to `/start` and a dashboard that loads.

---

### Sprint 2 — Smart Reminders & Messaging (Weeks 3–4)
**Goal:** Users can upload CSV data, create reminder templates, and schedule messages.

**Backend Tasks:**
- [ ] CSV upload endpoint with validation
- [ ] Reminder scheduling engine (cron-based)
- [ ] Custom message template CRUD
- [ ] Telegram group/channel broadcast endpoint
- [ ] Scheduled message delivery via Telegram
- [ ] Background task worker setup (Celery or APScheduler)

**Frontend Tasks:**
- [ ] CSV upload page with drag-and-drop
- [ ] Client/contact list view (table with search/filter)
- [ ] Reminder creation form (template + time + recipients)
- [ ] Scheduled messages list view
- [ ] Template editor page

**Sprint Review:** Upload a CSV → schedule a reminder → Telegram delivers it at the right time.

---

### Sprint 3 — AI Auto-Responder & FAQ System (Weeks 5–6)
**Goal:** Bot answers FAQs automatically and escalates unknown queries.

**Backend Tasks:**
- [ ] FAQ management CRUD API
- [ ] Keyword-based FAQ matching engine
- [ ] AI-powered fallback (OpenAI API or local model — configurable)
- [ ] Human escalation flow (forward to admin chat)
- [ ] Conversation logging & analytics
- [ ] Learning mechanism (approved answers enrich FAQ)

**Frontend Tasks:**
- [ ] FAQ editor page (add/edit/delete Q&A pairs)
- [ ] Conversation history view
- [ ] Escalation queue dashboard (admin view)
- [ ] Auto-responder configuration page (toggle AI vs. keyword mode)
- [ ] Response analytics cards (answered vs. escalated ratio)

**Sprint Review:** Send a FAQ question to the bot → get auto-reply. Send unknown query → escalated to dashboard.

---

### Sprint 4 — Analytics Dashboard & Content Scheduler (Weeks 7–8)
**Goal:** Full analytics visibility and Telegram channel content scheduling.

**Backend Tasks:**
- [ ] Message delivery stats API (sent, delivered, failed)
- [ ] Engagement metrics API (responses, clicks if applicable)
- [ ] Scheduled content/posts CRUD
- [ ] Telegram channel post publishing
- [ ] Report generation endpoint (PDF/CSV export)
- [ ] Best-time-to-post analysis (basic)

**Frontend Tasks:**
- [ ] Analytics dashboard with charts (Chart.js or Recharts)
- [ ] Date-range filter for analytics
- [ ] Content calendar view (schedule posts)
- [ ] Post creation form (text, image, schedule)
- [ ] Export reports button (PDF download)
- [ ] Real-time status indicators via WebSocket

**Sprint Review:** View analytics charts, schedule a Telegram channel post, see it publish.

---

### Sprint 5 — Client Data Manager, Auth & Security (Weeks 9–10)
**Goal:** Full user management, role-based access, and data security.

**Backend Tasks:**
- [ ] Role-based access control (RBAC) — admin, manager, agent
- [ ] JWT authentication with refresh tokens
- [ ] Client data CRUD with encryption
- [ ] CSV export/import with data validation
- [ ] Audit logging (who did what, when)
- [ ] GDPR compliance — data deletion & anonymization endpoints
- [ ] Rate limiting & API security hardening

**Frontend Tasks:**
- [ ] User management page (invite, roles, permissions)
- [ ] Profile/settings page
- [ ] Client data table with inline edit
- [ ] Data import wizard (multi-step CSV import)
- [ ] Audit log viewer
- [ ] Permission-based UI (hide/show features by role)

**Sprint Review:** Admin creates a manager account → manager imports client data → agent can only view, not delete.

---

### Sprint 6 — Polish, Testing & Deployment (Weeks 11–12)
**Goal:** Production-ready system with thorough testing and deployment.

**Tasks (All Team):**
- [ ] End-to-end testing of all features
- [ ] Unit test coverage (backend ≥ 80%, frontend ≥ 60%)
- [ ] Performance testing (load test with 100+ concurrent users)
- [ ] Security audit (dependency scanning, OWASP top 10 checks)
- [ ] Bug fixing & edge case handling
- [ ] Documentation finalization
- [ ] Production environment provisioning (Linux VPS)
- [ ] CI/CD pipeline setup (GitHub Actions)
- [ ] Docker Compose production configuration
- [ ] SSL certificate setup (Let's Encrypt)
- [ ] Deployment dry-run on staging
- [ ] Production deployment
- [ ] Post-deployment monitoring setup

**Sprint Review:** Fully deployed system. All tests pass. Documentation complete.

---

## 3. Team Responsibility Matrix

| Feature Area | Backend 1 | Backend 2 | Frontend 1 | Frontend 2 | Lead |
|-------------|-----------|-----------|------------|------------|------|
| Telegram Bot | Primary | Support | — | — | Review |
| Reminder Engine | Primary | Support | — | — | Review |
| AI Auto-Responder | Support | Primary | — | — | Review |
| REST API | Primary | Primary | — | — | Review |
| Dashboard UI | — | — | Primary | Support | Review |
| Analytics Charts | — | — | Support | Primary | Review |
| Content Calendar | — | — | Primary | Support | Review |
| Auth & Security | Support | Primary | — | — | Review |
| Client Data Manager | — | — | Support | Primary | Review |
| CI/CD & Deployment | Primary | Support | — | — | Lead |
| Testing | Primary | Primary | Primary | Primary | Review |
| Documentation | Support | Support | Support | Support | Lead |

---

## 4. Task Management Standards

Per WDG-PM-STD-001 Section 08:

| Rule | How We Apply |
|------|-------------|
| Every task must have an owner | Assigned in GitHub Projects |
| Every task must have a deadline | Linked to sprint milestone |
| Every task must have a priority level | P0 (blocker), P1 (critical), P2 (important), P3 (nice-to-have) |
| Tasks > 3 days → broken into subtasks | All sprint tasks broken down in planning |
| Regular progress updates | Daily standup (async via Telegram group or sync 10-min call) |

### Subtask Format Example

```
Task: Implement CSV import for reminders
  Subtask 1: Create CSV upload endpoint [Backend 1]
  Subtask 2: Write CSV parsing & validation logic [Backend 1]
  Subtask 3: Create import preview modal [Frontend 1]
  Subtask 4: Build confirmation & error display UI [Frontend 1]
  Subtask 5: Write unit tests for CSV parser [Backend 1]
```

---

## 5. Git Workflow

Per section 09 of PM standards:

```
main ── Protected (no direct commits)
  ├── feature/reminder-engine
  ├── feature/dashboard-ui
  ├── feature/ai-responder
  ├── bugfix/csv-timezone
  └── release/v1.0.0
```

**Rules:**
1. Create feature branch from `main`
2. Open Pull Request when ready
3. At least 1 reviewer must approve
4. All CI checks must pass
5. Squash-merge to `main`
6. Delete branch after merge

**Branch naming:**
- `feature/<short-description>` — new features
- `bugfix/<short-description>` — bug fixes
- `release/<version>` — release branches
- `docs/<short-description>` — documentation

---

## 6. Quality Assurance

Per section 10 of PM standards, before any deployment:

- [ ] Code review completed (at least 1 peer)
- [ ] All automated tests pass
- [ ] Security vulnerabilities resolved (npm audit, pip-audit)
- [ ] Documentation updated
- [ ] Critical bugs fixed (P0/P1)
- [ ] UI matches approved wireframes

### Testing Strategy

| Type | Tool | Target |
|------|------|--------|
| Unit tests | pytest (backend) / Vitest (frontend) | All core logic |
| Integration tests | pytest + httpx | API endpoints |
| E2E tests | Playwright | Critical user flows |
| Performance | Locust | Reminder scheduling, concurrent users |
| Security | Bandit / npm audit | Dependency & code scan |

---

## 7. Key Performance Indicators (KPIs)

Per section 13:

| KPI | Target | How Measured |
|-----|--------|-------------|
| On-time delivery rate | ≥ 85% | Sprint completion vs. plan |
| Sprint completion rate | ≥ 80% of committed points | GitHub velocity tracking |
| Bug resolution rate | P0/P1 within 24 hours | Issue tracking |
| System uptime | ≥ 99.5% | Monitoring (Uptime Robot) |
| Team productivity | Consistent velocity ± 15% | Sprint burndown charts |
| Test coverage | Backend ≥ 80%, Frontend ≥ 60% | Coverage reports |

---

## 8. Risk Register

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Telegram API changes/rate limits | Medium | High | Monitor API changelog, implement retry logic |
| Team member unavailability | Medium | Medium | Cross-train, document knowledge |
| Scope creep (feature requests mid-sprint) | High | Medium | Strict backlog prioritization, "next sprint" bucket |
| Deployment environment issues | Low | High | Dockerize everything, staging mirror of production |
| AI API costs (OpenAI) | Medium | Medium | Use keyword mode as fallback, cap API spending |
| CSV data quality issues | Medium | Medium | Strict validation with clear error messages |

---

## 9. Communication Plan

Per section 12:

| Event | Frequency | Channel | Duration |
|-------|-----------|---------|----------|
| Daily standup | Every workday | Telegram group or 10-min call | 10 min |
| Sprint planning | Start of sprint | Discord/Google Meet | 1 hour |
| Sprint review | End of sprint | Discord/Google Meet | 30 min |
| Sprint retrospective | After review | Discord/Google Meet | 30 min |
| Weekly check-in | Every Friday | Telegram group | Async |

---

## 10. Documentation Requirements

Per section 15, the following docs will be maintained:

| Document | Owner | Status |
|----------|-------|--------|
| README.md | Lead | ✅ Created |
| BUILDPLAN.md | Lead | ✅ Created |
| Architecture Diagram | Backend 1 | 🔜 Sprint 0 |
| API Documentation | Backend 1 & 2 | 🔜 Sprint 1+ |
| Installation Guide | Backend 1 | 🔜 Sprint 0 |
| Deployment Guide | Backend 2 | 🔜 Sprint 6 |
| User Manual | Frontend 1 & 2 | 🔜 Sprint 6 |

---

## 11. Change Management Process

Any change affecting scope, timeline, or architecture:

1. **Submit** — Team member documents the change request
2. **Review** — Lead evaluates impact on timeline/scope
3. **Decide** — Accept (adds to backlog), Defer (next sprint), Reject
4. **Communicate** — Decision shared with entire team
5. **Update** — BUILDPLAN and backlog updated accordingly

---

## 12. Project Completion Criteria

Per section 14, this project is complete when:

- [ ] All 6 sprints delivered and reviewed
- [ ] All tests pass (unit, integration, E2E)
- [ ] Production deployment live and verified
- [ ] All documentation finalized
- [ ] Stakeholder approval received
- [ ] Project closure report approved
- [ ] Lessons learned documented

---

## 13. Phase 2 Roadmap (Post-MVP)

Once the Telegram-based MVP is stable and deployed:

1. **WhatsApp Business API** — Meta business verification, API integration
2. **Instagram Scheduler** — Content posting, hashtag analytics
3. **Facebook Messenger** — Cross-platform unified inbox
4. **Native Mobile App** — React Native for iOS & Android
5. **CRM Integrations** — HubSpot, Salesforce sync
6. **White-Label** — Multi-tenant agency mode with custom branding
7. **Advanced AI** — Custom-trained models, sentiment analysis

---

> **Built by Web Developers Student Group**  
> Standards: WDG-PM-STD-001 v1.0  
> Last updated: June 2026