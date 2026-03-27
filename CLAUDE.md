# Alveos

Acoustic wearable startup building Alveos One — a magnet-attached device that continuously monitors breathing to derive novel biomarkers (respiratory rate variability, mouth-vs-nose ratio, Nervous System Index). Category: State Regulation Wearable. Finnish company, pre-seed stage closing €2M Seed (April 2026).

## Team

- **Patrick** — CEO & co-founder. Also CCO at Nosto (80-person team). Primary decision-maker.
- **Lisa Haxel** (PhDc) — Science & Data Lead (Tübingen AI Center/Hertie Institute)
- **Vasilii Zhuravskii** (PhD) — Hardware Lead (18+ yrs embedded/medical/aerospace)
- **Jani Nummela** — Design & Development (20+ yrs UX; Netflix, Polar, Suunto, Nokia)
- **Oliver Obolgogiani** — Growth & Operations
- **Antonia Schroff** — Signal Processing intern (ex-Wolt/DoorDash)
- **Teemu Havisalo** — Operations Lead (ex-Suunto)
- **Mark Zahar** — Firmware Engineer (ex-Playtronica)
- **Rajasimha N.** — Backend Engineer (ex-IQM Quantum Computers)

## Product

- Patented mechano-acoustic sensor fusion
- 99.8% respiratory rate accuracy, 96.6% oral/nasal detection
- €399 device + €9.99/month subscription
- Biomarkers: respiratory rate, RRV, mouth/nose ratio, Nervous System Index, sleep breathing patterns
- Kickstarter: 300+ orders, 200%+ funded, AOV €253
- Clinical validation partner: University of Kent (Prof. John Dickinson)

## Regulatory

- Current positioning: wellness device (not SaMD/Class II MDR)
- Gray zone strategy: respiratory wellness monitor, not diagnostic
- GDPR compliance required for all user health data
- CE marking in progress
- Never make diagnostic or treatment claims in any copy or code

## Architecture Overview

- **Firmware**: C/C++ on embedded (Mark owns this)
- **Backend**: Python-based, maintained by Rajasimha
- **Mobile app**: consumer-facing, breathing insights and biomarker dashboard
- **Data pipeline**: biomarker ingestion from device → cloud → app
- **Infrastructure**: cloud-hosted AWS

## Code Standards

- Use type hints on all Python functions
- TypeScript strict mode for any JS/TS code, no `any` types
- All health data handling must assume GDPR sensitivity — never log PII or raw health data in plaintext
- Prefer named exports over default exports
- Write tests for any data transformation or biomarker calculation logic
- Commit messages: conventional commits format (`feat:`, `fix:`, `chore:`, etc.)

## Common Commands

Check the project's `package.json` or `Makefile` before assuming commands. When in doubt, read the file first.

## Key Directories

Each alveos repo may have its own structure. At the start of a session, run `find . -maxdepth 2 -type f -name "*.md" | head -20` to orient yourself. Look for a local `README.md` or nested `CLAUDE.md` for repo-specific context.

## Working Patterns

- **Plan before coding.** For anything non-trivial, outline the approach first and confirm before implementing.
- **Health data is sacred.** Any code touching user breathing data, biomarkers, or personal info must be reviewed with extra care. Default to encryption at rest and in transit.
- **Small PRs.** Keep changes focused. One feature or fix per branch.
- **Test biomarker logic rigorously.** Edge cases in respiratory data (apnea events, mouth-breathing during exercise, sensor disconnects) matter more than in typical apps.
- **Don't over-engineer.** We're a 9-person startup closing a Seed round. Ship fast, iterate, keep it simple.

## Domain Knowledge

- "RRV" = Respiratory Rate Variability (our novel biomarker, analogous to HRV)
- "NSI" = Nervous System Index (composite autonomic marker)
- "SRW" = State Regulation Wearable (our category)
- "Oral/nasal ratio" = proportion of mouth vs nose breathing
- Breathing is positioned as the "fourth pillar of health" (alongside sleep, exercise, nutrition)
- Key competitors: Oura, Ultrahuman, Whoop — none do continuous respiratory monitoring

## External Tools & Integrations

- **Notion**: primary workspace (investor pipeline, OKRs, team wiki, Kickstarter tracker)
- **Google Workspace**: email, calendar, docs
- **Netvisor / Revolut**: financial data (consolidation is a known pain point)

## What NOT To Do

- Never hardcode API keys or secrets — use environment variables or a secrets manager
- Never store raw audio from the wearable without explicit user consent handling
- Never make medical claims in user-facing strings ("diagnoses," "treats," "cures")
- Never commit `.env` files
- Don't add dependencies without checking if an existing one already covers the need

## When Compacting

Always preserve: the current task scope, list of modified files, any test commands used, and the regulatory/GDPR constraints above.
