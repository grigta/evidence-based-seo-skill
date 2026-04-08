# Technical SEO Reference

## Crawl Budget Optimization

### robots.txt Strategy
- Block low-value pages (faceted navigation, internal search, admin)
- Allow all critical CSS/JS (Google needs to render pages)
- Use Crawl-delay carefully (not all bots respect it)
- Sitemap directive must point to the XML sitemap
- Audit prompt template for robots.txt analysis

### Sitemap.xml Architecture
- Separate sitemaps by content type (pages, images, video, news)
- Include only canonical, indexable URLs
- lastmod must be accurate (Google ignores if it detects fake dates)
- For large sites: sitemap index file with sub-sitemaps of max 50,000 URLs
- Priority and changefreq are largely ignored by Google — focus on lastmod

### URL Architecture
Aligned with SegIndexer's expectations:
- Flat hierarchy (max 3 levels deep from root)
- Semantic URL slugs containing primary keyword
- Avoid parameters where possible (use path segments)
- Consistent trailing slash convention
- URL structure should mirror the semantic cocoon hierarchy

## Core Web Vitals

### LCP (Largest Contentful Paint) — target < 2.5s
- Optimize hero images (WebP/AVIF, proper sizing, preload)
- Minimize server response time (TTFB)
- Remove render-blocking resources
- Use font-display: swap for web fonts
- Implement critical CSS inlining

### INP (Interaction to Next Paint) — target < 200ms
- Break up long JavaScript tasks
- Use requestIdleCallback for non-critical work
- Minimize main thread blocking
- Debounce input handlers
- Use web workers for heavy computation

### CLS (Cumulative Layout Shift) — target < 0.1
- Set explicit dimensions on images/videos
- Reserve space for dynamic content (ads, embeds)
- Avoid inserting content above existing content
- Use CSS contain on layout-shifting elements

### CWV and Google Signals
- Good CWV prevents clutterScore penalties
- Poor mobile CWV affects isSmartphoneOptimized
- CWV is a tiebreaker in ranking, not a primary factor — but poor CWV triggers quality demotions

## Canonicalization

### Strategy Rules
- Every page must have a self-referencing canonical tag
- Choose canonical based on: most complete content, most linked version, preferred URL format
- Cross-domain canonicals work but are treated as hints, not directives
- Canonical chains (A→B→C) are bad — always point directly to the final canonical
- Pagination: use rel="canonical" to the paginated page itself (not page 1), and implement rel="next"/"prev" for discovery

## Mobile-First Optimization

### isSmartphoneOptimized Checklist
- Responsive design with proper viewport meta tag
- Tap targets ≥ 48px with ≥ 8px spacing
- No horizontal scrolling
- Font size ≥ 16px base
- No Flash or unplayable media
- Mobile page content must match desktop (Google indexes mobile version)

### isSmearedSignal Prevention
When Google determines a page isn't mobile-friendly:
- Desktop ranking signals get "smeared" (diluted) in mobile results
- The page may rank well on desktop but poorly on mobile
- Fix: ensure full mobile equivalence

### Mobile clutterScore
- Interstitials are more damaging on mobile
- Ad density limits are stricter
- Pop-ups trigger adsDensityInterstitialViolationStrength more easily

## JavaScript SEO

### Rendering Considerations
- Google uses a two-phase indexing: HTML first, then rendered JS (delayed)
- Critical content should be in initial HTML
- Use server-side rendering (SSR) or static generation for SEO-critical pages
- Dynamic rendering as a fallback for complex JS applications

### JS SEO Audit Checklist
1. Can Googlebot access all JS/CSS resources?
2. Is critical content visible in raw HTML (View Source)?
3. Do internal links use standard `<a href>` tags (not JS click handlers)?
4. Are meta tags (title, description, canonical) in the initial HTML?
5. Does the page work without JavaScript enabled?
6. Test with Google's Mobile-Friendly Test and Rich Results Test

## Hreflang Implementation
- Use x-default for language/region selection pages
- Hreflang must be reciprocal
- Include self-referencing hreflang
- Implement via: HTML link tags, HTTP headers (for non-HTML), or XML sitemap
- Common errors: missing reciprocal tags, incorrect language codes, mixing region and language

## Log Analysis

### Analysis Prompt Template
```
Analyze this crawl log data:
[LOG DATA SUMMARY]

Identify:
1. Crawl budget waste: URLs crawled that shouldn't be
2. Under-crawled sections: Important pages crawled less than expected
3. Bot behavior patterns: Is Googlebot favoring certain sections?
4. Status code issues: Unusual 5xx patterns, redirect chains
5. Recommendations: Specific actions to optimize crawl budget
```

## Redirect Strategy
- 301 for permanent moves (passes ~95% of link equity)
- 302 only for genuinely temporary redirects
- Avoid redirect chains (max 1 hop)
- Redirect old URLs after site migration — maintain for minimum 1 year
- Server-side redirects preferred over meta refresh or JS redirects

## Structured Data (Schema.org)

### Priority Schema Types by Site Type
| Site type | Priority schemas |
|-----------|-----------------|
| E-commerce | Product, Offer, AggregateRating, BreadcrumbList, FAQPage |
| Content/Blog | Article, Person (author), BreadcrumbList, FAQPage, HowTo |
| Local business | LocalBusiness, PostalAddress, OpeningHoursSpecification, Review |
| SaaS | SoftwareApplication, FAQPage, Organization, BreadcrumbList |
| News | NewsArticle, Person, Organization, BreadcrumbList |

### Schema Best Practices
- Use JSON-LD format (Google's preferred)
- Only mark up content visible on the page
- Validate with Google's Rich Results Test
- Nest entities (author within article, address within business)
- Keep schema current

## Latent Optimization Techniques

### Entity Shadow Audit
```
For the URL [URL], compare:
1. Intended entities: [YOUR TARGET ENTITIES]
2. Detected entities: [entities extracted from Google's cache/NLP analysis]

Identify shadows and gaps. Provide specific content adjustments.
```

### Inference Path Engineering
- Explicitly state relationships between entities
- Use structured data to reinforce relationships
- Co-mention related entities in close proximity
- Build inference chains: if A relates to B, and B relates to C, ensure all three appear together

### Semantic Canonicalization
- No two pages should target the same entity cluster
- If pages overlap semantically, either merge them or differentiate their entity focus
- Use siteFocusScore as a guide

### SCDL Anchor Pages
- Main site page → links to social profiles, press mentions, industry directories
- Each external presence reinforces the same entity relationships
- Creates a coherent semantic footprint across the web
