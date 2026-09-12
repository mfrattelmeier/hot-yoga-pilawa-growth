# Open Decisions

Status: decision register created from the 2026-09-12 read-only audit. Owners and due dates are unassigned unless Michael and Kat decide otherwise.

## Priority decisions

| ID | Decision | Why it matters | Status |
| --- | --- | --- | --- |
| D01 | Approve lifecycle and studio-status definitions | All 382 HubSpot contacts are still Lead. | **BUSINESS DECISION REQUIRED** |
| D02 | Assign lead owner, response SLA, and disposition vocabulary | Lead handling cannot be measured consistently today. | **BUSINESS DECISION REQUIRED** |
| D03 | Approve Fitssey user GUID as primary operational join key | Email/phone are incomplete or duplicated. | **BUSINESS DECISION REQUIRED** |
| D04 | Approve identity conflict and duplicate-review policy | Fitssey has 28 duplicate-phone groups; HubSpot has two. | **BUSINESS DECISION REQUIRED** |
| D05 | Approve the minimal HubSpot property set | No schema changes are allowed without documented approval. | **BUSINESS DECISION REQUIRED** |
| D06 | Choose contact properties, custom acquisition object, or external event store for repeat Meta submissions | Current form questions create sparse properties and overwrite risk. | **BUSINESS DECISION REQUIRED** |
| D07 | Choose first-touch, last-touch, view-through, and lookback rules | Meta ad sets use mixed attribution windows. | **BUSINESS DECISION REQUIRED** |
| D08 | Decide whether/how to backfill the 322-lead Meta history gap | Aggregate leads exceed retrievable person records 400 to 78. | **BUSINESS DECISION REQUIRED** |
| D09 | Confirm Fitssey financial reconciliation source and currency | Sales row count conflicts with endpoint total. | **BUSINESS DECISION REQUIRED** |
| D10 | Approve lawful purposes, legal bases, notices, consent categories, retention, and deletion rules | Cross-system CRM/advertising/analytics uses personal data. | **BUSINESS DECISION REQUIRED** |
| D11 | Decide whether and when to connect GA4 | Website analytics and Consent Mode are not configured/audited. | **BUSINESS DECISION REQUIRED** |
| D12 | Decide whether future Meta offline conversion/audience feedback is in scope | It creates a new outbound data flow and consent risk. | **BUSINESS DECISION REQUIRED** |

## Technical follow-ups requiring a later read-only phase

- **TECHNICAL FOLLOW-UP REQUIRED:** Confirm Fitssey visit-status labels before attendance/no-show metrics.
- **TECHNICAL FOLLOW-UP REQUIRED:** Reconcile Fitssey sales pagination using `count`, unique GUIDs, UI totals, zero-sales, voids/refunds, tax, discounts, and currency.
- **TECHNICAL FOLLOW-UP REQUIRED:** Complete aggregate phone-based HubSpot/Fitssey/Meta matching after the Fitssey rate window resets.
- **TECHNICAL FOLLOW-UP REQUIRED:** Review HubSpot list, form, workflow, marketing-email, and import inventories only if read scopes are explicitly approved; current calls return 403.
- **TECHNICAL FOLLOW-UP REQUIRED:** Determine whether the Meta 1970 campaign start time is a platform artifact or misconfiguration.
- **TECHNICAL FOLLOW-UP REQUIRED:** Audit Pixel event names, parameters, deduplication, domain setup, and consent only after scope approval.
- **TECHNICAL FOLLOW-UP REQUIRED:** Produce a dry-run identity crosswalk and duplicate queue before any external writes.

## Known unknowns

- **UNKNOWN:** Current privacy notices, consent evidence, marketing subscriptions, processor agreements, transfer safeguards, and retention policies.
- **UNKNOWN:** Whether free-text data contains health or other special-category information.
- **UNKNOWN:** Whether minors are stored directly or guardians are the contacts for child-related offerings.
- **UNKNOWN:** HubSpot marketing asset state due missing read scopes.
- **UNKNOWN:** Full historical person-level Meta lead data beyond the 78 retrievable records.
- **UNKNOWN:** Current HubSpot website tracking, GA4, cookie banner, and Consent Mode implementation.

## Decision log

- **CONFIRMED:** No implementation decisions were made during Phase 1; all recommendations remain proposals.
