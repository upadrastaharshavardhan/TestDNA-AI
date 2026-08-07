# Test Memory AI

**The AI Brain for Enterprise Test Automation.**

An AI-powered organizational memory for test automation: semantic search across
every indexed test, real duplicate detection, a live knowledge graph, impact
analysis, failure memory, and daily AI recommendations — all backed by a real
database and real algorithms, not mock data.

## What's real vs. what's an upgrade path

Everything in this codebase runs and computes real results from real data:

| Feature | How it works today | How to scale it later |
|---|---|---|
| Semantic search / duplicate detection | TF-IDF + cosine similarity (scikit-learn), zero external dependency | Swap `backend/app/services/embeddings.py`'s `Embedder` for Azure OpenAI / OpenAI embeddings + a vector DB (Qdrant) — one seam, no router changes |
| Repository scanning | Live GitHub REST API calls, real file parsing (regex-based) for Playwright/Cypress/Selenium/pytest | Add the same pattern for Azure DevOps / GitLab / Bitbucket in `backend/app/services/` (stubs for these providers are one file each) |
| Knowledge graph | Built live from your relational data with `networkx` | Swap for Neo4j by writing the same nodes/edges to Cypher instead of an in-memory graph |
| AI Chat | Retrieval-grounded: real search results, listed directly | Set `AZURE_OPENAI_ENDPOINT` + `AZURE_OPENAI_API_KEY` in `backend/.env` to have an LLM summarize the same retrieved context instead |
| Dashboard, recommendations, impact analysis, failure memory, business flows | All computed live from the SQL database — no hardcoded numbers | Point `DATABASE_URL` at Postgres for production scale |

The database ships seeded with a realistic multi-project dataset (4 projects,
10 repositories, ~275 tests, page objects, APIs, requirements, and execution
history) so every page has real numbers on first run — generated once through
the real ORM, not hand-authored JSON in the frontend.

## Quick start (Docker — recommended)

```bash
cp backend/.env.example backend/.env
docker compose up --build
```

- Frontend: http://localhost:3000
- Backend API + docs: http://localhost:8000/docs

## Quick start (local dev)

**Backend**
```bash
cd backend
python -m venv venv && source venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
python -m app.seed        # one-time: seeds realistic demo data
uvicorn app.main:app --reload --port 8000
```

**Frontend**
```bash
cd frontend
cp .env.local.example .env.local
npm install
npm run dev
```

Open http://localhost:3000.

## Architecture

```
backend/            FastAPI + SQLAlchemy
  app/
    main.py          app entrypoint, router registration, CORS
    models.py         Project, Repository, TestCase, PageObject, ApiEndpoint,
                       Requirement, Execution, Recommendation, ChatMessage
    seed.py            realistic demo-data generator
    routers/          one file per feature area (12 routers = 12 pages)
    services/
      embeddings.py    TF-IDF/cosine semantic search + duplicate detection
      github_scanner.py  real GitHub API repo scanning + test parsing
      graph_builder.py   networkx knowledge graph builder

frontend/            Next.js 14 (App Router) + TypeScript + Tailwind
  app/                one route per feature area, all fetching live data
  components/         Sidebar, TopBar, glass cards, stat cards, confidence rings
  lib/api.ts           typed API client
```

## Connecting real repositories

From the **Repository Scanner** page, add a repo with a GitHub `owner` and
`repo` name (e.g. `facebook` / `react`) and it will pull the actual file tree
via the GitHub API, download test-like files, and parse them for framework,
locators, assertions, and API calls. Set `GITHUB_TOKEN` in `backend/.env` for
private repos or to avoid unauthenticated rate limits.

Azure DevOps / GitLab / Bitbucket / Confluence / SharePoint connectors follow
the same shape — `backend/app/services/github_scanner.py` is the reference
implementation to copy for each additional provider's REST API.

## Fonts

The UI ships with a system-font fallback stack so it builds with zero network
access. For production, load the real Space Grotesk / Inter / IBM Plex Mono
trio via `next/font/google` in `app/layout.tsx` — one import, no other
changes needed.

## Security notes before production

- Set a strong `SECRET_KEY` and put real auth (JWT is already a dependency)
  in front of every router — none of the routers currently require a token.
- Restrict `allow_origins` in `backend/app/main.py`'s CORS config to your
  real frontend origin(s).
- Point `DATABASE_URL` at Postgres, not SQLite, for concurrent production
  traffic.
