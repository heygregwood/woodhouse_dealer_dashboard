# Woodhouse Dealer Dashboard (V2)

Full Allied Air dealer performance dashboard with before/after Woodhouse partnership comparisons.

**Status:** Ready for deployment  
**Dealers:** 110  
**Distributors:** 17

## Overview

This V2 dashboard provides:
- Individual dealer detail pages with before/after metrics
- Distributor summary pages
- Network-wide benchmarks
- Chart.js visualizations
- Before/after Woodhouse partnership comparisons

## Metrics Tracked

All metrics use **organic data only** (excludes paid/boosted):

- **Posts** — Content published by Woodhouse
- **Impressions** — Organic reach
- **Engagements** — Likes, comments, shares, clicks
- **Video Views** — Organic video views
- **Leads** — Messages received
- **% Change** — Before vs after Woodhouse partnership

## Tech Stack

- Static HTML + Tailwind CSS (CDN)
- Chart.js for visualizations
- Vanilla JavaScript
- Vercel-ready

## Directory Structure

```
├── index.html           # Main dashboard
├── all/index.html       # Network summary
├── dealer/[slug]/       # 110 dealer detail pages
├── distributor/[slug]/  # 17 distributor pages
└── assets/img/          # Logos
```

## Top Performers

Dealers with 6+ months and 20+ posts before Woodhouse:

| Dealer | Avg % Change |
|--------|--------------|
| Kerr County A/C & Heating | +21,808% |
| McDonald Mechanical Services | +1,423% |
| DeLong and Sons HVAC | +632% |
| Chipps Residential Services | +360% |
| Paramount Plumbing Heating & Air | +349% |

## Development

```bash
# Clone
git clone https://github.com/heygregwood/woodhouse_dealer_dashboard.git

# Edit files directly - no build step
# Test by opening index.html in browser

# Deploy
git add . && git commit -m "message" && git push
```

## Pending

- [ ] Replace placeholder logos with real dealer logos (129 needed)
- [ ] Deploy to Vercel
- [ ] Set up custom domain

## Related

- [woodhouse_agency_turnkey_perfomance](https://github.com/heygregwood/woodhouse_agency_turnkey_perfomance) - Ihrie Supply dashboard (LIVE)
- [woodhouse_social](https://github.com/heygregwood/woodhouse_social) - Main SaaS platform
