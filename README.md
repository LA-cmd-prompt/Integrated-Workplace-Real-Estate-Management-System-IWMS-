# Integrated Workplace Real Estate Management System IWMS
# IWMS Project Requirements Specification (v2.0)

**Client:** VDI Group  
**Project:** Integrated Workplace & Real Estate Management System (IWMS)  
**Prepared by:** Lola A., CISA, CIPP/C  
**Version:** 2.0 – Revised for Feasibility & Clarity

---

## Value-Add Note (Developer Lens)

This document demonstrates the difference between requirements written by an everyday Business Analyst versus a BA who understands developer feasibility, technical constraints, and long-term maintainability.

All requirements have been reviewed for realism, testability, integration complexity, and alignment with relevant regulations(PIPEDA)

---

## Everyday BA vs. Developer-Lens BA: Key Differences

| Area                  | Everyday BA Approach (Original Style)                                      | Developer-Lens BA Approach (This Document)                                                                 | Why It Matters |
|-----------------------|----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|----------------|
| Performance           | “Landing page must support at least 6000 staff per hour and allow navigation within 6 seconds” | “Target response time 3–6 seconds under normal load; validated through load testing; 99th percentile monitoring in production” | Prevents impossible promises and scope disputes during UAT |
| Platform Support      | “Must run on Windows XP and Mac without change in behaviour”               | “Support current versions of major desktop browsers (Chrome, Firefox, Edge) on Windows and macOS; responsive design” | Windows XP is end-of-life; avoids legacy technical debt and security risks |
| Uptime                | “99.9% uptime availability” (absolute)                                     | “Target 99.9% uptime with defined maintenance windows and documented rollback procedures”                   | Sets realistic SLAs and makes the requirement actionable for architects |
| Security              | “Robust security measures to protect sensitive information”                | “Industry-standard controls (encryption in transit/rest, RBAC, MFA support, regular vulnerability scanning); aligned with PIPEDA” | Makes it testable and auditable; demonstrates compliance awareness |
| Integration           | “Ability to integrate with HR and accounting software”                     | “Bi-directional integration with QuickBooks and HR systems; error handling, logging, and data-sync monitoring required” | Reduces integration surprises and change requests |
| Scalability           | “Accommodate 6000 staff and more at a time”                                | “Support minimum 6,000 concurrent users; designed for horizontal scaling; load testing required during implementation” | Forces architecture discussion early instead of late-stage refactoring |

**Developer Lens Summary**  
- Removed absolute, non-testable language  
- Added acceptance criteria, validation gates, and risk notes  
- Considered Canadian regulatory and accessibility realities  
- Flagged legacy or high-risk items early  
- Made requirements traceable, measurable, and ready for sprint planning

---

## 1. Functional Requirements

| ID     | Functional Requirement                                                                 | Priority | Developer Feasibility Notes |
|--------|----------------------------------------------------------------------------------------|----------|-----------------------------|
| FR-01  | HR administrators can manage remote-work programs (time tracking, attendance, schedules, time-off requests) | High     | Workflow engine + audit trail required; integrate with existing HR system where possible |
| FR-02  | Secure, centralized repository of tenant/property information across all locations     | High     | Role-based access control + encryption at rest; data retention policy needed |
| FR-03  | Real-time dashboards and customizable reporting for management                         | High     | Consider Power BI/Tableau embedding or built-in reporting; export formats required |
| FR-04  | Facilities management (maintenance requests, inspections including virtual, work orders) | High     | Mobile-friendly; photo/document upload; integration with existing asset system |
| FR-05  | Public property search + virtual inspection interest form                              | Medium   | Public-facing module; contact routing to assigned property manager |
| FR-06  | Prospective tenant profile (job title, income range, household composition)            | Medium   | Consent capture + data minimization; only used for internal assessment |
| FR-07  | Role-based login with MFA support                                                      | High     | Standard authentication library; session management and timeout controls |
| FR-08  | Integration with HR and accounting systems (e.g., QuickBooks)                          | High     | Bi-directional sync preferred; define error handling and monitoring requirements |

---

## 2. Non-Functional Requirements (with Developer Lens)

| ID     | Non-Functional Requirement     | Target / Feasibility Notes |
|--------|--------------------------------|----------------------------|
| NFR-01 | Scalability                    | Minimum 6,000 concurrent users; architected for horizontal scaling; load testing required in implementation phase |
| NFR-02 | Performance                    | Page response 3–6 seconds under normal load on current desktop browsers; performance monitoring in production |
| NFR-03 | Reliability & Availability     | Target 99.9% uptime; scheduled maintenance windows (e.g., Friday 12:00–3:00 a.m.); documented rollback procedures |
| NFR-04 | Security                       | Encryption in transit and at rest; RBAC; MFA support; regular vulnerability scanning; aligned with PIPEDA expectations |
| NFR-05 | Maintainability                | CI/CD pipeline support; automated logging and monitoring; scheduled maintenance with minimal user impact |
| NFR-06 | Compatibility & Portability    | Current versions of Chrome, Firefox, Edge on Windows and macOS; responsive design |
| NFR-07 | Usability & Accessibility      | Intuitive navigation; WCAG 2.1 AA compliance (Canadian AODA expectations) |
| NFR-08 | Integration & Localization     | Bilingual (English/French) capability; integration points with HR, Finance, and Asset Management systems |

---

## 3. Stakeholder Requirements (User Stories)

| ID     | As a…                        | I want to…                                                                 | So that…                                      | Priority |
|--------|------------------------------|----------------------------------------------------------------------------|-----------------------------------------------|----------|
| US-01  | HR Manager                   | Manage employee schedules, time-off requests, and remote-work program participation from a single interface | I can support a distributed workforce efficiently | High     |
| US-02  | Finance / Accounting User    | Access QuickBooks integration for capital planning, budget tracking, vendor contracts, and invoices | I have accurate, real-time financial visibility | High     |
| US-03  | Property Manager             | View real-time occupancy, maintenance requests, and facility data across all locations | I can respond quickly to operational issues     | High     |
| US-04  | Property Manager             | Track and manage virtual inspection requests                               | Prospective tenants can be engaged remotely and efficiently | Medium   |
| US-05  | COO / Executive              | Access asset management, material usage, and portfolio-level reporting     | I can make informed strategic decisions         | High     |
| US-06  | Head of Procurement          | Manage vendor contracts, inventory, and invoices in one system             | Procurement processes are streamlined and auditable | Medium   |
| US-07  | Company Secretary            | Access a company-wide calendar and scheduling tools                        | Meetings and resources are coordinated effectively | Low      |
| US-08  | Construction / Project Architect | View and update building project assignments, progress, and timelines   | Project delivery remains on track               | Medium   |
| US-09  | CFO                          | Coordinate and allocate financial resources across the organization        | Budget decisions are data-driven                | High     |
| US-10  | Head of IT                   | Provide real-estate teams with a secure portal to view and suggest designs for the property portfolio | Collaboration on portfolio optimization is supported | Medium   |

---

## 4. Gap Analysis Summary (High-Level)

| Strategic Objective                          | Current State                          | Gap     | Recommended Actions                                                                 | Key Risks / Mitigations |
|----------------------------------------------|----------------------------------------|---------|-------------------------------------------------------------------------------------|-------------------------|
| Increase real estate sales & lease targets by 40% | 10% achievement; investor funding concerns | 30%     | Improve website usability, sales funnel automation, targeted marketing, agent performance tracking | Data privacy & security risks → implement encryption and consent management |
| Improve operational efficiency by 80%        | 20% (manual processes)                 | 60%     | Implement IWMS with automation, integrations (QuickBooks, HR), and role-based configuration | Budget approval & change management → phased rollout + training program |
| Reduce annual overhead costs by 60%          | ~30% of budget spent on energy/office space | 30%     | Enable remote work, optimize space utilization, provide energy-consumption visibility | Office-space mismanagement → clear remote-work policy and monitoring |

---

*Document prepared to demonstrate practical, client-ready business analysis with a developer-informed perspective.*
