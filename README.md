# SEO reporting workflows (n8n)

Three importable n8n workflows that pull data, compare periods and use Claude (Haiku) to write short, plain-English summaries.

| File | What it does |
| --- | --- |
| `weekly-seo-flag-report.json` | Compares each week with the same week last quarter and last year across Search Console, GA4 and AccuRanker. Flags only threshold breaches and emails a summary. |
| `monthly-seo-audit.json` | Monthly audit using Search Console, GA4, AccuRanker, PageSpeed, Business Profile and a LibreCrawl crawl. Writes a Google Doc and logs a snapshot to a Sheet. |
| `competitor-sitemap-monitor.json` | Saves each competitor's XML sitemap weekly, diffs it against the last copy and emails what appeared, disappeared or changed. |

## Design choices
- Failed calls are retried, and missing data is reported as missing rather than as a drop to zero.
- Only threshold breaches are flagged, to keep the reports short.

## Setup
1. Import each JSON into n8n. They import inactive.
2. Reattach your own credentials on every node (all were removed).
3. Replace the placeholders: `YOUR_GOOGLE_SHEET_ID`, the notification email, `YOUR_GBP_ACCOUNT_ID`, and in the monthly audit `YOUR_GOOGLE_API_KEY` (better still, move it into a credential).
4. The client and competitor details are examples. Add your own.
