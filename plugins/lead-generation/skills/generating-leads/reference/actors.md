# Actor Reference

Detailed input schemas and output fields for supported Apify actors.

---

## Google Maps Scraper

**Actor ID:** `compass~crawler-google-places`

Scrape local businesses from Google Maps with contact details, ratings, and reviews.

### Key Input Parameters

```json
{
  "searchStringsArray": ["coffee shops"],
  "locationQuery": "Seattle, USA",
  "maxCrawledPlacesPerSearch": 50,
  "language": "en"
}
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `searchStringsArray` | array | Search terms (e.g., "restaurant", "gym") |
| `locationQuery` | string | Location (e.g., "New York, USA") |
| `maxCrawledPlacesPerSearch` | integer | Max results per search term |
| `language` | string | Results language (default: "en") |
| `scrapeContacts` | boolean | Extract emails/socials from websites |

### Output Fields

| Field | Description |
|-------|-------------|
| `title` | Business name |
| `address` | Full address |
| `phone` | Phone number |
| `website` | Website URL |
| `totalScore` | Average rating (1-5) |
| `reviewsCount` | Number of reviews |
| `categoryName` | Business category |
| `openingHours` | Operating hours |

---

## Contact Details Scraper

**Actor ID:** `vdrmota~contact-info-scraper`

Extract emails, phone numbers, and social media profiles from websites.

### Key Input Parameters

```json
{
  "startUrls": [{"url": "https://example.com"}],
  "maxRequestsPerStartUrl": 20,
  "mergeContacts": true
}
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `startUrls` | array | URLs to scrape |
| `maxRequestsPerStartUrl` | integer | Max pages per URL |
| `mergeContacts` | boolean | Merge contacts per domain |
| `maxDepth` | integer | Link depth to follow |
| `sameDomain` | boolean | Stay within domain |

### Output Fields

| Field | Description |
|-------|-------------|
| `domain` | Website domain |
| `emails` | Email addresses found |
| `phones` | Phone numbers found |
| `linkedIns` | LinkedIn profile URLs |
| `twitters` | Twitter/X profile URLs |
| `instagrams` | Instagram profile URLs |
| `facebooks` | Facebook page URLs |
| `youtubes` | YouTube channel URLs |
| `tiktoks` | TikTok profile URLs |

---

## Instagram Profile Scraper

**Actor ID:** `apify~instagram-profile-scraper`

Scrape Instagram profile data including followers, bio, and recent posts.

### Key Input Parameters

```json
{
  "usernames": ["nike", "adidas"]
}
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `usernames` | array | Instagram usernames to scrape |
| `includeAboutSection` | boolean | Include join date and country |

### Output Fields

| Field | Description |
|-------|-------------|
| `username` | Instagram handle |
| `fullName` | Display name |
| `biography` | Profile bio |
| `followersCount` | Number of followers |
| `followsCount` | Number following |
| `postsCount` | Total posts |
| `isBusinessAccount` | Business account flag |
| `verified` | Verification status |
| `externalUrl` | Website link in bio |
| `businessCategoryName` | Business category |

---

## TikTok Profile Scraper

**Actor ID:** `clockworks~tiktok-profile-scraper`

Scrape TikTok profiles and their video content.

### Key Input Parameters

```json
{
  "profiles": ["apifytech"],
  "resultsPerPage": 100
}
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `profiles` | array | TikTok usernames |
| `resultsPerPage` | integer | Max videos per profile |
| `profileSorting` | string | "latest", "popular", or "oldest" |

### Output Fields

| Field | Description |
|-------|-------------|
| `authorMeta.name` | Username |
| `authorMeta.nickName` | Display name |
| `authorMeta.fans` | Follower count |
| `authorMeta.heart` | Total likes |
| `authorMeta.video` | Video count |
| `authorMeta.signature` | Bio |
| `text` | Video caption |
| `playCount` | Video views |
| `diggCount` | Video likes |
| `commentCount` | Video comments |
| `shareCount` | Video shares |

---

## Facebook Pages Scraper

**Actor ID:** `apify~facebook-pages-scraper`

Extract data from Facebook pages including contact info and engagement metrics.

### Key Input Parameters

```json
{
  "startUrls": [{"url": "https://www.facebook.com/nasa"}]
}
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `startUrls` | array | Facebook page URLs |

### Output Fields

| Field | Description |
|-------|-------------|
| `title` | Page name |
| `pageUrl` | Facebook page URL |
| `likes` | Page likes |
| `followers` | Page followers |
| `website` | Website URL |
| `email` | Contact email |
| `phone` | Phone number |
| `address` | Business address |
| `rating` | Page rating |
| `categories` | Page categories |
| `intro` | Page description |

---

## Facebook Groups Scraper

**Actor ID:** `apify~facebook-groups-scraper`

Scrape posts from Facebook groups to find buying intent.

### Key Input Parameters

```json
{
  "startUrls": [{"url": "https://www.facebook.com/groups/example"}],
  "maxPosts": 100
}
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `startUrls` | array | Group URLs |
| `maxPosts` | integer | Max posts to scrape |

### Output Fields

| Field | Description |
|-------|-------------|
| `text` | Post content |
| `authorName` | Post author |
| `authorUrl` | Author profile URL |
| `likes` | Reaction count |
| `comments` | Comment count |
| `shares` | Share count |
| `postUrl` | Direct post URL |

---

## Google Search Scraper

**Actor ID:** `apify~google-search-scraper`

Scrape Google search results for lead discovery.

### Key Input Parameters

```json
{
  "queries": "software companies in Austin",
  "maxResultsPerPage": 100
}
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `queries` | string/array | Search queries |
| `maxResultsPerPage` | integer | Results per query |
| `countryCode` | string | Country for results |
| `languageCode` | string | Language for results |

### Output Fields

| Field | Description |
|-------|-------------|
| `title` | Result title |
| `url` | Result URL |
| `description` | Result snippet |
| `position` | Ranking position |

---

## YouTube Scraper

**Actor ID:** `apify~youtube-scraper`

Scrape YouTube channels for creator partnerships.

### Key Input Parameters

```json
{
  "startUrls": [{"url": "https://www.youtube.com/@channel"}],
  "maxResults": 50
}
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `startUrls` | array | Channel URLs |
| `maxResults` | integer | Max videos to scrape |

### Output Fields

| Field | Description |
|-------|-------------|
| `channelName` | Channel name |
| `subscriberCount` | Subscribers |
| `videoCount` | Total videos |
| `viewCount` | Total views |
| `description` | Channel description |

---

## Google Maps Email Extractor

**Actor ID:** `apify~google-maps-email-extractor`

Extract emails directly from Google Maps listings.

### Key Input Parameters

```json
{
  "searchQueries": ["coffee shops New York"],
  "maxResults": 100
}
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `searchQueries` | array | Search terms with location |
| `maxResults` | integer | Max results |

### Output Fields

| Field | Description |
|-------|-------------|
| `name` | Business name |
| `email` | Extracted email |
| `phone` | Phone number |
| `website` | Website URL |
| `address` | Business address |

---

## LinkedIn Profile Scraper

**Actor ID:** `apify~linkedin-profile-scraper`

Scrape LinkedIn profiles for B2B prospecting.

### Key Input Parameters

```json
{
  "startUrls": [{"url": "https://www.linkedin.com/in/username"}]
}
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `startUrls` | array | Profile URLs |

### Output Fields

| Field | Description |
|-------|-------------|
| `name` | Full name |
| `headline` | Profile headline |
| `company` | Current company |
| `location` | Profile location |
| `connections` | Connection count |
| `about` | Profile summary |
