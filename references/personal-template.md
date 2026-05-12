# Personal Project README Template

For portfolio / side projects. Audience: recruiters, hiring managers, fellow devs evaluating "does this person write good code and ship things?".

## Section order (top to bottom)

1. **Title** — `# project-name` (use the actual repo name)
2. **One-line pitch** — bold, immediately under the title. Plain language. No marketing words. Under 20 words.
3. **(If deployed) Live demo link** — `**[Try it live](https://...)**` on its own line.
4. **(If hero asset exists) Demo image** — `![demo](path/to/screenshot.png)` if a good one is in the repo.
5. **Quick start** — fenced code block. Three commands max: clone, enter dir, run. No commentary inside the block.
6. **Open localhost line** — `Then open [localhost:PORT](http://localhost:PORT).`
7. **Prerequisites** — one short line, only if non-obvious (e.g., "You need [Docker](https://docs.docker.com/get-docker/) installed."). Skip for projects with no special deps.
8. **`---` separator**
9. **What this is** — H2 heading. 2-4 plain-language sentences. Explain the project as if to a smart non-domain person. Skip if title + pitch already cover it.
10. **Stack** — H2 heading + markdown table. Two columns: `Layer | Technology`. Order: top of the stack down (Frontend → Backend → DB → Infra).
11. **How it works** — H2 heading. One paragraph is the default. Add an ASCII diagram **only** if the project has a genuine spatial story — multiple services, a request flowing across system boundaries, or several long-lived components in different processes. Do **not** draw a diagram that just lists function calls in order — that duplicates the prose and reads as filler. If the project is one process with a few internal functions, the prose paragraph alone is the right answer. When you do diagram, show *systems* (frontend, API, database, contract) as boxes, with arrows labeled by what crosses the boundary (e.g. `HTTP POST /api/shorten`, `kv.set`, `redirect`).
12. **Project structure** — H2 heading + fenced code block of `tree`-style output (only top 2 levels, only meaningful files/dirs). Add inline `# comments` on the important pieces.
13. **(Optional) Running it differently** — H2. Alternative dev mode (e.g., "Without Docker", "Local development with hot reload"). Use when the primary quick-start uses Docker but local dev is also valuable.
14. **(Optional) A note on X** — H2. Caveats worth knowing — ephemeral state, known limitations, security notes. Keep to 2-3 sentences each.

## What NOT to include

- "What I learned" section
- Badges (build status, version, etc.) unless the user explicitly has CI set up and asks for them
- "Contributing" section (this is a personal project)
- Long roadmap / TODO lists
- Author bio (the GitHub profile already shows this)

## Worked example

```markdown
# todo-fullstack

A full-stack todo app — React frontend, Express + SQLite backend, dockerized end to end. **One command brings up the whole stack.**

```bash
git clone https://github.com/USER/todo-fullstack.git
cd todo-fullstack
docker compose up --build
```

Then open [localhost:8080](http://localhost:8080).

You need [Docker](https://docs.docker.com/get-docker/) installed.

---

## What this is

A working todo app where the frontend, backend, and database all run in their own containers. Todos persist across restarts via a Docker volume. Built to learn end-to-end containerization on a project with realistic moving parts.

## Stack

| Layer | Technology |
| ----- | ---------- |
| Frontend | React 19 + Vite + TypeScript |
| Backend | Express + better-sqlite3 |
| Database | SQLite (volume-persisted) |
| Orchestration | Docker Compose |

## How it works

Two services: a Node backend serving JSON on `:3000` and an nginx-served React build on `:8080`. The database file lives in a named Docker volume so it survives `docker compose down`.

## Project structure

```
todo-fullstack/
├── backend/
│   ├── server.js           # Express + SQLite API
│   ├── Dockerfile
│   └── data/               # mounted volume — todos.db lives here
├── frontend/
│   ├── src/                # React app
│   └── Dockerfile          # multi-stage: Node build → nginx serve
└── docker-compose.yml      # backend + frontend + named volume
```

## Running it without Docker

Two terminals:

```bash
# Terminal 1 — backend
cd backend && npm install && node server.js

# Terminal 2 — frontend
cd frontend && npm install && npm run dev
```
```

Use this as a model for *shape*, not a copy-paste. The actual content reflects the real project.
