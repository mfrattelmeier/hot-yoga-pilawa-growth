# Customer Lifecycle

Status: proposed framework updated by the 2026-09-13 Phase 1A read-only reconciliation and historical business evidence. No lifecycle automation, schema change, or external write is authorized. Historical prices, packages, class times, and schedules are not current truth.

## Confirmed current state

- **CONFIRMED PHASE 1 SNAPSHOT:** All 382 audited HubSpot contacts were at Lead and had blank Lead Status. Phase 1A counted 383 non-archived contacts after one new contact was created on 2026-09-13, but did not re-audit the new record's lifecycle properties. [Sources: audits/hubspot/current-state.md; audits/fitssey/identity-follow-up.md]
- **CONFIRMED:** Fitssey currently returns 467 clients in the default list plus 10 additional deleted records, and 8,283 visit-report rows through the requested future boundary. [Sources: audits/fitssey/current-state-reconciliation.md; audits/fitssey/visit-status-map.md]
- **CONFIRMED:** Fitssey status 0 means booked, 1 present, 2 absent, 3/4 early cancellation, 5/6 late cancellation, 7 class cancelled, 8 waiting list, and 9 unconfirmed. [Source: audits/fitssey/visit-status-map.md]
- **CONFIRMED:** HubSpot and Fitssey describe different slices of the population and are not currently a unified lifecycle view. [Source: audits/cross-system-gap-analysis.md]
- **INFERRED:** HubSpot lifecycle cannot presently distinguish prospect, booked visitor, attendee, purchaser, active customer, or lapsed customer. [Source: audits/hubspot/current-state.md]

## Historical business-language journey

The histories describe a human, community-oriented journey: someone hears about the studio through Meta/social, the website, an event, referral, or local word of mouth; asks a question or books through Fitssey; arrives with beginner concerns; receives reassurance, instruction, and modifications; buys a pass, course, or event; builds regularity; and may later renew, lapse, return, or refer another person. This is historical context, not proof that every handoff currently occurs. [Sources: marketing-content-history.md; kurs-jogi-od-podstaw-history.md; general-unprojected-chats-history.md]

Kat historically emphasized low-pressure entry, being looked after, clear first steps, regular practice, and community. Structured beginner courses were used to build confidence before regular hot classes, while WhatsApp and personal messages supported course participants. Historical inactive-client outreach and seasonal “return to routine” messaging suggest reactivation intent, but no current cadence or outcome data is confirmed. [Sources: marketing-content-history.md; general-unprojected-chats-history.md]

## Proposed lifecycle evidence model

| Stage/state | Business-language description | Minimum system evidence | Status |
| --- | --- | --- | --- |
| New lead | A person has expressed interest but has not yet booked or bought. | New HubSpot/Meta acquisition event with usable contact method | **BUSINESS DECISION REQUIRED:** approve entry and repeat-submission rules. |
| Contacting | The studio is attempting a timely, helpful response. | Owned lead plus recorded outreach attempt | **BUSINESS DECISION REQUIRED:** approve SLA, channels, cadence, and outcomes. |
| Connected | A two-way exchange confirms the person was reached. | Recorded human response | **BUSINESS DECISION REQUIRED:** define acceptable channels and evidence. |
| Qualified | The studio and person have identified a suitable next step. | Approved fit/intent criteria and next action | **BUSINESS DECISION REQUIRED:** minimize health-adjacent data and define disqualification. |
| First booking | A first future visit is reserved in Fitssey. | Earliest Fitssey visit with status 0 (booked) | **BUSINESS DECISION REQUIRED:** approve exclusions and treatment of later cancellation/waitlist transitions. |
| First attended visit | The person completed the first studio experience. | Earliest Fitssey visit with status 1 (present) | **BUSINESS DECISION REQUIRED:** approve eligibility and treatment of free/event/course visits. |
| First-time customer | The person completed the approved first commercial conversion. | First paid order or approved paid-attendance rule | **BUSINESS DECISION REQUIRED:** decide treatment of free trials, vouchers, events, and courses. |
| Regular / active customer | The person has a valid relationship evidenced by recent attendance and/or entitlement. | Approved Fitssey entitlement/activity rule | **BUSINESS DECISION REQUIRED:** define per product type and recency. |
| Course participant | The person is enrolled in a structured, time-bounded program. | Current course enrollment/attendance evidence | **BUSINESS DECISION REQUIRED:** decide whether this is a segment, state, or both. |
| At-risk | Engagement is falling or an entitlement is near expiry. | Approved decline/expiry trigger | **BUSINESS DECISION REQUIRED:** choose thresholds and exclusions. |
| Lapsed | No qualifying activity has occurred within an approved interval. | Fitssey activity/entitlement evidence | **BUSINESS DECISION REQUIRED:** choose separate class, course, and contract windows. |
| Reactivated | A previously lapsed person attends or purchases again. | New qualifying event after lapse | **BUSINESS DECISION REQUIRED:** define reset and credit rules. |
| Advocate | The person explicitly refers, reviews, or supports the studio. | Recorded referral/review/ambassador evidence | **BUSINESS DECISION REQUIRED:** never infer advocacy from spend alone. |

## Entry-path context

- **Historical beginner path:** campaign/content or referral → question/booking → beginner course or suitable first class → regular class/pass or membership concept. [Source: marketing-content-history.md]
- **Historical event path:** social/newsletter/message → event interest → direct message, form, or Fitssey purchase → attendance → community follow-up. The route varied and should be standardized only after current review. [Source: marketing-content-history.md]
- **Historical children’s path:** guardian sees promotion → submits/requests contact → trial or course booking → child attendance → paid continuation. This remained partly proposed and raises guardian/minor data-model and consent decisions. [Source: strona-www-i-fitssey-history.md]
- **Proposed longevity path:** baseline measurement → activity program → recovery → repeat measurement → renewal. This is a grant-era proposal, not a current lifecycle. [Source: grants-dotacje-history.md]

## Known friction and service moments

- Historical beginner fears included being insufficiently fit, flexible, or experienced and uncertainty about which class to choose. [Sources: marketing-content-history.md; kurs-jogi-od-podstaw-history.md]
- Historical operational friction included late cancellations, no-shows, speculative bookings, pass-expiry/make-up requests, and manual booking or pass exceptions. [Source: rozwoj-studia-history.md]
- Historical demand varied by season and time slot; old schedules must not define current lifecycle triggers. [Sources: marketing-content-history.md; rozwoj-studia-history.md]
- First-visit preparation, welcome, modification, and clear next-step recommendations are strategically important but not documented as a current standard process. [Sources: kurs-jogi-od-podstaw-history.md; general-unprojected-chats-history.md]

## HubSpot lifecycle versus studio status

- **INFERRED:** Keep HubSpot's standard lifecycle stage for broad relationship progression and add one controlled `studio_customer_status` only after approval. [Source: docs/data-model.md]
- **INFERRED:** A contact can remain `Customer` in HubSpot while moving between Active, At-risk, Lapsed, and Reactivated studio status.
- **BUSINESS DECISION REQUIRED:** Approve mapping from studio evidence to HubSpot Lead/MQL/SQL/Opportunity/Customer; do not equate a form submission automatically with MQL or a Fitssey account automatically with Customer.
- **BUSINESS DECISION REQUIRED:** Decide whether free visits, vouchers, staff/test accounts, guardians booking for children, and event-only buyers qualify as Customers.

## Ownership and service levels

- **CONFIRMED:** HubSpot exposes two active owners, but current ownership distribution and lead activities were not included in the audit output. [Source: audits/hubspot/current-state.md]
- **HISTORICAL:** Kat/Kasia was the central customer-facing operator, and communication often occurred through WhatsApp, direct messages, phone, or Fitssey newsletters. This does not establish current ownership or lawful marketing permission. [Sources: marketing-content-history.md; rozwoj-studia-history.md]
- **BUSINESS DECISION REQUIRED:** Assign default and backup owner, hours of operation, first-response target, attempt cadence, escalation, stop conditions, and mandatory outcomes.
- **BUSINESS DECISION REQUIRED:** Separate operational/service messages from marketing nurture and respect subscription/consent state.

## Retention and reactivation context

Historical tactics included course progression, regularity challenges, longer or seasonal passes, workshops/events, personal reminders, inactive-client outreach, and post-holiday return-to-routine campaigns. They are evidence of prior thinking, not approved automation or current commercial policy. [Sources: marketing-content-history.md; general-unprojected-chats-history.md]

Future retention should be based on status-1 attended visits and verified entitlement/purchase evidence, not status-0 reservations alone. Product-specific thresholds are necessary because a course participant, limited-pass customer, unlimited-contract customer, and event-only buyer have different expected rhythms. [Sources: audits/fitssey/visit-status-map.md; audits/fitssey/current-state-reconciliation.md; rozwoj-studia-history.md]

## Automation prerequisites

- **CONFIRMED TECHNICAL INPUT:** Fitssey visit-status semantics and the point-in-time service/pricing/contract catalog are reconciled. [Sources: audits/fitssey/visit-status-map.md; docs/current-offer-register.md]
- **TECHNICAL FOLLOW-UP REQUIRED:** Validate approved stage calculations on sampled records and produce a PII-safe dry-run identity crosswalk; do not create links yet.
- **BUSINESS DECISION REQUIRED:** Approve lifecycle, field definitions, consent/legal basis, suppression rules, quiet hours, and exit criteria.
- **TECHNICAL FOLLOW-UP REQUIRED:** Design automations as disabled specifications with test cases and rollback paths before any activation request.
- **CONFIRMED:** Under repository rules, no marketing automation may be built until the lifecycle and data model are approved. [Source: AGENTS.md]
