---
status: Blocked
targetDate: 2027-02-28
period: Q4 FY27
tshirt: M
---

# PCMS integration with Scribe to launch scribe from within the PCMS application and to directly record the output of scribe back into the relevant client or matter record in PCMS

## Release Information
**Product/Module:** PCMS Core Application + Scribe Integration
**Version:** Q4 FY26

## Headline
PCMS now integrates with Scribe, enabling fee earners to launch recordings directly within the practice management interface and automatically capture transcripts into client and matter records.

## Summary
This release integrates Scribe's audio recording and transcription capabilities directly into the PCMS Core Application, allowing solicitors and fee earners to initiate voice recordings without leaving their workflow. Scribe outputs—including transcripts and metadata—are automatically routed back into the relevant client or matter record, eliminating manual file handling and reducing non-billable administrative overhead.

## Problem Statement
Fee earners frequently need to capture verbal notes, client instructions, and procedural details during calls and in-person meetings but must switch between multiple applications to record, transcribe, and file outputs. This fragmentation creates operational friction, delays matter documentation, and introduces manual transcription errors. Currently, practitioners spend time copying transcripts between systems and manually organizing recordings by matter, diverting focus from billable client work and reducing matter velocity.

## Solution
PCMS now embeds Scribe launch and recording capabilities directly within the practice management interface. Fee earners can initiate a recording session with a single click, capture voice notes during client interactions, and have transcripts automatically ingested into the associated client or matter record. The integration handles routing, metadata tagging, and storage orchestration transparently, keeping practitioners in PCMS without context switching.

## Customer Impact

| Key Features | Key Benefits | Value & Impact Delivered |
|---|---|---|
| In-application Scribe launch from matter workspace | Eliminates context switching between PCMS and external recording tools | Recovers 15–20 minutes per fee earner per day of unbillable admin time |
| Automatic transcript ingestion into client/matter records | Transcripts appear in matter history without manual filing or copying | Accelerates matter documentation velocity and improves audit trail completeness |
| Metadata routing and jurisdiction-aware storage | Recordings and transcripts comply with SRA and Law Society of Scotland data governance rules | Reduces compliance risk and eliminates manual classification overhead |
| Seamless co-authoring and SharePoint Online integration | Transcripts sync with Office 365 workflows and matter document stores | Enables real-time co-authoring of matter notes and cross-border document continuity |

## Customer Quote (Imagined)
> "Scribe integration has transformed how we capture client instructions. No more switching between apps or copying transcripts into matter files—everything flows directly into PCMS. We've recovered nearly an hour a day per fee earner that we're now billing back to clients."

## Call to Action
Enable the Scribe integration in your PCMS settings under Integrations > Recording & Transcription. Contact your implementation partner or support team for jurisdiction-specific configuration and user training.

## Internal Notes
Integration uses Microsoft Graph API for SharePoint Online document routing and Azure Key Vault for Scribe API credential management. Scribe session metadata includes matter reference, user identity, timestamp, and jurisdiction flag for compliance audit trails. Quarterly roadmap includes voice-command matter tagging and automated legal document precedent assembly from transcripts.