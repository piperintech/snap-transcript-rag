# Terminal Commands — Copy & Paste

## Initial Setup

```bash
git clone https://github.com/YOUR_USERNAME/snap-transcript-rag.git
cd snap-transcript-rag
```

## First Push

```bash
git add .
git commit -m "Initial: SNAP Transcript RAG tool"
git push origin main
```

## Add New Patterns (Recurring)

```bash
git add snap-knowledge-base.json
git commit -m "Add: [describe pattern]"
git push origin main
```

## Check Status

```bash
git status
```

## See Commit History

```bash
git log --oneline
```

## See Changes Before Committing

```bash
git diff snap-knowledge-base.json
```

## Undo Last Commit (if needed)

```bash
git reset --soft HEAD~1
```

## Other Useful Commands

```bash
# See what's on GitHub (fetch without changing local)
git fetch

# Check which branch you're on
git branch

# See all recent commits
git log
```

---

**That's all you need for day-to-day use.**
