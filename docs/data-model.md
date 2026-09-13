# Data Model

Status: proposed design following the 2026-09-12 read-only audit. No schema changes are authorized by this document.

## Confirmed facts

- **CONFIRMED:** HubSpot contains 382 contacts and 432 contact property definitions; all contacts are paid-social form leads and all remain at lifecycle stage Lead.
- **CONFIRMED:** Fitssey exposes stable user GUIDs and internal client UUIDs on its client records and connects those identifiers to visits and sales.
- **CONFIRMED:** Meta exposes immutable identifiers for leads, forms, campaigns, ad sets, and ads, but only 78 of 400 reported lead actions are currently available as person-level Page-form lead records.
- **CONFIRMED:** Email-only matching links 107 HubSpot contacts to active Fitssey clients and eight currently retrievable Meta leads to Fitssey; all 78 current Meta leads link to HubSpot.
- **CONFIRMED:** Duplicate email/phone risks exist, especially in Fitssey; phone cannot be treated as a universal unique key.

## Canonical entities

| Entity | System of record | Key | Status |
| --- | --- | --- | --- |
| Person/contact | HubSpot for engagement view; Fitssey for operational identity | HubSpot contact ID + Fitssey user GUID | **BUSINESS DECISION REQUIRED:** approve dual-key ownership. |
| Acquisition event | Meta / analytical layer | Meta lead ID or event ID | **INFERRED:** keep repeat submissions separate from the person. |
| Booking/visit | Fitssey | visit GUID | **CONFIRMED:** connected to client/service/location keys. |
| Purchase/order | Fitssey | order/sale GUID | **CONFIRMED:** authoritative detail, subject to finance reconciliation. |
| Pricing entitlement | Fitssey | client pricing-option GUID | **CONFIRMED:** client relationship is available. |
| Contract/membership | Fitssey | client contract GUID | **CONFIRMED:** relationship is available. |
| Campaign/ad delivery | Meta | campaign/ad-set/ad IDs | **CONFIRMED:** authoritative media configuration/performance. |
| Website event | GA4/analytical layer | event/user/session identifiers | **CONFIRMED:** stream created and attached to an existing Google tag. **UNKNOWN:** collection, taxonomy, consent, conversions, and duplicate behavior are not validated. |

## Proposed HubSpot contact properties

Every item below is a proposal only. Names are internal-name candidates and must be checked for collisions, type limits, reporting needs, and privacy purpose before creation.

| Proposed property | Type | Source | Write rule | Status |
| --- | --- | --- | --- | --- |
| `fitssey_user_guid` | single-line text, unique if supported | Fitssey | immutable after verified link | **BUSINESS DECISION REQUIRED:** recommended primary operational key. |
| `fitssey_client_uuid` | single-line text | Fitssey | immutable after verified link | **BUSINESS DECISION REQUIRED:** secondary Fitssey key. |
| `fitssey_client_created_at` | datetime | Fitssey | source overwrite | **BUSINESS DECISION REQUIRED:** optional operational context. |
| `fitssey_last_synced_at` | datetime | integration | integration timestamp | **BUSINESS DECISION REQUIRED:** observability field. |
| `studio_customer_status` | enumeration | derived from Fitssey | controlled calculation | **BUSINESS DECISION REQUIRED:** values must follow approved lifecycle rules. |
| `studio_first_visit_at` | datetime | Fitssey visits | earliest immutable | **BUSINESS DECISION REQUIRED:** lifecycle evidence. |
| `studio_last_visit_at` | datetime | Fitssey visits | latest source overwrite | **BUSINESS DECISION REQUIRED:** retention signal. |
| `studio_attended_visit_count` | number | Fitssey visits | recompute after status mapping | **TECHNICAL FOLLOW-UP REQUIRED:** wait for visit-status confirmation. |
| `studio_next_booking_at` | datetime | Fitssey | latest future booking | **BUSINESS DECISION REQUIRED:** useful for service messaging. |
| `studio_active_entitlement_type` | enumeration/text | Fitssey | current-state summary | **BUSINESS DECISION REQUIRED:** define pass versus contract categories. |
| `studio_entitlement_expires_at` | datetime | Fitssey | current-state summary | **BUSINESS DECISION REQUIRED:** retention trigger candidate. |
| `studio_first_purchase_at` | datetime | Fitssey | earliest immutable | **BUSINESS DECISION REQUIRED:** customer conversion evidence. |
| `studio_last_purchase_at` | datetime | Fitssey | latest source overwrite | **BUSINESS DECISION REQUIRED:** recency signal. |
| `studio_lifetime_revenue_minor` | number | Fitssey | recomputed aggregate | **TECHNICAL FOLLOW-UP REQUIRED:** do not create until finance reconciliation. |
| `studio_revenue_currency` | enumeration | Fitssey/account configuration | controlled constant | **TECHNICAL FOLLOW-UP REQUIRED:** confirm currency first. |
| `meta_first_lead_id` | single-line text | Meta ingestion | first value only | **BUSINESS DECISION REQUIRED:** contact convenience field, not event history. |
| `meta_first_lead_form_id` | single-line text | Meta ingestion | first value only | **BUSINESS DECISION REQUIRED:** preserve source key. |
| `meta_latest_lead_id` | single-line text | Meta ingestion | latest by submission time | **BUSINESS DECISION REQUIRED:** convenience field. |
| `meta_latest_lead_form_id` | single-line text | Meta ingestion | latest by submission time | **BUSINESS DECISION REQUIRED:** convenience field. |
| `meta_latest_lead_at` | datetime | Meta ingestion | latest by submission time | **BUSINESS DECISION REQUIRED:** contact recency. |
| `acquisition_first_campaign_id` | single-line text | Meta/UTM | first value only | **BUSINESS DECISION REQUIRED:** attribution key. |
| `acquisition_first_adset_id` | single-line text | Meta | first value only | **BUSINESS DECISION REQUIRED:** attribution key. |
| `acquisition_first_ad_id` | single-line text | Meta | first value only | **BUSINESS DECISION REQUIRED:** attribution key. |
| `acquisition_latest_campaign_id` | single-line text | Meta/UTM | latest qualified touch | **BUSINESS DECISION REQUIRED:** define overwrite rule. |
| `acquisition_latest_adset_id` | single-line text | Meta | latest qualified touch | **BUSINESS DECISION REQUIRED:** define overwrite rule. |
| `acquisition_latest_ad_id` | single-line text | Meta | latest qualified touch | **BUSINESS DECISION REQUIRED:** define overwrite rule. |

## Data that should not be copied wholesale into HubSpot

- **INFERRED:** Individual Fitssey visit, order, instalment, and sales rows should remain in Fitssey and/or an analytical store; HubSpot should receive only approved keys and current-state summaries.
- **INFERRED:** Raw Meta performance time series should remain in Meta/analytics; HubSpot may receive acquisition keys, not campaign reporting tables.
- **INFERRED:** Repeated lead-form answers should be modeled as acquisition/submission events, not overwritten on a single contact property when history matters.
- **BUSINESS DECISION REQUIRED:** Decide whether HubSpot custom objects are justified for acquisition events. An external analytical layer is simpler for full event history and avoids CRM property proliferation.
- **BUSINESS DECISION REQUIRED:** Decide whether free-text motivation/health-adjacent answers are needed after lead handling; default to minimization and short retention.

## Identity resolution

1. **INFERRED:** Exact Fitssey user GUID match is deterministic and highest priority.
2. **INFERRED:** Verified normalized email match is the next-best automatic candidate only when unique in both systems.
3. **INFERRED:** Normalized phone may support a candidate match but should not auto-link unless unique and corroborated.
4. **INFERRED:** Name alone must never auto-link records.
5. **BUSINESS DECISION REQUIRED:** Conflicts, shared household phones, reused emails, and deleted clients require manual review and an auditable resolution reason.
6. **TECHNICAL FOLLOW-UP REQUIRED:** Build a dry-run crosswalk with match method, confidence, conflict reason, source timestamps, and no raw PII in logs.

## Duplicate policy

- **CONFIRMED:** HubSpot has no duplicate normalized email groups but has two duplicate normalized phone groups; Fitssey has four duplicate email and 28 duplicate phone groups.
- **INFERRED:** Synchronization should create neither new records nor merges when a candidate identity maps to multiple targets.
- **BUSINESS DECISION REQUIRED:** Name the data steward who can approve a link or merge and define evidence requirements.
- **TECHNICAL FOLLOW-UP REQUIRED:** Preserve source record IDs in any duplicate queue so decisions are reversible and auditable.

## Historical backfill boundaries

- **CONFIRMED:** HubSpot contact history starts 2025-07-15; Fitssey visits start 2025-08-28 and sales start 2025-08-20 in the returned reports.
- **CONFIRMED:** Meta exposes 400 aggregate lead actions but only 78 current person-level leads.
- **BUSINESS DECISION REQUIRED:** Select the authoritative export or archive for the 322-lead person-history gap, if backfill is required.
- **TECHNICAL FOLLOW-UP REQUIRED:** Backfill should be idempotent, preserve original event timestamps/IDs, and create a reconciliation report before any writes.

## Privacy and retention fields

- **BUSINESS DECISION REQUIRED:** Define lawful purpose, lawful basis, retention period, access role, and deletion behavior for every proposed field.
- **BUSINESS DECISION REQUIRED:** Keep marketing subscription/consent evidence distinct from service communications and contract-performance data.
- **UNKNOWN:** Existing consent and subscription records were outside the available audit scope.
