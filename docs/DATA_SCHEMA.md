# Data Schema

## Overview

The V2 dashboard uses JSON files embedded in HTML pages and a centralized data.json file. All metrics are **organic only** (excludes paid/boosted posts).

---

## Primary Data Structure

### Dealer Data Object

```json
{
  "profile": "Kerr County A/C & Heating",
  "slug": "kerr-county-a-c-heating",
  "distributor": "Johnson Supply & Equipment Corp",
  "first_post": "2022-03-07",
  "months_before": 25,
  "posts_before": 110,
  
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
  },
  
  "monthly": [
    {
      "month": "2020-01",
      "posts": 0,
      "impressions": 0,
      "engagements": 0,
      "video_views": 0,
      "messages": 0
    }
  ]
}
```

### Distributor Summary Object

```json
{
  "name": "Johnson Supply & Equipment Corp",
  "slug": "johnson-supply-equipment-corp",
  "dealer_count": 29,
  "total_posts": 8500,
  "total_impressions": 10054806,
  "total_engagements": 215774,
  "total_video_views": 125000,
  "total_messages": 4500,
  "avg_engagement_rate": 2.15
}
```

---

## Metrics Definitions

| Metric | Source | Description |
|--------|--------|-------------|
| posts | Post CSV | Count of posts published |
| impressions | Post CSV `Organic Impressions` | Organic reach only |
| engagements | Post CSV `Engagements` | Likes + comments + shares + clicks |
| video_views | Post CSV `Organic Video Views` | Organic video views only |
| messages | Profile CSV `Received Messages (Total)` | Lead count |

---

## % Change Calculation

```javascript
function calcPctChange(before, after) {
  if (before === 0) {
    return after > 0 ? 100 : 0;
  }
  return ((after - before) / before) * 100;
}

// Average across all 5 metrics
const avgPctChange = (
  calcPctChange(before.posts, after.posts) +
  calcPctChange(before.impressions, after.impressions) +
  calcPctChange(before.engagements, after.engagements) +
  calcPctChange(before.video_views, after.video_views) +
  calcPctChange(before.messages, after.messages)
) / 5;
```

---

## Network Benchmarks

Each dealer page shows comparison to network averages:

```json
{
  "network_avg": {
    "posts_per_month": 12.5,
    "impressions_per_month": 8500,
    "engagement_rate": 1.82,
    "video_view_rate": 15.2,
    "messages_per_month": 8.5
  }
}
```

---

## File Structure

### Individual Dealer Pages

Location: `dealer/[slug]/index.html`

Each page contains:
- Embedded JSON data in `<script>` tag
- Before/after comparison table
- Monthly trend chart (Chart.js)
- Network benchmark comparison

### Distributor Summary Pages

Location: `distributor/[slug]/index.html`

Each page contains:
- List of dealers under distributor
- Aggregate metrics
- Link to each dealer detail page

---

## Data Sources

### Post Performance CSV

Exported from Sprout Social: `Post_Performance_ALL_DEALERS_*.csv`

**Key columns:**
- `Profile` - Dealer name
- `Date` - Post date (used to determine month)
- `Organic Impressions` - Excludes paid
- `Engagements` - Total interactions
- `Organic Video Views` - Excludes paid

### Profile Performance CSV

Exported from Sprout Social: `Profile_Performance_ALL_DEALERS_*.csv`

**Key columns:**
- `Profile` - Dealer name
- `Date` - Report date
- `Received Messages (Total)` - Lead/message count

### Dealer Roster CSV

`all_full_dealers_with_first_post_date.csv`

**Key columns:**
- `Program Status` - Filter for "FULL"
- `First Post Date` - When Woodhouse started managing
- `Dealer Name` - Official dealer name
- `Distributor Branch Name` - Parent distributor

---

## Filtering Criteria for Top Performers

To qualify for meaningful before/after comparison:
- **Minimum 6 months** of pre-Woodhouse activity
- **Minimum 20 posts** before Woodhouse partnership

This ensures sufficient baseline data.

---

## Distributors (17)

| Distributor | Dealers | Slug |
|-------------|---------|------|
| Johnson Supply & Equipment Corp | 29 | johnson-supply-equipment-corp |
| GW Berkheimer | 23 | gw-berkheimer |
| APR Supply Co | 10 | apr-supply-co |
| Ihrie Supply Co | 7 | ihrie-supply-co |
| First Supply | 8 | first-supply |
| Shearer Supply LLC | 7 | shearer-supply-llc |
| Hercules Ind | 7 | hercules-ind |
| Dennis Supply Co | 5 | dennis-supply-co |
| Luce Schwab & Kase Inc | 3 | luce-schwab-kase-inc |
| ECCO Supply | 2 | ecco-supply |
| Famous Supply Co | 2 | famous-supply-co |
| Gustave A Larson Co | 2 | gustave-a-larson-co |
| Monroe Equipment | 1 | monroe-equipment |
| APCO Inc | 1 | apco-inc |
| Homans Associates | 1 | homans-associates |
| Winsupply Corporate | 1 | winsupply-corporate |
| Locke Supply Co | 1 | locke-supply-co |

---

## Notes

- Data current through December 15, 2025
- 10 dealers have paid impressions (2.31% of total) - excluded from analysis
- Kerr County A/C has highest paid impressions (50,367) - organic-only analysis shows more accurate results
