---
layout: project
title: n8n Headhunter Workflow – LLM Agent for Candidate Search
date: 2025-10-01
tags: [n8n, LangChain, LLM Agent, Supabase, Apify, Automation, Recruitment Tech]
problem: "Traditional candidate sourcing is expensive (LinkedIn Recruiter costs $800+/month), slow (manual searches take hours), and opaque (hard to audit search decisions and understand why candidates were selected or rejected)"
approach: "Built an LLM-powered agent workflow that takes natural language queries, searches multiple data sources, enriches profiles, and returns top candidates in 2 minutes with full auditability"
url: /shiyao.me/projects/n8n-headhunter
metrics:
  - label: Search Time
    value: "2 min"
  - label: Cost per Profile
    value: "$0.05"
  - label: Accuracy Improvement
    value: "20%"
  - label: Pipeline Auditability
    value: "90%"
  - label: Database Size
    value: "200M+"
cover_image: /assets/images/n8n-headhunter-cover.png
---

## Overview

An intelligent recruitment automation system built on n8n that uses LLM agents to transform natural language hiring requirements into structured candidate searches, automatically enriching profiles from multiple sources and providing full transparency into search decisions.

## The Problem

### Traditional Recruitment Challenges

**High Cost:**
- LinkedIn Recruiter: $800+ per month per seat
- Additional sourcing tools: hundreds more
- Scale limitations based on budget
- Expensive for startups and small teams

**Time-Intensive Process:**
- Manual searches take hours
- Repetitive filtering and screening
- Multiple platform switching
- Difficult to maintain consistency

**Lack of Transparency:**
- Black-box search algorithms
- Can't audit why candidates were selected
- Difficult to reproduce searches
- No insight into decision-making process

**Data Quality Issues:**
- Stale profile information
- Incomplete data across platforms
- Manual enrichment required
- Inconsistent data formats

## The Solution

### Intelligent Agent-Based Search

**Natural Language to Structured Search:**

**Example Query:**
```
"Find senior full-stack engineers in Singapore with 
React and Node.js experience, preferably from tech 
startups, who have worked on B2B SaaS products"
```

**Agent Processing:**
1. **Parse**: Extract requirements (skills, location, experience, industry)
2. **Structure**: Convert to database filters and search queries
3. **Search**: Query multiple data sources in parallel
4. **Enrich**: Gather additional profile information
5. **Validate**: Check candidates against criteria
6. **Rank**: Order by relevance
7. **Return**: Top 20 candidates with full audit trail

**Time:** Average 2 minutes from query to results

### Multi-Source Search Strategy

**Primary Source: People Dataset (200M+ entries)**

**Fast Filter-Based Retrieval:**
- Structured data queries
- 5-10 seconds per batch
- High-quality baseline data
- Supports complex filtering

**Supplementary: Web Search**

**Google Search (via Serper):**
- Fresh, real-time results
- Finds profiles not in dataset
- LinkedIn dorking techniques
- Cost-effective coverage

**Yahoo Search:**
- Parallel search for broader coverage
- Alternative perspective
- Redundancy and validation
- Extended reach

**Apify Enrichment:**
- Profile detail extraction
- LinkedIn data scraping
- Contact information discovery
- $0.05 per profile cost

**Combined Approach Benefits:**
- Fast initial results from database
- Comprehensive coverage from web search
- Fresh data from recent updates
- Cost-optimized sourcing

### LangChain-Stabilized Tool Calling

**Problem with Standard LLM Agents:**
- Random early termination
- Inconsistent tool usage
- Failure to complete search criteria
- Unpredictable behavior

**LangChain Code Node Implementation:**

**Ensures Agent Loops Until:**
- Target number of candidates found
- All search sources exhausted
- Explicit completion criteria met
- No valid candidates remain

**Stability Improvements:**
- 20% accuracy improvement
- Consistent search completion
- Reliable result counts
- Predictable execution

**Technical Approach:**
```python
# Conceptual implementation
while len(candidates) < target_count and not exhausted:
    # Agent tool calling
    results = agent.run(search_query)
    
    # Validation
    validated = validate_candidates(results)
    
    # Accumulation
    candidates.extend(validated)
    
    # Progress tracking
    log_progress(candidates, target_count)
```

### Full Auditability with Supabase Logging

**Every Agent Action Logged:**

**Tracked Events:**
- Search queries executed
- Data sources accessed
- Validation decisions
- Accept/reject reasons
- Enrichment steps
- Ranking criteria

**Logged to Supabase:**
- Real-time database writes
- Structured event data
- Timestamp tracking
- Session correlation

**Webhook Exposure for Live Progress UI:**

**Solves "Why is Nothing Happening?" Problem:**

**Live Progress Dashboard Shows:**
- Current search phase
- Candidates found so far
- Sources being queried
- Validation in progress
- Estimated time remaining

**Benefits:**
- User confidence during wait time
- Transparency into process
- Debugging capability
- Performance monitoring
- 90% pipeline auditability

**Example Progress Updates:**
```
[12:00:01] Parsing query...
[12:00:02] Searching database for 'React' + 'Singapore'...
[12:00:08] Found 45 candidates in database
[12:00:09] Launching Google search...
[12:00:15] Enriching top 30 profiles via Apify...
[12:00:45] Validating against criteria...
[12:01:23] Ranking by relevance...
[12:01:30] Top 20 candidates ready
```

## Architecture

### Workflow Components

**n8n Orchestration:**
```
Trigger (Natural Language Query)
    ↓
LLM Parser (Extract Requirements)
    ↓
Parallel Search Branches:
    ├─ Database Query (200M+ profiles)
    ├─ Google Search (via Serper)
    └─ Yahoo Search
    ↓
Result Aggregation
    ↓
Apify Enrichment ($0.05/profile)
    ↓
LangChain Agent Validation
    ↓
Supabase Logging + Webhook
    ↓
Ranking & Filtering
    ↓
Top 20 Candidates Output
```

### Technology Stack

**Automation Platform:**
- **n8n**: Workflow orchestration
- **LangChain Code Nodes**: Agent logic
- **Webhooks**: API endpoints

**Data Sources:**
- **People Dataset**: 200M+ profile database
- **Google Search**: Serper API
- **Yahoo Search**: Direct API
- **LinkedIn**: Via Apify scraping

**Storage & Logging:**
- **Supabase**: Event logging and progress tracking
- **PostgreSQL**: Candidate storage
- **Vector Database**: (Planned) Semantic search

**LLM & AI:**
- **OpenAI GPT**: Query parsing and validation
- **LangChain**: Agent framework
- **Embeddings**: (Planned) Semantic matching

### Search Pipeline

**Phase 1: Query Understanding**
- Natural language input
- LLM extracts structured requirements
- Validation of search criteria

**Phase 2: Multi-Source Search**
- Database: Fast structured queries
- Google: Fresh public profiles
- Yahoo: Extended coverage
- Parallel execution for speed

**Phase 3: Profile Enrichment**
- Apify LinkedIn scraping
- Contact information discovery
- Experience validation
- Skill verification

**Phase 4: Validation & Filtering**
- LangChain agent evaluates candidates
- Checks against original requirements
- Logs accept/reject decisions
- Maintains audit trail

**Phase 5: Ranking & Delivery**
- Relevance scoring
- Experience weighting
- Recency consideration
- Top 20 selection

## Key Features

### 1. Natural Language Queries
- Conversational search input
- No need to learn query syntax
- Flexible requirement expression
- Context understanding

### 2. Multi-Source Intelligence
- 200M+ profile database
- Real-time web search
- LinkedIn enrichment
- Comprehensive coverage

### 3. Cost Optimization
- $0.05 per enriched profile
- Free database queries
- Efficient API usage
- Massive savings vs. LinkedIn Recruiter

### 4. Stable Agent Execution
- LangChain-powered reliability
- Guaranteed completion
- Consistent behavior
- 20% accuracy improvement

### 5. Full Auditability
- Complete action logging
- Decision transparency
- Reproducible searches
- Performance analytics

### 6. Live Progress Tracking
- Real-time status updates
- Webhook-powered UI
- User confidence
- 90% pipeline visibility

## Performance Metrics

**Speed:**
- Average search time: 2 minutes
- Database queries: 5-10 seconds
- Enrichment: 30-60 seconds
- Total end-to-end: ~2 minutes

**Cost:**
- Profile enrichment: $0.05 each
- Monthly cost: Fraction of LinkedIn Recruiter
- Scalable pricing model
- Transparent cost tracking

**Accuracy:**
- 20% improvement with LangChain stabilization
- Consistent result quality
- Reliable candidate matching
- Reproducible searches

**Coverage:**
- 200M+ profiles in database
- Unlimited web search results
- Fresh data via Apify
- Comprehensive candidate pool

**Transparency:**
- 90% pipeline auditability
- Complete action logs
- Decision explanations
- Search reproducibility

## Use Cases

### 1. Startup Recruiting
- Cost-effective sourcing
- Fast candidate discovery
- Flexible search criteria
- No expensive subscriptions

### 2. Agency Recruiting
- Batch candidate searches
- Multi-client support
- Transparent reporting
- Scalable operations

### 3. Internal HR
- Talent pipeline building
- Proactive sourcing
- Market research
- Competitive intelligence

### 4. Freelance Recruiters
- Low barrier to entry
- Pay-per-use model
- Professional results
- Client transparency

## Future Development

**Planned Enhancements:**

### Semantic Search & RAG
- Vector embeddings for profiles
- Natural language matching
- Beyond keyword search
- Contextual understanding

### Stored Profile Intelligence
- Historical search results
- Profile versioning
- Trend analysis
- Relationship mapping

### Advanced Filtering
- Culture fit scoring
- Salary expectation matching
- Availability detection
- Geographic optimization

### Integration Expansion
- ATS integration
- Email outreach automation
- Interview scheduling
- CRM synchronization

### Machine Learning
- Ranking optimization
- Success prediction
- Preference learning
- Automated improvement

## Technical Insights

### LangChain Agent Design

**Tool Calling Stability:**
- Explicit loop conditions
- Progress validation
- Error recovery
- State management

**Decision Logging:**
- Structured event format
- Timestamp precision
- Context preservation
- Audit trail maintenance

### n8n Workflow Patterns

**Parallel Execution:**
- Simultaneous source queries
- Race condition handling
- Result aggregation
- Error tolerance

**Webhook Architecture:**
- Real-time updates
- Client subscriptions
- Event streaming
- Progress broadcasting

### Data Pipeline Optimization

**Batch Processing:**
- Efficient API usage
- Rate limit management
- Cost optimization
- Performance tuning

**Caching Strategy:**
- Frequent query results
- Profile data persistence
- Search result storage
- Update scheduling

## Impact

**For Recruiters:**
- Dramatically reduced costs (vs. $800+/month)
- Faster candidate sourcing (2 min vs. hours)
- Complete search transparency
- Reproducible results

**For Candidates:**
- Discoverable through multiple channels
- Fresh profile data considered
- Fair evaluation criteria
- Transparent selection process

**For Organizations:**
- Scalable recruitment operations
- Data-driven decision making
- Cost predictability
- Process standardization

## Technologies Used

**Automation:**
- n8n workflow platform
- LangChain agent framework
- Webhook integrations

**Data Sources:**
- 200M+ profile database
- Google Search (Serper API)
- Yahoo Search
- Apify LinkedIn scraping

**Storage:**
- Supabase PostgreSQL
- Event logging system
- Real-time databases

**AI/ML:**
- OpenAI GPT models
- Natural language processing
- Future: Vector embeddings

## Conclusion

The n8n Headhunter Workflow demonstrates how LLM agents, combined with multi-source data aggregation and complete auditability, can transform recruitment from an expensive, opaque manual process into a fast, transparent, and cost-effective automated system. The 90% auditability and live progress tracking set new standards for recruitment technology transparency.
