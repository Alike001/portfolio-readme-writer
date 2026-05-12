# Voice & Formatting Rules

These rules apply across both modes. Mode-specific tone notes are in each template.

## Voice — what to do

- **Plain language.** Write like you're explaining the project to a smart person who isn't in your domain. "Stores the value on-chain" beats "persists state to the immutable ledger".
- **Show, don't tell.** A code block proves a quick start works. The phrase "easy to install" doesn't.
- **Lead with the user benefit.** "One command brings up the whole stack" → user can immediately picture the value. "Built with Docker Compose" → just a tech fact.
- **Be specific.** Numbers, names, versions. "React 19 + Vite" beats "modern frontend stack". "2-minute demo" beats "short demo".
- **Cut every word that doesn't pay rent.** Read each sentence and ask: does this earn its space?

## Voice — what to avoid

Banned words and phrases (these scream "AI wrote this" or "marketing wrote this"):
- "revolutionary", "cutting-edge", "next-generation", "state-of-the-art"
- "leverages", "leveraging", "harnesses the power of"
- "seamlessly", "seamless integration"
- "robust", "scalable" (unless you actually demonstrate why)
- "AI-powered" (unless AI is genuinely the centerpiece)
- "blazingly fast" (a Rust meme — overused everywhere now)
- "in today's fast-paced world", "in an era of"
- "delve into", "embark on a journey", "unleash"
- Any sentence that starts with "Imagine if..."

## Formatting rules

### Headers
- Use `#` for the project title only (one per file)
- Use `##` for major sections
- Use `###` sparingly, only inside long sections
- Never use `####` or deeper — if you need that depth, the section should be its own page

### Code blocks
- Always specify the language: ` ```bash`, ` ```js`, ` ```solidity`, etc.
- Quick-start blocks have NO commentary inside the block — keep them copy-pasteable
- Multi-step workflows use one block per step with a `# Terminal 1 — purpose` comment line at the top

### Links
- Inline links over reference-style: `[text](url)` not `[text][1]`
- Demo links use clear descriptive text — `[Watch the 2-minute demo](url)` not `[click here](url)` or just the bare URL
- For prerequisites, link to the canonical install page: `[Docker](https://docs.docker.com/get-docker/)`

### Tables
- Use for stack lists, comparisons, anything with parallel structure
- Two columns is ideal (`Layer | Technology`); three columns is the max
- Align columns with proper markdown padding so the raw markdown is also readable

### Emojis
- **None.** Not in headers, not in body. The user explicitly chose this.
- Exception: for hackathon mode, the demo video link can be styled with text indicators like `[Watch the demo →]` (using `→`, an arrow, not an emoji).

### Diagrams
- ASCII only — no Mermaid, no embedded images of diagrams
- Use box-drawing characters: `┌─┐`, `│`, `└─┘`, arrows `─►` or `▶`
- Wrap diagrams in a fenced code block (no language specified)
- Keep them small — if it doesn't fit on one screen, it's too complex for a README
- Diagrams must show **systems and boundaries**, not function call sequences. If your "diagram" is a vertical column of function names connected by arrows, delete it — the prose already says that. A real diagram earns its space by showing something spatial that words can't (frontend talks to API talks to DB; service A waits for service B; data crosses a network boundary)

### Jargon
Domain-specific words land differently for different audiences. The same word that signals expertise to one reader confuses another. Rule of thumb:
- **Inside the niche** (web3 README for a web3 hackathon): use jargon freely — "soulbound", "EIP-712", "ERC-4626", "subgraph". Audience knows it.
- **Crossing audiences** (recruiter who codes but isn't a domain expert; general-track judge at a multi-track hackathon): use the term, then briefly explain it in parens the first time. Example: `quadratic-funding-style matching pools (matched contributions are weighted by the number of unique donors, not just total ETH)`
- **Skip entirely**: don't use jargon as decoration. If a plain-language word works as well, prefer it.

### Lists
- Bullets for unordered things (features, team members)
- Numbered lists only when order matters (setup steps, request flow)
- Keep bullets to one line each where possible

## Length budget

- **Total README**: 80-200 lines is the sweet spot. Longer is fine if there's substance, but trim ruthlessly.
- **One-line pitch**: under 20 words
- **Each H2 section**: under 15 lines unless it's the architecture or stack
- **Quick start block**: 3-5 commands

## Final check before writing

Re-read the draft and ask:
1. Could a recruiter / judge skim this in 30 seconds and know what it is, what stack, and how to run it?
2. Is there a single banned phrase? Cut it.
3. Does every section earn its place? If not, remove the section.
4. Are the code blocks copy-pasteable without edits? They must be.
5. (Hackathon) Is the demo video link in the first 5 lines? If not, move it.
