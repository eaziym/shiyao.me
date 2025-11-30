---
layout: project
title: PKF-CAP - Self-Service Analytics Platform
date: 2025-06-01
tags: [n8n, Analytics, RBAC, Automation, Data Integration, Webhooks, Dashboard]
problem: "Manual operational processes (CaseWare access, charge codes, QC forms) created bottlenecks, while fragmented data sources made partner-level analytics slow and labor-intensive"
approach: "Built self-service analytics platform with Role-Based Access Control and n8n workflows, integrating operational data via webhooks for pseudo real-time analytics"
url: /shiyao.me/projects/pkf-analytics
metrics:
  - label: Workflow Lifecycle Reduction
    value: "70%"
  - label: Data Aggregation Workload Reduction
    value: "80%"
  - label: Role
    value: "Technology & Analytics Associate"
cover_image: /assets/images/pkf.png
---

## Overview

As Technology & Analytics Associate at PKF-CAP LLP (Jun 2025 - Present), I built a comprehensive self-service analytics platform that automated operational workflows and provided real-time business intelligence for partner decision-making.

## The Problem

### Manual Operational Bottlenecks

**CaseWare Access Management:**
- Manual request processing
- Slow approval workflows
- No self-service capability
- Tracking via emails/spreadsheets

**Charge Code Access:**
- Repetitive access requests
- Manual provisioning
- Delayed project onboarding
- Administrative overhead

**Quality Control Forms:**
- Paper-based or static forms
- Manual data collection
- Delayed review cycles
- Difficult to track completion

**Common Pain Points:**
- Long end-to-end workflow lifecycles
- Manual intervention required at each step
- Lack of transparency into status
- Inefficient resource allocation

### Fragmented Data for Analytics

**Data Scattered Across:**
- Operational spreadsheets
- Upstream source systems
- Email threads
- Manual reports
- Legacy databases

**Analytics Challenges:**
- Manual data aggregation required
- Time-consuming partner reviews
- Stale data for decision-making
- No real-time visibility
- 80%+ workload on data preparation

**Impact:**
- Delayed business insights
- Reactive rather than proactive decisions
- Limited analytical capacity
- Partner frustration

## The Solution

### Self-Service Analytics Platform

**Comprehensive Platform Features:**

**1. Role-Based Access Control (RBAC)**

**Permissions System:**
- User role definitions
- Granular access controls
- Secure data visibility
- Audit logging

**Benefits:**
- Appropriate data access per role
- Security compliance
- Self-service within boundaries
- Reduced admin overhead

**2. n8n Automated Workflows**

**Process Automation:**

**CaseWare Access Workflow:**
```
Request Submission (Self-Service)
    ↓
Automated Validation
    ↓
Role-Based Routing
    ↓
Approval (if required)
    ↓
Automatic Provisioning
    ↓
Notification to User
```

**Charge Code Access Workflow:**
```
User Request Form
    ↓
Project Code Validation
    ↓
Manager Approval (async)
    ↓
System Provisioning
    ↓
Access Granted
    ↓
Confirmation Email
```

**Quality Control Forms Workflow:**
```
Form Submission
    ↓
Validation Rules
    ↓
Assignment to Reviewer
    ↓
Review Process
    ↓
Status Updates
    ↓
Completion Notification
    ↓
Analytics Integration
```

**Workflow Benefits:**
- **70% reduction** in end-to-end lifecycle time
- No manual bottlenecks
- Transparent status tracking
- Scalable processes
- Consistent execution

### Real-Time Analytics Integration

**n8n Webhook Architecture:**

**Data Flow:**
```
Operational Data Sheets
    ↓
n8n Webhooks (triggered on changes)
    ↓
Data Transformation
    ↓
Analytics Dashboard Update
    ↓
Pseudo Real-Time Refresh
```

**Upstream Source Integration:**
```
Source Systems → Webhooks → ETL → Dashboard
```

**Key Features:**
- Automatic data synchronization
- Event-driven updates
- Minimal latency
- No manual refresh needed

**Analytics Dashboard Capabilities:**

**Partner Review Interface:**
- Real-time KPI tracking
- Operational metrics
- Resource utilization
- Project status
- QC completion rates
- Bottleneck identification

**Decision-Making Support:**
- Current vs. historical trends
- Drill-down capabilities
- Export functionality
- Customizable views
- Alert notifications

**Impact:**
- **80% reduction** in data aggregation workload
- Partners access analytics directly
- Data-driven decisions
- Proactive issue resolution

## Technical Implementation

### Architecture

**Platform Components:**

**Frontend:**
- Self-service request portals
- Analytics dashboards
- Status tracking interfaces
- Admin panels

**Backend:**
- n8n workflow engine
- RBAC system
- Database storage
- API integrations

**Data Layer:**
- Operational data store
- Analytics data warehouse
- Real-time sync engine
- Audit logs

**Integration:**
```
Users → Self-Service Portal → n8n Workflows → Systems
                                    ↓
Operational Data → Webhooks → ETL → Dashboards
```

### n8n Workflow Design

**Workflow Templates:**

**1. Access Request Processing**
- Form intake node
- Validation logic
- Approval routing (conditional)
- System provisioning API calls
- Notification triggers

**2. Data Integration**
- Webhook receivers
- Data transformation
- Deduplication
- Database upsert
- Dashboard refresh trigger

**3. Quality Control**
- Form submission handling
- Validation rules engine
- Assignment logic
- Status tracking
- Completion notifications

### RBAC Implementation

**Role Definitions:**
- Staff
- Senior Staff
- Manager
- Partner
- Admin

**Permission Matrix:**
```
Resource        Staff   Senior  Manager Partner Admin
CaseWare Access Request Request Approve View    Manage
Charge Codes    Request Request Approve View    Manage
QC Forms        Submit  Submit  Review  Review  Manage
Analytics       Limited Limited Full    Full    Full
Workflows       N/A     N/A     Monitor Monitor Manage
```

**Security Features:**
- Authentication integration
- Session management
- Access logging
- Compliance reporting

### Webhook-Driven Analytics

**Real-Time Data Pipeline:**

**Trigger Events:**
- New row in operational sheet
- Data update/modification
- Status change
- Completion event
- Error condition

**Webhook Processing:**
1. Event received
2. Data extracted
3. Validation performed
4. Transformation applied
5. Database updated
6. Dashboard notified
7. Cache refreshed

**Performance:**
- Sub-second webhook response
- Pseudo real-time updates (< 5 seconds)
- Scalable to high event volume
- Fault-tolerant processing

## Key Features

### 1. Self-Service Portal
- CaseWare access requests
- Charge code provisioning
- QC form submission
- Status tracking
- Request history

### 2. Automated Workflows
- Zero manual intervention
- Conditional routing
- Parallel processing
- Error handling
- Retry logic

### 3. Real-Time Analytics
- Live KPI dashboards
- Operational metrics
- Resource allocation
- Project tracking
- QC completion rates

### 4. RBAC Security
- Role-based permissions
- Secure data access
- Audit trails
- Compliance ready

### 5. Integration Layer
- Operational data sheets
- Upstream systems
- Email notifications
- Third-party APIs

## Impact & Metrics

**Operational Efficiency:**
- **70% reduction** in end-to-end workflow lifecycles
- Eliminated manual bottlenecks
- Self-service capability for staff
- Consistent process execution

**Analytics Productivity:**
- **80% reduction** in data aggregation workload
- Partners access insights directly
- Real-time vs. weekly/monthly reports
- More time for analysis vs. data prep

**User Experience:**
- Instant request submissions
- Transparent status tracking
- Fast provisioning
- Professional self-service

**Business Value:**
- Data-driven decision making
- Proactive issue resolution
- Resource optimization
- Improved partner satisfaction

## Use Cases

### 1. CaseWare Access Management
- New project onboarding
- Temporary access for audits
- Access revocation
- Compliance tracking

### 2. Charge Code Provisioning
- Project setup automation
- Time tracking enablement
- Cost center management
- Budget monitoring

### 3. Quality Control
- Engagement quality reviews
- Compliance checks
- Process improvement
- Training identification

### 4. Partner Analytics
- Performance dashboards
- Resource utilization
- Revenue tracking
- Project profitability

## Technologies Used

**Automation:**
- n8n workflow platform
- Webhook triggers
- API integrations

**Data:**
- Real-time ETL
- Data warehousing
- Dashboard tools
- Query optimization

**Security:**
- RBAC framework
- Authentication systems
- Audit logging
- Encryption

**Frontend:**
- Self-service portals
- Analytics dashboards
- Responsive design

## Future Enhancements

**Planned Features:**

**Advanced Analytics:**
- Predictive insights
- Machine learning models
- Anomaly detection
- Forecasting

**Workflow Expansion:**
- More automated processes
- Intelligent routing
- Dynamic approvals
- Process mining

**Integration:**
- Additional source systems
- CRM integration
- Financial systems
- HR platforms

**Mobile Access:**
- Mobile-responsive dashboards
- Push notifications
- Mobile request submission

## Context

**PKF-CAP LLP** is a Singapore-based accounting and business advisory firm. This role as **Technology & Analytics Associate** (Jun 2025 - Present) focuses on building internal technology solutions and business intelligence capabilities to improve operational efficiency and enable data-driven decision making.

## Conclusion

The self-service analytics platform transformed PKF-CAP's operational processes from manual, bottleneck-prone workflows to automated, transparent systems with real-time business intelligence. By reducing workflow lifecycles by 70% and data aggregation workload by 80%, the platform enables staff to work more efficiently and partners to make faster, data-driven decisions.
