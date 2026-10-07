---
status: Draft
targetDate: 2027-02-28
period: Q4 FY27
tshirt: M
grr: 17k
kpi_color_grr: emerald
enrolment: 120k
kpi_color_enrolment: emerald
---

# Perfect Portal – PCMS Integration Specification

## Headline
Perfect Portal and PCMS Integration Enables Seamless Quote-to-Matter Workflow with Real-Time Conflict Checking and Bi-Directional Data Synchronisation

## Summary
We are releasing a bi-directional integration between Perfect Portal and PCMS that automates the quote-to-matter conversion process, eliminates manual data entry, and keeps client and matter information synchronised across both systems in real time. Law firm users can now create a quote in Perfect Portal, run a conflict check against PCMS, convert the quote to a matter with a single click, and maintain visibility of case progression without leaving their workflow.

## Problem Statement
Legal practices currently operate Perfect Portal and PCMS as separate, disconnected systems. When a prospect quote is accepted, fee earners must manually re-enter client details, property information, and case type into PCMS, creating duplicate data entry, reconciliation overhead, and risk of transcription error. There is no real-time conflict checking during quote creation, no automated duplicate detection at conversion, and no way to see case progression in Perfect Portal once a matter is created. This friction slows down matter creation, increases administrative burden, and reduces the speed at which firms can convert quotes to active cases.

## Solution
The Perfect Portal–PCMS integration establishes a series of APIs and bi-directional data flows that connect quote creation and conversion in Perfect Portal directly to client and matter creation in PCMS. During quote creation, Perfect Portal calls PCMS to run a real-time conflict check before allowing the quote to proceed. At conversion, Perfect Portal automatically creates a client and matter record in PCMS, carrying across all captured details (client name, contact information, property data, case type, and assigned fee earner). PCMS returns a unique matter reference number that links the two systems. From that point forward, updates to client details in PCMS are pushed back to Perfect Portal, key stage progress is visible to the end user, and documents uploaded by the client via Perfect Portal are automatically filed into the corresponding PCMS matter.

## Customer Impact

| Key Features | Key Benefits | Value & Impact Delivered |
|---|---|---|
| Real-time conflict checking during quote creation | Eliminates risk of inadvertent conflict of interest before quote is accepted | Reduces compliance risk and improves client due diligence |
| Automated duplicate client detection at conversion | Prevents duplicate client records and reconciliation errors in PCMS | Maintains data integrity and reduces administrative overhead |
| One-click quote-to-matter conversion with auto-population | Eliminates manual re-entry of client, property, and case details | Reduces matter creation time by up to 60% and cuts administrative burden |
| Bi-directional client detail synchronisation | Keeps client name, contact info, and address aligned across both systems automatically | Eliminates reconciliation workflows and ensures single source of truth |
| Matter reference number linkage | Establishes persistent link between Perfect Portal quote and PCMS matter for all future communication | Enables seamless document filing and case progression visibility |
| Real-time key stage and workflow visibility | End users see case progression without leaving Perfect Portal or navigating to PCMS | Improves user experience and accelerates decision-making |
| Automated client document upload to PCMS | Documents supplied by clients via Perfect Portal are automatically filed into the corresponding matter | Eliminates manual document handling and improves file completeness |

## Customer Quote (Imagined)
> "The integration has cut our matter creation time in half. We no longer have to manually enter client details twice, and the conflict checking gives us confidence we're catching potential issues before we even accept the quote. It's exactly what we needed to scale our quote-to-matter process without hiring extra administrative staff." — Senior Partner, Mid-Market Legal Practice

## Call to Action
Validate this integration specification with the Perfect Portal and PCMS technical teams, confirm API contracts and authentication methods, and schedule a technical design session to define error handling, retry behaviour, and account-linking workflows. Contact the Product Owner to discuss go-live planning and training requirements for your practice.

## Internal Notes
Status: Draft v0.1 (06 August 2026). Specification covers 11 core interfaces (INT-01 through INT-11) and one configuration item (CFG-01). Key dependencies: confirmation of case type mapping scope (single lookup vs. per-office configuration), authentication and document storage approach for client uploads, embedded UI approach for key stage visibility (under review by Andrew Wilkins), and account-linking flow for law firm users. Next major milestone: technical API contract confirmation and case type mapping table agreement. Version history and open questions maintained in source integration specification document.