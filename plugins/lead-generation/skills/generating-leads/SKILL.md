---
name: generating-leads
description: Generates B2B/B2C leads by scraping Google Maps, websites, Instagram, TikTok, Facebook, LinkedIn, YouTube, and Google Search. Use when user asks to find leads, prospects, businesses, build lead lists, enrich contacts, or scrape profiles for sales outreach.
---

# Generating Leads

Scrape leads from multiple platforms using Apify actors.

## Prerequisites

- `.env` file with `APIFY_TOKEN`
- Python 3.9+ and `uv`

## Workflow

Copy this checklist and track progress:

```
Task Progress:
- [ ] Step 1: Determine lead source (select actor)
- [ ] Step 2: Ask user preferences (format, filename)
- [ ] Step 3: Run the lead finder script
- [ ] Step 4: Summarize results
```

### Step 1: Determine Lead Source

| User Need | Actor ID | Best For |
|-----------|----------|----------|
| Local businesses | `compass~crawler-google-places` | Restaurants, gyms, shops |
| Contact enrichment | `vdrmota~contact-info-scraper` | Emails, phones from URLs |
| Instagram profiles | `apify~instagram-profile-scraper` | Influencer discovery |
| TikTok profiles | `clockworks~tiktok-profile-scraper` | Creator outreach |
| Facebook pages | `apify~facebook-pages-scraper` | Business contacts |
| Facebook groups | `apify~facebook-groups-scraper` | Buying intent signals |
| Google Search | `apify~google-search-scraper` | Broad lead discovery |
| YouTube channels | `apify~youtube-scraper` | Creator partnerships |
| Google Maps emails | `apify~google-maps-email-extractor` | Direct email extraction |
| LinkedIn profiles | `apify~linkedin-profile-scraper` | B2B prospecting |

See [reference/actors.md](reference/actors.md) for detailed input schemas and output fields.

### Step 2: Ask User Preferences

Before running, ask:
1. **Output format**: CSV or JSON? (default: CSV)
2. **Output filename**: Suggest descriptive name based on search

### Step 3: Run the Script

```bash
uv run --with python-dotenv --with requests \
  ${CLAUDE_PLUGIN_ROOT}/skills/generating-leads/reference/scripts/run_actor.py \
  --actor "ACTOR_ID" \
  --input 'JSON_INPUT' \
  --output OUTPUT_FILE \
  --format csv|json
```

The script handles:
- Loading `APIFY_TOKEN` from `.env`
- Starting and polling the actor run
- Downloading results in requested format
- Reporting record count and file size

### Step 4: Summarize Results

After completion, report:
- Number of leads found
- File location
- Key fields available
- Suggested next steps (filtering, enrichment)

## Quick Examples

**Google Maps - Local businesses:**
```bash
uv run --with python-dotenv --with requests \
  ${CLAUDE_PLUGIN_ROOT}/skills/generating-leads/reference/scripts/run_actor.py \
  --actor "compass~crawler-google-places" \
  --input '{"searchStringsArray": ["coffee shops"], "locationQuery": "Seattle, USA", "maxCrawledPlacesPerSearch": 50}' \
  --output coffee-shops-seattle.csv \
  --format csv
```

**Contact enrichment from websites:**
```bash
uv run --with python-dotenv --with requests \
  ${CLAUDE_PLUGIN_ROOT}/skills/generating-leads/reference/scripts/run_actor.py \
  --actor "vdrmota~contact-info-scraper" \
  --input '{"startUrls": [{"url": "https://example.com"}], "maxRequestsPerStartUrl": 20}' \
  --output contacts.json \
  --format json
```

See [reference/workflows.md](reference/workflows.md) for detailed step-by-step guides for each use case.

## Error Handling

| Error | Solution |
|-------|----------|
| `APIFY_TOKEN not found` | Create `.env` with `APIFY_TOKEN=your_token` |
| `Actor not found` | Check actor ID spelling (use `~` not `/`) |
| `Run FAILED` | Check Apify console link in error output |
| `Timeout` | Reduce input size or increase `--timeout` |

If errors occur:
1. Verify `.env` exists with valid token
2. Check Apify console link for details
3. Adjust input parameters if needed
