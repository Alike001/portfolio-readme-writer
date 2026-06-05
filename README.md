# portfolio-readme-writer

An agent skill that writes a polished, ship-ready README for a finished project. Two modes — **personal** (portfolio piece, recruiter audience) and **hackathon** (submission, judge audience).

Different audiences, different shapes. The goal is a README that earns trust in 30 seconds.

## What it does

Claude reads your repo, asks for what it cannot infer (one-line pitch, hackathon track, etc.), and writes a `README.md` that follows a tight structure:

- **Personal mode** — title, pitch, quick start, stack table, how it works, caveats. Clean voice, no fluff.
- **Hackathon mode** — title, pitch, demo video link, problem, solution (2-3 sentences hard cap), quick start, stack, architecture, sponsor / track alignment, future roadmap, team.

It enforces voice rules:

- No emojis
- No "What I learned" section
- No banned hype words (`revolutionary`, `leverages`, `seamlessly`, `blazingly fast`, `delve into`, ...)
- ASCII architecture diagrams only when there is a real spatial story to show — never a vertical column of function names
- Jargon gets a parenthetical explanation when crossing audiences

If a `README.md` already exists, the skill shows a diff and asks before overwriting.

## Install

Install with the [`skills`](https://github.com/vercel-labs/skills) CLI — the open standard for agent skills:

```bash
npx skills add Alike001/portfolio-readme-writer
```

This works across 18+ coding agents — Claude Code, Cursor, Codex, GitHub Copilot, Cline, and more. To install it for a specific agent only:

```bash
npx skills add Alike001/portfolio-readme-writer -a claude-code
```

Restart your agent and the skill is active.

### Verify install

List your installed skills:

```bash
npx skills list
```

You should see `portfolio-readme-writer`. In Claude Code you can also run `/skills`.

### For development

To read or edit the source, clone the repo:

```bash
git clone https://github.com/Alike001/portfolio-readme-writer.git
```

## How to use

Just ask. The skill auto-triggers on phrases like:

- `write a README`
- `document this project`
- `prep this for my portfolio`
- `make this repo look good`
- `hackathon submission README`
- `add docs before I push to GitHub`

You can also force it explicitly:

```
Use portfolio-readme-writer to write the README for this project.
```

The skill will:

1. Ask whether this is a personal project or a hackathon submission (skipped if obvious from context).
2. Read your repo to infer the stack, structure, and existing assets.
3. Ask a single batched message for whatever it could not infer.
4. Write `README.md` at the repo root — diffing first if one already exists.

## Two modes at a glance

| Mode | Audience | Voice | Required inputs |
| ---- | -------- | ----- | --------------- |
| Personal | Recruiter, hiring manager, future collaborator | Clean, confident, specific | one-line pitch, quick-start commands |
| Hackathon | Judge scoring against a rubric | Punchier, leads with impact | hackathon name, track, problem, demo video link, team, roadmap |

## What this skill does NOT do

Scope discipline. The skill writes the README. That is the whole job.

- Does not push to GitHub
- Does not generate screenshots, GIFs, or videos
- Does not write `CONTRIBUTING.md`, `LICENSE`, `CHANGELOG.md`, or other docs
- Does not deploy the project
- Does not modify code

## How it is structured

```
portfolio-readme-writer/
├── SKILL.md                    # workflow Claude follows when triggered
└── references/
    ├── personal-template.md    # section order + worked example for personal mode
    ├── hackathon-template.md   # section order + worked example for hackathon mode
    └── style.md                # voice rules, banned words, formatting, jargon rule
```

The `references/` files are loaded on demand, so the skill stays cheap to invoke.

## Requirements

- Node.js (for `npx`) and a coding agent that supports the [Agent Skills](https://github.com/vercel-labs/skills) standard — Claude Code, Cursor, Codex, GitHub Copilot, and others
- A project that is actually finished — the skill is for documenting work, not planning it
