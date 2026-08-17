# SNAP Transcript RAG — Self-Learning Claims Tool

A bilingual (English/Spanish) RAG-enhanced system for SNAP Insurance adjusters to **translate**, **summarize**, and **learn from** claim transcripts.

Built with Claude API + RAG + Knowledge Base management.

---

## What It Does

1. **Translator** (`snap-transcript-rag.html`)
   - Paste a call transcript (English or Spanish)
   - Get clean English translation
   - Generate two summary formats:
     - **MT Entry** — Ultra-compact for MODOTECH (1-3 sentences, ALL CAPS)
     - **Claims Summary** — Professional narrative for adjuster review

2. **KB Manager** (`snap-kb-manager.html`)
   - Add new SNAP abbreviations, incident patterns, FNOL examples
   - Download your KB as JSON for backup/Git
   - Import updated KBs to restore or merge changes
   - Track version history

3. **Knowledge Base** (`snap-knowledge-base.json`)
   - 15 core abbreviations (IV, CV, R/E, CLMT, etc.)
   - 8 incident type patterns (rear-end, parking lot, border, etc.)
   - 10+ FNOL examples (raw → compact transformation)
   - Manu's communication voice + SNAP professional tone
   - Integrations: MODOTECH, CLADIS, Lucy bot

---

## Quick Start

### Live (Recommended)

Go to:
- **Translator:** https://snap-transcript-rag-xxx.netlify.app/snap-transcript-rag.html
- **KB Manager:** https://snap-transcript-rag-xxx.netlify.app/snap-kb-manager.html

(Replace `xxx` with your Netlify site name)

### Local

```bash
git clone https://github.com/YOUR_USERNAME/snap-transcript-rag.git
cd snap-transcript-rag
open snap-transcript-rag.html
```

---

## How to Self-Learn (Add New Patterns)

### Weekly Workflow

1. **Monday–Friday:** Adjusters use Translator for daily claims

2. **You spot a new pattern:**
   - E.g., motorcycle collisions, border checkpoints, rental vehicles

3. **Open KB Manager:**
   - Click **Incident Patterns** tab
   - Add the type, FNOL pattern, characteristics
   - Add 2–3 FNOL examples showing raw → compact

4. **Commit to GitHub:**
   ```bash
   git add snap-knowledge-base.json
   git commit -m "Add: motorcycle collision pattern"
   git push origin main
   ```

5. **Next similar claim:**
   - RAG automatically retrieves your new pattern
   - Translator + Summarizer use updated context
   - No code changes needed

### Result: Living Documentation

Your KB becomes a **living record** of every claim type SNAP processes. Team can see full history in Git commits, review changes via pull requests, and roll back if needed.

---

## File Structure

```
snap-transcript-rag/
├── netlify/functions/claude-api.js    ← Serverless API proxy
├── snap-transcript-rag.html            ← Translator tool
├── snap-kb-manager.html                ← KB Manager tool
├── snap-knowledge-base.json            ← Your KB (Git-tracked)
├── netlify.toml                        ← Netlify config
├── README.md                           ← This file
└── .gitignore                          ← Git best practices
```

---

## Setup: GitHub + Netlify (One-Time)

### GitHub

1. Create repo: `https://github.com/YOUR_USERNAME/snap-transcript-rag`
2. Push these files to main branch

### Netlify

1. Go to **https://netlify.com**
2. Sign up with GitHub
3. Click **"Add new site"** → **"Import an existing project"**
4. Select `snap-transcript-rag` repo
5. Click **"Deploy"**
6. Wait ~1 min for deploy to finish
7. Your site URL: `https://snap-transcript-rag-xxx.netlify.app`

### Environment Variable

1. Go to Netlify dashboard → your site → **Site settings**
2. Click **"Build & deploy"** → **"Environment"**
3. Click **"Edit variables"**
4. Add:
   ```
   Key: ANTHROPIC_API_KEY
   Value: sk-ant-YOUR_ACTUAL_KEY
   ```
5. Save

(Get your API key from **https://console.anthropic.com/api-keys** — free tier available)

---

## SNAP Terminology (Quick Reference)

| Abbr | Full | Usage |
|------|------|-------|
| IV | Insured Vehicle | SNAP's client's car |
| CV | Claimant Vehicle | The other party's car |
| R/E | Rear Ended | Hit from behind |
| CLMT | Claimant | Other party making claim |
| INSD | Insured | SNAP's policyholder |
| PSGR | Passenger | Non-driver in vehicle |
| PKG LOT | Parking Lot | Loss at parking area |
| APTS | Apartments | Loss at residential complex |
| UNINS | Uninsured | Other party has no insurance |
| SUBR | Subrogation | Pursue other at-fault party |

---

## Integrations

### MODOTECH
MT Entry format (ultra-compact, 1–3 sentences, ALL CAPS) feeds directly into SNAP's claims system for fast intake.

### Lucy Bot (FNOL Voice)
Future: This RAG system can improve Lucy's prompt generation for call transcription + auto-FNOL.

### CLADIS
Design system: Navy deep (#051c2b), Arsenal serif titles, Inter body text. All tools match the unified SNAP design language.

---

## Troubleshooting

### KB Not Loading?
- Check browser console (F12 → Console)
- Verify `snap-knowledge-base.json` is in repo root
- Netlify may need ~1 min to deploy changes

### Translator Returns Error?
- Verify ANTHROPIC_API_KEY is set in Netlify
- Check browser console for error details
- Ensure transcript is not empty

### Changes Not Showing?
- Hard refresh browser (Cmd+Shift+R or Ctrl+Shift+R)
- Clear browser cache
- Check that JSON is valid

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-08-12 | Initial release: Translator, KB Manager, 15 abbreviations, 8 incident patterns, 10 FNOL examples |

---

**Built with ❤️ for SNAP adjusters by Manu**
