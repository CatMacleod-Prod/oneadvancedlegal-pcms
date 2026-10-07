---
status: Draft
---

# Product Vision

## Executive Summary

The Practice Case Management System (PCMS) is an enterprise-grade cloud solution engineered for mid-market law firms (50 to 100+ staff) across England and Wales. The core mission is to eliminate non-billable administrative drag and liberate fee earners (partners, associates, solicitors) and legal assistants from repetitive case admin tasks. By automating high-volume administrative tasks—such as 1-click email filing, automatic attachment indexing, document generation, client onboarding (eIDV/AML), and MoJ-compliant electronic court bundling—the platform recovers 1.5 to 2 hours of billable capacity per fee earner every day while maintaining strict regulatory compliance across the practice.

### Differentiation

- **Defect-Free Dual-Outlook Co-Existence**: Sub-second, bi-directional email and attachment indexing operating seamlessly across both Classic Outlook (Win32 desktop) and New Outlook for Windows / Outlook on the Web, eliminating the crashes and freezes typical of legacy COM/VSTO add-ins.
- **Embedded Legal Workflow Automation Engine**: Out-of-the-box, event-driven workflow automation pipelines tailored for core England & Wales disciplines with built-in digital onboarding, AML verifications, and automated court bundling.
- **Enterprise-Grade Concurrency & Speed**: High-performance cloud architecture supporting 100+ concurrent active fee earners and operational staff without performance degradation or record locking.

### Competitive Position

- **Displacing Legacy Desktop Solutions (Access Legal / Proclaim / P4W)**: Replaces unstable plugins, legacy on-premise architectures, and slow sync mechanisms with a unified modern cloud platform.
- **Outperforming Complex ERPs (Advanced ALB)**: Provides a streamlined, modern user experience with flexible workflow configurations and faster time-to-value.
- **Unifying Disconnected Point Solutions**: Eliminates the need for separate standalone bundling, onboarding, and document management subscriptions by delivering an end-to-end integrated suite.

### Strategic Fit

Aligns directly with mid-market legal practices modernizing their technology stacks around Microsoft 365. By solving the core operational friction of unchargeable administrative overhead, the product improves fee-earner realization rates, accelerates matter velocity, and scales practice capacity without requiring proportional headcount increases.

## Ideal Customer Profiles

### ICP A — [Segment / Industry / Region]

#### Company Profile
- **Size:** 50 - 500+ total staff (50 - 100+ concurrent active fee earners and legal assistants)
- **Industry:** Legal Services (Commercial & Civil Litigation, Conveyancing, Family Law, Private Client/Probate, Corporate) in England & Wales
- **Maturity:** Established multi-partner and multi-office law firms modernizing from legacy on-premise case management systems to cloud-native platforms

#### Pain Points Addressed by Product
- Fee earners losing up to 2 hours per day on non-billable administrative tasks, email sorting, and manual filing.
- Frequent Outlook desktop add-in crashes and lack of support for Microsoft's New Outlook and web clients.
- Fragmented workflows requiring manual copy-pasting across disparate onboarding, verification, and court bundling point tools.
- Administrative bottlenecks on legal assistants managing high-volume matter intake and court documentation.

#### Key Persona
- **Role:** Senior Associate / Fee-Earning Solicitor & Practice Group Head
- **Responsibilities:** Managing active case portfolios, advising clients, meeting annual billing targets, drafting legal pleadings, and supervising administrative case progression.
- **Goals:** Maximize billable hours, accelerate matter turnaround, minimize administrative context-switching, and deliver error-free client service.
- **Challenges:** Drowning in non-billable administrative overhead, chasing email attachments, manual client onboarding, and assembling court bundles.
- **Buying Criteria:** Flawless Microsoft Outlook integration stability, automated matter workflows, sub-second search and indexing speeds, and minimal user training requirements.

## Product and Module Scope

The product scope centers on core practice case management for England & Wales legal practices, focusing specifically on deep Microsoft Outlook add-in capabilities (Classic and New), automated legal workflow orchestration, integrated digital client onboarding (eIDV/AML), and automated court bundling. Scottish-specific legal aid billing (SLAB) and Law Society of Scotland specific accounting engines are explicitly excluded from this release.

## Modules Overview

### Module 1
- **Purpose & Objectives:** High-Performance Dual-Environment Outlook Integration Engine and Practice Workflow Orchestrator. Enables 1-click bi-directional email and attachment filing across Classic Win32 Outlook and New Outlook / Outlook on the Web, while automating event-driven matter tasks, milestone progressions, digital client onboarding (eIDV/AML), and MoJ-compliant electronic court bundling.
- **Key Personas Targeted:** Fee-Earning Solicitors, Senior Associates, Legal Assistants, and Paralegals.
- **Dependencies:** Microsoft Graph API, Office.js Add-in Framework, PCMS Document Management Service, and 3rd-Party eIDV/AML Integration Feeds.

## Features Overview

### Feature 1
- **Quick Description:** 1-Click Outlook Email & Attachment Filing with Automated Matter Workflow Triggers. Enables fee earners to file correspondence and extract/index attachments directly into matter timelines from any Outlook environment with a single click, instantly triggering automated next-step tasks, document templates, and milestone updates.
- **Module:** Module 1
- **Key Personas Targeted:** Fee-Earning Solicitors, Associates, Legal Secretaries, and Paralegals.