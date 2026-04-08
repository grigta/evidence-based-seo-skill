# Google Internal Signals Reference (API Leak 2024)

## Data Structures
- **CompositeDoc**: The master document object Google builds for every indexed page. Contains all collected signals.
- **PerDocData**: Per-document signal storage within CompositeDoc. Every signal below lives here.

## Q* (Quality Signals)

### Site-Level Quality
- **siteAuthority** (int32): Aggregate site authority score. Built from backlink profile, brand signals, and historical quality. Higher = more trusted.
- **predictedDefaultNsr** (Normalized Site Rank): Machine-learned prediction of overall site quality. Used as a baseline quality filter in Mustang retrieval.
- **siteQuality.nsr** variants: nsr, nsrSitechunkAdjusted, nsrVariedDomain, nsrDataOverride, nsrHealthEpoch — different NSR calculations for different contexts.
- **pandaDemotion**: Boolean/severity flag. Triggered by thin content, low content-to-ads ratio, poor UX patterns. One of the most impactful negative signals.
- **lowQuality**: Binary flag marking pages/sites as low quality.

### Page-Level Quality
- **contentEffort**: Numeric score reflecting how much effort went into creating the content. Factors: word count, original data, formatting depth, media integration.
- **OriginalContentScore**: Measures how much content is original vs. copied/scraped. Affects indexing priority.
- **goldmineBlockbertFactor**: BERT-based content quality assessment at block level.
- **clutterScore**: Measures page clutter (ads, popups, navigation noise). High clutterScore = quality demotion.
- **adsDensityInterstitialViolationStrength**: Specific penalty for intrusive interstitials and ad density.

### Author/Entity Quality
- **authorReputationScore**: Score attached to identified content authors.
- **authorObfuscatedGaiaStr**: Hashed author identifier linking content to Google's Knowledge Graph identity.
- **productReview** signals: reviewRating, reviewCount, isProductReview — for review content quality.

## P* (Popularity/User Signals)

### Direct Traffic
- **chromeInTotal**: Total direct visits measured via Chrome browser data. One of the hardest signals to manipulate. Strong brand indicator.

### NavBoost (Click Signals)
NavBoost is Google's click-based re-ranking system. It processes click data to adjust rankings after initial retrieval:
- **goodClicks**: Clicks followed by engagement (long dwell, page interaction, no pogo-sticking).
- **badClicks**: Clicks followed by quick returns to SERP (pogo-sticking indicator).
- **lastLongestClicks**: The last click in a search session where user stayed longest. Extremely strong positive signal.
- **unsquashedClicks**, **squashedClicks**: Raw vs. normalized click counts.
- **impressions**: How often the page appeared in SERP for a query.

### Behavioral Metrics
- Dwell time (derived from NavBoost click patterns)
- Click-through rate (from impressions vs. clicks)
- Session-level satisfaction signals

## T* (Topicality Signals)

### ABC Model (Anchors, Body, Clicks)
Google determines page topicality through three sources:
- **Anchors (A)**: Text in inbound links pointing to the page. Tells Google what others think the page is about.
- **Body (B)**: On-page content analysis. Entity extraction, keyword density, semantic relevance.
- **Clicks (C)**: Which queries lead users to click this page. Real-world topicality validation.

### Semantic Signals
- **EntityAnnotations**: Entities recognized on the page via Knowledge Graph matching. Each entity has: name, type, salience score, midCount.
- **siteFocusScore**: How topically focused the entire site is. Niche sites score higher. Related to topical authority.
- **siteRadius**: Semantic breadth of the site's content. Smaller radius = more focused.
- **site2vecEmbedding**: Vector embedding representing the site's overall semantic position.
- **TopicEmbeddings**: Per-page topic vectors used for semantic matching.

### Term-Level Signals
- **avgTermWeight**: Average importance weight of terms on the page. Anomalous values (too high = stuffing, too low = thin) trigger flags.
- **QBST (Query-Based Salient Terms)**: Terms Google considers most important for matching queries to pages.

## Link Signals

### Authority
- **PageRank-NearestSeeds**: Modern PageRank variant. Measures link authority relative to a set of trusted seed sites. Proximity to seeds matters more than raw link count.
- **sourceType** in link data: Classification of linking source (news, blog, forum, directory, etc.).

### Penalty Signals
- **anchorMismatchDemotion**: Triggered when anchor text distribution looks unnatural (over-optimized exact-match anchors).
- **spamrank**: Spam probability score based on link graph analysis.
- Link index tiers: Tier 1 (highest quality, fully processed), Tier 2 (medium), Tier 3 (lowest quality, minimal processing).

## Brand Signals
- **queriesForWhichOfficial**: Queries for which Google considers this site the official result.
- **chromeInTotal**: Also a brand signal — direct type-in traffic indicates brand recognition.
- **brickAndMortarStrength**: For businesses with physical locations, how strong the physical presence signal is.

## Local Signals
- **LocalWWWInfo**: Local business information associated with the domain.
- **brickAndMortarStrength**: Physical business presence score.
- **geotopicality**: How relevant the content is to a specific geographic area.
- NAP (Name, Address, Phone) consistency across citations.

## Mobile Signals
- **isSmartphoneOptimized**: Whether the page is properly optimized for mobile.
- **isSmearedSignal**: When a page isn't mobile-optimized, its desktop signals get "smeared" (diluted) rather than fully transferred to mobile rankings.
- **clutterScore** on mobile: Evaluated separately for mobile viewport.

## Freshness Signals
- Content update frequency
- Historical data patterns in PerDocData
- Freshness Twiddlers in the final ranking stage

## How Signals Interact

Signals don't work in isolation. Key interactions:
1. **Q* gates P***: A page needs minimum quality to even benefit from user signals. pandaDemotion can nullify good NavBoost data.
2. **T* gates retrieval**: Without topicality match, a page never enters the candidate set for re-ranking.
3. **P* confirms T***: Click patterns validate whether the page actually satisfies the topic. Clicks component of ABC reinforces Body and Anchor signals.
4. **Brand amplifies everything**: High chromeInTotal and queriesForWhichOfficial create a halo effect across all three pillars.

## Signal Strength Hierarchy (approximate)

From the API leak and observed behavior, rough signal importance:
1. chromeInTotal + NavBoost (P*) — strongest for established queries
2. siteAuthority + PageRank-NearestSeeds (Q*) — strongest for new/ambiguous queries
3. Entity coverage + siteFocusScore (T*) — strongest for topical matching
4. contentEffort + OriginalContentScore (Q*) — differentiation factor
5. Anchor text + siteFocusScore (T*) — topical authority building
6. Mobile optimization + CWV (Q*) — hygiene factors (absence hurts more than presence helps)
