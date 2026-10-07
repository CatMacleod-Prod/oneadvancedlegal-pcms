---
status: Draft
---

# Architecture Document

## System Overview

### Purpose
The Practice Case Management System (PCMS) Core Application is an enterprise legal practice, case management, and legal accounting SaaS platform engineered for mid-market and large UK and cross-border legal practices (50 to 500+ staff, supporting 100+ to 450 concurrent fee earners across England, Wales, and Scotland). It operates as the authoritative operational system of record for matter lifecycles, cross-border automated practice workflows (Conveyancing across Land Registry and Registers of Scotland, Probate/Executry, Family, Litigation, and Criminal Defence), digital client onboarding (eIDV/AML), dual-jurisdiction legal accounting (compliant with both Solicitors Regulation Authority and Law Society of Scotland Accounts Rules), Open Banking reconciliations, direct digital public funding submissions (Legal Aid Agency Family Fixed Fee schemes, LAA Crown Court Litigators' Graduated Fee Scheme / LGFS, and Scottish Legal Aid Board Online claims), AI-driven Matter Quality Review (MQR), user-defined dynamic custom fields (UDF), operational realisation and matter velocity reporting, dynamic ethical walls, and regulatory audit trails. The system processes up to 500 cases per day per firm with sub-200ms interactive transaction latency, integrating seamlessly across Classic Win32 Outlook and New Outlook for Windows/Web, while delegating raw document binary persistence and heavy PDF court bundling to the external Document Management & Integration Service.

### Architecture Style
Strangler-Fig Hybrid Architecture transitioning from a legacy Modular Monolith (Wisej-3 / .NET Framework 4.8 / .NET 7) into bounded-context cloud-native .NET 8 REST APIs, containerized Azure Container Apps (ACA) microservices, and serverless Azure Durable Functions coordinated via Azure API Management (APIM) and Azure Service Bus.

### Key Design Principles
- **Tenant-Isolated Compute & Data Partitioning**: Enforces strict customer tenancy isolation via dedicated per-tenant Azure App Service instances and per-tenant Azure SQL databases (`sqldb-adv-uks-{env}-{customer}-001`), resolved dynamically at runtime using `organisation_reference` (`OrgRef`) claims from JWT tokens and Azure Key Vault secrets.
- **Strangler Fig API Modernisation**: Incrementally decouples business capabilities from the legacy Wisej-3 monolith into standalone .NET 8 microservices (`pcms-api`, `udf-api`, `workflow-api`, `legal-ai-mqr`) fronted by a unified Azure API Management (APIM) gateway.
- **Asynchronous Task & Event-Driven Processing**: Decouples CPU-intensive and long-running workloads (Exchange Graph notifications, PDF document generation, MQR compliance checks) using Azure Service Bus queues/topics, KEDA-scaled Azure Container Apps, and Azure Durable Functions.
- **Dual-Environment Microsoft 365 Continuity**: Provides zero-defect, high-performance integration across both legacy Classic Outlook (Win32/VSTO) and modern New Outlook / OWA (React 19 + Vite Office.js Add-in) for 1-click filing, contact synchronization, and matter correspondence tracking.
- **Dual Regulatory Compliance (SRA & Law Society of Scotland)**: Zero-tolerance enforcement of both SRA Accounts Rules and Law Society of Scotland Accounts Rules (including invested client funds, Scottish ledger balancing, and statutory audit reporting), UK GDPR sovereignty within Azure UK South, and immutable tamper-evident audit trails.
- **AI-Driven Matter Quality Review (MQR)**: Automated background compliance evaluation and matter review pipeline executing asynchronous heuristic and AI rule checks against open legal matters via scheduled Azure Functions and Service Bus worker pipelines.
- **Decoupled Document Binary Delegation**: Defers all heavy document binary storage, SharePoint Graph API interactions, and asynchronous PDF court bundling (compliant with MoJ and Scottish Courts and Tribunals Service) to the external Document Management Service via message queues and REST contracts.

## System Context

### External Systems
- **Azure API Management (APIM)**: Centralized enterprise API gateway exposing unified REST endpoints (`/legal/pcms/*`, `/legal/udf/*`, `/legal/workflow/*`, `/legal/mqr/*`, `/legal/outlook-addin/*`) with policy-driven JWT token validation, rate-limiting, and routing.
- **Microsoft Graph API & SharePoint Online**: Microsoft 365 cloud fabric providing bidirectional Exchange mailbox sync (Emails, Events, Tasks) via webhooks and delta queries, alongside SharePoint Online document libraries for authoritative binary persistence and Office 365 co-authoring.
- **OneAdvanced Identity Platform / Azure AD B2C**: Enterprise identity provider issuing OpenID Connect (OIDC) / OAuth 2.0 JWT access tokens containing user identifiers, role scopes, and the tenant `organisation_reference` (`OrgRef`) claim.
- **Document Management & Integration Service**: Dedicated .NET microservice managing Microsoft Graph API tokens, SharePoint folder provisioning, document metadata pointers, and asynchronous court bundling for English Courts and Scottish Courts and Tribunals Service (SCTS).
- **Open Banking Aggregation Gateway (FCA-Regulated AISP/PISP)**: Secure banking API gateway providing automated, read-only transaction feeds and statement synchronization for client and office bank accounts.
- **Judicial & Public Funding Gateways (LAA & SLAB)**: External integration endpoints for direct digital submission of Legal Aid Agency (LAA) Family Fixed Fee, Crown Court LGFS graduated fee claims, and Scottish Legal Aid Board (SLAB Online) claims.
- **Digital Onboarding & eIDV/AML Service Providers**: Third-party compliance providers (e.g., LexisNexis, Creditsafe, Experian) conducting electronic identity verification, anti-money laundering checks, and source-of-funds validation across UK jurisdictions.

### Users & Actors
- **Equity & Salaried Partners**: Executive practice leads and Cashroom Partners in England, Wales, and Scotland monitoring department realization rates, matter profitability, fee-earner capacity, billing velocity, and firm-wide regulatory compliance.
- **Compliance Officers (COFA, COLP & Scottish Cashroom Managers)**: Financial and legal gatekeepers managing SRA and Law Society of Scotland client/office ledgers, single and bulk transfer requisitions, purchase ledger invoice approvals, and automated Open Banking reconciliations.
- **Solicitors, Advocates & Senior Associates**: Primary fee earners conducting matter intake, tracking statutory deadlines, executing workflow milestones, recording chargeable time, and managing client correspondence via Outlook.
- **Criminal Defence Litigators & Legal Aid Specialists**: Fee earners managing Crown Court representations, calculating LGFS graduated fee tariffs, logging Pages of Prosecution Evidence (PPE), tracking trial days, and lodging public funding claims.
- **Paralegals & Legal Secretaries**: Operational legal staff handling matter intake forms, eIDV onboarding verification, document collation, and billing claim preparation for LAA and SLAB schemes.
- **Platform Admins & DevOps Engineers**: Operations personnel managing continuous delivery pipelines (Harness), cloud infrastructure provisioning (Terraform), and system monitoring across tenant instances.

### Components
#### Wisej-3 Web Monolith (`oneadvancedlegal-pcms`)
- **Responsibility**: Delivers the primary desktop-grade web application UI, running legacy WinForms-style business logic (`IRIS.Law.*`), domain models, DxDashboard, and in-process `Solicitors.WebApi` endpoints for legacy client interaction.
- **Technology**: Wisej-3 (.NET 4.8 / .NET 7 hybrid) hosted on per-customer dedicated Azure App Service instances (`app-adv-uks-{env}-lc-<customer>`).
- **Interfaces**: Stateful WebSockets and HTTP/HTTPS to client browsers; internal domain calls; outbound HTTPS to APIM and Exchange Service.

#### Modern PCMS Integration API (`oneadvancedlegal-pcms-api`)
- **Responsibility**: Exposes modern domain REST APIs for matter management, client entities, fee earners, billing codes, share-link generation, and document metadata routing under `/v1/[controller]`.
- **Technology**: ASP.NET Core (.NET 8) Web API on shared App Service (`app-adv-uks-{env}-api-001`), Entity Framework Core with dynamic multi-tenant `DbContextFactory`.
- **Interfaces**: RESTful HTTPS under APIM route `/legal/pcms/*`; invokes Document Generation HTTP starter; connects to Azure SQL and Azure Key Vault.

#### User Defined Fields API (`oneadvancedlegal-udf-api`)
- **Responsibility**: Manages dynamic, tenant-specific custom fields, picklists, validation rules, custom record types, and import/export schemas without requiring core database schema changes.
- **Technology**: ASP.NET Core (.NET 8) Web API on App Service, utilizing `CustomFieldsDbContext` connected to a dedicated UDF SQL Database with Azure Redis Cache for schema/token caching.
- **Interfaces**: RESTful HTTPS under APIM route `/legal/udf/v1/workplaces/{workplaceRef}/*`.

#### Workflow API (`oneadvancedlegal-workflow-api`)
- **Responsibility**: Manages cross-border practice workflow automation, milestone transitions (Conveyancing for Land Registry/Registers of Scotland, Family, Probate, Criminal Defence), prerequisite task chains, and automated stage gates.
- **Technology**: ASP.NET Core (.NET 8) Web API with Clean Architecture and EF Core.
- **Interfaces**: RESTful HTTPS under APIM route `/legal/workflow/*`; integrates with Azure Service Bus for asynchronous workflow events.

#### Exchange Sync Service (`oneadvancedlegal-pcms-exchange-service`)
- **Responsibility**: Manages high-throughput, bidirectional Microsoft Exchange calendar, email, task, and contact synchronization via Microsoft Graph API webhooks and delta queries.
- **Technology**: Containerized .NET 8 background workers running on Azure Container Apps (ACA) in a dedicated environment (`cae-adv-pcmsexchange-uks-{env}`) with KEDA auto-scalers. Consists of:
  - `ca-pcms-webhook`: Webhook handler receiving Graph change notifications and pushing them to Service Bus (`graph-notifications`).
  - `ca-pcms-notifproc`: Notification processor consuming Service Bus messages to execute Graph delta queries and synchronize records.
  - `ca-pcms-deltaproc`: Scheduled delta processor maintaining subscriptions, renewing tokens, and executing catch-up synchronizations.
- **Interfaces**: Ingress HTTPS endpoint `POST /api/graph/notifications`; Azure Service Bus producer/consumer; SQL database updates via `ExchangeSyncStore`.

#### Document Generation Service (`oneadvancedlegal-pcms-document-generation`)
- **Responsibility**: Executes asynchronous, serverless legal document generation, OpenXML token merging, and precedent rendering.
- **Technology**: Azure Durable Functions (.NET 8 Isolated Worker) on dedicated App Service Plan (`plan-adv-uks-{env}-doc-gen-001`).
- **Interfaces**: HTTP starter endpoint `POST /api/orchestrators/DocumentGenerationOrchestrator/{jobId}`; downstream FQN resolver API calls via APIM; stores outputs in Azure Blob Storage.

#### Matter Quality Review Engine (`legal-ai-mqr`)
- **Responsibility**: Evaluates open legal matters against compliance rubrics, regulatory standards, and quality criteria using AI and rule-based evaluation workers.
- **Technology**: ASP.NET Core (.NET 8) API (`app-adv-uks-{env}-mqr-001`), Azure Functions processor (`func-adv-uks-{env}-mqr-001`), dedicated SQL database (`sqldb-adv-uks-{env}-mqr-001`), and Azure Service Bus queue (`oneadvancedlegal-mqr`).
- **Interfaces**: RESTful HTTPS under APIM route `/legal/mqr/*`; Service Bus event-driven triggers.

#### Outlook Add-in Suite
- **Responsibility**: Provides seamless 1-click matter filing, email attachment indexing, contact synchronization, and matter context viewing inside Microsoft Outlook across all platforms.
- **Technology**: Modern React 19 + Vite Office.js Single Page Application hosted on Azure Static Web Apps (`stwapp-adv-uks-{env}-outlook-001`) with a companion .NET 8 backend API (`app-adv-uks-{env}-outlook-001`) and Redis cache, alongside a legacy Win32 COM/VSTO Add-in for Classic Outlook.
- **Interfaces**: RESTful HTTPS calls routed through APIM (`/legal/outlook-addin/*`) and direct Microsoft Graph API calls.

## Data Architecture

### Data Models
- **Client & Organization**: Contact entities, commercial clients, corporate structures, KYC/eIDV verification statuses, and billing profiles.
- **Matter**: Relational core entity capturing unique case references, jurisdiction (England & Wales vs. Scotland), practice area, assigned fee earners, priority levels, workflow milestone states, and lifecycle statuses.
- **Dual-Jurisdiction Legal Accounts & Ledgers**: Multi-currency, double-entry financial models including Client Ledger, Office Ledger, Invested Client Funds Ledger (Scotland), Nominal Ledger, Purchase Ledger, and Disbursement accounts maintaining SRA and Law Society of Scotland compliance.
- **Custom Field & User-Defined Schema (UDF)**: Workplace metadata, dynamic field definitions, field data types, picklist values, and entity extension records stored in the dedicated UDF database.
- **Exchange Sync Mapping**: Maps `TenantId`, Microsoft Graph `SubscriptionId`, `GraphId`, user mailbox pointers, and delta sync watermark tokens.
- **MQR Compliance Evaluation Record**: Stores matter compliance audit results, quality scores, risk classifications, rule execution traces, and partner review flags.
- **Public Funding Claim Record (LAA, LGFS & SLAB)**: Legal aid certificate/representation order numbers, offense class, Pages of Prosecution Evidence (PPE) page counts, trial duration metrics, statutory tariffs, and digital claim transmission payloads.
- **Asynchronous Job Request**: Tracks background job state (Document Generation, Bulk Transfers, Data Import), progress percentage, execution logs, and output Blob Storage references.
- **Audit Event**: Immutable, append-only records capturing user identity, IP address, timestamp, action type, entity ID, changed fields, and regulatory classification in SQL Temporal Tables.

### Data Flow
1. **Interactive API Request & Dynamic Tenancy Resolution**: User or client application issues HTTPS request to Azure APIM; APIM validates JWT access token issued by OneAdvanced Identity and forwards request to `pcms-api` with `organisation_reference` claim; `DbContextFactory` queries Azure Key Vault for the customer's specific SQL connection string and instantiates a scoped `AppDbContext` connected directly to `sqldb-adv-uks-{env}-{customer}-001`.
2. **Exchange Email & Calendar Synchronization**: Microsoft Graph detects an email or event change and posts a notification to `ca-pcms-webhook` (`/api/graph/notifications`); the webhook validates and publishes a message to the `graph-notifications` Service Bus queue; KEDA scales `ca-pcms-notifproc` instances, which consume the message, query Graph delta APIs for message payloads, match the matter reference, and persist records to the customer SQL database.
3. **Asynchronous Legal Document Generation**: Fee earner triggers document assembly in `pcms-api`; the service logs an `AsyncJobRequest` and issues an HTTP POST to the Durable Functions orchestrator (`/api/orchestrators/DocumentGenerationOrchestrator/{jobId}`); the orchestrator resolves field tokens via the FQN Resolver API, merges data bindings into the OpenXML precedent, streams the generated PDF/DOCX to Azure Blob Storage, and marks the job complete.
4. **AI Matter Quality Review (MQR) Pipeline**: Scheduled Azure Function or fee-earner trigger enqueues a matter evaluation request into the `oneadvancedlegal-mqr` Service Bus queue; `ComplianceMessageFunction` processes the event, invokes rule evaluators against PCMS APIs and MQR database models, calculates quality and compliance scores, and publishes review alerts to the MQR UI dashboard.
5. **Dual-Jurisdiction Legal Accounting & Requisition Sign-Off**: Fee earner submits a client-to-office transfer requisition; `pcms-api` verifies cleared client balances against SRA or Law Society of Scotland rules; requisition routes through multi-tier sign-off (Fee Earner -> Cashroom Partner -> COFA); upon final approval, double-entry ledger transactions post atomically with ACID isolation in the tenant SQL database.

### Storage Strategy
- **Primary Database**: Azure SQL Database (vCore purchasing model, General Purpose/Business Critical tier with Zone Redundancy enabled). Deployed as dedicated per-customer databases (`sqldb-adv-uks-{env}-{customer}-001`) for core PCMS data, alongside dedicated databases for UDF (`CustomFieldsDbContext`) and MQR (`sqldb-adv-uks-{env}-mqr-001`).
- **Caching**: Azure Cache for Redis (`redis-adv-uks-{env}-outlook-001` and UDF Redis cache) for session tokens, Graph access tokens, and dynamic custom field schemas, combined with in-memory local caching (`IMemoryCache`) for static lookups and ethical wall policies.
- **File Storage**: Azure Blob Storage accounts (`stadvuks{env}mqr001`, customer-specific storage containers) for generated document artifacts, function execution payloads, and temporary staging; SharePoint Online via Microsoft Graph API for authoritative long-term legal matter document binaries.

## API Design

### API Style
RESTful JSON APIs over HTTPS (TLS 1.3) following OpenAPI/Swagger specifications, managed through Azure API Management (APIM), supplemented by stateful WebSockets for Wisej-3 desktop UI interaction and Azure Service Bus messaging for asynchronous workflows.

### Key Endpoints
- `POST /legal/pcms/v1/matters`: Creates a new legal case matter and initializes practice workflow templates and SharePoint workspaces.
- `GET /legal/pcms/v1/matters/{matterId}`: Retrieves case details, assigned fee earners, statutory dates, and financial summary.
- `POST /legal/pcms/v1/documents/{documentId}/share-links`: Generates secure, role-restricted time-limited share links for legal document collaboration.
- `POST /legal/pcms/v1/accounts/requisitions`: Submits a client-to-office fund transfer requisition with SRA / Law Society of Scotland validation.
- `PUT /legal/pcms/v1/accounts/requisitions/{id}/approve`: Executes multi-tier digital sign-off (Partner / COFA / Cashroom Manager) on pending financial transfers.
- `POST /legal/pcms/v1/accounts/open-banking/sync`: Ingests automated Open Banking statement feeds and executes automated reconciliation.
- `GET /legal/udf/v1/workplaces/{workplaceRef}/custom-fields`: Retrieves dynamic user-defined custom field configurations and picklists for a tenant workspace.
- `POST /legal/udf/v1/workplaces/{workplaceRef}/entities/{entityId}/values`: Saves custom field values for a specific client or matter record.
- `POST /legal/exchange/api/graph/notifications`: Public webhook receiver for Microsoft Graph change notifications (Exchange Sync).
- `POST /legal/docgen/api/orchestrators/DocumentGenerationOrchestrator/{jobId}`: Durable Functions HTTP starter triggering asynchronous document generation pipelines.
- `POST /legal/mqr/api/v1/matters/{matterId}/reviews`: Enqueues an automated AI Matter Quality Review and compliance audit job.
- `GET /legal/pcms/v1/reports/realisation`: Retrieves fee-earner billable time utilization, WIP aging, and matter realization metrics.

### Authentication & Authorization
- **Authentication**: Centralized via **OneAdvanced Identity Platform** (Azure AD B2C / Entra ID) using OpenID Connect (OIDC) and OAuth 2.0. Users and services authenticate to obtain JWT bearer tokens containing standard claims (`sub`, `email`, `roles`) and tenant identification (`organisation_reference` / `OrgRef`).
- **Authorization**: Multi-layered authorization enforcement:
  - **APIM Gateway Level**: Validates JWT token signatures, expiration, and rate-limiting policies before proxying requests to downstream App Services.
  - **Application Service Level**: PCMS and UDF APIs enforce Role-Based Access Control (RBAC) combined with Attribute-Based Access Control (ABAC).
  - **Data Layer Level**: Dynamic multi-tenancy filters validate `OrgRef` on every database query, ensuring tenant isolation, while in-memory Ethical Wall controllers enforce conflict-of-interest barriers across sensitive matters.

## Infrastructure

### Deployment Architecture
- **Cloud Provider & Region**: Microsoft Azure, deployed exclusively in **UK South** (Primary) with Availability Zones enabled for high availability and strict UK data sovereignty under UK GDPR.
- **Subscription Structure**:
  - **Platform APIM Subscription**: Hosts shared OneAdvanced API Management instances (`2eed7f36...` Non-Prod, `45df0eac...` Prod) fronted by Azure Application Gateway with Web Application Firewall (WAF).
  - **Workload Subscriptions**: Dedicated Non-Prod (`97d1b43a...`) and Prod (`70722ca3...`) subscriptions hosting `pcms-base`, `rg-adv-pcmsexchange-uks-{env}`, `legal-mqr-{env}`, and `outlook-addin-{env}` resource groups.
- **Hosting Model**:
  - **Core Web Monolith**: Tenant-isolated Azure App Service instances (`app-adv-uks-{env}-lc-<customer>`) deployed to customer App Service Plans.
  - **Domain APIs**: Shared Linux/Windows App Service Plans hosting `pcms-api`, `udf-api`, `workflow-api`, and `legal-ai-mqr`.
  - **Exchange Background Services**: Azure Container Apps (ACA) running inside a dedicated Container Apps Environment (`cae-adv-pcmsexchange-uks-{env}`) connected to Azure Container Registry (`acrpcmsexchangeproduks`).
  - **Document Generation**: Serverless Azure Durable Functions hosted on dedicated App Service Plans (`plan-adv-uks-{env}-doc-gen-001`).
  - **Outlook Add-in**: Azure Static Web Apps for React 19 UI with App Service backend APIs.
- **Infrastructure as Code (IaC) & CI/CD**: Fully automated provisioning using Terraform modules (`pcms-iac`, `pcms-exchange-service-iac`, `pcms-mqr-iac`, `pcms-outlook-iac`) deployed through Harness CI/CD pipelines.

### Scaling Strategy
- **Horizontal**:
  - **Exchange Sync (ACA)**: KEDA auto-scaler dynamically scales `ca-pcms-notifproc` worker replicas between 0 and 20 instances based on Service Bus queue length (target: 10 messages per replica) and scales CPU-bound workers based on 70% utilization thresholds.
  - **Domain APIs & Monolith**: Azure App Service instances scale out automatically across Availability Zones based on CPU (>70%) and Memory (>75%) metrics.
  - **Document Generation**: Azure Durable Functions scale instances dynamically to accommodate high-volume batch precedent rendering.
- **Vertical**:
  - **Azure SQL Databases**: vCore purchasing model enables independent scaling of compute (vCores) and storage with Provisioned IOPS to accommodate peak billing and financial reconciliation windows.
- **Auto-scaling**: Managed autoscale rules configured with cooldown periods and minimum/maximum replica boundaries across all compute tiers, allowing background workers to scale to zero during idle periods to minimize operational cost.

### Monitoring & Observability
- **Logging**: Centralized structured JSON telemetry collected across all App Services, Container Apps, Functions, and APIM instances via Azure Log Analytics Workspace and Application Insights, enriched with `TraceId`, `OrgRef`, `UserId`, and transaction correlation identifiers.
- **Metrics**: Real-time performance dashboards tracking App Service CPU/Memory utilization, ACA replica counts, Service Bus queue depths and dead-letter message counts, Azure SQL DTU/vCore saturation, and API latency (P95 < 200ms, P99 < 500ms).
- **Alerting**: Automated Azure Monitor alert rules configured to notify SRE and Application Support teams via PagerDuty/Teams upon high error rates (>0.01% over 5 min), Service Bus dead-letter queue spikes, App Service health check failures, and Key Vault secret access exceptions.

## Security Architecture

### Security Layers
- **Network Security & Perimeter Isolation**: Azure Landing Zone architecture with Virtual WAN (VWAN), Azure Virtual Network (VNet) peering, Network Security Groups (NSGs), and Private Endpoints for Azure SQL Database, Redis, Key Vault, and Storage Accounts. Public ingress is strictly restricted to HTTPS (TLS 1.3) through Azure Application Gateway with Web Application Firewall (WAF) OWASP rulesets.
- **Identity & Access Governance**: Centralized authentication via OneAdvanced Identity Platform (OAuth 2.0 / OIDC / Azure AD B2C); fine-grained RBAC and ABAC for matter ethical walls; Managed Identities enabled for all Azure compute resources eliminating hardcoded credentials.
- **Data Protection & Encryption**: All data encrypted in transit using TLS 1.3 and at rest using Transparent Data Encryption (TDE) with customer-managed keys (Azure Key Vault) for Azure SQL Database, and AES-256 encryption for Azure Blob Storage and Cosmos DB.
- **Regulatory Compliance & Tenancy Protection**: Strict tenant isolation enforced at database and compute boundaries preventing cross-tenant data leakage; automated dual-jurisdiction compliance checks for SRA and Law Society of Scotland Accounts Rules; immutable SQL Temporal Tables maintaining tamper-evident audit logs; automated UK GDPR data retention enforcement within Azure UK South.