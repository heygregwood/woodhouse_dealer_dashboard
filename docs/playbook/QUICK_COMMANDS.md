# Quick Commands

Dev environment quick reference for Woodhouse Dealer Dashboard (Allied Air V2).

---

## Environment

- **Machine:** Windows 11 + WSL2 Ubuntu
- **User:** heygregwood
- **Repo:** `~/woodhouse_dealer_dashboard`
- **Status:** Ready to deploy (not yet live)

---

## Bash Aliases

```bash
gp        # git pull
gs        # git status
ga        # git add .
gpush     # git push
```

---

## Git Commands

```bash
# Check status
gs

# Pull latest
gp

# Stage everything
ga

# Commit
git commit -m "message"

# Push
gpush

# Full workflow
ga && git commit -m "message" && gpush
```

---

## Common Tasks

```bash
# Navigate to repo
cd ~/woodhouse_dealer_dashboard

# View files
ls -la

# Edit index.html
code index.html   # VS Code
nano index.html   # Terminal editor

# Test locally (just open in browser)
# Open index.html in Chrome/Edge
```

---

## File Structure

```
~/woodhouse_dealer_dashboard/
├── index.html              # Main Allied Air dashboard
├── all/index.html          # Network summary
├── dealer/[slug]/          # 110 dealer detail pages
├── distributor/[slug]/     # 17 distributor pages
├── assets/img/             # Logos (need 129 replacements)
└── docs/                   # Documentation
```

---

## Deployment

Not yet deployed. To deploy to Vercel:

```bash
# Option 1: Vercel CLI
cd ~/woodhouse_dealer_dashboard
vercel --prod

# Option 2: Connect GitHub repo to Vercel
# Go to vercel.com → New Project → Import woodhouse_dealer_dashboard
```

After deployment, pushes auto-deploy:
```bash
ga && git commit -m "Update dashboard" && gpush
```

---

## File Paths (for Claude/AI tools)

WSL path format for Desktop Commander:
```
\\wsl$\Ubuntu\home\heygregwood\woodhouse_dealer_dashboard\[file]
```

**DO NOT use:**
- `C:\Users\greg\...`
- `/home/heygregwood/...`
- `~/...`

---

## Data Updates

When new Sprout Social data comes in:

1. Export Post Performance CSV (use Organic Impressions)
2. Export Profile Performance CSV
3. Run Python scripts to regenerate dealer data
4. Regenerate HTML pages
5. Push to deploy

---

## Key Stats

- **Dealers:** 110
- **Distributors:** 17
- **Data through:** December 15, 2025
- **Metrics:** Organic only (excludes paid/boosted)

---

## Top Distributors by Dealer Count

| Distributor | Dealers |
|-------------|---------|
| Johnson Supply | 29 |
| GW Berkheimer | 23 |
| APR Supply | 10 |
| Ihrie Supply | 7 |
| First Supply | 8 |

---

## Recovery

```bash
# Reset to last good commit
gp
git reset --hard origin/main

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Discard changes to specific file
git checkout -- path/to/file
```

---

## Pending Tasks

- [ ] Deploy to Vercel
- [ ] Replace 129 placeholder logos
- [ ] Set up custom domain (optional)
- [ ] Consider auth protection for distributor privacy

---

*See CLAUDE.md for full project context.*
