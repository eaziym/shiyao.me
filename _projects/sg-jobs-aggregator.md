---
layout: project
title: SG Jobs Aggregator – Data Integration Platform
date: 2025-10-01
tags: [n8n, Web Scraping, Data Pipeline, Python, GitHub Pages, Automation]
problem: "Singapore job seekers face fragmented job listings across hundreds of company career sites with no centralized, up-to-date aggregation platform specific to Singapore market"
approach: "Built 20+ n8n workflows to scrape, normalize, and aggregate 4,000+ job listings in 20 minutes, deployed as an automated daily data platform on GitHub Pages"
url: /shiyao.me/projects/sg-jobs
demo_url: "https://eaziym.github.io/sg-jobs"
external_links:
  - label: "Live Site"
    url: "https://eaziym.github.io/sg-jobs"
  - label: "GitHub"
    url: "https://github.com/eaziym/sg-jobs"
metrics:
  - label: Total Listings
    value: "4,000+"
  - label: Workflows
    value: "20+"
  - label: Scraping Time
    value: "20 min"
  - label: Update Frequency
    value: "Daily"
cover_image: /assets/images/sg-jobs-cover.png
---

## Overview

SG Jobs Aggregator is a comprehensive data integration platform that automatically scrapes, normalizes, and publishes Singapore job listings from 20+ company career sites. Built entirely on n8n workflows, it demonstrates end-to-end data engineering from heterogeneous sources to a clean, user-friendly web interface.

## The Problem

### Fragmented Job Market

**Scattered Listings:**
- Each company maintains own career site
- No standard format or structure
- Different application processes
- Varying update frequencies

**Time-Consuming Search:**
- Job seekers visit dozens of sites manually
- Difficult to track new postings
- Miss opportunities between visits
- Repetitive checking across platforms

**Existing Solutions Fall Short:**
- General job boards miss company-specific listings
- Paid aggregators focus on global markets
- Singapore-specific sites incomplete
- No automation for updates

**Data Heterogeneity:**
- Different HTML structures per site
- Various API formats
- Inconsistent metadata
- Diverse categorization schemes

## The Solution

### Comprehensive n8n Workflow System

**20+ Custom Workflows:**

Each workflow tailored to specific company:
- Custom HTML parsers
- API integrations
- Data extraction logic
- Error handling
- Rate limiting

**Supports Multiple Source Types:**
- Static HTML career pages
- Dynamic JavaScript-rendered sites
- REST APIs
- GraphQL endpoints
- RSS/Atom feeds

### End-to-End Data Platform

**Complete Pipeline Architecture:**

```
Information Gathering
        ↓
Data Cleaning & Normalization
        ↓
Database Insert
        ↓
JSON Generation
        ↓
index.html Generation
        ↓
GitHub Pages Deployment
```

**Fully Automated:**
- Scheduled daily executions
- No manual intervention
- Automatic error recovery
- Self-healing workflows

### Fast Aggregation

**Performance Metrics:**
- **4,000+ listings** aggregated
- **20 minutes** total execution time
- **20+ workflows** run in parallel
- **Daily updates** automatically scheduled

**Optimization Strategies:**
- Parallel workflow execution
- Efficient scraping patterns
- Smart rate limiting
- Incremental updates

## Technical Implementation

### Phase 1: Information Gathering

**Web Scraping Techniques:**

**For Static Sites:**
```javascript
// n8n HTTP Request + HTML Extract
GET company-careers-url
→ Parse HTML
→ Extract job listings
→ Structure data
```

**For Dynamic Sites:**
- JavaScript rendering
- API endpoint discovery
- XHR request interception
- JSON data extraction

**For API-First Companies:**
- REST API integration
- Authentication handling
- Pagination logic
- Response parsing

**Challenges Solved:**
- Anti-scraping measures
- Rate limiting
- Dynamic content loading
- Authentication requirements
- CAPTCHA avoidance

### Phase 2: Data Cleaning & Normalization

**Heterogeneous Data → Unified Schema:**

**Standardized Fields:**
```json
{
  "company": "string",
  "title": "string",
  "location": "string",
  "type": "Full-time | Part-time | Contract | Internship",
  "category": "Engineering | Sales | Marketing | ...",
  "applyUrl": "string",
  "postedDate": "ISO 8601",
  "description": "string",
  "metadata": {}
}
```

**Normalization Steps:**
1. **Title Cleaning**: Remove company names, standardize formats
2. **Location Parsing**: Extract city, country, remote status
3. **Type Classification**: Map various terms to standard types
4. **Category Inference**: Classify by keywords and patterns
5. **Date Standardization**: Convert to consistent format
6. **URL Validation**: Ensure valid application links

**Data Quality:**
- Deduplication logic
- Validation rules
- Completeness checks
- Consistency enforcement

### Phase 3: Database Management

**Supabase PostgreSQL:**

**Schema Design:**
```sql
CREATE TABLE jobs (
  id SERIAL PRIMARY KEY,
  company VARCHAR(255),
  title TEXT,
  location VARCHAR(255),
  type VARCHAR(50),
  category VARCHAR(100),
  apply_url TEXT,
  posted_date TIMESTAMP,
  description TEXT,
  metadata JSONB,
  scraped_at TIMESTAMP,
  updated_at TIMESTAMP
);
```

**Operations:**
- Upsert logic (insert or update)
- Historical tracking
- Expired job removal
- Performance indexing

### Phase 4: Output Generation

**Multi-Format Export:**

**JSON API:**
```json
{
  "lastUpdated": "2025-12-01T08:00:00Z",
  "totalJobs": 4127,
  "companies": 23,
  "jobs": [...]
}
```

**Static HTML:**
- Searchable table interface
- Filter by company, type, category
- Sort by date, company, title
- Responsive design
- Fast client-side operations

**GitHub Pages Deployment:**
- Automatic git commits
- Static site generation
- CDN distribution
- Zero hosting cost

### Phase 5: Orchestration & Scheduling

**n8n Cron Triggers:**
- Daily execution at 8 AM SGT
- Parallel workflow launches
- Result aggregation
- Error notifications

**Workflow Dependencies:**
```
Scraping Workflows (parallel)
        ↓
Aggregation Workflow
        ↓
Cleaning Workflow
        ↓
Database Workflow
        ↓
Generation Workflow
        ↓
Deployment Workflow
```

**Error Handling:**
- Retry logic for failed scrapes
- Fallback data sources
- Alert notifications
- Manual intervention triggers

## n8n Workflow Architecture

### Individual Company Workflows

**Template Structure:**

**Nodes:**
1. **Schedule Trigger**: Cron-based execution
2. **HTTP Request**: Fetch career page/API
3. **Data Extraction**: Parse HTML or JSON
4. **Transformation**: Normalize to schema
5. **Validation**: Check data quality
6. **Database Insert**: Upsert to Supabase
7. **Error Handler**: Log and notify failures

**Example: Tech Company API Workflow**
```
Cron Trigger (daily 8am)
    ↓
HTTP Request → GET /api/jobs
    ↓
JSON Parse → Extract jobs array
    ↓
Loop → For each job
    ↓
Transform → Map to standard schema
    ↓
Validate → Check required fields
    ↓
Supabase → Upsert job record
    ↓
Success/Error notification
```

### Aggregation Workflow

**Combines All Sources:**

**Process:**
1. Wait for scraping workflows to complete
2. Query Supabase for all recent jobs
3. Apply global deduplication
4. Generate aggregated JSON
5. Build static HTML
6. Commit to GitHub
7. Trigger Pages deployment

## Data Pipeline Features

### 1. Automatic Deduplication

**Strategies:**
- URL-based matching
- Fuzzy title comparison
- Company + title + location combo
- Temporal proximity checks

**Prevents:**
- Duplicate listings
- Data bloat
- User confusion
- Processing overhead

### 2. Category Classification

**Intelligent Categorization:**
- Keyword-based classification
- Job title analysis
- Description NLP (planned)
- Company industry mapping

**Categories:**
- Engineering
- Data & Analytics
- Sales & Business Development
- Marketing
- Operations
- Finance
- Human Resources
- Customer Success
- Design
- Product Management

### 3. Link Validation

**Ensures Quality:**
- HTTP status checks
- Redirect following
- Dead link removal
- Canonical URL resolution

**User Experience:**
- No broken application links
- Direct to actual job page
- Tracked click-throughs
- Working apply buttons

### 4. Weekly Update Automation

**Scheduled Maintenance:**
- Remove expired listings
- Refresh active jobs
- Update company data
- Regenerate outputs
- Performance optimization

## Key Features

### User-Facing

**Job Seeker Benefits:**
- 4,000+ current listings
- Daily updates
- Single search location
- Fast filtering
- Direct application links
- Mobile-responsive

**Search Capabilities:**
- Full-text search
- Company filter
- Job type filter
- Category filter
- Location filter
- Date sorting

### Technical

**Data Engineering:**
- ETL pipeline automation
- Multi-source integration
- Real-time processing
- Scalable architecture

**Reliability:**
- Error recovery
- Data validation
- Monitoring alerts
- Uptime tracking

**Performance:**
- 20-minute full refresh
- Parallel processing
- Efficient storage
- Fast page loads

## Impact & Metrics

**Coverage:**
- **20+ companies** tracked
- **4,000+ active listings**
- **Daily updates** guaranteed
- **Comprehensive** Singapore market

**Performance:**
- **20 minutes** full aggregation
- **Daily** automatic execution
- **Zero manual** intervention
- **Self-healing** workflows

**Cost:**
- **$0** hosting (GitHub Pages)
- **Minimal** compute (n8n cloud free tier)
- **Low** API costs
- **High** value delivery

**User Value:**
- Single source for SG jobs
- Time saved vs. manual search
- Never miss new postings
- Clean, organized interface

## Use Cases

### 1. Active Job Seekers
- Daily check for new listings
- Filter by preferences
- Track application progress
- Market research

### 2. Career Explorers
- Survey available opportunities
- Understand market demand
- Identify growing companies
- Salary research

### 3. Recruiters
- Competitive intelligence
- Market mapping
- Company tracking
- Candidate sourcing

### 4. Data Analysts
- Job market trends
- Hiring patterns
- Skill demand analysis
- Economic indicators

## Technical Challenges & Solutions

### Challenge 1: Heterogeneous Data Sources

**Problem:** Each company has unique structure

**Solution:**
- Custom workflow per company
- Flexible extraction patterns
- Adaptive normalization
- Template system for common patterns

### Challenge 2: Rate Limiting

**Problem:** Avoid being blocked

**Solution:**
- Respect robots.txt
- Implement delays
- Rotate user agents
- Use API when available

### Challenge 3: Data Freshness

**Problem:** Jobs expire quickly

**Solution:**
- Daily updates
- Automatic cleanup
- Posted date tracking
- Staleness detection

### Challenge 4: Deployment Automation

**Problem:** Manual publishing is tedious

**Solution:**
- Git automation
- GitHub Pages integration
- Atomic deployments
- Rollback capability

## Future Enhancements

**Planned Features:**

### Expanded Coverage
- 50+ companies target
- Regional expansion (APAC)
- Remote job inclusion
- Freelance opportunities

### Advanced Features
- Email alerts for new jobs
- Saved searches
- Application tracking
- Company reviews integration

### Data Intelligence
- Salary predictions
- Skill demand trends
- Company growth indicators
- Market analytics dashboard

### API Access
- Public JSON API
- Webhooks for updates
- Developer documentation
- Rate-limited access

## Technologies Used

**Automation:**
- n8n workflow platform
- Cron scheduling
- Webhook triggers

**Data Processing:**
- HTML parsing
- JSON manipulation
- Data normalization
- Validation logic

**Storage:**
- Supabase PostgreSQL
- GitHub repository
- JSON files
- Static assets

**Deployment:**
- GitHub Pages
- Git automation
- CDN distribution

**Monitoring:**
- Error notifications
- Performance tracking
- Uptime monitoring

## Links

- **Live Site:** [eaziym.github.io/sg-jobs](https://eaziym.github.io/sg-jobs)
- **GitHub:** [github.com/eaziym/sg-jobs](https://github.com/eaziym/sg-jobs)
- **API Endpoint:** Coming soon

## Conclusion

SG Jobs Aggregator demonstrates how modern workflow automation tools like n8n can build production-grade data platforms without traditional backend infrastructure. By orchestrating 20+ specialized workflows into a cohesive pipeline, it delivers daily-updated, comprehensive job listings to Singapore job seekers while showcasing data engineering best practices in web scraping, ETL, and automated deployment.
