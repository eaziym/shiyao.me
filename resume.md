---
layout: resume
title: Resume
permalink: /resume/
author: Shiyao Meng
phone: +65 8815 6005
email: e0773600@u.nus.edu
pdf_url: /assets/docs/Meng Shiyao_01122025.pdf
---

## Education

**NATIONAL UNIVERSITY OF SINGAPORE (NUS)**  
Master of Computing in Artificial Intelligence

<div class="job-title">
  <span>Aug 2025 - Present</span>
</div>

- Cloud Computing (AWS, Azure, GCP, VPCs, K8s, MapReduce-based distributed processing)
- Focus on high-performance networking, probabilistic data structures, and cloud platforms for scalable, low-latency, data-intensive systems

**NATIONAL UNIVERSITY OF SINGAPORE (NUS)**  
Bachelor of Business Administration, Honours (Distinction)

<div class="job-title">
  <span>Aug 2021 - Jun 2025</span>
</div>

- Specialization in Business Analytics
- Second Major in Data Science and Analytics

## Work Experience

### PKF-CAP LLP, SINGAPORE

<div class="job-title">
  <span>Technology & Analytics Associate</span>
  <span>Jun 2025 - Present</span>
</div>

- Built a self-service analytics platform with Role-Based Access Control and n8n automated workflows to streamline operational processes (e.g. CaseWare access, charge code access, Quality Control forms); reduced end-to-end workflow lifecycles by 70%
- Integrated operational data sheets and upstream sources to analytics dashboards via n8n webhooks to achieve pseudo real-time data updates and analytics for partners' review and decision-making, reducing data aggregation workloads by 80%

### [AMMO AI, LONDON](https://ammoai.io/)

<div class="job-title">
  <span>Software Engineer Intern, Remote</span>
  <span>Jul 2024 - Jun 2025</span>
</div>

- Led full-stack development for Fakers Labs, an experimental AI content lab, shipping features such as AI-generated podcasts that orchestrated multi-step LLM pipelines (outline → script → style transfer → TTS) on top of existing content, increasing user engagement by 30%
- Developed a Twitter AI agent for context-aware responses and analytics dashboard to run A/B tests on prompts and measure engagement (sentiment, click-through), enabling data-driven iteration on model prompts and content strategies, supporting 1.5k daily interactions

### MODULAR ASSET MANAGEMENT, SINGAPORE

<div class="job-title">
  <span>Operations Intern</span>
  <span>May 2024 - Jun 2024</span>
</div>

- Streamlined operational workflow for day-to-day trade booking with full-stack web dashboard to display centralized birds-eye tabulated view of disputed trade info from disparate FXPB and MTM platforms, supporting sub-10 seconds pseudo real-time updates of data, and searching, filtering, sorting, column drag&drop, conditional highlighting

### PFK-CAP LLP

<div class="job-title">
  <span>Audit Intern</span>
  <span>Jan 2024 - May 2024</span>
</div>

- Directed implementation of 'Potato Audit', an automated software using Flask as backend, Selenium for streamlining repetitive tasks, and React for developing a user-friendly front-end interface accessible by non-technical audit staff
- Reduced financial announcements and statutory audit processing time from days to sub-10 minutes and semi-automated invoice data extraction of similar formats from manual reviews with 98% accuracy, handling ~28 invoices/min
- Engineered a new systematic staff booking system to minimize booking errors and enhance resource management efficiency
- Received commendation for developing innovative automation solutions - [View Testimonial]({{ '/assets/docs/PKF_Testimonial_Letter.pdf' | relative_url }})

### JASPER VAULT TECHNOLOGY PTE LTD, SINGAPORE

<div class="job-title">
  <span>Business Analyst Intern</span>
  <span>May 2023 - Oct 2023</span>
</div>

- Developed and optimized dashboards analyzing Ethereum (ETH) Staking, Smart Money holdings and crypto market trends using Dune SQL; presented in weekly investment meeting for fund management
- Streamlined data retrieval and analysis workflows by integrating various API providers using Python/Power Query
- Researched and backtested AI-powered algorithmic trading with optimized parameters on TradingView

## Personal Projects

### CTO – CHIEF TALENT OFFICER

<div class="job-title">
  <span>Creator</span>
  <span>Nov 2025</span>
</div>

- Built an AI-powered career platform that ingests a candidate's GitHub, LinkedIn, and project docs to produce a unified enriched profile, then uses LLMs to generate async tailored resumes, cover letters, and outreach messages per job description within 30 seconds
- Implemented RAG over user-provided sources, so the LLM grounds its responses in actual documents and project history instead of a single compressed resume, reducing hallucination by 20%
- Integrated Apify-based flows to search for HR / hiring-manager contacts and link them with LLM-generated personalized outreach content, closing the loop from job description → profile → contact, reducing manual search workload by 30%
- Designed the system so it can be extended into a conversational analytics interface over a user's career data (e.g. "What are my top 3 projects relevant to this JD?")
- See [cto.shiyao.dev](https://cto.shiyao.dev) and [GitHub](https://github.com/eaziym/cto)

### N8N HEADHUNTER WORKFLOW

<div class="job-title">
  <span>Creator</span>
  <span>Oct 2025</span>
</div>

- Developed workflows that take natural language query → parse into structured filters → search and enrich profiles → top 20 candidates in ave. 2min
- Deployed search-first approach using Google (via Serper) + LinkedIn dorking + Apify enrichment for fresher, lower-cost data ($0.05 per profile)
- Configured LangChain-based code node to stabilise tool-calling, ensuring the agent loops until the target number of candidates is found and avoiding random early termination, improving accuracy by 20%
- Logged all agent actions (searches, validations, accepts/rejects) to Supabase and exposed them via webhook for live progress UI, solving the "why is nothing happening?" problem and making the pipeline 90% auditable and explainable
- Connected to a people dataset (200M+ entries) for fast filter-based retrieval (5–10 seconds per batch), while parallel Yahoo/Google search improves coverage for profiles not in the dataset; designed for future semantic search / RAG over stored profiles

### SG JOBS AGGREGATOR

<div class="job-title">
  <span>Creator</span>
  <span>Oct 2025</span>
</div>

- Built 20+ n8n workflows to scrape Singapore companies' official career sites, normalise heterogeneous APIs/HTML, and aggregate 4,000+ listings in about 20 minutes (title, apply URL, metadata) into a unified dataset
- Implemented an end-to-end mini data platform: information gathering → cleaning → DB insert → JSON and index.html generation → deployment to GitHub Pages, orchestrated as scheduled daily flows
- See [sg-jobs](https://eaziym.github.io/sg-jobs) and [GitHub](https://github.com/eaziym/sg-jobs)

## Co-Curricular Activities

### COMLINK BEFRIENDERS

<div class="job-title">
  <span>Volunteer</span>
  <span>Oct 2023 - Aug 2024</span>
</div>

- Engaged with local families for monthly visits and activities

## Skills and Interests

**Languages & Databases**  
Python, Java (OOP & data structures – NUS CS2040), C, JavaScript, TypeScript, SQL, MongoDB, PostgreSQL, SQLite

**LLMs, AI & Automation**  
LangChain, CrewAI, RAG, OpenAI, Dify, TTS, Whisper, OCR, n8n, Make.com, Supabase

**Data Platforms, Web & Services**  
React, Next.js, Node/Express, Flask, REST APIs, Selenium  
Experience building internal analytics dashboards and data-collection services over financial, audit, and job-market data

**Cloud & Infrastructure**  
Azure (AI Foundry, Document Intelligence, VMs, NSGs), AWS (EC2, VPC, S3), Digital Ocean, Docker, Traefik  
Familiarity with distributed systems concepts (MapReduce, cloud-native architectures) from NUS Cloud Computing coursework
