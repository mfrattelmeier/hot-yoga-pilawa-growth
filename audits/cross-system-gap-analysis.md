# Cross-System Gap Analysis and Executive Summary

Audit date: 2026-09-12. This is a read-only point-in-time assessment of HubSpot, Meta, and Fitssey. No external system was modified. Google Analytics was outside the audit. Post-audit update: a GA4 website stream was created and attached to the studio’s existing Google tag, but it is not fully configured or validated.

## Executive summary

- **CONFIRMED:** Meta currently drives the audited CRM intake: all 382 HubSpot contacts are paid-social form leads, and all 78 Meta leads currently retrievable through Page forms match HubSpot by normalized email and phone.
- **CONFIRMED:** HubSpot has not progressed those contacts operationally: all 382 remain at Lead and all have blank Lead Status.
- **CONFIRMED:** Fitssey contains the richer customer reality: 466 active clients, 8,137 visit rows, pricing/contract entitlements, and sales history linked by stable GUIDs.
- **CONFIRMED:** Only 107 of 382 HubSpot contacts match active Fitssey clients by email. Only eight of the 78 currently retrievable Meta leads match Fitssey by email; these are lower bounds because Fitssey phone matching was rate-limited.
- **CONFIRMED:** Meta reports 400 lead actions, while only 78 person-level Page-form leads are currently retrievable. Current APIs therefore cannot reconstruct all historical lead identities.
- **INFERRED:** The business has a functioning lead-generation path but not a closed-loop CRM: lead, booking, attendance, purchase, membership, retention, and revenue states are not joined in one approved model.
- **INFERRED:** Fitssey should remain operational source of truth; HubSpot should become the engagement/lifecycle view; Meta should remain media-delivery and ad-performance truth; the newly created GA4 stream should later provide consent-aware website behavior after validation.
- **BUSINESS DECISION REQUIRED:** Do not build automation or bulk synchronization until lifecycle definitions, identity resolution, lawful purposes, consent, retention, and backfill boundaries are approved.

## Major data-quality problems

- **CONFIRMED:** HubSpot last name is missing on 231/382 contacts.
- **CONFIRMED:** HubSpot has two duplicate-phone groups covering four contacts and 11 non-E.164-style phone values.
- **CONFIRMED:** Fitssey has four duplicate-email groups covering eight records and 28 duplicate-phone groups covering 57 records; 24 records have neither email nor phone.
- **CONFIRMED:** Meta form schemas vary between Polish/English identity keys and proliferate event-specific questions; HubSpot now has 30 Lead Ad Properties with sparse usage.
- **CONFIRMED:** Meta has a 1970 start-time anomaly on an active engagement campaign and mixed attribution windows across ad sets.
- **CONFIRMED:** Fitssey sales pagination returned 1,164 rows while reporting 1,082, so the provisional monetary sum is not finance-grade.
- **INFERRED:** Any automatic email/phone-only merge would create avoidable identity errors; stable external IDs and a review queue are required.

## Source-of-truth recommendation

| Domain | Recommended source | Rationale/status |
| --- | --- | --- |
| Client operational identity | Fitssey | **INFERRED:** Stable user GUID and client UUID connect visits and sales. |
| Bookings, visit/attendance states | Fitssey | **CONFIRMED:** Complete visit report and schedule relationships exist. |
| Purchases, passes, contracts, revenue | Fitssey | **INFERRED:** Richest operational records; finance totals still require reconciliation. |
| Contact engagement profile | HubSpot | **INFERRED:** Appropriate destination once lifecycle and synchronization are approved. |
| Lifecycle, segmentation, communications | HubSpot | **BUSINESS DECISION REQUIRED:** Intended role; current data does not implement it. |
| Media configuration and delivery | Meta | **CONFIRMED:** Campaign/ad objects and insights are authoritative there. |
| Website behavior | GA4 | **CONFIRMED POST-AUDIT:** Stream created and attached to an existing Google tag. **UNKNOWN:** reliable collection and configuration remain unvalidated. |
| Cross-system reporting | External analytical layer | **INFERRED:** Needed for immutable event history and multi-source attribution without overloading HubSpot. |

## Recommended target schema

- **INFERRED:** Use Fitssey user GUID as the primary operational foreign key on a HubSpot contact, retaining Fitssey client UUID as a secondary relationship key.
- **INFERRED:** Keep detailed visits, orders, contracts, and sales in Fitssey or an analytical store; synchronize only approved current-state summaries and stable IDs into HubSpot.
- **INFERRED:** Preserve immutable Meta lead/form/campaign/ad-set/ad IDs at ingestion, plus submission timestamp and UTM/click identifiers.
- **INFERRED:** Separate person identity from acquisition events: one person may submit multiple forms and attend/purchase many times.
- **BUSINESS DECISION REQUIRED:** Decide whether acquisition events belong in a HubSpot custom object or only in an external warehouse. No custom object is authorized.
- **TECHNICAL FOLLOW-UP REQUIRED:** The proposed property dictionary and write rules are documented in `docs/data-model.md`; every property must be approved before creation.

## Recommended synchronization direction

- **INFERRED:** Meta -> HubSpot: new lead identity and acquisition metadata, preferably through a controlled ingestion path that preserves immutable IDs.
- **INFERRED:** Fitssey -> HubSpot: stable identity key plus approved booking/attendance/purchase/membership summaries, one-way at first.
- **INFERRED:** HubSpot -> Fitssey: no write-back in the initial architecture; there is no approved operational use case.
- **INFERRED:** HubSpot/Meta/Fitssey/GA4 -> analytical layer: append-only snapshots/events for attribution and retention analysis.
- **BUSINESS DECISION REQUIRED:** Any reverse write, audience upload, offline conversion, or CRM mutation needs a separate approval and consent/legal review.

## Phased implementation roadmap

1. **BUSINESS DECISION REQUIRED:** Approve lifecycle stages, lead ownership/SLA, consent model, retention periods, identity conflict rules, and reporting definitions.
2. **TECHNICAL FOLLOW-UP REQUIRED:** Reconcile Fitssey finance pagination/status codes and complete phone-based aggregate matching after rate reset.
3. **TECHNICAL FOLLOW-UP REQUIRED:** Produce a dry-run identity crosswalk with hashed diagnostics, duplicate queues, and no external writes.
4. **BUSINESS DECISION REQUIRED:** Approve the minimal HubSpot property set and whether an acquisition-event object/warehouse is needed.
5. **TECHNICAL FOLLOW-UP REQUIRED:** Build read-only incremental extractors with checkpoints, rate limits, PII-safe logs, and monitoring.
6. **BUSINESS DECISION REQUIRED:** Authorize a small pilot write into a non-production/test segment only after review; no pilot is part of Phase 1.
7. **TECHNICAL FOLLOW-UP REQUIRED:** Validate lifecycle calculations against sampled records, then design—but do not yet activate—automation.
8. **BUSINESS DECISION REQUIRED:** Validate GA4 collection and website consent tooling, then later decide on offline conversion or audience feedback to Meta.

## Top 10 decisions for Michael and Kat

1. **BUSINESS DECISION REQUIRED:** What exact event makes someone Lead, MQL, SQL, Opportunity, Customer, Active Customer, Lapsed, and Reactivated?
2. **BUSINESS DECISION REQUIRED:** Who owns a new lead, what is the contact SLA, and what outcomes must be recorded?
3. **BUSINESS DECISION REQUIRED:** Is Fitssey user GUID approved as the primary operational identity key in HubSpot?
4. **BUSINESS DECISION REQUIRED:** When email and phone point to different people, who reviews the conflict and what evidence permits a merge?
5. **BUSINESS DECISION REQUIRED:** Which Fitssey summaries should be visible in HubSpot, and which detailed operational data must stay outside?
6. **BUSINESS DECISION REQUIRED:** Should repeat Meta form submissions be stored as acquisition events/custom objects, or only in an external analytical layer?
7. **BUSINESS DECISION REQUIRED:** What first-touch, last-touch, and conversion definitions will be used for marketing and revenue reporting?
8. **BUSINESS DECISION REQUIRED:** What lawful basis, notice, consent, opt-out, and retention rule applies to lead follow-up, marketing, analytics, and audience uploads?
9. **BUSINESS DECISION REQUIRED:** How should legacy Meta leads beyond the 78 retrievable records be backfilled, and what evidence source is acceptable?
10. **BUSINESS DECISION REQUIRED:** What financial report in Fitssey is the reconciliation control for revenue, refunds/voids, free orders, tax, and discounts?

## GDPR and Poland/EU considerations

- **CONFIRMED:** GDPR Article 5 requires purpose limitation, data minimization, accuracy, storage limitation, and accountability; Article 6 requires a lawful basis; Articles 13/14 require transparent information; Article 28 addresses processor contracts; Article 32 requires risk-appropriate security; and Chapter V governs third-country transfers: <https://eur-lex.europa.eu/eli/reg/2016/679/oj/eng>.
- **CONFIRMED:** Google states that Consent Mode communicates choices from a consent banner and does not itself provide the banner; advanced mode can transmit cookieless pings when consent is denied: <https://support.google.com/analytics/answer/10000067>.
- **INFERRED:** Cross-system identifiers, form answers, visit behavior, and purchase history are personal data and should be synchronized only when necessary for a documented purpose.
- **UNKNOWN:** Current privacy notices, lawful-basis records, processor terms, international-transfer safeguards, retention schedules, marketing subscription status, and consent evidence were not audited.
- **UNKNOWN:** Whether any free-text answers or operational notes contain health information or other special-category data was not inspected and must not be assumed.
- **BUSINESS DECISION REQUIRED:** Obtain Polish/EU privacy counsel review before activating tracking, automated marketing, special-category processing, minors' data flows, audience uploads, or offline conversion sharing. This repository is not legal advice.
