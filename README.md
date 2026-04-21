# Jobindex Jobs Feed

Extract structured data from [Jobindex.dk](https://Jobindex.dk) — structured job listings from Denmark's largest job portals — Jobindex.dk, IT-Jobbank.dk, and Ofir.dk. Returns title, company with ratings and social media, location with GPS coordinates, full descriptions, and 39 fields per listing.

**[Jobindex Scraper - Denmark Job Listings on Apify →](https://apify.com/blackfalcondata/jobindex-scraper?fpr=1h3gvi)**

---

## Key features






**Search with filters** — Search by keyword and location. Filter by portal, employment type, work place, and more.

**Detail enrichment** — Fetch full job descriptions, structured metadata for each listing.

**Incremental mode** — Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

**Compact output** — Emit core fields only (AI-agent / MCP-friendly). Keeps response size small for LLM workflows.

**Description truncation** — Cap description length per listing to control output size and cost.

**Result cap** — Stop after N listings (up to 5.000). Set to 0 for the full catalog.

**Export anywhere** — Download as JSON, CSV, or Excel. Stream via Apify API, webhooks, or integrations with Make, Zapier, Airbyte, Keboola.

**Structured data** — Clean JSON output with consistent field naming. All fields always present — `null` when unavailable, never omitted.

---

## Use cases






**Data pipeline automation**
Integrate with your ETL pipeline to collect structured listings from jobindex.dk on a schedule. Export to CSV, JSON, or directly to your database. Use compact mode to control output size.

**Market research**
Monitor listings, track trends, and analyze market dynamics with structured, deduplicated data from jobindex.dk.

**Change monitoring**
Run daily or hourly in incremental mode to capture only new, updated, or expired listings. Perfect for price-tracking, churn analysis, and alerting pipelines.

**AI / LLM training data**
Structured JSON per listing is ready for RAG pipelines, embeddings, and agent workflows. Compact mode trims tokens for LLM context windows.

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


## Output fields

Every listing returns the same 40-field schema. Missing values are `null` — never omitted.

- `jobId`
- `portalId`
- `title`
- `company`
- `companyId`
- `companyUrl`
- `companyLogo`
- `companyFollowers`
- `companyRatingScore`
- `companyRatingCount`
- `companyCareerPage`
- `companyAbout`
- `companyMotherCompany`
- `companyEvaluationCount`
- `companySocialFacebook`
- `companySocialLinkedin`
- `companySocialYoutube`
- `companySocialInstagram`
- `companySocialTwitter`
- `location`
- `city`
- `zipCode`
- `address`
- `latitude`
- `longitude`
- `employmentType`
- `isRemote`
- `description`
- `applyUrl`
- `portalUrl`
- `url`
- `postedDate`
- `deadline`
- `deadlineAsap`
- `isPromoted`
- `hasVideo`
- `videoUrl`
- `categories`
- `scrapedAt`
- `source`


## Sample output

One object per listing. Here is a real example from a production run:

```json
{
  "jobId": "698811193af9e712ee4ea3ab61740a95fdff60236d5281c1f0bb7e42d2672b1c",
  "portalId": "h1631460",
  "title": "Senior Frontend Developer",
  "company": "Grundfos A/S",
  "companyId": 157,
  "companyUrl": "https://www.grundfos.com/dk",
  "companyLogo": "https://www.jobindex.dk/img/logo/Grundfos_logo.gif",
  "companyFollowers": 12183,
  "companyRatingScore": 5,
  "companyRatingCount": 791,
  "companyCareerPage": "https://www.grundfos.com/dk/about-us/careers",
  "companyAbout": "Water is the heart and soul of Grundfos Grundfos moves and transforms water and other liquids via intelligent, sustainable and energy efficient solutions for use in buildings, indu…"
}
```

*Truncated — full records contain 40 fields. See Output fields for the complete schema.*


**[Try Jobindex Scraper - Denmark Job Listings now — $5 free credit, no credit card →](https://apify.com/blackfalcondata/jobindex-scraper?fpr=1h3gvi)**


## Pricing

Pay only for what you extract. No subscription required — Apify's free $5 credit covers thousands of results.

| Event | Price (USD) |
| --- | --- |
| Actor Start | $0.01 |
| Result | $0.002 |

See the [actor on Apify](https://apify.com/blackfalcondata/jobindex-scraper?fpr=1h3gvi) for current pricing.

---

## Related products by Black Falcon Data






- [StepStone Scraper](https://apify.com/blackfalcondata/stepstone-scraper?fpr=1h3gvi) — Job listings from 18 European portals
- [Indeed Job Scraper](https://apify.com/blackfalcondata/indeed-job-scraper?fpr=1h3gvi) — Indeed job listings with salary data
- [Glassdoor Job Scraper](https://apify.com/blackfalcondata/glassdoor-job-scraper?fpr=1h3gvi) — Glassdoor listings with company ratings
- [Arbeitsagentur Scraper](https://apify.com/blackfalcondata/arbeitsagentur-scraper?fpr=1h3gvi) — Germany's official job portal (1M+ listings)
- [SEEK Scraper](https://apify.com/blackfalcondata/seek-scraper?fpr=1h3gvi) — Australia & NZ's largest job board
- [Naukri Scraper](https://apify.com/blackfalcondata/naukri-scraper?fpr=1h3gvi) — India's largest job portal

---


## About Black Falcon Data

Black Falcon Data builds production-grade web scrapers for job boards and marketplace data. Browse our full actor catalog at [www.blackfalcondata.com](https://www.blackfalcondata.com).

---

## Getting started with Apify

New to Apify? [Create a free account with $5 credit](https://console.apify.com/sign-up?fpr=1h3gvi) — no credit card required.

1. [Sign up free](https://console.apify.com/sign-up?fpr=1h3gvi) — $5 credit included
2. Open the actor and paste your input
3. Click Start — results download as JSON, CSV, or Excel

Need more volume? [See pricing](https://apify.com/pricing?fpr=1h3gvi).

---

---

*Last updated: 2026 03*
