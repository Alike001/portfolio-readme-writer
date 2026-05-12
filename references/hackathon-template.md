# Hackathon Submission README Template

For hackathon entries. Audience: judges with limited time, scoring against a rubric. Often someone scrolling through 200+ submissions.

The single most important fact: **judges decide in the first 30 seconds whether to keep reading or move on**. The top of the README must hook them, prove the project is real, and make the scoring criteria easy to find.

## Section order (top to bottom)

1. **Title** — `# project-name`
2. **One-line pitch** — bold. Punchier than personal mode. Lead with the user benefit or the wow factor. Under 20 words.
3. **Demo video link** — prominent. Format: `**[▶ Watch the 2-minute demo](https://...)**` (replace ▶ with `▶` text — no emoji per skill rules; use a markdown link with clear text). The link goes immediately under the pitch. If no demo video link was provided, write `**Demo video: [TODO — record before submitting]**` so the user sees what's missing.
4. **(If hero asset exists) Demo image** — `![demo](path)` to show what the thing looks like.
5. **Hackathon badge line** — `*Built for [Hackathon Name] [Year] — [Track(s)] track. Sponsors targeted: [list].*` (italic, single line). This is what tells judges immediately whether this is in their pile.
6. **`---` separator**
7. **The problem** — H2. One paragraph. Concrete. Who has this pain, why it matters, why now. Don't be abstract.
8. **The solution** — H2. **Two to three sentences. Hard cap.** What you built, what it does, how it solves the problem. Judges skim — every extra sentence is a chance for them to stop reading. If you find yourself writing a fourth sentence, the extra detail belongs in "How it works" or "Sponsor / track alignment", not here.
9. **Quick start** — H2 + fenced code block. Same shape as personal mode — clone, install, run.
10. **`Then open [localhost:PORT]`** + prerequisite line if needed.
11. **Stack** — H2 + markdown table. Two columns: `Layer | Technology`. Highlight any sponsor SDKs/APIs you used (these win prizes).
12. **How it works** — H2. Architecture diagram (ASCII) + 2-3 sentences explaining the flow. For hackathon judges this is critical — they want to see the technical depth.
13. **Sponsor / track alignment** — H2. Bullet list. For each sponsor or track, one sentence explaining how the project fits. Be specific: "Used [Sponsor X SDK] for Y, which qualifies us for the Z prize."
14. **Future roadmap** — H2. 3-5 bullets. What you'd build next if this won / got funded. Judges score on "would this survive the hackathon".
15. **Team** — H2. Bulleted list: `- **Name** — Role — [GitHub](url) · [Twitter](url) · [LinkedIn](url)`. Roles like "Frontend & Smart Contracts" not "Developer".
16. **(Optional) Acknowledgements** — H2. One line crediting any open-source projects, mentors, or sponsors that helped.

## What NOT to include

- "What I learned" section
- Personal "thank you for reading" closers
- Long technical deep-dives (link to a separate ARCHITECTURE.md if needed)
- Apologies for incomplete features ("we ran out of time to..." — keep this offline)
- A roadmap longer than 5 bullets

## Voice notes for hackathon mode

Punchier than personal. Lead with impact. It's OK to use phrases like:
- "In 2 minutes you can..."
- "Built end-to-end during [Hackathon Name]"
- "First [thing] that [unique angle]"

But still avoid empty hype: skip "revolutionary", "cutting-edge", "leverages the power of", "AI-powered" (unless AI is genuinely central).

## Worked example

```markdown
# greetchain

**A smart contract you can talk to — change a greeting on-chain in one click. Built end-to-end at ETHGlobal NYC 2025.**

**[▶ Watch the 90-second demo](https://youtube.com/watch?v=...)**

![demo](docs/demo.gif)

*Built for ETHGlobal NYC 2025 — Beginner Track. Sponsors targeted: Hardhat, Alchemy.*

---

## The problem

Most onboarding tutorials for Ethereum dApps stop at "deploy a contract." New devs never see the *full* loop — UI calls contract, contract emits event, UI updates from chain state. Without that mental model, they freeze the moment they have to wire a real frontend to a real chain.

## The solution

A minimal but complete dApp: a Solidity contract that stores a string, a React frontend that reads and writes it via viem, and one Docker command that boots the whole stack — chain, deploy step, and frontend. Devs see the full loop in 60 seconds.

## Quick start

```bash
git clone https://github.com/USER/greetchain.git
cd greetchain
docker compose up --build
```

Then open [localhost:8080](http://localhost:8080).

You need [Docker](https://docs.docker.com/get-docker/) installed.

## Stack

| Layer | Technology |
| ----- | ---------- |
| Smart contract | Solidity 0.8.28 |
| Contract framework | **Hardhat 3** (Ignition, viem, ESM) |
| Local blockchain | **Hardhat Node** |
| Frontend | React 19 + Vite + TypeScript |
| Web3 client | viem |
| Orchestration | Docker Compose (3-service: chain + deploy + frontend) |

## How it works

(architecture diagram)

Three Docker services with proper sequencing — the deploy step waits for the chain to be healthy, the frontend waits for deploy to complete, so the UI never loads before the contract exists.

## Sponsor / track alignment

- **Hardhat** — Built on Hardhat 3 (latest), uses Ignition for declarative deploys and the viem-based runtime. Demonstrates the v2 → v3 migration path other devs will need.
- **Beginner Track** — Designed specifically as a teaching artifact. The README walks a total beginner from `git clone` to a working dApp in one command.

## Future roadmap

- Add wallet connection (MetaMask) so users sign their own transactions
- Multi-chain deploy with Sepolia + Base testnets
- On-chain event log streamed to the UI in real time
- Public hosted version on Vercel + Sepolia for permanent demo
- Tutorial blog post mapping each line of the contract → frontend → compose flow

## Team

- **Hammed Ali Oyeleye** — Smart contracts + frontend — [GitHub](https://github.com/Alike001) · [Telegram](https://t.me/IamAlikeX)
```

Use this for *shape*, not copy-paste. Real content reflects the real project.
