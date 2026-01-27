# Lead Generation Examples

Multi-step workflows combining Actors for complex lead generation tasks.

---

## B2B Lead List Building

**User:** "Build a lead list for SaaS companies in Austin"

### Checklist
- [ ] Clarify target industry and location
- [ ] Step 1: Run Google Maps Scraper for businesses
- [ ] Step 2: Run Contact Details Scraper on websites found
- [ ] Combine and deduplicate results
- [ ] Export final lead list

### Steps
1. Start with Google Search or Maps to find companies
2. Extract websites from results
3. Run Contact Details Scraper on each website
4. Merge results into single lead list

---

## YouTube Creator Lead Generation

**User:** "Find YouTube creators about Claude Code"

### Checklist
- [ ] Get topic/keyword from user
- [ ] Ask how many videos to search (default: 50)
- [ ] Run YouTube Scraper to find videos
- [ ] Extract unique channel names from results
- [ ] Run YouTube Scraper again for channel details
- [ ] Report creator stats and contact info

### Steps

1. Search videos about the topic:
```bash
node --env-file=.env ${CLAUDE_PLUGIN_ROOT}/reference/scripts/run_actor.js \
  --actor "streamers/youtube-scraper" \
  --input '{"searchKeywords": ["Claude Code"], "maxResults": 50}' \
  --output claude-code-videos.json --format json
```

2. Extract unique channels, then get details:
```bash
node --env-file=.env ${CLAUDE_PLUGIN_ROOT}/reference/scripts/run_actor.js \
  --actor "streamers/youtube-scraper" \
  --input '{"startUrls": [{"url": "https://www.youtube.com/@channel1"}]}' \
  --output youtube-creators.csv --format csv
```

### Tips
- Use specific keywords to find niche creators
- Filter results by subscriber count for influencer tiers
- Look for email in channel description for outreach
