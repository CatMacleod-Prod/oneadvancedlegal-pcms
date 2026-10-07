---
status: Draft
---

# UX Design Document

## Design Vision

### Product Experience Goals
- **Frictionless Matter & Cross-Border Practice Velocity:** Enable fee earners, solicitors, and advocates to create, locate, review, draft, and file matter documentation within seconds across both English and Scots law jurisdictions, recovering up to 2.5 hours of unbillable administrative time per day.
- **Cognitive Clarity in High-Density Workspaces:** Provide legal practitioners (partners, solicitors, paralegals, cashiers, criminal litigators, and administrators) with clean, structured desktop layouts that present deep matter histories, cross-border workflow milestones, legal aid claims (LAA Family, Crown Court LGFS, and SLAB), and financial ledgers without cognitive overload.
- **Fail-Safe Multi-Jurisdiction Compliance & Accounts Governance:** Make adherence to Solicitors Regulation Authority (SRA) Standards and Law Society of Scotland Accounts Rules completely transparent and protective through proactive visual indicators, multi-tier digital authorization barriers, and automated Open Banking reconciliation feedback.
- **Seamless Desktop, Office 365 & Dual-Outlook Continuity:** Deliver an uninterrupted filing, drafting, and real-time co-authoring experience across web workspaces, Microsoft Word/Excel via SharePoint Online, and both Classic Win32 Outlook desktop and New Outlook for Windows / Outlook on the Web.
- **Continuous User Satisfaction Through Quarterly Delighters:** Ensure ongoing practitioner delight through an agile quarterly enhancement cadence that continuously refines email filing heuristics, document micro-interactions, and real-time operational realization visibility without disrupting core workflows.

### Design Principles
- **Clarity Over Novelty:** Legal professionals, cashiers, and litigators prioritize speed, precision, and predictability over decorative trends. Standardized dense data tables, explicit action labels, and standard keyboard conventions take precedence across all modules.
- **Proactive Context & State Preservation:** Retain user state, active filters, selected matter contexts, unsubmitted transfer requisitions, live document co-authoring sessions, and draft legal aid / LGFS submissions across tab switches and multi-window workflows.
- **Fail-Safe Financial & Data Governance:** Every irreversible or high-risk action (client-to-office money transfers, permanent document purges, external court bundle transmissions, LAA/SLAB claim submissions, ethical wall reconfigurations) includes clear confirmation barriers, whereas daily retrieval, note taking, and email filing operate with instantaneous zero-latency feedback.
- **Continuous Incremental Enhancement:** Surface new quarterly productivity shortcuts and workflow micro-services through unobtrusive discovery tooltips and non-breaking UI enhancements that adapt to practitioner habits over time.
- **Accessible by Default (OneAdvanced Standards):** Ensure all workflows are completely accessible without specialized modes—featuring robust screen-reader semantic markup, full keyboard traversal, and high-contrast visual cues compliant with WCAG 2.1/2.2 AA.

### Brand Alignment
The user experience reflects OneAdvanced's brand commitment to reliability, enterprise rigor, modern legal productivity, and human-centered design. Visual styling balances a professional legal aesthetic with crisp modern typography, calm focused palettes, and purposeful micro-interactions that communicate trust, data integrity, and compliance assurance across private practice and publicly funded legal sectors.

## User Research Summary

### Target Users
- **Primary**: Fee Earners, Solicitors & Advocates — High-volume legal practitioners managing matter lifecycles, milestone workflows (Conveyancing, Family, Probate/Executry, Litigation), dynamic precedent drafting, live Office 365 co-authoring, and 1-click email/document filing across Classic and New Outlook.
- **Secondary**: Criminal Litigators & Public Funding Specialists — Legal aid practitioners managing Crown Court representations, verifying Pages of Prosecution Evidence (PPE) counts, calculating LGFS graduated fee tariffs, logging trial days, and lodging direct digital claims with the Legal Aid Agency (LAA) and Scottish Legal Aid Board (SLAB).
- **Tertiary**: Paralegals & Legal Assistants — Operational power users executing high-volume client onboarding (eIDV/AML verification), batch document filing, HMCTS/SCTS electronic court bundle collation with Bates stamping, and claim preparation.
- **Quaternary**: Legal Cashiers, COFAs & Scottish Cashroom Partners — Financial and compliance gatekeepers overseeing dual-jurisdiction client and office ledgers, multi-tier transfer requisition sign-offs, purchase ledger invoice approvals, and automated Open Banking reconciliations.
- **Executive**: Practice Partners, COLPs & Firm Administrators — Senior stakeholders monitoring real-time department realization rates, fee-earner billable utilization, WIP aging, matter velocity, statutory filing deadlines, ethical wall restrictions, and SRA / Law Society of Scotland audit trails.

### Pain Points Addressed
- **Chargeable Time Erosion in Document & Email Filing**: Addressed via global instant search (`Ctrl+K`), predictive 1-click matter filing drawers in Classic and New Outlook, recent matter pinning, and quarterly email shortcut enhancements that surface case records in under 2 clicks.
- **Complex Crown Court Legal Aid & LGFS Billing Friction**: Addressed through integrated PPE evidence counters, automated offense class tariff calculators, and direct digital LAA/SLAB submission pipelines that eliminate manual double-entry.
- **Multi-Jurisdiction Compliance & Accounts Risk**: Addressed through dynamic regulatory rule-switching between SRA and Law Society of Scotland Accounts Rules, automated cleared-funds validation, and digital multi-tier sign-off workflows for client-to-office requisitions.
- **Lack of Actionable Realisation & Productivity Visibility**: Addressed via lightweight, zero-latency operational realization and matter velocity dashboards embedded directly into partner and cashier workspaces.
- **High Administrative Burden in Court Bundling & Cross-Border Conveyancing**: Addressed using drag-and-drop bundle builders with HMCTS and SCTS presets, automated Bates stamping, and structured milestone stage-gates for Land Registry and Registers of Scotland workflows.
- **Version Sprawl During Collaborative Drafting**: Addressed via native Microsoft Graph / SharePoint Online co-authoring indicators, live presence chips, and automatic version history tracking.

## Information Architecture

### Site Map / App Structure
- **Global Header**: Firm Identity, Global Omnibox Search (`Ctrl+K`), Active Matter Quick-Switcher, Dual-Jurisdiction Indicator (EW / SCT), Quarterly Delighter Notification Hub, System Notifications, and User Profile/Settings.
- **Primary Navigation (Left Rail)**:
  - **Dashboard / My Workspace**: Active assigned matters, urgent workflow tasks, pending requisition approvals, recent documents, and personal billable utilization metrics.
  - **Matters & Cases**: Comprehensive matter directory, active case workspaces, cross-border workflow templates (Conveyancing, Probate/Executry, Family, Criminal Defence, Litigation), and matter creation wizard.
  - **Documents & Precedents**: Centralized repository search, precedent template library, corporate document storage, and Office 365 co-authoring launchpad.
  - **Bundling & Production**: Electronic court bundle builder, transaction bibles, automated Bates stamping presets, and HMCTS / SCTS export hub.
  - **Legal Accounts & Cashroom**: Dual-jurisdiction client and office ledgers, single/bulk transfer requisitions, purchase ledger invoice approvals, and Open Banking bank reconciliation.
  - **Public Funding & Legal Aid**: LAA Family Fixed Fee claims, Crown Court LGFS (Litigators' Graduated Fee Scheme) claims management, SLAB Advice & Assistance / ABWOR / Civil submissions, and tariff tracking.
  - **Operational & Realisation Reports**: Practice group realization rates, fee-earner billable utilization, WIP aging analysis, matter milestone velocity, and department lockup tracking.
  - **Audit & Governance**: SRA and Law Society of Scotland compliance logs, Subject Access Requests (SARs), retention schedules, and ethical wall rule configurations.
  - **Settings & Firm Admin**: Entra ID user directory, branch office management, practice groups, custom metadata fields, and integration connectors.
- **Matter Workspace (Contextual Hub)**:
  - **Overview**: Case summary, jurisdiction badge, client details, assigned fee earners, key statutory dates, and financial balances (Client vs. Office).
  - **Workflow & Milestones**: Interactive stage-gate tracker, prerequisite task chains, and automated onboarding (eIDV/AML) verification status.
  - **Document Repository**: Folder hierarchy, filtered lists, version timelines, SharePoint Online sync status, Office 365 co-authoring triggers, and bulk CRUD actions.
  - **Correspondence**: Synced Outlook emails, attachments, client notes, and dispatch logs.
  - **Accounts & Billing**: Matter-specific client/office ledger entries, unbilled time, disbursement logs, and transfer requisitions.
  - **Legal Aid & Crown Court Claims**: Matter-level LAA/SLAB certificate details, PPE prosecution evidence page counter, LGFS graduated fee calculators, and claim submission history.
  - **Bundles & Exhibits**: Compilations, court bundles, and transaction closing packs.
  - **Access & Security**: Matter-specific ethical walls, collaborator permissions, and tamper-evident audit logs.

### Navigation Model
- **Primary Navigation**: Collapsible persistent left-hand navigation rail with iconic (64px) and expanded (240px) modes, featuring active section badges and notification pips.
- **Secondary Navigation**: Horizontal contextual tabs within the Matter Workspace (Overview, Workflow, Documents, Correspondence, Accounts, Legal Aid / LGFS, Bundles, Audit) combined with split-pane master-detail sub-views.
- **Search**: Centrally positioned global Omnibox (`Ctrl+K` / `Cmd+K`) supporting multi-entity queries (client name, matter ID, document title, full-text OCR content, PPE reference, legal aid certificate) with instant keyboard navigation and recent history.

### Content Hierarchy
- **Level 1 (Top Level / Portfolio)**: Cross-matter firm dashboards, global document search, cashroom financial reconciliations, firm-wide legal aid queues, operational realization metrics, and macro administrative oversight.
- **Level 2 (Matter Level)**: Specific matter context containing case metadata, jurisdiction rules (EW vs SCT), workflow milestone state machines, assigned fee earners, PPE metrics, and matter-specific sub-modules.
- **Level 3 (Entity / Record Level)**: Individual document previews, transfer requisition sign-off cards, LAA/LGFS/SLAB claim line items, version history logs, bundle compilation tables, and permission management dialogs.

## Interaction Design

### Interaction Patterns
- **Dense Master-Detail Data Grids**: High-density table views with sorting, multi-column filtering, inline status badges, and quick-action hover toolbars for rapid Create, Retrieve, Update, and Share operations across matters and ledgers.
- **Dual-Outlook Contextual Filing Panel**: Non-intrusive side-panel in Classic Win32 and New Outlook with predictive matter matching, 1-click filing, attachment multi-select, and automatic time recording prompts.
- **Split-View Document & Reconciliation Drawers**: Non-modal right-side preview drawer allowing users to inspect document text, version diffs, PPE evidence schedules, or Open Banking transaction matching without losing context of the primary list.
- **Live Office 365 Co-Authoring & Presence Badges**: Collaborative document header showing real-time avatar chips of active co-authors in Word/Excel, lock indicators, and automated SharePoint Online version synchronizations.
- **Crown Court LGFS & PPE Evidence Analyzer**: Interactive multi-step calculator allowing litigators to verify served prosecution pages, input offense class and trial days, inspect tariff breakdowns, and submit electronic claims in 1 click.
- **Multi-Tier Digital Sign-Off Modals**: Structured approval overlays for cashroom requisitions requiring dual authorization (Fee Earner $\rightarrow$ Cashroom Partner / COFA) with instant cleared-funds balance checks.
- **Drag-and-Drop Batch Management**: Multi-select drag-and-drop capabilities for filing loose files into matter folders, reordering bundle exhibits, and bulk tagging metadata.

### Micro-interactions
- **Instant Save & Auto-Sync Indicators**: Subtle status badges in document headers ("All changes saved to SharePoint", "Syncing...", "Live Lock by D. Smith") providing reassurance without interrupting workflow.
- **Filing Feedback & Toast Confirmations**: Compact bottom-right toast notifications confirming successful filing, legal aid submission, or batch updates with an instant "Undo" or "View Record" action link (auto-dismissing after 5 seconds).
- **Quarterly Delighter Micro-Tips**: Non-intrusive contextual discovery pips highlighting new quick-win shortcuts (e.g., "New: Drag attachments directly into subfolders") that auto-dismiss upon first interaction.
- **Open Banking Match Confidence Feedback**: Interactive confidence chips (e.g., "98% Auto-Match", "Review Suggested") with single-click reconciliation confirmation.
- **Realisation Metric Trend Indicators**: Compact inline sparklines and color-coded delta chips (+4.2% billable utilization vs target) on partner and fee-earner overview cards.
- **Copy Link & Share Hover Feedback**: Tooltip transition from "Copy Matter Link" to "Copied to Clipboard!" with checkmark micro-animation on user click.
- **Loading & Skeleton States**: Smooth pulsing skeleton rows during data table hydration to maintain visual layout stability and perceived sub-200ms performance.

### Error Handling
- **Validation**: Real-time inline field validation with debounced formatting checks (e.g., matter reference syntax, LAA/LGFS certificate format, SLAB legal aid reference, PPE page counts, required SRA/Law Society retention class selection) highlighting fields before form submission.
- **Error Messages**: Constructive, non-technical, and empathetic phrasing explaining the exact issue and remediation step (e.g., "Client-to-office transfer cannot exceed available cleared client funds of £1,450.00. Please adjust requisition amount or wait for pending lodgments to clear.").
- **Recovery**: Automatic draft persistence in local storage for matter notes, requisition drafts, and legal aid / LGFS claim line items; single-click retry options for transient network failures; recycle bin with 30-day soft-delete recovery before permanent purge.

## Visual Design Direction

### Color System
- **Primary**: Deep Legal Navy (`#0F2537` for primary navigation and high-emphasis headers) and Cobalt Accent (`#0066CC` for primary action buttons, active tabs, and interactive focus rings).
- **Secondary**: Slate Neutral (`#4A5568` for secondary text and subheadings), Cool Gray Surface (`#F8FAFC` for page backgrounds), and Crisp White (`#FFFFFF` for workspace cards and table surfaces).
- **Semantic**:
  - Success / Compliant: Forest Green (`#15803D` background, `#166534` text)
  - Warning / Attention: Amber (`#B45309` background, `#92400E` text)
  - Error / Restricted Wall / Deficit: Crimson Red (`#B91C1C` background, `#991B1B` text)
  - Information / In Progress: Blue Slate (`#1D4ED8` background, `#1E40AF` text)
  - Scottish Law Accent: Heather Purple (`#6B21A8` background, `#581C87` text) for clear Scots law / SLAB / SCTS visual tagging.
  - Criminal Legal Aid / LGFS Accent: Teal Slate (`#0D9488` background, `#115E59` text) for Crown Court PPE metrics and claims.

### Typography
- **Headings**: Inter / System Segoe UI, Bold/Semi-Bold (H1: 24px/32px line-height; H2: 20px/28px; H3: 16px/24px).
- **Body**: Inter / System Segoe UI, Regular/Medium (Body Regular: 14px/20px; Body Small: 12px/16px for secondary metadata).
- **UI Elements**: 13px/18px Medium for table cells, button labels, and navigation links; 11px/14px Bold Monospace for Matter References, Bates Stamp codes, PPE page counts, and Legal Aid Certificate numbers.

### Spacing & Layout
- **Grid System**: 12-column responsive grid with flexible layout containers, fixed left-rail navigation (64px collapsed, 240px expanded), and responsive right preview pane (400px fixed or 50% split).
- **Spacing Scale**: 8pt grid base unit (4px `xs`, 8px `sm`, 16px `md`, 24px `lg`, 32px `xl`, 48px `2xl`).
- **Breakpoints**: Desktop-optimized layout scaling gracefully down to laptop and tablet formats.

### Iconography
- **Style**: Modern 2px outlined stroke style with rounded terminals, optimized for high legibility at 16x16px and 20x20px.
- **Library**: Lucide Icons / Fluent System Icons (for seamless visual alignment with Microsoft 365 and Outlook desktop suite).

## Accessibility

### Standards
- **WCAG Level**: WCAG 2.1 & 2.2 Level AA Compliance across all screens and components, strictly adhering to OneAdvanced Accessibility Design Guidelines.
- **Key Requirements**: Minimum 4.5:1 text-to-background contrast for standard text; minimum 3:1 contrast for all UI controls and interactive boundaries; zero keyboard trapping; strict logical DOM tab ordering; visible 2px focus indicators on all focusable elements.

### Considerations
- **Screen Readers**: Full ARIA landmark structure (`role="main"`, `role="navigation"`, `role="complementary"`), dynamic `aria-live="polite"` regions for asynchronous save/sync, co-authoring changes, and Open Banking matching updates, and comprehensive `aria-label` tags for icon buttons.
- **Keyboard Navigation**: Complete keyboard operability for data grids (arrow key cell navigation, `Enter` to open, `Space` to select, `Esc` to dismiss drawers), with visible high-contrast focus rings (`#0066CC` outline with 2px offset).
- **Color Contrast**: All status chips, badges, and warning banners pair color coding with clear textual labels and distinct geometric iconography to avoid relying on color alone (e.g., pairing green badges with checkmarks and red flags with warning shields).
- **Motion**: Full adherence to `prefers-reduced-motion` media queries; all transition animations (drawers, modal popovers, toasts) degrade instantly to zero-duration opacity shifts for users with vestibular sensitivities.

## Responsive Design

### Breakpoints
- **Mobile**: 320px – 767px (Read-only matter search, notification viewing, quick time recording, realization summary cards, and urgent document access).
- **Tablet**: 768px – 1023px (Compact matter workspace, stacked master-detail views, touch-friendly list actions, and requisition approvals).
- **Desktop**: 1024px – 1920px+ (Primary production environment with dense multi-column grids, split-screen document preview drawers, dual-ledger cashroom views, PPE evidence calculators, realization dashboards, and full side-by-side bundling/reconciliation tools).