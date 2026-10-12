# SNAP Transcript RAG — Bilingual Claims Translator

**Paste a Spanish or English claim call transcript and get a clean English translation plus two ready-to-use summaries, grounded in a knowledge base of SNAP's own claims vocabulary that the team keeps growing.**

Built for SNAP Insurance Service LLC (bilingual non-standard auto MGA, Texas & New Mexico)

---

## The problem

A large share of SNAP's claim calls are in Spanish. Adjusters were translating and summarizing by hand, using inconsistent abbreviations, and generic AI translation didn't know insurance shorthand (IV, CV, R/E, CLMT) or how SNAP writes notes.

## What it does

**1. Translator** (`snap-transcript-rag.html`)
- Paste a transcript in English or Spanish → clean English translation
- Two output formats:
  - **MT Entry:** ultra-compact, 1–3 sentences, ALL CAPS, for pasting into Modotech (the claims system)
  - **Claims Summary:** a professional narrative for adjuster review
- Shows which knowledge-base entries were retrieved for that claim type

**2. Knowledge Base Manager** (`snap-kb-manager.html`)
- Add new abbreviations, incident patterns and FNOL examples without touching code
- Import/export the KB as JSON, with version history

**3. Knowledge base** (`snap-knowledge-base.json`)
- Core claims abbreviations, incident-type patterns (rear-end, parking lot, border crossing…), raw → compact FNOL examples, and SNAP's voice and tone

## How the RAG works

```
transcript ──► detect incident type ──► retrieve matching patterns,
                                         abbreviations & examples from KB
                                                   │
                                                   ▼
                               Claude API (via Netlify function) ──► translation
                                                                  ├─► MT Entry
                                                                  └─► Claims Summary
```

When the team sees a new kind of claim, they add it in the KB Manager and commit the JSON. The next similar transcript automatically gets the new context. No code changes needed.

## Stack

HTML/CSS/JavaScript · Claude API · Netlify serverless function (keeps the API key off the client) · JSON knowledge base tracked in Git

## Run it yourself

1. Fork this repo and import it into **Netlify** ("Add new site" → "Import an existing project").
2. In Netlify → Site settings → Environment variables, add `ANTHROPIC_API_KEY` with your key.
3. Open `/snap-transcript-rag.html` on your Netlify URL.

```
├── netlify/functions/claude-api.js   serverless API proxy
├── snap-transcript-rag.html          translator
├── snap-kb-manager.html              KB manager
├── snap-knowledge-base.json          knowledge base
└── netlify.toml
```

## Quick reference

| Abbr | Meaning |
|---|---|
| IV / CV | Insured vehicle / Claimant vehicle |
| R/E | Rear-ended |
| CLMT / INSD | Claimant / Insured |
| PSGR | Passenger |
| UNINS | Uninsured |
| SUBR | Subrogation |

> No real transcripts are stored in this repo.

---

Built by **Manuela Gonzalez Piper** · Product & AI · [GitHub](https://github.com/piperintech) · Earlier version: [snap-transcript](https://github.com/piperintech/snap-transcript)
