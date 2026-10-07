---
status: Draft
---

# Product Requirements Document (PRD)

## Executive Summary
This Product Requirements Document defines a modern, cloud-native practice and document management platform engineered specifically for mid-market and large UK legal practices with 50 or more staff. Legal documentation—including pleadings, contracts, court bundles, correspondence, and compliance filings—serves as the primary operational deliverable of UK law firms. Today, fee earners lose between 1.5 and 2.5 hours daily navigating fragmented repositories, legacy on-premise systems, and fragile desktop add-ins. This platform delivers a unified, matter-centric workspace combining intelligent document lifecycle management, automated precedent drafting, and instant compliant court bundling directly within fee earners' natural workflows (native Microsoft 365 and Outlook). In parallel with major capability releases, the product operates a dedicated quarterly continuous enhancement cadence—shipping high-impact iterative delighters across email handling, document micro-services, and operational reporting to ensure ongoing user satisfaction and immediate productivity gains. By eliminating non-billable administrative drag, the solution directly recovers billable capacity, protects realization rates, and ensures strict compliance with Solicitors Regulation Authority (SRA) standards and UK GDPR mandates.

### Differentiation
- **Native Microsoft 365 Integration & Quarterly Iterations:** Integrates natively with Microsoft Outlook, Word, and Teams via modern cloud APIs rather than unstable legacy COM add-ins. Rapid quarterly enhancement cycles continuously refine email predictive filing, attachment handling, and document services based on direct fee-earner telemetry.
- **Unified Case & Document Management:** Integrates practice case metadata directly with document lifecycle workflows, eliminating context switching between separate practice management and document repositories.
- **Automated Court & Transaction Bundling:** Built-in PDF bundling engine capable of instant automated pagination, index generation, hyperlinking, and OCR text layering compliant with UK court standards.
- **Embedded SRA Compliance & Governance:** Granular role-based security, automated retention rules, information barriers (ethical walls), and tamper-evident audit trails out of the box.
- **Actionable Operational & Realisation Reporting:** Out-of-the-box, lightweight reporting delighters providing practice leads and cashiers real-time visibility into matter velocity, fee-earner time utilization, and billing realization without complex BI overhead.

### Competitive Position
- **Incumbent Enterprise DMS (iManage, NetDocuments):** High feature maturity but excessive total cost of ownership, complex administration, and poor native matter-management workflows for mid-market firms. Our platform matches core document governance while delivering superior ease of use, integrated case management, faster release velocity with quarterly delighters, and a lower total cost of ownership.
- **Legacy UK Practice Management Systems (Access Legal Proclaim, Tikit P4W):** Deep UK market penetration but burdened by legacy on-premise architectures, outdated user interfaces, slow innovation cycles, and unreliable document handling add-ins. Our solution offers modern cloud mobility, continuous quarterly refinements, automated bundling, and modern Microsoft 365 integration.

### Strategic Fit
Directly captures the £185M Serviceable Addressable Market (SAM) across 50+ person UK law firms undergoing cloud modernization. By solving the primary cause of margin erosion—unbillable administrative time spent locating, drafting, and assembling case files—the product establishes a high-retention operational system of record. Furthermore, our strategic roadmap bridges near-term civil/commercial practices with high-volume public funding sectors: while initial releases target civil litigation, family, and standard legal aid, the long-term roadmap incorporates full Legal Aid Agency (LAA) Crown Court fee schemes (such as Litigators' Graduated Fee Scheme / LGFS), positioning the platform as the comprehensive market leader across both privately funded and publicly funded UK legal sectors.

## Ideal Customer Profiles

### ICP A — [Segment / Industry / Region]

#### Company Profile
- **Size:** 50 to 500+ total staff (20 to 250+ fee earners)
- **Industry:** Legal Services (Commercial Litigation, Corporate/M&A, Real Estate, Family & Child Care, Criminal Defence & Public Funding, Private Client, Insurance Defence)
- **Maturity:** Established UK practice with mature matter workflows seeking to migrate away from legacy on-premise servers to modern cloud infrastructure.

#### Pain Points Addressed by Product
- **Chargeable Time Leakage:** Solicitors losing 1.5–2.5 hours per day searching across network drives, re-formatting documents, and manually logging email correspondence.
- **Version Sprawl & Disclosure Risk:** Uncontrolled document variants distributed across email threads and local drives, increasing the risk of sending outdated drafts or breaching client confidentiality.
- **High Administrative Burden in Bundling:** Paralegals and legal assistants spending days manually collating, paginating, and indexing court bundles and transaction closing bibles.
- **Slow Feature Innovation & Stagnant Vendor Support:** Frustration with legacy PMS vendors who rarely deliver practical workflow improvements or requested micro-features.
- **Complex Public Funding Billing Backlogs:** Manual re-keying of fee claims for public funding and Crown Court legal aid schemes causing cash-flow drag.

#### Key Persona
- **Role:** Senior Partner / Practice Group Leader & Head of Operations
- **Responsibilities:** Managing practice group profitability, ensuring fee-earner utilization targets, client relationship management, and regulatory compliance oversight.
- **Goals:** Maximise fee-earner billable realization, accelerate matter velocity, maintain strict SRA compliance, and ensure ongoing adoption through continuous quarterly tool improvements.
- **Challenges:** Fee earners resisting clunky administrative software; managing rising overheads under fixed-fee pressure; mitigating risk of disclosure errors; navigating intricate LAA billing rules.
- **Buying Criteria:** Fast fee-earner adoption, native Microsoft 365 compatibility, robust document version control, automated UK-compliant electronic bundling, steady cadence of quarterly enhancements, and long-term public funding roadmap (including LAA Crown Court fee claims).

## Product and Module Scope
The platform scope encompasses the complete matter lifecycle: matter workspace organization, email and file management, automated document assembly, electronic bundling, operational reporting, SRA compliance controls, and long-term expansion into Legal Aid Agency (LAA) Crown Court fee management.

## Modules Overview

### Module 1
- **Purpose & Objectives:** Provide a unified case and document management core embedded seamlessly into Outlook and Word to automate filing, eliminate version ambiguity, generate court-ready bundles, deliver fast quarterly customer-delight enhancements (email shortcuts, document micro-services, matter productivity reports), enforce SRA regulatory compliance, and support specialized public funding workflows (expanding to LAA Crown Court fees in the long-term roadmap).
- **Key Personas Targeted:** Partners, Senior Associates, Solicitors, Paralegals, Legal Secretaries, Legal Cashiers, and Compliance Officers for Legal Practice (COLP).
- **Dependencies:** Microsoft Graph API, Cloud Object Storage, Search Indexing Engine, PDF/OCR Processing Engine, Entra ID, and Legal Aid Agency (LAA) digital claim submission gateways.

## Features Overview

### Feature 1
- **Quick Description:** Predictive one-click email and attachment filing from Outlook, matter-centric version control with redlining, automated electronic court bundle generation with hyperlinking and OCR, dynamic precedent assembly, ethical wall information barriers, continuous quarterly enhancement releases (delivering quick-win email filing filters, document service optimizations, and operational realization reports), and a phased public funding billing engine scaling into LAA Crown Court fee schemes.
- **Module:** Module 1
- **Key Personas Targeted:** Solicitors, Senior Associates, Paralegals, Legal Secretaries, Practice Managers, and Compliance Officers.