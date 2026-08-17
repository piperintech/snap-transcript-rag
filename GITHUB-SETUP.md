# GitHub + Netlify Setup Guide

## One-Time Setup

### 1. Create GitHub Repo

```bash
# Create a new repo on github.com called: snap-transcript-rag
# Then clone it:
git clone https://github.com/YOUR_USERNAME/snap-transcript-rag.git
cd snap-transcript-rag
```

### 2. Add All Files

Copy all the files from this zip into your repo folder:
```
netlify/functions/claude-api.js
snap-transcript-rag.html
snap-kb-manager.html
snap-knowledge-base.json
netlify.toml
README.md
.gitignore
GITHUB-SETUP.md
GITHUB-COMMANDS.md
INAZA-INTRO.md
```

### 3. First Commit

```bash
git add .
git commit -m "Initial commit: SNAP Transcript RAG tool"
git push origin main
```

### 4. Deploy to Netlify

1. Go to **https://netlify.com**
2. Click **"Add new site"** → **"Import an existing project"**
3. Select **GitHub** → find `snap-transcript-rag`
4. Click **"Deploy site"**
5. Wait ~1-2 minutes

Your site is now live at: `https://snap-transcript-rag-xxx.netlify.app`

### 5. Set Environment Variable

1. Netlify dashboard → your site → **Site settings**
2. **Build & deploy** → **Environment**
3. **Edit variables** → **Add**
4. ```
   Key: ANTHROPIC_API_KEY
   Value: sk-ant-YOUR_KEY
   ```
5. Save (Netlify auto-redeploys in ~1 min)

Get your API key from: **https://console.anthropic.com/api-keys** (free tier available)

---

## Day-to-Day: Add New Patterns

### Workflow

1. Adjusters use Translator for daily claims
2. You spot a new pattern → Open KB Manager
3. Add new abbreviations/patterns/FNOL examples
4. Download the JSON
5. Commit to Git:
   ```bash
   git add snap-knowledge-base.json
   git commit -m "Add: border crossing pattern"
   git push origin main
   ```

**Next claim:** RAG automatically uses new patterns. No code changes needed.

---

## Testing

1. Go to: `https://snap-transcript-rag-xxx.netlify.app/snap-transcript-rag.html`
2. Paste a Spanish transcript
3. Click **"Process"**
4. See Translation appear
5. Click **"MT Entry"** tab → **"Generate"** → ultra-compact format
6. Click **"Claims Summary"** tab → **"Generate"** → professional narrative

---

## Troubleshooting

### Netlify Can't See My Repo

GitHub → Settings → Applications → Installed GitHub Apps → Find Netlify → Edit → Select `snap-transcript-rag`

### API Key Not Working

Make sure you:
1. Set `ANTHROPIC_API_KEY` in Netlify environment variables
2. Used a real key from **https://console.anthropic.com/api-keys**
3. Netlify redeploy finished (wait ~1 min after setting env var)

### Changes Not Showing

Hard refresh: **Cmd+Shift+R** (Mac) or **Ctrl+Shift+R** (Windows/Linux)

---

That's it! Your tool is live and self-learning.
