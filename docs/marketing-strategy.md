# Marketing Strategy

Status: strategy synthesis only. It does not authorize campaigns, tracking, automation, schema changes, or external writes. Historical offers, prices, packages, class times, and schedules must not be advertised as current until reconciled against Fitssey and approved.

## Executive Summary

Hot Yoga Pilawa has historically marketed a supportive local studio where beginners can start without pressure and regular clients can combine strength, mobility, heat, recovery, and community. Meta is the only currently audited acquisition source, and HubSpot currently contains 382 paid-social form contacts. The histories add useful campaign and messaging context, but almost no reliable closed-loop performance evidence. The next marketing system should connect acquisition to first booking, attendance, first paid purchase, and retention while preserving consent and source-native identifiers. [Sources: audits/meta/current-state.md; audits/hubspot/current-state.md; audits/cross-system-gap-analysis.md; marketing-content-history.md]

## Current Acquisition Channels

- **CONFIRMED CURRENT:** Meta/Facebook lead generation feeds the audited HubSpot contact base; all 382 contacts have paid-social/form origins. [Source: audits/hubspot/current-state.md]
- **CONFIRMED CURRENT AS PLATFORM INVENTORY:** Meta contains 16 campaigns, 14 active lead forms, and 400 reported lead actions; only 78 person-level leads were retrievable. [Source: audits/meta/current-state.md]
- **HISTORICAL:** Instagram/Facebook organic content, website and Fitssey booking routes, WhatsApp, direct messages, phone, newsletters, events, reviews, referrals, and local partnerships. Current contribution and ownership are unknown. [Sources: marketing-content-history.md; general-unprojected-chats-history.md]

## Meta / Facebook

- Historical campaigns and concepts covered beginner yoga, Hot Pilates, general studio promotion, children’s yoga, workshops/events, seasonal challenges, and retreats. Implementation and results vary and must be verified against Meta. [Sources: marketing-content-history.md; strona-www-i-fitssey-history.md; general-unprojected-chats-history.md]
- The current audit confirms 15 lead-objective campaigns, one engagement campaign, 12 creative-referenced form IDs, mixed attribution windows, inconsistent naming, and a 322-lead person-history gap. [Source: audits/meta/current-state.md]
- Form schemas historically accumulated event-specific questions and inconsistent identity keys. Future forms should use a small stable identity/consent core and store repeat submissions as events rather than overwriting contact context. [Sources: audits/meta/current-state.md; docs/data-model.md]
- **GUARDRAIL:** No historical campaign copy, audience, radius, trial, price, timetable, or availability claim is approved for reuse without current offer and policy confirmation.

## Website / SEO

- **HISTORICAL:** The studio website and Fitssey booking page were used or referenced, and content was prepared for class descriptions, beginner FAQs, children’s offerings, workshops, retreats, and Bikram/Vinyasa education. Publication and current accuracy are uneven or unknown. [Sources: marketing-content-history.md; kurs-jogi-od-podstaw-history.md; rozwoj-studia-history.md]
- **UNKNOWN:** Current CMS ownership, SEO visibility, Search Console, conversion pages, form behavior, booking handoff, local-search performance, and current pricing/schedule accuracy. [Sources: general-unprojected-chats-history.md; docs/architecture.md]
- Future content should prioritize high-intent local questions: who a class is for, beginner readiness, what to expect, what to bring, safety/heat preparation, current availability, and one measurable next action. Claims require owner and compliance review.

## Google / Analytics

- **CONFIRMED:** A GA4 website stream has been created for `https://hotyogapilawa.pl` with Measurement ID `G-P4P791087B` and Stream ID `15766835455`, and it was attached to the existing Google tag already used by the studio’s Google Ads account. This confirms creation and attachment only—not reliable collection, event or conversion configuration, consent behavior, Consent Mode v2, Google Ads linkage/configuration, Search Console, HubSpot tracking, or duplicate-event handling. [Source: docs/architecture.md]
- A consent-aware minimum event taxonomy should be approved before deployment; candidate events are form start/submit, booking handoff/start/complete, purchase confirmation where technically and lawfully available, and consent update. [Source: docs/architecture.md]
- UTMs need controlled lowercase values and stable creative versions. GA4 must not receive names, emails, phones, health-adjacent text, or raw Fitssey identifiers. [Source: docs/architecture.md]
- Google Business Profile/review requests have historical support, but current profile ownership, review volume, and links are unknown. [Source: marketing-content-history.md]

## Organic Social

Historical practice was active, campaign-led Facebook/Instagram content using authentic studio images, direct CTAs, community language, behind-the-scenes context, educational benefits, and event promotion. Authentic photography, correct branding, correct Polish diacritics, and avoiding fabricated people/body changes were recurring production requirements. [Sources: marketing-content-history.md; general-unprojected-chats-history.md]

## Content Strategy

Historically recurring content pillars:

- beginner confidence: no need to be flexible, fit, or experienced; practice at one’s own pace;
- strength, conditioning, posture, mobility, flexibility, and regularity;
- stress relief, calm, breath, recovery, and “return to self”;
- community, attentive instruction, and the experience of being cared for;
- method education for Bikram/hot yoga, Hot Pilates, yoga styles, and first-visit preparation;
- seasonal return-to-routine, summer consistency, challenges, workshops, and community events;
- proposed longevity/recovery themes such as **Siła i Długowieczność** and **Regeneracja Premium**, always labeled proposed until launch is confirmed.

[Sources: marketing-content-history.md; kurs-jogi-od-podstaw-history.md; grants-dotacje-history.md]

## Local Marketing

Historical work emphasized Pilawa and the surrounding Garwolin-area community, local events, referrals, neighboring organizations, and potential partnerships with municipalities, schools, cultural centers, senior groups, businesses, hotels, spas, and specialists. Most partnership ideas are proposals rather than confirmed channels. Geographic radius and audience origin should come from current customer and campaign data, not historical targeting suggestions. [Sources: grants-dotacje-history.md; marketing-content-history.md; general-unprojected-chats-history.md]

## Referral / Review Opportunities

Historical messages asked clients or parents for Google/Facebook reviews and used community events or children’s birthday sessions as potential referral moments. No formal referral program or measured review-to-booking result is evidenced. A future program should use explicit attribution, non-coercive requests, and an approved reward policy. [Source: marketing-content-history.md]

## Email / CRM Opportunities

- HubSpot is intended to manage lifecycle, segmentation, communications, and attribution, but all audited contacts remain Lead with blank Lead Status. [Sources: audits/hubspot/current-state.md; docs/architecture.md]
- Historical communication relied heavily on WhatsApp, messages, and Fitssey newsletter concepts; response ownership and consent boundaries are unclear. [Sources: marketing-content-history.md; rozwoj-studia-history.md]
- Candidate future communication moments include lead response, booking assistance, first-visit preparation, missed booking follow-up, course progression, entitlement expiry, lapse, reactivation, and review/referral. None is authorized for automation.

## Customer Segments

Historically evidenced segments include beginners, course participants, regular yoga/hot-yoga clients, strength/fitness clients, wellness/recovery seekers, mature adults, children/teenagers, event/workshop clients, athletes, sedentary workers, women and men where explicitly discussed, and local residents. Perimenopause, corporate/BUR, remote/hybrid, and retreat segments are strategic proposals, not validated current audiences. [Sources: marketing-content-history.md; kurs-jogi-od-podstaw-history.md; grants-dotacje-history.md; general-unprojected-chats-history.md]

## Customer Problems and Motivations

Historical messaging addresses fear of not being fit/flexible/experienced enough; uncertainty about where to begin; stress, tension, fatigue, overthinking, poor routine, sedentary discomfort, desire for strength or body confidence, and need for supportive community. Operational evidence adds schedule fit, price/value, booking friction, cancellations, and pass expiry as possible barriers. These are historical observations or messaging hypotheses, not a validated current research dataset. [Sources: marketing-content-history.md; kurs-jogi-od-podstaw-history.md; rozwoj-studia-history.md]

## Offer Strategy

- Use a verified core offer hierarchy: beginner entry route → appropriate first booking → paid first purchase → repeat practice/entitlement → retention. Exact products and terms await Fitssey reconciliation.
- Preserve course-led onboarding as a historically promising hypothesis, because structured beginner courses were reported as commercially useful and confidence-building. Test it against current data before investment. [Source: marketing-content-history.md]
- Treat workshops, challenges, seasonal passes, recovery/longevity, hybrid, retreats, and children’s programs as separate offer hypotheses until current status, economics, capacity, and rules are approved.
- Do not use historical prices, package names, visit counts, expiry, schedule, or free-trial claims as current marketing facts.

## Funnel Strategy

Proposed measurable funnel: impression/click → lead submission → assigned lead → first response → connected/qualified → Fitssey registration → first booking → attended first visit → first paid purchase → repeat attendance → active/at-risk/lapsed/reactivated. Meta, HubSpot, and Fitssey each own different evidence layers; the analytical layer should join events after identity and consent decisions. [Sources: docs/attribution-model.md; docs/customer-lifecycle.md; audits/cross-system-gap-analysis.md]

## Retention / Reactivation Opportunities

Historical opportunities include first-to-second-visit support, course-to-regular transition, entitlement-expiry outreach, seasonal return-to-routine, declining-frequency detection, lapsed-client outreach, workshop/community invitations, and review/referral asks. Historical no-show and speculative-booking problems mean retention should reward real attendance, not only reservations or pass purchase. Thresholds and messaging require approval. [Sources: marketing-content-history.md; rozwoj-studia-history.md]

## Measurement Priorities

1. Lead volume, source/form/campaign, response time, contact outcome, and lead-to-booking conversion.
2. First-booking show rate and first-to-second attended-visit conversion after Fitssey status codes are confirmed.
3. First paid purchase, product category, repeat attendance, entitlement renewal, lapse, and reactivation.
4. Class utilization by verified current service/time, cancellation/no-show behavior, and seasonality.
5. Revenue reconciliation and contribution margin by approved offer.
6. Meta platform metrics alongside independently joined operational conversions; do not conflate the two.
7. Website conversion and UTM integrity after consent-aware GA4 deployment.

[Sources: audits/fitssey/current-state.md; audits/meta/current-state.md; docs/attribution-model.md]

## Historical Marketing Lessons

- Structured beginner education reduced anxiety and supported progression; historical demand was stronger for some evening cohorts than mornings. [Source: marketing-content-history.md]
- Regularity and commitment were recurring themes in passes and challenges, but aggressive discounting created concern about perceived value. [Source: marketing-content-history.md]
- Summer attendance declined historically, supporting seasonal retention planning rather than assuming steady demand. [Source: marketing-content-history.md]
- Event conversion routes varied among Meta forms, direct messages, Fitssey purchase, and newsletters; fragmented routes weaken attribution and operational ownership. [Source: marketing-content-history.md]
- Broad “all classes are beginner-friendly” messaging conflicted with historical intermediate service labels; future copy should route beginners precisely. [Source: kurs-jogi-od-podstaw-history.md]
- No historical narrative reliably establishes spend-to-revenue performance; current strategy must be measurement-led. [Sources: marketing-content-history.md; audits/cross-system-gap-analysis.md]

## Proposed Future Marketing System

Meta should remain media and lead-form truth; HubSpot should hold the consent-aware engagement profile and approved lifecycle state; Fitssey should remain operational conversion and revenue truth; GA4 should provide consent-aware website behavior; and an analytical layer should maintain immutable cross-system events. Begin with read-only reconciliation and disabled specifications. No write-back, audience upload, offline conversion, workflow, or campaign is authorized. [Source: docs/architecture.md]

## Business Decisions Required

- Confirm the current offer, prices, packages, schedules, class suitability, policies, and claims from Fitssey/owner review.
- Approve lead owner, SLA, disposition vocabulary, and channel handoffs.
- Approve core audience priorities and the beginner entry promise.
- Choose form/booking routes and a reusable lead-form data standard.
- Approve lifecycle, retention, attribution, UTM, identity, privacy, consent, and retention rules.
- Decide which historical programs are active, seasonal, paused, or abandoned.
- Decide when GA4 validation, event design, consent testing, HubSpot tracking, offline conversion, audience feedback, and automation enter scope.

## Open Questions

- Which current offers should paid and organic marketing prioritize?
- What is the verified first-time-client journey and primary conversion event?
- Who responds to each lead channel, how quickly, and how is the outcome recorded?
- Which messages and benefits are approved claims for each class/service?
- What channel drove each attended first visit and first paid purchase?
- What current behaviors predict renewal, lapse, and successful reactivation?
- Which privacy notices and consent signals govern service messages, marketing, analytics, and ad-platform feedback?
