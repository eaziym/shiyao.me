---
layout: project
title: SG Internship Listing
tags:
  [Web Scraping, Data Analytics, Python, Selenium, Bing API, Community Building]
problem: "Job searching process is fragmented and time-consuming, with students spending hours manually searching across multiple platforms and filling repetitive applications"
approach: "Built an automated job aggregation platform that consolidates opportunities across 250+ companies, with weekly updates and a growing community of 380+ students"
demo_url: "https://github.com/eaziym/sg-internship-listing"
metrics:
  - label: Company Count
    value: "250+"
  - label: Active Listings
    value: "1000+"
  - label: Community Size
    value: "380+"
---

## The Journey

### 1. Problem Identification

During my own job search experience, I identified several critical pain points:

- Scattered job listings across numerous company career pages
- Repetitive form filling across different application platforms
- Need for manual tracking of application statuses
- Lack of centralized platform for Singapore-specific opportunities
- Time-consuming process of searching and applying

### 2. Solution Evolution

#### Initial Vision

Planned comprehensive features:

- AI-powered resume generation from user experiences
- Job-tailored cover letter generation
- Interview simulation system with industry-specific questions
- Standardized application form auto-fill
- Centralized interview scheduling platform

#### Current Implementation

Focused on core functionality:

- Automated job listing aggregation
- Weekly updates of opportunities
- Direct application links
- Category-based organization
- Active community engagement

### 3. Technical Implementation

#### Data Collection Pipeline

1. **Company Career Pages Scraping**
   Example from our database showing diverse roles:

| Company | Position                                 | Category           |
| ------- | ---------------------------------------- | ------------------ |
| PWC     | Risk Services - Digital Audit            | Product Innovation |
| PWC     | Technology - Risk Services (Cloud Trust) | Product Innovation |
| PWC     | Digital Innovation Garage                | Assurance          |

2. **Bing API Integration**

```python
def search_job_link(company, position):
    search_query = f"{company} {position} careers singapore"
    search_url = f"https://api.bing.microsoft.com/v7.0/search?q={search_query}"
    response = requests.get(search_url, headers=headers)
    results = response.json()
    return results['webPages']['value'][0]['url']
```

3. **Data Processing**

- Automated deduplication
- Category classification
- Link validation
- Weekly updates

### 4. Data Organization

#### Structured Categories

Based on actual listings:

1. **Technology & Innovation**

- Digital Audit
- Cloud Trust Services
- Process Automation

2. **Risk & Assurance**

- Data Trust Services
- Digital Client Services
- ESG Advisory

3. **Strategy & Operations**

- Digital Ventures
- Change Management
- Technology Strategy

### 5. Impact & Growth

#### Current Statistics

- 250+ companies covered
- ~1,000 active job postings
- Weekly automated updates
- 380+ active community members

#### Community Engagement

- Job search tips sharing
- Application experience exchange
- Industry insights discussion
- Career guidance support

### 6. Technical Stack

1. **Web Scraping**

- Selenium for dynamic content
- BeautifulSoup for parsing
- Rotating proxies for reliability

2. **Search Integration**

- Bing API for direct links
- Custom search query optimization
- Rate limiting implementation

3. **Data Management**

- Automated deduplication
- Category classification
- Weekly update automation
- Version control

4. **Distribution**

- GitHub Pages hosting
- Markdown generation
- Social media integration
- Community platform

### 7. Key Learnings

1. **Project Scope**

- Start with core features
- Validate with user feedback
- Iterate based on usage
- Focus on reliability

2. **Technical Challenges**

- Rate limiting handling
- Data consistency
- Link validation
- Update automation

3. **Community Building**

- Value of user feedback
- Importance of regular updates
- Building trust through consistency
- Power of solving real problems

### 8. Future Development

Planned features based on user feedback:

- Resume builder with AI assistance
- Application tracking system
- Chrome extension for form auto-fill
- Interview scheduling platform
- Cover letter generator
- Mock interview system

[View Live Site](https://eaziym.github.io/sg-internship-listing)
[View on GitHub](https://github.com/eaziym/sg-internship-listing)
