---
status: Draft
targetDate: 2026-11-30
period: Q3 FY27
tshirt: XS
enrolment: 120k
kpi_color_enrolment: emerald
operational: 0
kpi_color_operational: pink
arr: 424.2k
kpi_color_arr: blue
---

# Press Release

## Headline

PCMS Initiates Sprint 17 Technical Discovery Spike to Validate Bundledocs Cloud API and De-Risk Downstream Implementation

## Summary

Advanced has initiated a dedicated technical discovery spike in Sprint 17 (LSS-2374) to investigate and validate the integration between the Practice Case Management System (PCMS) and the third-party Bundledocs Cloud REST API. An engineering spike lead will exercise sandbox endpoints, evaluate the `.NET` SDK, resolve architectural unknowns around authentication and document streaming, and establish validated story point estimates for downstream delivery stories (US-2 to US-10). This discovery sprint establishes the technical feasibility required before committing engineering resources to production development.

## Problem Statement

Transitioning legal court bundling workflows from legacy desktop systems (ALB) to cloud-native PCMS involves third-party integration unknowns across API behavior, OAuth2 authentication, payload formats, and event polling mechanics. Without empirical sandbox validation, downstream story estimates (US-2 to US-10) carry high uncertainty and risk under-estimation or delivery blockers. Development teams require concrete technical findings on PCMS trigger points, parallel document transfer feasibility, credential security, and failure state semantics before pulling implementation stories into active sprints.

## Solution

Sprint 17 delivers a comprehensive technical feasibility spike (LSS-2374) where engineering exercises the Bundledocs REST API (`swagger.json`) and `.NET` SDK against a dedicated developer sandbox account. The spike produces a definitive technical findings note detailing token acquisition/expiry, endpoint request/response contracts, event action codes, rate limits, and PCMS storage architecture. Additionally, the spike delivers validated story point and day estimates with MoSCoW priority classifications for all downstream stories (US-2 through US-10), surfacing all architectural risks and dependencies to Product before build commitment.

## Customer Impact

| Key Features                                     | Key Benefits                                                                                    | Value & Impact Delivered                                                                            |
| ------------------------------------------------ | ----------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| Empirical Bundledocs API Sandbox Validation      | Direct testing of authentication, create-bundle, template, tree, upload, and download endpoints | Eliminates architectural blindspots and prevents integration blockers during production development |
| Validated Story Point Estimation (US-2 to US-10) | Engineering-backed point and day estimates with clear complexity rationales                     | Guarantees predictable sprint planning and accurate delivery velocity for future bundling releases  |
| Architectural Trigger & Storage Specification    | Defined PCMS data context, trigger hooks, and PDF matter filing architecture                    | Establishes robust, compliant design patterns for fee-earner matter document integration            |
| Security & Credential Isolation Architecture     | Defined sandbox credential handling, in-memory token lifecycle, and rotation protocols          | Guarantees compliance with SRA data governance standards and secures API integration boundaries     |
| Comprehensive Risk & Dependency Register         | Early identification of rate limits, polling intervals, and .NET SDK functional gaps            | Protects product roadmaps by resolving third-party vendor dependencies prior to feature build       |

**Business case data:**

| Detail       | GRR risk                                   | iARR opportunity            | Blocked Enrolment  |
| ------------ | ------------------------------------------ | --------------------------- | ------------------ |
| Cohort 1/2/3 | Existing referral revenue stream (minimal) | £424.2k of ARR (2x NB opps) | £120k (Streathers) |