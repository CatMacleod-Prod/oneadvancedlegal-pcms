---
status: Draft
targetDate: 2026-11-30
period: Q3 FY27
tshirt: S
---

# Press Release



## Headline
Internal Tech Spike: Engineering Investigates Strategy and Tooling for Multi-Tenant Database Schema Harmonisation

## Summary
This internal technical spike investigates database schema divergence across PCMS customer instances to design a unified harmonisation and migration blueprint. The engineering team will audit schema variations, test automated alignment scripts in staging, and establish a validated roadmap for future zero-downtime schema standardisation. No production schema updates or customer-facing changes will be deployed during this exploratory phase.

## Problem Statement
Historical deployments and tenant-specific customizations have caused database schema drift across law firm environments. This divergence increases maintenance overhead, complicates compliance auditing, and blocks automated continuous deployment pipelines. Engineering requires a comprehensive audit of all schema variances and a validated, low-risk technical strategy before executing live database migrations across customer instances.

## Solution
Execute an internal engineering spike focused on: (1) auditing and cataloging all table, index, and constraint discrepancies across customer databases; (2) benchmarking and testing automated, idempotent schema synchronisation scripts in isolated environments; and (3) producing a technical specification and rollout plan to safely execute schema harmonisation in subsequent release cycles.

## Customer Impact

| Key Features | Key Benefits | Value & Impact Delivered |
|---|---|---|
| Comprehensive Schema Variance Audit | Complete visibility into schema divergence and tenant discrepancies across all environments | 100% discovery of schema anomalies prior to executing any production changes |
| Migration Strategy & Automated Script Prototyping | Prototyped and benchmarked migration tooling tested safely in staging environments | De-risks production execution and establishes a validated zero-downtime migration strategy |
| Harmonisation Technical Specification & Rollout Plan | Clear architectural blueprint and prerequisites for upcoming engineering sprints | Removes technical blockers for automated CI/CD pipelines and long-term platform consistency |