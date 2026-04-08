# Local, Mobile & Vertical SEO

## Local SEO

### Google Business Profile (GBP) Optimization
Key signals: LocalWWWInfo, brickAndMortarStrength, geotopicality

#### GBP Optimization Prompt
```
Role: Local SEO specialist
Input: Business name, address, category, services, current GBP listing

Optimize:
1. Business description (750 chars max, keywords + location)
2. Categories: Primary + 2-5 secondary
3. Services/Products with local keywords
4. Attributes
5. Photos: storefront, interior, team, products (geotagged)
6. Q&A: 10 seed questions
7. Posts: weekly calendar
```

### Review Response Generation
```
Generate response to review:
Review: [TEXT], Rating: [1-5], Business type: [TYPE]

Rules:
- Positive (4-5): Thank, reference specifics, invite return
- Negative (1-2): Acknowledge, don't argue, offer resolution, take offline
- Neutral (3): Thank, address concerns, highlight improvements
- Include business name + 1-2 service keywords
- 50-100 words, professional warm tone
```

### Local Landing Pages
```
Create local landing page:
Business: [NAME], Service: [SERVICE], Location: [CITY]

Structure: H1, Hero, Hyperlocal content (landmarks, statistics, community), Service details, NAP block, Google Map, Local reviews, LocalBusiness schema, Internal links.
```

### NAP Consistency Audit
Inconsistent NAP weakens brickAndMortarStrength and entity recognition.

## Mobile SEO

### Mobile-First Signals
- isSmartphoneOptimized: Binary assessment
- isSmearedSignal: Desktop signals diluted if not mobile-optimized
- clutterScore: Stricter on mobile

### Mobile Optimization Checklist
1. Viewport meta tag
2. Responsive images (srcset, WebP/AVIF)
3. Tap targets ≥48px
4. Font size ≥16px
5. No horizontal scroll
6. Touch-friendly navigation
7. Critical CSS inline
8. Form optimization
9. Content parity with desktop

### Voice Search / AEO
```
Optimize for voice search:
1. FAQ section with conversational phrasing
2. 40-60 word featured snippet format answers
3. Natural language patterns (who/what/where/when/how/why)
4. Speakable schema
5. Factual accuracy
6. "Near me" variations for local
```

### AI Overviews / SGE Preparation
```
Requirements:
1. Clear factual answer in first 2 paragraphs
2. Structured data (FAQ, HowTo, Article)
3. Authoritative sourcing
4. Concise formatting
5. Entity-rich content
6. Unique data or perspective
7. E-E-A-T signals
```

## E-Commerce SEO

### Product Page Optimization
```
Generate:
1. Unique product description (300-500 words)
2. Product schema JSON-LD
3. FAQ section (3-5 questions)
4. Internal linking (category, related products, buying guide)
5. Meta title and description
```

### Category Page Strategy
- Balance SEO content with UX
- Intro text (100-200 words), filters, FAQ at bottom
- Faceted navigation: noindex filter combinations
- Schema: CollectionPage or ItemList

### E-Commerce Technical Essentials
- Out-of-stock: Keep indexed with "unavailable" + related products
- Seasonal: URL patterns that work year-round
- Variants: Canonical to main product
- Internal search: Noindex results pages

## Image SEO

### Semantic Alt-Attributes
- 120-150 characters, include primary entity, describe content, don't start with "Image of"

### Technical Requirements
- WebP/AVIF format, proper sizing, lazy loading, srcset, image sitemap, descriptive filenames

## Video SEO

### Video Key Moments
- Clip schema, SeekToAction schema, optimized title, description with timestamps, VideoObject JSON-LD

### Technical Requirements
- YouTube for indexing + embed on site for dwell time
- Provide transcript
- Video sitemap
- VideoObject schema mandatory

## Multimodal SEO
- 3D/AR: Describe in alt text, 3DModel schema
- Audio/Podcast: Audio maps, transcripts, PodcastEpisode schema
- Adaptive: Content adapts across smartwatch, mobile, desktop, VR
