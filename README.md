# Jobindex Jobs Feed

Extract structured data from [Jobindex.dk](https://Jobindex.dk) — structured job listings from Denmark's largest job portals — Jobindex.dk, IT-Jobbank.dk, and Ofir.dk. Returns title, company with ratings and social media, location with GPS coordinates, full descriptions, and 39 fields per listing.

**[Jobindex Scraper - Denmark Job Listings on Apify →](https://apify.com/blackfalcondata/jobindex-scraper)**

---

## Key features




**Search with filters** — Search by keyword and location. Filter by portal, employment type, work place, and more.

**Detail enrichment** — Fetch full job descriptions, structured metadata for each listing.

**Incremental mode** — Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

---

## Use cases




**Data pipeline automation**
Integrate with your ETL pipeline to collect structured listings from jobindex.dk on a schedule. Export to CSV, JSON, or directly to your database. Use compact mode to control output size.

**Market research**
Monitor listings, track trends, and analyze market dynamics with structured, deduplicated data from jobindex.dk.

---

## Quick start

```json
{
  "query": "software engineer",
  "maxResults": 50,
  "includeDetails": true
}
```

---

## Input parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `query` | string | — | Job search keywords (e.g. 'software engineer', 'sygeplejerske', 'data analyst'). |
| `portal` | enum | `"jobindex.dk"` | Which portal to search. jobindex.dk is the main site (~30K+ jobs). it-jobbank.dk is the IT-vertical subset. Ofir.dk redirects to Jobindex. |
| `location` | string | — | City, municipality, or region (e.g. 'København', 'Aarhus', 'Fyn'). |
| `employmentType` | enum | — | Filter by employment type. |
| `workPlace` | enum | — | Filter by workplace arrangement. |
| `maxResults` | integer | `50` | Maximum total results to return (0 = unlimited). |
| `includeDetails` | boolean | `true` | Enrich results with company social media, career page, about text, and evaluation data. Adds one request per unique company. Disable for faster scraping. |
| `descriptionMaxLength` | integer | `0` | Truncate description to N characters. 0 = no truncation. |
| `compact` | boolean | `false` | Return core fields only (ideal for AI-agent/MCP workflows). |

---

## FAQ

<!-- WRITE: 4-6 Q&A pairs relevant to this product -->

**Is it legal to scrape Jobindex.dk?**
Web scraping of publicly available data is generally legal. This actor only accesses publicly visible information. Always check the target site's terms of service for your specific use case.

**How does incremental mode work?**
Each listing gets a content hash. On subsequent runs, only new or changed listings are emitted — saving time, compute, and storage.

---

## Known limitations

<!-- WRITE: 4-6 honest limitations -->

- <!-- WRITE: limitation 1 -->
- <!-- WRITE: limitation 2 -->

---

## Related products by Black Falcon Data




- [StepStone Scraper](https://github.com/BlackFalconData-org/stepstone-scraper) — Job listings from 18 European portals
- [Indeed Job Scraper](https://github.com/BlackFalconData-org/indeed-job-scraper) — Indeed job listings with salary data
- [Glassdoor Job Scraper](https://github.com/BlackFalconData-org/glassdoor-job-scraper) — Glassdoor listings with company ratings

---

*Last updated: 2026 03*
