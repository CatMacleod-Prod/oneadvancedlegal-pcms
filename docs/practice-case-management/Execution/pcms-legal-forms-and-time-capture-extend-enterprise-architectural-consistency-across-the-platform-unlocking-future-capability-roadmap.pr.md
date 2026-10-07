---
status: Draft
targetDate: 2027-08-31
period: Q2 FY28
tshirt: M
---

# Architectural upgrade, wave two

## Release Information
**Product/Module:** PCMS, Legal Forms, Time Capture
**Version:** Wave 2 – Q4 FY26

## Headline
PCMS, Legal Forms, and Time Capture extend enterprise architectural consistency across the platform, unlocking future capability roadmap.

## Summary
Wave Two of our architectural upgrade extends the cloud-native, microservice-driven foundation to Practice Case Management System (PCMS), Legal Forms, and Time Capture modules. This release standardizes API contracts, data governance, and deployment patterns across the entire platform, eliminating architectural silos and positioning all three products for rapid future enhancements in AI-driven quality review, cross-jurisdiction compliance automation, and real-time operational analytics.

## Problem Statement
Legacy architectural fragmentation across PCMS, Legal Forms, and Time Capture creates operational inconsistency, blocks cross-module automation, and slows quarterly feature delivery. Practitioners experience context-switching friction between disconnected systems; compliance teams struggle with fragmented audit trails; and engineering teams face elevated maintenance overhead and reduced deployment velocity. Unified architecture is essential to unlock next-generation capabilities—Matter Quality Review, predictive legal aid submission optimization, and live matter velocity dashboards—that depend on seamless data flow and consistent governance across the entire platform.

## Solution
Wave Two standardizes PCMS, Legal Forms, and Time Capture on a unified event-driven microservice architecture, containerized Azure deployment, PostgreSQL data persistence, and shared governance frameworks. All three modules now operate as bounded contexts within a single platform mesh, sharing common API contracts, centralized audit logging, multi-jurisdiction compliance enforcement, and Open Banking / legal aid integration hooks. This architectural alignment eliminates manual data reconciliation, enables real-time cross-module workflows, and provides engineering teams with a consistent, scalable foundation for rapid quarterly innovation.

## Customer Impact

| Key Features | Key Benefits | Value & Impact Delivered |
|---|---|---|
| Unified event-driven microservice architecture across PCMS, Legal Forms, Time Capture | Seamless cross-module workflows without manual reconciliation; reduced operational friction for practitioners | Practitioners recover 1–2 hours per week from manual data entry and context-switching; engineering velocity increases 30% quarter-over-quarter |
| Standardized Azure Container Apps deployment & PostgreSQL persistence | Consistent performance, reliability, and compliance posture across all three modules | Sub-200ms transaction latency maintained; 99.95% uptime SLA across all products; 100% regulatory audit trail coverage |
| Centralized multi-jurisdiction compliance and audit governance | Dual-jurisdiction SRA / Law Society of Scotland compliance enforced consistently; automated regulatory reporting | Zero compliance drift; audit preparation time reduced by 60%; cross-border matter handling now fully compliant by design |
| Shared legal aid submission and Open Banking integration hooks | Real-time LAA Family, Crown Court LGFS, and SLAB claim submission orchestration; automated bank reconciliation across all practices | Claims submitted 3–5 days faster; reconciliation errors reduced by 85%; cash flow visibility improved for 100+ concurrent users per firm |

## Customer Quote (Imagined)
> "Wave Two feels like a completely different experience—our PCMS, forms, and time capture now talk to each other without us having to chase data around. We're already seeing our billing teams work 40% faster, and our compliance team finally has a single source of truth for all three modules. This is what we've been asking for." — Managing Partner, Mid-Market UK Practice

## Call to Action
Upgrade to Wave Two during your next scheduled maintenance window or contact your account manager to arrange a phased rollout. Access the architectural transition guide and module compatibility matrix in the customer portal. Early adopters will gain priority access to Q1 FY27 AI-driven Matter Quality Review features, available exclusively to Wave Two deployments.

## Internal Notes
Wave Two completes the architectural foundation work begun in Wave One (core PCMS infrastructure). Wave Three (planned Q1 FY27) will introduce AI-driven Matter Quality Review and predictive legal aid optimization, both dependent on this unified data mesh. Ensure all customer success and support teams are trained on the new shared compliance audit model and Open Banking reconciliation workflows before go-live. Monitor early adoption metrics closely; target 85% customer base migration within 60 days of release.