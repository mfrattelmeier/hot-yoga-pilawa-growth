# Historical Business Knowledge Synthesis

Prepared from immutable historical ChatGPT extracts and the 2026-09-12 read-only technical audit. This is a decision-support layer, not an operating catalog. Historical pricing, package structures, class times, and schedules are never treated as current truth; current commercial and timetable facts must be reconciled against Fitssey and independently approved.

Evidence labels used below: **CONFIRMED CURRENT**, **HISTORICAL FACT**, **HISTORICAL PROPOSAL**, **INFERRED**, **UNKNOWN**, **BUSINESS DECISION REQUIRED**, and **TECHNICAL AUDIT CORRECTION**.

## 1. Executive Summary

Hot Yoga Pilawa is an operating boutique yoga and movement studio in Pilawa with meaningful booking, visit, sale, and paid-lead history. The strongest current evidence comes from the technical audit: Fitssey exposes 466 active clients, 8,137 visit rows, 45 class services, 45 pricing options, two contract products, and sales history; HubSpot contains 382 paid-social form contacts, all still at Lead; Meta reports 400 lead actions and currently exposes 78 person-level Page-form leads. [Sources: audits/fitssey/current-state.md; audits/hubspot/current-state.md; audits/meta/current-state.md]

The histories explain how the business developed: beginner courses, varied group classes, passes, community communication, events, challenges, and personal follow-up were used to build confidence and regularity. They also document operational strain from late cancellations, no-shows, speculative reservations, pass exceptions, seasonality, and manual administration. [Sources: marketing-content-history.md; rozwoj-studia-history.md]

Recurring strategic ambition extends beyond classes into **Siła i Długowieczność**, **Regeneracja Premium**, **Studio Hybrydowe**, recovery, measurement-led programs, retreats, BUR/corporate services, and digital content. Most of these are proposals or grant-era plans rather than verified current services. [Sources: grants-dotacje-history.md; general-unprojected-chats-history.md]

The central implementation problem is not a lack of data but a lack of approved joins and definitions. Meta and HubSpot describe acquisition; Fitssey describes customers and operations; no approved model currently connects lead → booking → attendance → purchase → retention. Identity, lifecycle, consent, offer truth, finance reconciliation, and attribution must be decided before schema creation or automation. [Source: audits/cross-system-gap-analysis.md]

## 2. Confirmed Business Facts

- **CONFIRMED CURRENT:** Hot Yoga Pilawa operates in Pilawa; the current Meta Page is categorized as a Yoga Studio. [Sources: audits/meta/current-state.md; general-unprojected-chats-history.md]
- **CONFIRMED CURRENT:** Fitssey is the richest operational system in the audit, containing clients, services, schedules/visits, entitlements, contracts, purchases, and sales linked through stable GUIDs. [Source: audits/fitssey/current-state.md]
- **CONFIRMED CURRENT:** HubSpot contains 382 contacts, all originating from paid-social forms and all still at Lead with blank Lead Status. [Source: audits/hubspot/current-state.md]
- **CONFIRMED CURRENT:** Meta contains 16 campaigns, 15 lead-objective campaigns, 14 active lead forms, and 400 reported lead actions; two campaigns were active at audit time. [Source: audits/meta/current-state.md]
- **CONFIRMED CURRENT:** Fitssey and HubSpot are not a unified customer view. Only 107 HubSpot contacts matched active Fitssey clients by normalized email in the audited comparison. [Source: audits/cross-system-gap-analysis.md]
- **CONFIRMED CURRENT:** A GA4 website stream has now been created for `https://hotyogapilawa.pl` and attached to the studio’s existing Google tag. This confirms creation and attachment only; live collection and configuration have not been validated. [Source: docs/architecture.md]
- **CONFIRMED HISTORICAL IDENTITY:** The business operated under the Hot Yoga Pilawa name and used a multi-instructor, community-oriented studio model. Current staff responsibilities were not established by the technical audit. [Sources: kurs-jogi-od-podstaw-history.md; rozwoj-studia-history.md]

## 3. Historical Business Facts

- The studio historically sold paid group practice through single entries, passes/packages, structured courses, contracts/membership concepts, and paid events. Exact current availability and terms are unknown. [Sources: marketing-content-history.md; rozwoj-studia-history.md; general-unprojected-chats-history.md]
- Structured beginner courses were actually delivered in 2025, including multiple cohorts, staged curriculum, instructor/student materials, homework, and WhatsApp follow-up. The owner described courses as commercially stronger than relying only on a broad drop-in schedule. [Source: marketing-content-history.md]
- Dated Fitssey screenshots from 2026 show a broad yoga/Pilates/mobility portfolio and multiple instructors. They are historical snapshots, not the current timetable. [Sources: kurs-jogi-od-podstaw-history.md; rozwoj-studia-history.md]
- The studio historically ran or prepared workshops, community challenges, children’s programming, seasonal campaigns, and a completed yoga/Pilates retreat. Current recurrence and economics are unknown. [Sources: marketing-content-history.md; general-unprojected-chats-history.md]
- Historical communications used Facebook, Instagram, website/Fitssey, WhatsApp, phone/messages, and newsletters. Reviews, events, referrals, and local relationships were also acquisition or advocacy themes. [Sources: marketing-content-history.md; general-unprojected-chats-history.md]
- Booking misuse, late cancellations, no-shows, course/pass exceptions, and owner-managed changes were reported as real operating problems in early 2026. Rules were tightened in response, but the final/current configuration is unverified. [Source: rozwoj-studia-history.md]
- Summer attendance decline, weaker historical morning demand, and stronger evening demand were observed in specific periods. These observations do not establish current seasonality or schedule strategy. [Sources: marketing-content-history.md; rozwoj-studia-history.md]
- Historical facility narratives describe rented premises, heated practice infrastructure, a principal studio room, and a smaller additional room considered for new services. Exact current dimensions, capacity, and fit-out status are unverified. [Sources: grants-dotacje-history.md; general-unprojected-chats-history.md]

## 4. Current or Likely Current Offers

Only system-level existence can be elevated safely:

- **CONFIRMED CURRENT AT CATALOG LEVEL:** Fitssey exposes 45 class services, of which 28 are classroom and 17 are course services. [Source: audits/fitssey/current-state.md]
- **CONFIRMED CURRENT AT COMMERCIAL-SYSTEM LEVEL:** Fitssey exposes 45 pricing options and two contracts; 26 pricing options and both contracts are sold online. [Source: audits/fitssey/current-state.md]
- **LIKELY CURRENT CATEGORY, NOT ITEM-LEVEL CONFIRMATION:** Group yoga and movement classes remain central, given the current system inventory and Page category. Individual names, heat levels, schedule, instructors, prices, inclusions, and suitability still require Fitssey/owner reconciliation. [Sources: audits/fitssey/current-state.md; audits/meta/current-state.md]
- **UNKNOWN CURRENT STATUS:** No particular historical pass, class, course, event, free trial, membership, timetable, or price is declared current by this synthesis.

## 5. Historical / Proposed Offers

| Offer family | Historical evidence | Current treatment |
| --- | --- | --- |
| Bikram Joga (26&2), HOT JOGA / hot yoga | Appeared in delivered courses and dated schedules. | **HISTORICAL; reconcile in Fitssey.** |
| Inferno Hot Pilates / Gorący Pilates HIIT / Hot Pilates START | Classes, internal instructor material, and campaigns were prepared or delivered. | **HISTORICAL; names, format, claims, and level may have changed.** |
| Classical Pilates, Hatha, Vinyasa, Iyengar, Yin/fascial, mobility/stretching, healthy-spine/gentle practice, breathing/relaxation | Appeared across dated schedules and marketing. | **HISTORICAL; current catalog/schedule unknown.** |
| Kurs Jogi od Podstaw, Level 1/2 beginner pathways | Multiple cohorts and course sessions were delivered. | **HISTORICAL; strategically promising but not assumed live.** |
| Children’s yoga, teen/age-band courses, birthdays | Some delivery evidence exists; campaigns and age structures also contain proposals. | **HISTORICAL OR PROPOSED; minor/guardian rules unresolved.** |
| Workshops/events: HOT 20, Karmazynowy Koń, Poczuj Siebie, women’s events, sound-bath concepts, other community events | Mix of implemented preparation, published historical terms, and completed activities. | **HISTORICAL; recurrence and current offer unknown.** |
| Multi-entry, OPEN/unlimited, Premium, Family, seasonal and commitment passes | Many historical versions, promotions, suspensions, and rule changes. | **HISTORICAL; no price or structure is current truth.** |
| Retreats / weekends | At least one community retreat is described as completed; additional models were proposed. | **HISTORICAL OR PROPOSED; current availability unknown.** |
| **Siła i Długowieczność** | Core grant-era expansion pillar. | **HISTORICAL PROPOSAL; launch/funding unknown.** |
| **Regeneracja Premium** | Core grant-era recovery pillar with equipment and forecast work. | **HISTORICAL PROPOSAL; launch/funding unknown.** |
| **Studio Hybrydowe** | Live/recorded/digital delivery concept with extensive AV planning. | **HISTORICAL PROPOSAL; deployment unknown.** |
| BUR/corporate wellbeing, private/specialist services, retail, teacher training | Explored as expansion routes. | **HISTORICAL PROPOSAL; validate demand, scope, and legal/operational readiness.** |

[Sources: marketing-content-history.md; kurs-jogi-od-podstaw-history.md; grants-dotacje-history.md; rozwoj-studia-history.md; general-unprojected-chats-history.md]

## 6. Customer Segments

Historically evidenced or explicitly targeted segments include:

- beginners and people returning after a break;
- regular yoga and hot-yoga practitioners;
- strength, conditioning, Hot Pilates, and fitness-oriented clients;
- people seeking mobility, flexibility, back-care-oriented movement, breathing, calm, or recovery;
- structured-course participants and workshop/event clients;
- mature/older adults and active-ageing prospects;
- children and teenagers, with guardians as likely decision-makers;
- women and men where explicitly mentioned, including perimenopause as a proposed niche;
- athletes and sedentary/office workers;
- local customers centered on Pilawa and the wider Garwolin-area context;
- proposed corporate/BUR, remote/hybrid, retreat, and recovery/longevity audiences.

The histories do not establish present segment size, profitability, retention, geographic radius, or prioritization. [Sources: marketing-content-history.md; kurs-jogi-od-podstaw-history.md; grants-dotacje-history.md; general-unprojected-chats-history.md]

## 7. Customer Journey Evidence

| Journey stage | Historical evidence | Current evidence/gap |
| --- | --- | --- |
| Discovery | Meta/Facebook/Instagram, website, community, events, reviews/referrals, local relationships. | Meta is audited; other channel contribution is unknown. |
| Lead/inquiry | Meta forms, messages, phone, WhatsApp, website/Fitssey routes. | HubSpot has paid-social leads, but no populated operational outcomes. |
| Follow-up | Historically personal/manual, often owner-led; proposed callback/contact flows. | Current owner, SLA, cadence, and disposition are unknown. |
| Registration/booking | Fitssey used for schedule, registration, and customer self-service; manual exceptions occurred. | Fitssey is operational truth, but visit-status codes remain unresolved. |
| First visit | Historical reassurance emphasized own pace, modifications, clear preparation, and being looked after. | No current standardized first-visit process was audited. |
| Purchase | Pass, course, event, or contract concepts; structured courses supported progression. | Fitssey sales exist; current product and finance semantics need reconciliation. |
| Repeat/active | Regular practice and course progression were explicit goals; some highly engaged clients reportedly attended frequently. | Active/regular thresholds are not approved. |
| At-risk/lapsed | Seasonal decline, inactivity, expiry, or falling attendance were recognized informally. | No approved trigger or HubSpot status exists. |
| Reactivation | Personal outreach, return-to-routine, seasonal passes, and event invitations were used/proposed. | No current automation or measured outcome. |
| Advocate | Review requests, referrals, community events, and word of mouth were encouraged. | No formal referral field or program is confirmed. |

[Sources: marketing-content-history.md; rozwoj-studia-history.md; general-unprojected-chats-history.md; audits/cross-system-gap-analysis.md]

## 8. Marketing History and Themes

The historical marketing style was active, local, and campaign-driven. Meta/Facebook and Instagram supported beginner acquisition, Hot Pilates, children’s yoga, workshops, challenges, seasonal passes, events, and retreat promotion. The preferred voice was warm, direct, encouraging, community-oriented, premium, and non-judgmental. Authentic studio photography, correct logo usage, and correct Polish language/diacritics mattered. [Sources: marketing-content-history.md; kurs-jogi-od-podstaw-history.md; general-unprojected-chats-history.md]

Recurring themes included “start without pressure,” strength plus calm, regularity, return to routine, being cared for, stress relief, body awareness, supportive community, and practical benefits. Polish terms worth preserving include **Kurs Jogi od Podstaw**, **Poczuj Siebie**, **Siła i Długowieczność**, **Regeneracja Premium**, **Studio Hybrydowe**, “Do zobaczenia na macie,” and “Spokojnie, bez presji i we własnym tempie.” These are historical language assets, not blanket approval of associated claims or offers. [Sources: marketing-content-history.md; kurs-jogi-od-podstaw-history.md; grants-dotacje-history.md]

No historical source reliably provides complete spend-to-revenue results. The current Meta audit supplies platform delivery totals, but the lead-to-Fitssey conversion chain remains incomplete. [Sources: audits/meta/current-state.md; audits/cross-system-gap-analysis.md]

## 9. Customer Needs, Objections, and Motivations

- Fear of not being flexible, fit, experienced, or able to keep up. [Sources: marketing-content-history.md; kurs-jogi-od-podstaw-history.md]
- Uncertainty about which method or first class is appropriate. [Source: kurs-jogi-od-podstaw-history.md]
- Desire for strength, conditioning, posture, mobility, flexibility, body confidence, energy, and routine. [Sources: marketing-content-history.md; kurs-jogi-od-podstaw-history.md]
- Desire for calm, stress relief, reduced tension, breath, rest, recovery, and a protected hour for oneself. [Sources: marketing-content-history.md; grants-dotacje-history.md]
- Need for supportive instruction, modifications, community, and practical first-visit reassurance. [Sources: marketing-content-history.md; kurs-jogi-od-podstaw-history.md]
- Buying/return barriers historically included schedule fit, seasonality, price/value, pass expiry, late cancellation, no-show behavior, and booking administration. [Sources: marketing-content-history.md; rozwoj-studia-history.md]

These are historical observations and messaging themes, not a quantified current voice-of-customer study.

## 10. Operational Practices

- Fitssey historically supported registration, schedules, bookings, pricing/pass administration, and instructor visibility; the current audit confirms its broader operational data role. [Sources: rozwoj-studia-history.md; audits/fitssey/current-state.md]
- Client self-booking and self-cancellation were emphasized after owner-managed exceptions became burdensome. [Source: rozwoj-studia-history.md]
- Historical rules covered cancellation lead time, minimum class size, pass validity, freezes, make-ups, transferability, and vouchers, but versions conflict and some differed from displayed Fitssey settings. No historical rule is current by default. [Source: rozwoj-studia-history.md]
- Instructor and heating costs were reasons to manage minimum attendance and released capacity. [Source: rozwoj-studia-history.md]
- Course delivery used curriculum plans, instructor notes, handouts/homework, attendance tracking, and WhatsApp follow-up. [Source: marketing-content-history.md]
- Historical schedules show multi-instructor coverage and a range of morning/evening/weekend activity. No class time or schedule in the histories is current truth. [Sources: kurs-jogi-od-podstaw-history.md; rozwoj-studia-history.md]

## 11. Business Goals and Growth Priorities

Supported recurring goals were to increase attendance and regularity, improve conversion from beginner/course participation to ongoing practice, fill weaker classes, reduce no-shows and manual administration, improve retention/reactivation, build premium events and new revenue streams, improve paid-ad efficiency, strengthen website/analytics, and create measurable growth beyond owner-taught classes. [Sources: marketing-content-history.md; rozwoj-studia-history.md; general-unprojected-chats-history.md]

The current technical priority is to define lifecycle and identity, reconcile Fitssey product/finance semantics, and build a consent-aware measurement foundation before campaign or automation expansion. [Sources: audits/cross-system-gap-analysis.md; docs/architecture.md]

## 12. Grant-Related Initiatives

Grant work evolved into three principal service pillars: **Regeneracja Premium**, **Siła i Długowieczność**, and **Studio Hybrydowe**. Associated planning covered red-light/recovery equipment, pressotherapy, cold plunge, body-composition measurement, strength equipment, AV/live delivery, customer measurement loops, staffing/internship, BUR, corporate services, and 2027–2030 forecasts. [Source: grants-dotacje-history.md]

The histories document many vendor, quantity, budget, tax, staffing, and forecast revisions. They do not confirm final application submission, award, accepted budget, purchase, installation, service launch, or current revenue. All grant outputs remain historical plans until reconciled against signed documents and live operations. [Sources: grants-dotacje-history.md; general-unprojected-chats-history.md]

The intended positioning was explicitly non-medical: monitor progress and support movement/recovery without diagnosing or treating. Qualified operator, contraindication, hygiene, maintenance, consent, incident, insurance, and claims rules remain required decisions. [Source: grants-dotacje-history.md]

## 13. Website / Fitssey / Digital History

- The website and Fitssey front office historically acted as information and booking routes. Draft content included class descriptions, beginner FAQs, children’s offers, workshops, retreats, and educational pages. Publication/current accuracy is unknown. [Sources: marketing-content-history.md; kurs-jogi-od-podstaw-history.md; rozwoj-studia-history.md]
- Fitssey historically displayed schedules, levels, instructor assignments, and availability; current API data confirms rich operational entities but not human-readable visit-status meanings or a reconciled finance total. [Sources: kurs-jogi-od-podstaw-history.md; audits/fitssey/current-state.md]
- Hybrid/live/VOD delivery and a paid library were repeatedly proposed, with substantial AV planning, but deployment and demand were not confirmed. [Sources: grants-dotacje-history.md; general-unprojected-chats-history.md]
- The historical sources and Phase 1 audit did not establish GA4, Search Console, Google Ads configuration, or current HubSpot website tracking. Post-audit, a GA4 stream was created and attached to the existing Google tag; all listed validation/configuration questions remain open. [Sources: docs/architecture.md; general-unprojected-chats-history.md]

## 14. Recurring Strategic Themes

1. Reduce beginner anxiety through education, precise routing, and supportive instruction.
2. Build regularity rather than depend on isolated drop-ins.
3. Combine strength, mobility, heat, calm, and community without losing clarity.
4. Protect premium value while using time-bounded challenges or offers carefully.
5. Use authentic local content and human follow-up.
6. Expand from classes toward higher-value programs only when demand, capacity, safety, and economics are proven.
7. Reduce manual exceptions with clear policies and systems.
8. Measure lead-to-attendance-to-revenue, not platform leads alone.
9. Keep recovery/longevity positioning non-medical and evidence-aware.
10. Preserve source IDs and business history so attribution and lifecycle decisions are auditable.

[Sources: marketing-content-history.md; rozwoj-studia-history.md; grants-dotacje-history.md; audits/cross-system-gap-analysis.md]

## 15. Contradictions and Superseded Information

- **Business start date:** a historical CEIDG extract says 27 May 2025; another narrative says 31 May 2025. [Sources: grants-dotacje-history.md; general-unprojected-chats-history.md]
- **Customer/class scale:** historical active-client, weekly-class, room-capacity, and timetable figures vary by date and source. None should be used as current without Fitssey reconciliation.
- **Pricing/packages:** single-entry, multi-entry, OPEN, Premium, seasonal, challenge, course, and event terms changed repeatedly. Some figures were proposals, some published historically, and some were later replaced or suspended. None is current truth. [Sources: marketing-content-history.md; rozwoj-studia-history.md; general-unprojected-chats-history.md]
- **Beginner promise:** broad “all classes” accessibility messaging conflicts with historical intermediate labels for some services. [Source: kurs-jogi-od-podstaw-history.md]
- **Booking rules:** cancellation deadlines, minimum class sizes, freeze length, and course/pass structures differ across historical versions; one reported Fitssey freeze setting conflicted with intended policy. [Source: rozwoj-studia-history.md]
- **Children’s offer:** age bands and free-trial scope differed between brief and proposed targeting/copy. [Source: strona-www-i-fitssey-history.md]
- **Grant/procurement:** equipment quantities/models, AV scope/budget, treatment table, recovery price, 2030 recovery volume, forecasts, and internship design changed repeatedly. [Source: grants-dotacje-history.md]
- **Business finances:** historical monthly turnover/cost ranges and forecast models differ and were not reconciled to accounting. [Sources: grants-dotacje-history.md; general-unprojected-chats-history.md]
- **Abandoned/superseded concepts:** several visual directions, an initial OPEN structure, parts of the AV design, NAS/Zoom Rooms/dedicated media equipment, some procurement variants, and multiple campaign routes were dropped or replaced during planning. [Sources: marketing-content-history.md; grants-dotacje-history.md]

## 16. Unknowns

- Current Fitssey service names, active schedule, instructors, capacities, prices, contracts, passes, package rules, introductory offers, and customer-facing descriptions.
- Final meanings of Fitssey visit status codes and finance-grade revenue/refund/void/tax totals.
- Current lead ownership, response times, activity logging, outcomes, and handoff to booking.
- Current customer motivations, objections, segment sizes, referral sources, retention, lapse, and reactivation performance.
- Reliable GA4 live collection; event taxonomy; consent/banner behavior; Consent Mode v2; Google Ads linkage/configuration; Search Console; HubSpot website tracking; conversion definitions; and duplicate-event behavior.
- Current privacy notices, lawful bases, consent evidence, processor terms, retention/deletion practices, and special-category/minor-data handling.
- Whether grant applications were approved and which proposed equipment/services were funded, purchased, installed, launched, or abandoned.
- Current financial truth and contribution margin by offer.
- Complete historical person-level Meta lead history beyond the 78 retrievable records.

## 17. Business Decisions Required

1. Approve current offer and commercial truth from Fitssey, explicitly replacing historical prices/packages/schedules.
2. Define lead, qualified lead, first-time customer, active, at-risk, lapsed, reactivated, course participant, and advocate.
3. Assign lead ownership, SLA, cadence, disposition, escalation, and stop rules.
4. Approve Fitssey GUID linkage, duplicate/conflict review, and guardian/minor identity treatment.
5. Approve a minimal HubSpot schema and event-history architecture.
6. Decide historical backfill scope and acceptable evidence for the 322-lead gap.
7. Approve booking/cancellation/no-show/expiry/freeze/refund rules and ensure Fitssey configuration matches.
8. Confirm beginner routing and approved claims by service.
9. Prioritize or retire proposed expansion offers and grant initiatives.
10. Approve retention windows and interventions by product type.
11. Approve attribution definitions, UTMs, canonical timezone/currency, and reporting ownership.
12. Approve privacy, consent, tracking, retention, minor-data, and audience/offline-conversion boundaries.

## 18. Technical Audit Conflicts / Corrections

- **TECHNICAL AUDIT CORRECTION:** Historical assumptions that Fitssey client details, prices, or rules were unknown are superseded at the inventory level by the current API audit, but item-level current offer truth still needs reconciliation. [Source: audits/fitssey/current-state.md]
- **TECHNICAL AUDIT CORRECTION:** Historical sources contained little or no HubSpot evidence; the audit confirms 382 paid-social contacts, 432 contact properties, and an unimplemented lifecycle state. [Source: audits/hubspot/current-state.md]
- **TECHNICAL AUDIT CORRECTION:** Historical marketing narratives do not establish Meta performance. The audit confirms platform inventories and delivery totals, while also showing incomplete person history and mixed attribution. [Source: audits/meta/current-state.md]
- **TECHNICAL AUDIT CORRECTION:** Historical assumptions that email/phone could connect systems cleanly are unsafe. Fitssey contains duplicate and missing identity fields; phone-only automatic matching is not acceptable. [Sources: audits/fitssey/current-state.md; docs/data-model.md]
- **TECHNICAL AUDIT CORRECTION:** Historical visit and sales labels cannot be inferred safely. Fitssey numeric visit statuses need vendor confirmation, and sales pagination must be reconciled before attendance or revenue reporting. [Source: audits/fitssey/current-state.md]
- **TECHNICAL AUDIT CORRECTION:** GA4 now exists as a website stream attached to the studio’s existing Google tag, but it is not yet a validated measurement source. Reliable collection, events, consent, advertising configuration, conversions, and duplicate handling remain unknown. [Source: docs/architecture.md]
- **TECHNICAL AUDIT CORRECTION:** Fitssey should remain operational truth, HubSpot the future engagement/lifecycle view, Meta media truth, and an analytical layer the cross-system history. No write-back is authorized. [Sources: AGENTS.md; docs/architecture.md]

## 19. Source Map

- `INDEX.md` — immutable-source inventory, provenance, and duplicate-collapse notes.
- `general-unprojected-chats-history.md` — broad studio history, owner narrative, offers, events, marketing, facility, and strategy.
- `grants-dotacje-history.md` — legal/business snapshot, grant pillars, procurement, forecasts, recovery/longevity/hybrid concepts, BUR and internship planning.
- `kurs-jogi-od-podstaw-history.md` — delivered beginner/IHP instructional history, dated Fitssey schedules, class positioning, and beginner-message conflicts.
- `marketing-content-history.md` — course-led business model, campaigns, events, passes/promotions, customer communications, seasonality, reviews, and content language.
- `rozwoj-studia-history.md` — historical pricing/rule changes, booking friction, dated timetable, operations, facility, staffing, and early grant/expansion ideas.
- `strona-www-i-fitssey-history.md` — narrow historical children’s-yoga campaign and proposed lead/guardian journey; limited evidence of actual website/Fitssey implementation.
- `audits/cross-system-gap-analysis.md` — authoritative Phase 1 cross-system findings and target ownership recommendations.
- `audits/hubspot/current-state.md` — current HubSpot inventory, permissions, contact state, and data quality.
- `audits/meta/current-state.md` — current Meta inventory, performance aggregates, lead-history limits, and form schema findings.
- `audits/fitssey/current-state.md` — current Fitssey inventory, client/identity quality, visits, sales, and API constraints.
- `docs/architecture.md`, `docs/attribution-model.md`, `docs/customer-lifecycle.md`, and `docs/data-model.md` — proposed technical context; none authorizes implementation.
