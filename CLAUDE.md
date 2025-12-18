# Woodhouse Dealer Dashboard (V2) - AI Assistant Context

**Status:** Not deployed (ready for deployment)  
**Repo:** https://github.com/heygregwood/woodhouse_dealer_dashboard

---

## Purpose

Full Allied Air dealer performance dashboard showing before/after Woodhouse partnership metrics for all dealers. This is V2 - the polished version with network benchmarks, Chart.js visualizations, and individual dealer detail pages.

**Contains:**
- 110 active dealers
- 17 distributors
- Before/after Woodhouse comparisons
- Network-wide benchmarks

---

## File Access (CRITICAL for Desktop Commander)

Use this path format:
```
\\wsl$\Ubuntu\home\heygregwood\woodhouse_dealer_dashboard\[file_path]
```

**DO NOT use:** `C:\Users\...`, `/home/heygregwood/...`, or `~/...`

---

## Stack

- **Static HTML** with Tailwind CSS (CDN)
- **Chart.js** for visualizations
- **Vanilla JavaScript** for dynamic rendering
- **JSON data files** for metrics
- **Host-ready for:** Vercel

---

## Directory Structure

```
woodhouse_dealer_dashboard/
├── index.html                    # Main Allied Air summary dashboard
├── assets/
│   └── img/
│       ├── woodhouse_logo.png
│       └── [placeholder logos - 129 needed]
├── all/
│   └── index.html               # Network-wide summary
├── dealer/
│   └── [dealer-slug]/
│       └── index.html           # Individual dealer detail pages (110)
├── distributor/
│   └── [distributor-slug]/
│       └── index.html           # Distributor summary pages (17)
└── .git/
```

---

## Data Model

Each dealer page includes:

### Before/After Comparison
```json
{
  "before": {
    "posts": 59,
    "impressions": 21949,
    "engagements": 1214,
    "video_views": 48,
    "messages": 27
  },
  "after": {
    "posts": 1074,
    "impressions": 472534,
    "engagements": 40591,
    "video_views": 44775,
    "messages": 2414
  }
}
```

### Network Benchmarks
Each dealer shows how they compare to network averages:
- Posts per month
- Impressions per month
- Engagement rate
- Video view rate
- Lead conversion rate

---

## Key Metrics Definitions

- **Posts** — Total content published (Woodhouse-managed)
- **Impressions** — Organic reach only (excludes paid/boosted)
- **Engagements** — Likes, comments, shares, clicks
- **Video Views** — Organic video views only
- **Leads** — Messages received (potential customer inquiries)
- **% Change** — ((after - before) / before) × 100

---

## Distributors (17)

1. Johnson Supply & Equipment Corp (29 dealers)
2. GW Berkheimer (23 dealers)
3. APR Supply Co (10 dealers)
4. Ihrie Supply Co (7 dealers)
5. First Supply (8 dealers)
6. Shearer Supply LLC (7 dealers)
7. Hercules Ind (7 dealers)
8. Dennis Supply Co (5 dealers)
9. Luce Schwab & Kase Inc (3 dealers)
10. ECCO Supply (2 dealers)
11. Famous Supply Co (2 dealers)
12. Gustave A Larson Co (2 dealers)
13. Monroe Equipment (1 dealer)
14. APCO Inc (1 dealer)
15. Homans Associates (1 dealer)
16. Winsupply Corporate (1 dealer)
17. Locke Supply Co (1 dealer)

---

## Top Performers (6+ months, 20+ posts pre-Woodhouse)

Using organic impressions only:

| Rank | Dealer | Avg % Change |
|------|--------|--------------|
| 1 | Kerr County A/C & Heating | +21,808% |
| 2 | McDonald Mechanical Services | +1,423% |
| 3 | DeLong and Sons HVAC | +632% |
| 4 | Chipps Residential Services | +360% |
| 5 | Paramount Plumbing Heating & Air | +349% |

---

## Deployment

To deploy to Vercel:

1. Create new Vercel project linked to `woodhouse_dealer_dashboard` repo
2. Or manually deploy:
```bash
cd ~/woodhouse_dealer_dashboard
vercel --prod
```

---

## Pending Work

- [ ] Replace 129 placeholder logos with real dealer logos
- [ ] Deploy to Vercel
- [ ] Set up custom domain (e.g., reports.woodhouseagency.com)
- [ ] Consider Vercel Auth protection or password protection for distributor privacy

---

## Related Repos

| Repo | Purpose |
|------|---------|
| `woodhouse_agency_turnkey_perfomance` | Ihrie Supply-specific dashboard (LIVE) |
| `dealer_reports` | Legacy V1 dashboard (deprecated) |
| `woodhouse_social` | Main SaaS platform |
| `prospect_engine` | National HVAC contractor database |

---

## Git Workflow

```bash
# Push changes
ga && git commit -m "message" && gpush

# Pull changes locally
gp
```

---

## Development Notes

- Static site - no build step
- Edit HTML/JSON directly
- Test locally by opening index.html in browser
- Logo images in `assets/img/` need to match slug patterns
