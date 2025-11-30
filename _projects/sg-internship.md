---
layout: project
title: SG Internship Listing
date: 2024-04-01
tags:
  [Web Scraping, Data Analytics, Python, Selenium, GitHub Pages, Community Building]
problem: "Job searching process is fragmented and time-consuming, with students spending hours manually searching across multiple platforms and filling repetitive applications"
approach: "Built an automated job aggregation platform using Selenium to gather 550+ positions from 30+ companies, hosted on GitHub Pages with weekly updates and a growing community of 300+ members"
url: /shiyao.me/projects/sg-internship
demo_url: "https://eaziym.github.io/sg-internship-listing"
metrics:
  - label: Total Views
    value: "13,000+"
  - label: Internship Positions
    value: "550+"
  - label: Companies Tracked
    value: "30+"
  - label: Community Members
    value: "300+"
  - label: Social Engagement
    value: "569 Likes"
cover_image: /assets/images/sg-intern-cover.png
images:
  - path: /assets/images/sg-intern-jobs.png
    caption: Jobs View
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

**Company Career Pages Scraping**
Example from our database showing diverse roles:

| Company | Position                                 | Category           |
| ------- | ---------------------------------------- | ------------------ |
| PWC     | Risk Services - Digital Audit            | Product Innovation |
| PWC     | Technology - Risk Services (Cloud Trust) | Product Innovation |
| PWC     | Digital Innovation Garage                | Assurance          |

**Bing API Integration**

```python
def search_job_link(company, position):
    search_query = f"{company} {position} careers singapore"
    search_url = f"https://api.bing.microsoft.com/v7.0/search?q={search_query}"
    response = requests.get(search_url, headers=headers)
    results = response.json()
    return results['webPages']['value'][0]['url']
```

**Data Processing**

- Automated deduplication
- Category classification
- Link validation
- Weekly updates

### 4. Data Organization

#### Structured Categories

Based on actual listings:

**Technology & Innovation**

- Digital Audit
- Cloud Trust Services
- Process Automation

**Risk & Assurance**

- Data Trust Services
- Digital Client Services
- ESG Advisory

**Strategy & Operations**

- Digital Ventures
- Change Management
- Technology Strategy

### 5. Impact & Growth

#### Current Statistics

- **550+ internship positions** gathered from **30+ companies**
- Hosted on **GitHub Pages** with weekly updates
- **13,000+ total views** across platforms
- **569 likes**, **133 comments**, **469 favourites** on Xiaohongshu (social media)
- **300+ active community members** for career info exchange

#### Community Engagement

- Job search tips sharing
- Application experience exchange
- Industry insights discussion
- Career guidance support
- Active student and fresh grad network
- Weekly listing updates and notifications

### 6. Technical Stack

**Web Scraping**

- Selenium for dynamic content
- BeautifulSoup for parsing
- Rotating proxies for reliability

**Search Integration**

- Bing API for direct links
- Custom search query optimization
- Rate limiting implementation

**Data Management**

- Automated deduplication
- Category classification
- Weekly update automation
- Version control

**Distribution**

- GitHub Pages hosting
- Markdown generation
- Social media integration
- Community platform

### 7. Key Learnings

**Project Scope**

- Start with core features
- Validate with user feedback
- Iterate based on usage
- Focus on reliability

**Technical Challenges**

- Rate limiting handling
- Data consistency
- Link validation
- Update automation

**Community Building**

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
