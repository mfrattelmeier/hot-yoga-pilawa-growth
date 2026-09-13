# Business Decision Brief

Audience: Michael and Kat. This brief prioritizes decisions that must be made before Phase 1A design or implementation. Recommendations are defaults for discussion, not authorization. Historical prices, packages, class times, and schedules are excluded from current truth until Fitssey reconciliation.

## D01 — Current offer and commercial truth

- **Question:** Which services, courses, pricing options, contracts, introductory offers, schedules, capacities, and policies are current?
- **Why it matters:** Marketing, lifecycle, reporting, and automation cannot use historical offer versions safely.
- **Evidence from historical chats:** Numerous classes, passes, events, and prices were used or proposed, then changed, suspended, or contradicted. [Sources: marketing-content-history.md; rozwoj-studia-history.md; general-unprojected-chats-history.md]
- **Evidence from technical audit:** Fitssey exposes 45 class services, 45 pricing options, and two contracts, but Phase 1 did not approve an item-level current catalog. [Source: audits/fitssey/current-state.md]
- **Recommended default:** Produce a dated, read-only Fitssey catalog reconciliation and owner-approved offer register; treat every historical commercial detail as stale until matched.
- **Alternatives:** Use only broad categories temporarily; or postpone offer-specific CRM/marketing design.
- **What Michael/Kat need to decide:** Which entries are active, customer-facing, strategic, and authoritative, and who owns future catalog changes.

## D02 — Lifecycle definitions

- **Question:** What exact evidence makes someone a Lead, Qualified, First-time Customer, Active, At-risk, Lapsed, Reactivated, Course Participant, or Advocate?
- **Why it matters:** These definitions drive schema, segmentation, reporting, and any future automation.
- **Evidence from historical chats:** The studio distinguished inquiries, beginners, course participants, regulars, inactive clients, returning clients, and community advocates, but never set stable thresholds. [Sources: marketing-content-history.md; general-unprojected-chats-history.md]
- **Evidence from technical audit:** All 382 HubSpot contacts remain Lead while Fitssey contains visit and sale evidence. [Sources: audits/hubspot/current-state.md; audits/fitssey/current-state.md]
- **Recommended default:** Use event-backed stages and separate HubSpot relationship stage from a product-aware studio engagement status.
- **Alternatives:** Minimal lead/customer split; or lifecycle reporting only in an analytical layer.
- **What Michael/Kat need to decide:** Entry/exit evidence, recency windows, exclusions, and treatment of free visits, events, courses, guardians, and staff/test accounts.

## D03 — Lead ownership and response standard

- **Question:** Who owns each new lead, how quickly must the studio respond, and which outcomes must be recorded?
- **Why it matters:** Paid leads currently have no audited operational progression in HubSpot.
- **Evidence from historical chats:** Kat/Kasia often handled communication manually through phone, WhatsApp, messages, and Fitssey; a customer-advisor role was later proposed. [Sources: marketing-content-history.md; grants-dotacje-history.md]
- **Evidence from technical audit:** HubSpot Lead Status is blank for every contact; current activities and ownership distribution were not established. [Source: audits/hubspot/current-state.md]
- **Recommended default:** One primary owner, one backup, a business-hours response target, a short attempt cadence, and controlled outcome values.
- **Alternatives:** Shared queue; channel-based ownership; outsourced first response.
- **What Michael/Kat need to decide:** Owner/backup, service hours, SLA, cadence, escalation, stop conditions, and required outcomes.

## D04 — Identity key and conflict handling

- **Question:** May Fitssey user GUID become the operational join key in HubSpot, and how are ambiguous matches handled?
- **Why it matters:** Bad merges could expose or corrupt customer history.
- **Evidence from historical chats:** Fitssey was historically the practical customer/booking home; guardian/child flows and shared contact details may exist. [Sources: rozwoj-studia-history.md; strona-www-i-fitssey-history.md]
- **Evidence from technical audit:** Fitssey has stable GUIDs but also duplicate emails/phones and 24 records without either; phone alone is unsafe. [Source: audits/fitssey/current-state.md]
- **Recommended default:** GUID-first linking; unique email as a candidate; phone only when uniquely corroborated; manual conflict queue; never match on name alone.
- **Alternatives:** Keep systems unlinked; use an external master-person ID.
- **What Michael/Kat need to decide:** Approved key, evidence threshold, conflict owner, merge/link authority, and guardian/minor model.

## D05 — Minimal HubSpot schema

- **Question:** Which operational and acquisition summaries genuinely belong on a HubSpot contact?
- **Why it matters:** Historical form variation already created sparse property proliferation.
- **Evidence from historical chats:** Campaigns asked different event-, motivation-, schedule-, and eligibility-specific questions. [Sources: marketing-content-history.md; strona-www-i-fitssey-history.md]
- **Evidence from technical audit:** HubSpot has 30 Lead Ad Properties with sparse use; `docs/data-model.md` proposes a controlled minimal set. [Sources: audits/hubspot/current-state.md; docs/data-model.md]
- **Recommended default:** Store stable IDs and a small approved current-state summary; keep detailed visits, purchases, and raw form history outside contact properties.
- **Alternatives:** HubSpot custom acquisition object; external event store only.
- **What Michael/Kat need to decide:** Required fields, reporting purpose, owner, retention, and whether any custom object is justified.

## D06 — Acquisition-event history

- **Question:** Where should repeat Meta submissions and campaign/form/ad context be stored?
- **Why it matters:** A person can submit multiple forms; overwriting contact fields destroys attribution history.
- **Evidence from historical chats:** Multiple campaign routes and event-specific lead forms were proposed or used. [Source: marketing-content-history.md]
- **Evidence from technical audit:** Meta form schemas vary, 12 form IDs appear in creatives, and only 78 person-level leads remain retrievable. [Source: audits/meta/current-state.md]
- **Recommended default:** Append-only acquisition events in an analytical layer, with first/latest approved summaries in HubSpot.
- **Alternatives:** HubSpot custom object; contact-only summaries with accepted history loss.
- **What Michael/Kat need to decide:** Required history depth, reporting needs, retention, and CRM-versus-analytics ownership.

## D07 — Historical backfill boundary

- **Question:** Should the missing historical Meta person-level lead data be pursued, or should reliable attribution start from a clean date?
- **Why it matters:** Meta reports 400 lead actions but only 78 person-level records are retrievable, leaving a gap of 322.
- **Evidence from historical chats:** Chats name campaigns and offers but cannot reconstruct individual identities or verified outcomes. [Sources: marketing-content-history.md; general-unprojected-chats-history.md]
- **Evidence from technical audit:** Current Graph reads cannot provide the full history. [Source: audits/meta/current-state.md]
- **Recommended default:** Accept partial historical attribution unless an approved export exists; begin complete prospective event capture from an agreed date.
- **Alternatives:** Obtain approved Meta/HubSpot exports; use aggregate-only historical reporting.
- **What Michael/Kat need to decide:** Backfill effort, acceptable source, cutover date, and confidence labels for old reporting.

## D08 — Booking and commercial policies

- **Question:** What are the authoritative booking, cancellation, no-show, waitlist, expiry, freeze, make-up, refund, and transfer rules?
- **Why it matters:** Policies affect capacity, customer experience, retention, and lifecycle signals.
- **Evidence from historical chats:** Rules tightened after no-shows and speculative bookings, but versions conflict on deadlines, minimum attendance, freeze length, course rules, and OPEN status. [Source: rozwoj-studia-history.md]
- **Evidence from technical audit:** Fitssey visit-status labels and some product semantics remain unresolved. [Source: audits/fitssey/current-state.md]
- **Recommended default:** One owner-approved policy matrix mapped directly to Fitssey settings and customer-facing text.
- **Alternatives:** Product-specific rules; simplified universal rules where operationally viable.
- **What Michael/Kat need to decide:** Exact rules, exceptions, authority, enforcement, and communication ownership.

## D09 — Beginner entry promise

- **Question:** Which current services are appropriate first steps for true beginners, and what can marketing promise?
- **Why it matters:** Overbroad reassurance may route people into unsuitable classes; excessive caution may suppress conversion.
- **Evidence from historical chats:** Beginner confidence and own-pace practice were central, but some dated Fitssey services were labeled intermediate. Structured courses historically improved readiness. [Sources: marketing-content-history.md; kurs-jogi-od-podstaw-history.md]
- **Evidence from technical audit:** Current item-level suitability was not audited.
- **Recommended default:** Publish a verified beginner route by need and service; say modifications are available only where instructors approve.
- **Alternatives:** Dedicated intro course; consultation/first-visit recommendation; broad all-levels promise after review.
- **What Michael/Kat need to decide:** Approved entry offers, contraindication/claim language, and owner of suitability updates.

## D10 — Retention and lapse model

- **Question:** What behavior indicates active, at-risk, lapsed, and reactivated status for each product type?
- **Why it matters:** Courses, limited passes, unlimited contracts, and event buyers have different expected rhythms.
- **Evidence from historical chats:** Regularity, course progression, challenges, seasonal passes, inactive-client outreach, and return-to-routine campaigns recur; summer decline and booking misuse were real concerns. [Sources: marketing-content-history.md; rozwoj-studia-history.md]
- **Evidence from technical audit:** Fitssey has 8,137 visit rows, but status codes require confirmation. [Source: audits/fitssey/current-state.md]
- **Recommended default:** Product-aware windows based on attended visits and entitlement expiry, validated on historical aggregates.
- **Alternatives:** One universal recency window; manual segments initially.
- **What Michael/Kat need to decide:** Thresholds, exclusions, desired interventions, and success measures.

## D11 — Expansion and grant-offer portfolio

- **Question:** Which proposed offers are launched, funded, strategic next, paused, or abandoned?
- **Why it matters:** Schema, content, staffing, safety, and measurement should not be built around stale grant scenarios.
- **Evidence from historical chats:** **Siła i Długowieczność**, **Regeneracja Premium**, **Studio Hybrydowe**, retreats, BUR/corporate, private/recovery services, and digital products were planned to varying degrees. [Sources: grants-dotacje-history.md; general-unprojected-chats-history.md]
- **Evidence from technical audit:** Catalog counts are known, but grant approval, equipment, launch, and product mapping were not audited.
- **Recommended default:** Place each initiative in a portfolio state with owner, evidence, next gate, and no current-marketing status until verified.
- **Alternatives:** Focus only on the current core; select one controlled pilot after approval.
- **What Michael/Kat need to decide:** Status, priority, funding reality, commercial owner, success threshold, and stop criteria.

## D12 — Claims, safety, and sensitive data

- **Question:** Which claims, screening questions, measurements, and operator responsibilities are approved?
- **Why it matters:** Hot, recovery, measurement, longevity, and minor-related services may involve health-adjacent or special-category data and safety obligations.
- **Evidence from historical chats:** Benefit and therapeutic language appears widely; grant work explicitly moved toward non-medical positioning. [Sources: marketing-content-history.md; grants-dotacje-history.md]
- **Evidence from technical audit:** Free-text health content was not inspected; privacy and consent governance remain unknown. [Source: audits/cross-system-gap-analysis.md]
- **Recommended default:** Non-medical claims, data minimization, qualified-operator review, and documented safety/consent procedures before promotion.
- **Alternatives:** Avoid collecting health-adjacent data; obtain specialist/legal review for narrowly necessary processing.
- **What Michael/Kat need to decide:** Approved claims, required screening, storage/retention, access, qualifications, and escalation.

## D13 — Attribution model and reporting control

- **Question:** Which first-touch, last-touch, view-through, lookback, conversion, timezone, currency, and reconciliation rules govern reporting?
- **Why it matters:** Meta windows differ, person history is incomplete, and Fitssey finance totals are provisional.
- **Evidence from historical chats:** Marketing used multiple online and offline/community channels, but results were seldom measured end to end. [Sources: marketing-content-history.md; general-unprojected-chats-history.md]
- **Evidence from technical audit:** Meta attribution windows are mixed; the post-audit GA4 stream exists but is unvalidated; Fitssey currency and sales counts need reconciliation. [Sources: audits/meta/current-state.md; audits/fitssey/current-state.md; docs/architecture.md]
- **Recommended default:** Report Meta platform attribution beside an independently joined operational model; use Europe/Warsaw provisionally and publish no finance total until reconciled.
- **Alternatives:** First-touch only; last-non-direct only; aggregate channel reporting during the data-gap period.
- **What Michael/Kat need to decide:** Rules, dashboard owner, currency/timezone, reporting cadence, and acceptable historical confidence.

## D14 — Website analytics and consent

- **Question:** How and when should the existing GA4 stream be validated, and when should HubSpot website tracking be assessed, under an approved consent design?
- **Why it matters:** Website performance is currently unknown; tracking can create privacy and duplication risk.
- **Evidence from historical chats:** Website/Fitssey CTAs and content were used or proposed, but reliable analytics were not evidenced. [Sources: marketing-content-history.md; general-unprojected-chats-history.md]
- **Evidence from technical audit:** GA4 has been created and attached to the existing Google tag, but reliable collection, events, conversions, consent/banner behavior, Consent Mode v2, Google Ads linkage/configuration, Search Console, HubSpot tracking, and duplicate-event behavior remain unknown. [Source: docs/architecture.md]
- **Recommended default:** Do not treat the stream as production-ready. Approve purpose, banner/CMP behavior, event taxonomy, UTMs, and data minimization before validation or reporting; then test collection, duplicates, conversions, and every Consent Mode v2 state.
- **Alternatives:** Privacy-minimal aggregate analytics; postpone analytics and use booking-system outcomes only.
- **What Michael/Kat need to decide:** Tools, lawful basis, consent categories, events, identifiers, retention, and launch owner.

## D15 — Automation and outbound data boundary

- **Question:** What must be true before CRM automation, Meta audience uploads, or offline conversions are allowed?
- **Why it matters:** These actions can contact people or transmit customer behavior to third parties.
- **Evidence from historical chats:** Manual follow-up and retention communication created workload, but there is no approved automated operating model. [Sources: marketing-content-history.md; rozwoj-studia-history.md]
- **Evidence from technical audit:** Lifecycle, identity, consent, and attribution are unresolved; current Meta permissions are broader than audit needs. [Sources: audits/cross-system-gap-analysis.md; audits/meta/current-state.md]
- **Recommended default:** No automation or outbound feedback until approved lifecycle/schema, verified identity, consent/suppression rules, test cases, rollback, and a small reviewed pilot.
- **Alternatives:** Human-only CRM tasks; internal alerts without customer contact; read-only dashboards.
- **What Michael/Kat need to decide:** Entry criteria, prohibited uses, approval owner, pilot scope, monitoring, and rollback authority.

## Suggested review order

1. D01 current offer truth, D08 policies, and D09 beginner route.
2. D02 lifecycle, D03 lead ownership, D04 identity, and D05–D06 data model.
3. D10 retention, D13 attribution, and D14 consent-aware analytics.
4. D07 backfill, D11 expansion portfolio, D12 claims/safety, and D15 automation boundary.
