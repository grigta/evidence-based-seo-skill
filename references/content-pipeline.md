# Content Pipeline & Semantic Cocoon

## The 4-Stage Content Pipeline

### Stage 0: System Configuration
- Define role: "You are an SEO content strategist specializing in [niche]"
- Set constraints: target language, tone, audience level, word count ranges
- Define output format: markdown, HTML, structured JSON
- Specify domain-specific terminology and entities
- Include anti-hallucination instruction

### Stage 1: Entity Collection
**Process:**
1. Analyze top 10-20 SERP results
2. Extract all named entities, concepts, and related terms
3. For each entity, determine: Salience score (0-1), midCount, Entity type, Knowledge Graph presence

**Entity Collection Prompt:**
```
Analyze the following topic: [TOPIC]

List all entities for comprehensive coverage.
For each: name, type, salience, related entities, expected context.
Focus on Knowledge Graph entities. Aim for 30-50 entities.
```

### Stage 2: Taxonomy Design
**3-Level Structure:**
- Level 1 — Target Pages (pillar/money pages)
- Level 2 — Mixed Pages (bridge commercial and informational)
- Level 3 — Support Pages (pure informational, long-tail)

**Taxonomy Prompt:**
```
Given these entities for [TOPIC]:
[ENTITY LIST]

Design a 3-level content taxonomy:
Level 1 (Target): 3-5 pages
Level 2 (Mixed): 8-15 pages
Level 3 (Support): 15-30 pages

For each page: title, primary keyword, search intent, key entities, internal linking targets.
```

### Stage 3: Content Generation + Validation
**Generation Rules:**
- Every entity from the plan must appear naturally
- Entity density should match top SERP competitors
- Use entities in headings, first paragraph, body, conclusion, meta description
- Include entity relationships
- Add original data to boost contentEffort

**Validation Prompt:**
```
Review content against entity plan:
Content: [CONTENT]
Required entities: [ENTITY LIST WITH SALIENCE]

Check: entity coverage, density, context, factual accuracy, content effort signals, Schema.org opportunities.
Output: coverage score (0-100) and improvement actions.
```

## Semantic Cocoon Architecture

### Entity Salience and TopicEmbeddings
- Salience > 0.7: Must be in title, H1, first paragraph
- Salience 0.3-0.7: In H2/H3 headings and body
- Salience < 0.3: Once or twice for depth

### midCount Optimization
- midCount > 15: Must include prominently
- midCount 5-15: Should include
- midCount < 5: Include for differentiation

### The 3-Level Hierarchy
```
Level 1: TARGET PAGES (Mother)
├── Level 2: MIXED PAGES (Daughter)
│   ├── Level 3: SUPPORT PAGES (Niece)
│   └── Level 3: SUPPORT PAGES (Niece)
└── Level 2: MIXED PAGES (Sister to Daughters)
```

### Matriarchal Linking Model
- Mother → Daughter: Passes authority, defines scope
- Daughter → Mother: Reinforces topical authority
- Sister ↔ Sister: Lateral coherence
- Daughter → Niece: Distributes PageRank
- Niece → Daughter: PageRank flow back up
- Niece → Mother: Strategic deep-to-shallow links

**Linking Rules:**
1. Every page: at least 2 internal links pointing to it
2. Anchor text: entity-rich, semantically relevant
3. Links within contextually relevant paragraphs
4. Clear hierarchy — no random cross-cluster linking
5. LinkValue = (PageRank of source × Anchor relevance) / Total outbound links

### Content Requirements by Level
**Level 1 (Target):** 2000-4000 words, all high-salience entities, commercial intent, 4-8 Daughter links
**Level 2 (Mixed):** 1500-2500 words, medium-salience entities, 1 Mother + 2-3 Sisters + 2-4 Nieces
**Level 3 (Support):** 800-1500 words, deep coverage of 1-2 entities, 1 Daughter + 1 Mother link

### Schema.org Integration
```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "mainEntity": {"@type": "[EntityType]", "name": "[Primary Entity]"},
  "about": [{"@type": "Thing", "name": "[Entity 2]"}],
  "author": {"@type": "Person", "name": "[Author]", "url": "[Author URL]"}
}
```

### TopicAuthority Audit
```
Audit semantic cocoon for topical authority:
Site: [URL], Topic cluster: [TOPIC]
Pages: [LIST WITH URLS, TITLES, ENTITIES]

Evaluate: entity coverage, hierarchy coherence, internal linking, gaps, cannibalization risk, siteFocusScore projection.
Output: TopicAuthority score (0-100) + prioritized improvements.
```

## Content Quality Signals

| Signal | How to optimize |
|--------|----------------|
| contentEffort | Original data, research, examples, multimedia |
| OriginalContentScore | Write from scratch, add unique analysis |
| goldmineBlockbertFactor | Each section should stand alone as valuable |
| avgTermWeight | Natural keyword distribution |
| EntityAnnotations | All target entities in proper context |

## Creativity Techniques

### Verbalized Sampling
Generate 5 angles, select the most original.

### Bias Breaking (6 techniques)
1. Reverse perspective
2. Temporal shift
3. Domain transfer
4. Constraint creativity
5. Audience shift
6. Devil's advocate

### Control Tokens
- P1: "CRITICAL:", "MANDATORY:", "MUST:"
- P2: "IMPORTANT:", "REQUIRED:"
- P3: "RECOMMENDED:", "PREFERRED:"
- P4: "OPTIONAL:", "CONSIDER:"

## The Master Prompt Structure (7 levels)
1. System role
2. Context
3. Task
4. Constraints
5. Format
6. Examples
7. Validation

## Entity Density Analysis
```
Target Density = (midCount of entity / total midCount) × 0.015
Example: midCount 20, total 200 → 0.15% → ~3 mentions in 2000 words
```

### Entity Relationship Mapping
- Hierarchical, Compositional, Temporal, Causal, Associative

## Cocoon Validation Metrics

| Metric | Target |
|--------|--------|
| Entity coverage | > 90% |
| Entity density alignment | < 10% variance |
| Linking structure | 100% matriarchal compliance |
| siteFocusScore | > 0.75 |
| Internal link anchors | > 80% entity-rich |
| Cannibalization | Zero |
| Content effort | > 3 original elements |
