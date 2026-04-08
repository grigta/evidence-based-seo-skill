# SEO Analytics with LLM

## Google Analytics 4 (GA4) Analysis

### Conversion Analysis Prompt
```
Analyze this GA4 conversion data:
[DATA]

Identify:
1. Top converting landing pages and their traffic sources
2. Conversion path patterns (first touch → last touch)
3. Pages with high traffic but low conversion (optimization opportunities)
4. Pages with high conversion but low traffic (scaling opportunities)
5. Behavioral signals: dwell time, pages per session, bounce rate by segment
6. Recommended actions prioritized by estimated impact
```

### Behavioral Reports
Key metrics to analyze with LLM:
- **Dwell time by page type**: Normalize by expected dwell (product page ~2min, article ~4min, tool ~6min)
- **Bounce rate in context of intent**: High bounce on a quick-answer FAQ is normal; high bounce on a product page is bad
- **First-screen structure impact**: Does above-the-fold content correlate with engagement?
- **Exit point analysis**: Where users leave the site — pattern detection
- **Cluster page comparison**: Compare pages within same semantic cluster for behavioral anomalies

### Content Anomaly Detection
```
Analyze these pages with high impressions but poor engagement:
[PAGE DATA: URL, impressions, clicks, avg_session_duration, bounce_rate]

For each page:
1. What's the likely disconnect between search appearance and content?
2. Is the title/description misleading (CTR bait)?
3. Does the content match the search intent for its ranking queries?
4. Content quality assessment based on engagement metrics
5. Specific improvement recommendations
```

### Audience Segmentation
```
Segment this GA4 audience data by behavior:
[USER FLOW DATA]

Create segments:
1. Semantic intent clusters (group users by query patterns)
2. Behavior scenario clusters (group by navigation patterns)
3. Commercial vs. non-commercial separation
4. Sub-intent detailing within each segment
5. Targeting descriptions for marketing team
6. Content recommendations per segment
```

## Google Search Console (GSC) Analysis

### Query Data Processing
Before analysis, always clean GSC data:
- **Normalize queries**: lowercase, remove extra spaces, handle encoding
- **Intent classification**: Classify each query as Informational/Commercial/Transactional/Navigational
- **Position interpretation**: Don't use mean position naively — it's distorted by long-tail queries with few impressions. Weight by impressions.
- **CTR interpretation**: Compare against expected CTR for position (position 1 ~28%, position 2 ~15%, position 3 ~11%, etc.)

### Low-Hanging Fruit Analysis
```
Analyze this GSC data to find low-hanging fruit:
[QUERY/PAGE DATA: query, page, position, impressions, clicks, CTR]

Filter for:
1. Positions 8-20 (page 1-2 boundary — small improvements = big traffic gains)
2. Commercial/Transactional intent queries (higher value)
3. Low CTR relative to position (title/description optimization needed)
4. High impressions but low clicks (visibility without capture)

For each opportunity:
- Current state (position, impressions, CTR)
- Estimated traffic gain if moved to top 5
- Specific optimization actions (content expansion, title rewrite, internal linking boost)
- Priority score (potential traffic × commercial value)
```

### Cannibalization Detection
```
Detect keyword cannibalization in this GSC data:
[DATA: query, page, position, impressions, clicks]

Cannibalization occurs when multiple pages rank for the same query.
For each cannibalized query:
1. Which pages are competing?
2. Which page should be the canonical target?
3. Resolution strategy:
   - Merge content into the stronger page
   - Differentiate the weaker page to target a different intent
   - Add canonical or redirect
   - Adjust internal linking to concentrate authority
```

### Query-Page Mismatch
```
Analyze query-to-page mapping:
[GSC DATA]

Identify cases where:
1. A query is landing on the wrong page (intent mismatch)
2. A page ranks for queries it wasn't designed for
3. Queries that should have a dedicated page but land on a generic one
4. Recommend page-to-query realignment actions
```

## Traffic Anomaly Detection

### Detection Framework
1. **Statistical detection**: Use ARIMA or Prophet to identify anomalies
2. **LLM attribution**: Feed anomaly data + context to LLM for root cause analysis
3. **Multi-source cross-check**: Compare GSC + GA4 + server logs + changelog

### Anomaly Classification
```
Classify this traffic anomaly:
[ANOMALY DATA: date range, affected pages/queries, traffic change %]
[CONTEXT: recent site changes, Google updates, seasonal patterns]

Classify as:
1. Technical (server issues, indexing problems, redirect errors)
2. Content (quality update impact, content changes, new competitor content)
3. Algorithmic (Google core update, specific signal change)
4. Seasonal (expected pattern based on historical data)
5. External (news event, market change, competitor action)

For each classification:
- Evidence supporting this classification
- Confidence level (High/Medium/Low)
- Verification steps
- Recovery/capitalization actions
```

### Sharp Drop Analysis
```
Analyze this traffic drop:
[TRAFFIC DATA: before/after comparison]
[GSC DATA: query/page level changes]
[CHANGELOG: recent technical/content changes]

Investigate:
1. Is the drop site-wide or localized?
2. Did it coincide with a known Google update?
3. What queries lost the most positions?
4. Are there technical issues?
5. Did competitor content improve?
6. Hypothesis with evidence for each potential cause
7. Priority recovery actions
```

## Traffic Forecasting

### Methodology
```
Create a traffic forecast for [SITE/SECTION]:

Historical data: [12+ months of GSC/GA4 data]
Planned actions: [content calendar, technical improvements, link building plans]
External factors: [seasonality, market events, competitor activity]

Process:
1. Decompose historical data: trend + seasonality + residual
2. Apply planned action impact estimates
3. Factor in seasonality patterns
4. Account for market growth/contraction
5. Produce monthly forecast with confidence intervals
6. Segment by: organic brand vs. non-brand, page type, intent category

Output:
- Monthly traffic projections (pessimistic/baseline/optimistic)
- Key assumptions and risk factors
- Milestones that would validate or invalidate the forecast
```

## Report Generation

### Executive SEO Report Template
```
Generate an executive SEO report:

Period: [DATE RANGE]
Data sources: [GA4, GSC, rank tracking, backlink data]

Structure:
1. Executive Summary (3-5 bullet points, focus on business impact)
2. Key Metrics Dashboard
3. Notable Wins
4. Concerns
5. Actions Taken This Period
6. Recommendations for Next Period
7. Competitive Landscape Changes

Keep language non-technical for executive audience.
All claims must be backed by specific data points.
```

## Behavioral Factor Optimization

### Dwell Time Analysis
```
Analyze dwell time data:
[PAGE DATA: URL, page_type, avg_dwell_time, word_count, media_count]

Normalize by page type:
- Product pages: expected 1.5-3 minutes
- Blog articles: expected 3-6 minutes
- Tool pages: expected 5-10 minutes
- Landing pages: expected 1-2 minutes

Identify:
1. Pages with dwell time significantly below type average
2. Content structure issues
3. Engagement boosters that work
4. Recommendations per page to increase dwell time
```

### Optimization Priority Matrix
```
Create an optimization priority matrix:
[PAGE DATA with all behavioral metrics]

Score each page on:
- Traffic potential
- Current performance gap
- Commercial value
- Implementation effort

Output a prioritized list with expected ROI and recommended actions.
```
