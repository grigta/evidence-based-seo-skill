# Link Building & External Optimization

## How Google Evaluates Links

### Three-Tier Link Index
- **Tier 1**: Highest quality links. Fully crawled, indexed, and processed. Full PageRank and anchor signal transfer.
- **Tier 2**: Medium quality. Indexed but with reduced signal transfer.
- **Tier 3**: Lowest quality. Minimally processed. Spammy sources, link farms, PBN-like patterns.

### PageRank-NearestSeeds
- Google maintains a set of manually curated seed sites (high-trust domains)
- Your PageRank depends on how many link hops separate you from these seeds
- One link from a site close to seeds > many links from sites far from seeds

### Anchor Text in the ABC Model
- Must be diverse and natural-looking
- Over-optimization triggers anchorMismatchDemotion
- Ideal anchor distribution: ~30% branded, ~30% URL/naked, ~20% topical/LSI, ~15% generic, ~5% exact match

### anchorMismatchDemotion
Triggered when:
- Too many exact-match keyword anchors
- Anchor text doesn't match page content
- Sudden spikes in anchor patterns
- Mismatch between anchor profile and natural link growth pattern

### spamrank
Based on:
- Link graph patterns (reciprocal link networks, link wheels)
- Source site quality and patterns
- Velocity of link acquisition
- Association with known spam networks

## Donor Identification

### Semantic Role Analysis
```
Analyze this potential link donor:
Domain: [DONOR URL]
Our site topic: [YOUR TOPIC]

Evaluate:
1. Topical relevance
2. Entity overlap
3. Audience overlap
4. Link neighborhood
5. Semantic role
6. Risk assessment

Score: Relevance (1-10), Authority (1-10), Risk (1-10)
```

### Divergence Score
- Low divergence (0-0.3): Highly relevant donor
- Medium divergence (0.3-0.6): Related but not identical topic
- High divergence (0.6-1.0): Largely irrelevant
- Ideal: Mix of low and medium divergence donors

### 5 Latent Donor Techniques
1. **Semantic gap donors**: Sites covering adjacent topics lacking your expertise
2. **Entity co-occurrence donors**: Sites mentioning same entities without deep content
3. **Inference chain donors**: Sites where linking creates a logical information chain
4. **SCDL nodes**: Platforms forming your Semantic Content Distribution Layer
5. **Competitive displacement**: Sites linking to competitors' weak content

## Outreach Strategy

### Outreach Letter Framework
```
Subject: [SPECIFIC VALUE PROPOSITION]

Hi [NAME],

I noticed [SPECIFIC OBSERVATION about their content].
[ONE SENTENCE about what you/your site does]
[THE VALUE PROPOSITION: what's in it for them]
[SPECIFIC SUGGESTION: where/how the link would fit]
[SOFT CLOSE]
```

### Anchor Profile Balancing
```
Analyze the current anchor profile for [DOMAIN]:
[ANCHOR DATA]

Compare against ideal distribution:
- Branded: ~30%
- URL/naked: ~25-30%
- Topical/LSI: ~20%
- Generic: ~10-15%
- Exact match: ~5%

Identify over/under-represented types and suggest next 10 acquisitions.
```

## Link Building Techniques

### Broken Link Building (7-stage conveyor)
1. Archive Analysis
2. Topic Extraction
3. Structure Reconstruction
4. Actualization
5. Improved Structure
6. Donor Adaptation
7. Outreach

### Guest Posts (6 Advanced Techniques)
1. Data-driven guest posts
2. Expert roundup contributions
3. Case study partnerships
4. Tool/resource creation
5. Controversy/counterpoint posts
6. Series contributions

### PR Generation (5W Format)
- Who, What, When, Where, Why

### Crowdsourcing with Link Integration
- Industry surveys
- Expert quote collections
- Collaborative tools or calculators
- Community-driven content projects

## Competitive Link Analysis

### Inference Footprint Mapping
```
Analyze the backlink profile of [COMPETITOR URL]:
[BACKLINK DATA]

Map:
1. Entity associations from linking sites
2. Semantic role of each major linking domain
3. Content types attracting most links
4. Anchor text patterns
5. Gaps — authoritative sites that DON'T link to them
```

### Functional Link Decomposition
- **Authority links**: High-authority domains, passing PageRank
- **Topicality links**: Topically relevant, passing entity/topic signals
- **Traffic links**: High-traffic pages, driving referral visits
- **Brand links**: Mentions and branded anchors

## Risk Assessment

### Link Risk Signals
- Rapid velocity spikes
- Over-reliance on one anchor type
- Links from semantically irrelevant sites
- Links from high spamrank sites
- Reciprocal link patterns
- Geographic/language mismatch

### Semantic Echoes Detection
```
Review recently acquired links:
[LINK DATA]

Check for:
1. Unintended entity associations
2. Topic dilution
3. Context alignment
4. Confusion about site identity
```
