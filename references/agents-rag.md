# LLM Agents & RAG for SEO

## SEO Agent Architecture

An SEO agent consists of three core components:
- **LLM** (reasoning engine): Processes inputs, makes decisions, generates outputs
- **Memory**: Short-term (conversation context) + Long-term (vector DB with historical data, past analyses, site knowledge)
- **Tool Use**: API wrappers for SEO tools (GSC, GA4, crawlers, rank trackers, backlink analyzers)

### Agent Types

#### SEO Analyst Agent
- **Purpose**: Automated data analysis and reporting
- **Tools**: GSC API, GA4 API, rank tracking API
- **Workflow**: Collect data → analyze patterns → generate insights → recommend actions
- **Memory**: Previous reports, historical baselines, KPI targets

#### SEO Researcher Agent
- **Purpose**: SERP analysis, keyword research, competitive intelligence
- **Tools**: SERP scraping, keyword databases, backlink APIs
- **Workflow**: Query SERP → extract entities/features → cluster keywords → map intent → identify opportunities
- **Memory**: Keyword history, competitor profiles, industry benchmarks

#### SEO Copywriter Agent
- **Purpose**: Multi-step content creation following the content pipeline
- **Tools**: NLP analyzers, plagiarism checkers, readability scorers
- **Workflow (4 steps)**:
  1. **Outline**: Generate structure from entity research and SERP analysis
  2. **Draft**: Write content following entity coverage plan
  3. **Data injection**: Insert statistics, examples, original data points
  4. **SEO edit**: Optimize headings, meta tags, internal links, schema markup
- **Memory**: Brand voice guide, entity requirements, previously published content

#### SEO Auditor Agent
- **Purpose**: Technical and content audits
- **Tools**: Lighthouse API, log file parser, crawl tools, Core Web Vitals API
- **Workflow**: Crawl → collect signals → compare against checklist → prioritize issues → generate report
- **Memory**: Previous audit results, issue resolution history, dynamic checklists that update based on site evolution

### Agent Prompt Development

Use Chain of Thought before tool selection:
```
You are an SEO analyst agent. Before taking any action:

1. THINK: What is the user asking? What data do I need?
2. PLAN: Which tools should I use and in what order?
3. EXECUTE: Call the tools
4. ANALYZE: Interpret the results
5. RESPOND: Provide insights and recommendations

thought_process_guide:
- Always check if you already have the needed data in memory before calling a tool
- Prefer specific API calls over broad data pulls
- Cross-reference multiple data sources before drawing conclusions
- Flag low-confidence conclusions explicitly
```

### Self-Correction via Chain of Hindsight
After initial output, agents should self-correct:
```
Phase 1 — GENERATION
[Agent produces initial analysis/content]

Phase 2 — CRITIQUE
Review your output against:
- Data accuracy: Are all numbers traceable to source data?
- Completeness: Did you address all aspects of the query?
- Actionability: Can the user implement your recommendations?
- Bias: Did you over-weight any single data source?

Phase 3 — REFINEMENT
Based on critique, improve the output:
- Fix any data inaccuracies
- Add missing aspects
- Make recommendations more specific
- Balance data interpretation
```

### Multi-Step Chains

#### Keyword Research → Content Chain
```
Step 1: Keyword Research Agent
Input: Seed topic
Output: Keyword clusters with intent, volume, difficulty
→ Pass to Step 2

Step 2: Content Outline Agent
Input: Keyword clusters + SERP analysis
Output: Content plan with entity mapping
→ Pass to Step 3

Step 3: Content Drafting Agent
Input: Content plan + brand voice + entity requirements
Output: Draft content
→ Pass to Step 4

Step 4: SEO Review Agent
Input: Draft content + target keywords + competitor benchmarks
Output: Optimized content with meta tags, schema, internal links
```

### Memory Management

**Short-term memory** (context window):
- Current task parameters
- Active data being analyzed
- Recent tool outputs
- Conversation history

**Long-term memory** (vector DB):
- Site-specific knowledge (architecture, key pages, history)
- Historical performance data
- Previous analyses and their outcomes
- Brand guidelines and content standards
- Industry benchmarks and competitor profiles

Implementation:
```python
memory = {
    "short_term": {
        "current_task": "...",
        "active_data": {},
        "tool_outputs": []
    },
    "long_term": {
        "site_profile": "vector_db_collection:site_knowledge",
        "historical_data": "vector_db_collection:performance_history",
        "brand_voice": "vector_db_collection:brand_guidelines"
    }
}
```

### Tool Use with Typed JSON
Agent tools should have strict input/output schemas:
```json
{
  "tool_name": "gsc_query_analysis",
  "input_schema": {
    "site_url": "string",
    "date_range": {"start": "date", "end": "date"},
    "dimensions": ["query", "page", "country"],
    "filters": [{"dimension": "string", "operator": "string", "value": "string"}]
  },
  "output_schema": {
    "rows": [{"query": "string", "page": "string", "clicks": "int", "impressions": "int", "ctr": "float", "position": "float"}],
    "totals": {"clicks": "int", "impressions": "int"}
  }
}
```

### Deployment Architecture
For production SEO agents:
- **Containerization**: Docker for consistent environments
- **Orchestration**: Kubernetes for scaling
- **Task queues**: Celery + RabbitMQ (or Kafka for high throughput)
- **Monitoring**: Prometheus + Grafana dashboards for agent performance
- **Prompt versioning**: Git-tracked prompt files with version tags

## RAG (Retrieval-Augmented Generation) for SEO

### 3-Stage Architecture

```
Stage 1: RETRIEVAL
Query → Vector search → Top-k relevant chunks
- Use embeddings optimized for SEO content (domain-specific fine-tuning)
- Chunk size: 150-400 tokens (optimal for SEO context)
- Metadata enrichment: each chunk tagged with URL, date, topic, entities

Stage 2: AUGMENTATION
Retrieved chunks → Context assembly → Prompt construction
- Rank chunks by relevance score
- Deduplicate overlapping information
- Add source attribution (chunk IDs for traceability)

Stage 3: GENERATION
Augmented prompt → LLM → Grounded output
- Output includes source references
- Confidence scoring per claim
- Hallucination flagging for ungrounded statements
```

### SEO-Specific RAG Applications

#### Topical Authority via Proprietary Data
```
You are writing about [TOPIC].

Use ONLY the following proprietary data sources for facts and statistics:
[RETRIEVED CHUNKS from proprietary database]

For each claim:
- Cite the source chunk ID
- If no source supports a claim, mark it [NO SOURCE]
- Never extrapolate beyond what the sources state
```

#### Content Freshness with RAG
- Index new industry reports, statistics, and news
- Query RAG when updating existing content
- Flag outdated claims by comparing against fresh data

#### Competitive Intelligence RAG
- Index competitor pages, blog posts, product pages
- Query: "What are competitors saying about [TOPIC]?"
- Use insights to differentiate your content

### Chunking Strategy for SEO
```
Optimal chunking for SEO content:
- Chunk size: 150-400 tokens
- Overlap: 50-100 tokens between chunks
- Boundaries: Respect heading structure (don't split mid-section)
- Metadata per chunk:
  {
    "chunk_id": "unique_id",
    "source_url": "url",
    "heading_path": "H1 > H2 > H3",
    "entities": ["entity1", "entity2"],
    "topic": "topic_label",
    "date_indexed": "date",
    "word_count": int
  }
```

### Quality Assessment
```
Evaluate this RAG-generated content:

Content: [GENERATED TEXT]
Source chunks: [RETRIEVED CHUNKS with IDs]

Check:
1. Source fidelity: Is every claim traceable to a source chunk?
2. Hallucination detection: Are there claims not supported by any chunk?
3. Completeness: Did the generation use all relevant chunks?
4. Coherence: Does the output read naturally despite multiple sources?
5. Attribution accuracy: Are source references correctly placed?

Score: Grounding (0-100), Completeness (0-100), Coherence (0-100)
```

### Advanced RAG Patterns

#### CoT + RAG Synthesis
```
Step 1: Retrieve relevant chunks for [QUERY]
Step 2: For each chunk, extract key facts and assess relevance (1-10)
Step 3: Identify contradictions or gaps between chunks
Step 4: Synthesize a coherent answer, prioritizing higher-relevance chunks
Step 5: Add source attribution and confidence scores
```

#### Agentic RAG
```
You have access to a knowledge base via the retrieve() tool.

Before answering any factual question:
1. Decide if you need external knowledge (vs. using your training data)
2. If yes, formulate a precise retrieval query
3. Evaluate retrieved results — if insufficient, reformulate and retrieve again
4. Only then generate your answer with source attribution

Do NOT guess. If retrieve() returns no relevant results, say "I don't have data on this."
```

### Hybrid Search + Reranking
1. **Sparse retrieval** (BM25): Catches exact keyword matches
2. **Dense retrieval** (embeddings): Catches semantic similarity
3. **Hybrid fusion**: Combine scores from both (reciprocal rank fusion)
4. **Reranking**: Use a cross-encoder to rerank top candidates for final precision

## Prompt Evaluation for SEO

### Metrics
- **Relevance**: Does the output address the intended query/task?
- **Coherence**: Is the output well-structured and logical?
- **Completeness**: Are all required entities/topics covered?
- **Toxicity**: Is the content appropriate and unbiased?

### Hallucination Detection
Two-layer approach:
1. **Source-based**: Compare generated claims against provided source data
2. **External fact-checking**: Verify key statistics and claims against authoritative sources
- Assign criticality scores: Critical (factual claims that could cause harm if wrong), Medium (supporting details), Low (general statements)

### A/B Testing Prompts
- Route 50% of requests to Prompt A, 50% to Prompt B
- Measure: output quality scores, token usage, latency, user satisfaction
- Statistical significance: minimum 100 samples per variant

### Production Monitoring
- **Quality drift detection**: Track output quality metrics over time, alert on degradation
- **Cost alerts**: Monitor token usage per task type, flag anomalies
- **Feedback loops**: Direct (user ratings) + Indirect (behavioral signals like edit rate)
- **Iterative improvement cycle**: Measure → Analyze → Optimize → Validate
