---
name: evidence-based-seo
description: >
  Evidence-Based SEO methodology from DrMax 2026 — a comprehensive system for SEO strategy,
  audits, content creation, semantic architecture, link building, technical optimization, and
  analytics, all grounded in Google's actual ranking signals from the 2024 API leak. Use this
  skill whenever the user asks about SEO strategy, site audits, keyword research, content
  optimization, semantic cocoons, link building, technical SEO, local SEO, e-commerce SEO,
  SERP analysis, E-E-A-T, Core Web Vitals, or any search engine optimization task. Also
  triggers on: "organic traffic", "ranking", "Google signals", "PageRank", "NavBoost",
  "anchor text", "topical authority", "content cluster", "internal linking", "site architecture",
  "SEO audit", "search visibility", "SERP features", "AI Overviews", "SGE", "AEO",
  "schema markup", "structured data". Use this even for tangentially related queries like
  "how to get more website visitors" or "improve my site's Google performance".
---

# Evidence-Based SEO 2026 (DrMax Methodology)

## Core Philosophy: Architectural Alignment

The central idea is **Architectural Alignment** — building your digital assets to structurally match how Google actually collects, stores, and evaluates information. Instead of chasing algorithm updates, you align your site's architecture with Google's internal data structures and ranking pipeline. This makes your site inherently compatible with how Google works, producing durable results.

## Google's Ranking Pipeline (simplified)

Understanding the pipeline helps you know *where* each optimization has its effect:

1. **Crawling & Indexing** (Alexandria/SegIndexer) → your page enters the index
2. **Initial Retrieval** (Mustang) → candidate selection based on topicality signals (T*)
3. **Quality Scoring** → quality signals (Q*) applied: siteAuthority, NSR, Panda
4. **User Signal Re-ranking** (NavBoost) → popularity signals (P*): clicks, dwell time
5. **Final Adjustments** (Twiddlers) → freshness, diversity, personalization, demotion filters

Every page Google processes becomes a **CompositeDoc** containing **PerDocData** — the collected signals about that document. Your job is to make every signal in PerDocData as strong as possible.

## The Three Signal Pillars: Q* · P* · T*

All Google ranking signals fall into three categories. Read `references/google-signals.md` for the full signal catalog with field names from the API leak.

| Pillar | What it measures | Key signals |
|--------|-----------------|-------------|
| **Q* (Quality)** | Site/page trustworthiness | siteAuthority, predictedDefaultNsr, pandaDemotion, lowQuality, clutterScore, contentEffort, OriginalContentScore |
| **P* (Popularity)** | Real user engagement | chromeInTotal, NavBoost (goodClicks, badClicks, lastLongestClicks), clickstream data |
| **T* (Topicality)** | Relevance to query | ABC signals (Anchors, Body, Clicks), siteFocusScore, siteRadius, site2vecEmbedding, EntityAnnotations |

## Workflow: How to Use This Skill

When approaching any SEO task, follow this decision tree:

### 1. Understand the Situation
- What type of site? (e-commerce, content, local business, SaaS, news)
- What's the current state? (new site, established, penalized, redesign)
- What's the goal? (traffic growth, conversions, brand visibility, local presence)

### 2. Choose the Right Reference
This skill has detailed reference files for each major area. Read the relevant one(s) before producing output:

| Task | Reference file |
|------|---------------|
| Understanding Google's internal signals | `references/google-signals.md` |
| Content strategy, semantic cocoons, entity optimization | `references/content-pipeline.md` |
| Technical audits, CWV, crawling, JS SEO, mobile | `references/technical-seo.md` |
| Link building, outreach, anchor profiles, donors | `references/link-building.md` |
| GA4/GSC analysis, anomaly detection, forecasting | `references/analytics-llm.md` |
| Ready-to-use professional prompt templates | `references/prompt-templates.md` |
| Building SEO agents, RAG pipelines, automation | `references/agents-rag.md` |
| Local SEO, mobile, e-commerce, video, image verticals | `references/local-mobile-verticals.md` |

### 3. Apply the Methodology
Every recommendation should be traceable to a specific Google signal. Don't just say "write quality content" — explain *which* signal you're targeting (e.g., "increase contentEffort by adding original research data, which feeds OriginalContentScore").

### 4. Validate with the Quality Cycle
After implementation, verify results through the **Quality Cycle**:
- Monitor Q* signals (site authority trends, Core Web Vitals)
- Track P* signals (CTR changes, behavioral metrics in GA4)
- Measure T* signals (keyword coverage, entity recognition, topical authority)

## E-E-A-T Mapping to Signals

E-E-A-T is not abstract — each component maps to concrete Google signals:

- **Experience** → contentEffort, OriginalContentScore, firsthand data signals
- **Expertise** → authorReputationScore, authorObfuscatedGaiaStr, topical entity density
- **Authoritativeness** → siteAuthority, PageRank-NearestSeeds, chromeInTotal, queriesForWhichOfficial
- **Trustworthiness** → predictedDefaultNsr (Normalized Site Rank), pandaDemotion absence, lowQuality absence, spamrank

## Content Strategy: The Semantic Cocoon

The **Semantic Cocoon** is the central content architecture methodology. It organizes content into a 3-level entity-driven hierarchy with strategic internal linking. Read `references/content-pipeline.md` for the full methodology including:

- Entity collection and salience scoring
- Taxonomy design (Target → Mixed → Support pages)
- Matriarchal linking model (Mother/Daughter/Sister/Niece)
- Content generation pipeline with validation
- Schema.org integration patterns
- TopicAuthority audit prompts

## The Content Pipeline (4 Stages)

For any content creation task, follow this pipeline:

- **Stage 0**: System configuration (role, constraints, output format)
- **Stage 1**: Entity collection from SERP analysis (entities, salience, midCount)
- **Stage 2**: Taxonomy design (cluster structure, hierarchy levels)
- **Stage 3**: Content generation + validation (write → check entity coverage → verify no hallucinations)

## Technical SEO Essentials

Read `references/technical-seo.md` for complete checklists. Key areas:
- Crawl budget optimization (robots.txt, Sitemap.xml architecture)
- Core Web Vitals (LCP, INP, CLS) mapped to Google's clutterScore and quality signals
- URL architecture aligned with Google's SegIndexer
- Canonicalization strategy
- Mobile-first (isSmartphoneOptimized, isSmearedSignal)
- JS SEO considerations
- Latent optimization techniques (Entity Shadow Audit, Inference Path Engineering)

## Link Strategy

Read `references/link-building.md` for the complete system. Core principles:
- Links are evaluated through a 3-tier link index system
- PageRank-NearestSeeds measures authority proximity to seed sites
- Anchor text influences T* through the ABC model (Anchors component)
- anchorMismatchDemotion penalizes unnatural anchor patterns
- Donor quality assessed via semantic role analysis and divergence scoring

## Brand & SERP Management

Brand signals are among the strongest ranking factors:
- **chromeInTotal** — direct visits from Chrome (P* signal, hard to manipulate)
- **queriesForWhichOfficial** — branded query recognition
- Build brand through consistent NAP, PR, social signals, and direct traffic campaigns

## Long-Term Strategy Concepts

- **Canonical Source of Truth** — become THE authoritative resource for your topic
- **SCDL (Semantic Content Distribution Layer)** — distribute semantic authority across platforms
- **Cyborg Method** — combine AI efficiency with human expertise for content at scale
- **Quality Cycle** — continuous measurement → analysis → optimization → validation

## Key Anti-Patterns (Things That Trigger Demotions)

- Thin content → pandaDemotion, lowQuality flag
- Keyword stuffing → avgTermWeight anomalies
- Unnatural anchors → anchorMismatchDemotion, spamrank
- Interstitials/clutter → clutterScore, adsDensityInterstitialViolationStrength
- Duplicate content → canonicalization issues in SegIndexer
- Ignoring mobile → isSmartphoneOptimized=false triggers isSmearedSignal

## Output Guidelines

When producing SEO deliverables:

1. **Always cite the specific Google signal** being targeted by each recommendation
2. **Prioritize by impact**: Q* foundation first, then T* topicality, then P* engagement
3. **Be actionable**: every recommendation should have a clear implementation step
4. **Use the book's prompt templates** from `references/prompt-templates.md` when generating content, audits, or analyses
5. **Validate**: include a validation step in any content or technical output
6. **Think architecturally**: individual page optimization matters less than site-wide structural alignment with Google's systems
