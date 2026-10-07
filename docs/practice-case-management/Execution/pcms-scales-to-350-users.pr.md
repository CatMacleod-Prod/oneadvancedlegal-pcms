---
status: Draft
targetDate: 2027-02-28
period: Q4 FY27
tshirt: M
---

# Press Release

## Headline
PCMS Unlocks Enterprise-Scale Concurrency to Power 350+ Active Fee Earners with Sub-Second Performance

## Summary
The Practice Case Management System (PCMS) introduces a high-scale architectural upgrade that expands concurrent user capacity from 100 to 350+ active fee earners and legal assistants without performance degradation. By decoupling heavy reporting and document generation workloads, optimizing critical SQL stored procedures, introducing pre-calculated dashboard read models, and enabling horizontal multi-instance scaling, legal practices can scale operations smoothly across multi-office teams.

## Problem Statement
Mid-market and large law firms operating with 100+ concurrent staff encounter severe response lag, UI freezes, thread-starvation cascades, and database lock-contention during peak operational hours. Heavy batch document assembly, background reporting queries, and complex dashboard widget calculations compete directly for interactive application threads, degrading client onboarding and matter management workflows for fee earners.

## Solution
This release re-architects core platform services to support 350 active concurrent users with consistent P95 sub-3-second transaction times. We extract reporting and document generation onto isolated background services, replace heavy dashboard SQL calculations with pre-computed read models, resolve database lock bottlenecks in matter onboarding, and introduce horizontal App Service scale-out with sticky session routing.

## Customer Impact

| Key Features | Key Benefits | Value & Impact Delivered |
|---|---|---|
| 350-User Concurrency & Multi-Instance Scaling | Eliminates system slowdowns and thread starvation during peak morning and billing periods across multi-office teams. | Sustained P95 ≤ 3s response times across 21 core workflows at 350 concurrent sessions. |
| Pre-Calculated Dashboard Read Models | Sub-second dashboard loading with zero impact on transactional database operations. | 98% reduction in dashboard CPU consumption and 87% reduction in database logical reads. |
| Isolated Reporting & Async Doc Generation | Fee earners can generate complex court bundles, correspondence, and reports without locking interactive screens. | 100% elimination of interactive session deadlocks caused by heavy document merge operations. |
| Core Journey & Onboarding Optimization | Rapid, friction-free client and matter creation without sequential lock contention. | 99% faster client creation response times (P95 reduced to under 2 seconds). |