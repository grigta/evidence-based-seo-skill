# Professional Prompt Templates for SEO

## RGC-F Prompt Model
- **R (Role)**: Who the LLM is
- **G (Goal)**: What needs to be accomplished
- **C (Context)**: Background information, data, constraints
- **F (Format)**: Expected output structure

## Prompting Methodologies

### Zero-Shot
```
Classify this query's search intent: "[QUERY]"
Output: Informational, Commercial, Transactional, or Navigational
```

### Few-Shot
```
"best running shoes 2026" → Commercial
"buy Nike Air Max" → Transactional
"how to tie running shoes" → Informational
Now classify: "[QUERY]"
```

### Chain of Thought (CoT)
```
Analyze ranking potential step by step:
1. Identify target query and intent
2. Evaluate content coverage vs competitors
3. Assess technical factors
4. Consider authority and link signals
5. Final assessment with confidence score
```

### Tree of Thought (ToT)
```
Improve rankings for [KEYWORD]. Consider three paths:
Path A: Content expansion
Path B: Technical optimization
Path C: Link building
Evaluate each: effort, timeline, risk, impact.
Recommend optimal combination.
```

## Professional Prompt 10.1: Visual Hierarchy Audit
```
Role: UX/SEO visual analyst
Input: [SCREENSHOT or URL]

BLOCK 1 — VISUAL HIERARCHY (eye flow, focal points, conversion guidance)
BLOCK 2 — TYPOGRAPHY & READABILITY (fonts, heading hierarchy, spacing, contrast)
BLOCK 3 — CTA ANALYSIS (visibility, contrast, copy, above-fold presence)
BLOCK 4 — MOBILE-FIRST (tap targets, reflow, above-fold content, loading priority)
BLOCK 5 — FIRST 3 SECONDS UX (immediate understanding, value proposition, intent match, trust)

Output: Scores (1-10) per block + prioritized fixes.
```

## Professional Prompt 10.2: Internal Linking Matrix
```
Role: SEO internal linking architect
Input: URLs with titles and target keywords

Generate CSV: Source URL | Source Title | Anchor Text | Target URL | Target Title | Link Type | Priority

Rules:
- LSI-based anchor phrases
- Matriarchal model
- Every page ≥2 incoming links
- No page >7 outbound links in cluster
- Report orphan pages, over-linked pages, missing connections
```

## Professional Prompt 10.3: Mixed Intent Analysis
```
Role: Search intent analyst
Input: [PAGE] + [TARGET QUERY]

Step 1 — VISUAL ANALYSIS (images, layout, CTAs)
Step 2 — TEXT ANALYSIS (headings, body, meta)
Step 3 — INTENT SYNTHESIS (visual vs textual alignment)
Step 4 — CLASSIFICATION (primary/secondary intent + confidence)
Step 5 — CONTENT RECOMMENDATIONS (visual + content + schema + linking changes)
```

## Professional Prompt 10.4: Article Weakness Finder
```
Role: Content gap analyst
Input: [ARTICLE]

Step 1 — CONTEXTUAL UNDERSTANDING
Step 2 — FACTUAL OMISSIONS (missing data, underrepresented entities)
Step 3 — SOURCE GAPS (uncited claims, missing evidence)
Step 4 — CONTROVERSIAL OR WEAK CONCLUSIONS
Step 5 — OUTREACH HOOKS (3-5 ready-to-use hooks for link building)
```

## Professional Prompt 10.5: Competitor Anchor Profile Analysis
```
Role: Link intelligence analyst
Input: [COMPETITOR BACKLINK DATA]

Step 1 — NORMALIZATION
Step 2 — CLASSIFICATION (Branded, URL, Exact, Partial, LSI, Generic, Image)
Step 3 — COMMERCIALIZATION INDEX (% commercial keyword anchors)
Step 4 — MANIPULATIVE PATTERN DETECTION (PBN, velocity anomalies, clustering)
Step 5 — SYNTHESIS (health score 0-100, risks, strengths)
Step 6 — RECOMMENDATIONS (anchor types to pursue/avoid, content strategies)
```

## Professional Prompt 10.6: Broken Link Building Strategy
```
Role: BLB strategist
Input: [BROKEN LINK DATA]

Stage 1 — ARCHIVE ANALYSIS
Stage 2 — TOPIC EXTRACTION
Stage 3 — STRUCTURE RECONSTRUCTION
Stage 4 — ACTUALIZATION (update for 2026)
Stage 5 — IMPROVED STRUCTURE
Stage 6 — DONOR ADAPTATION
Stage 7 — OUTREACH DRAFT (personalized, <150 words)

Output: Complete BLB campaign brief.
```
