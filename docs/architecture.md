# Architecture

Status: proposed target architecture following the 2026-09-12 read-only audit, with a post-audit GA4 status update. A GA4 website stream has been created and attached to an existing Google tag; it is not fully configured or validated. No synchronization or write-back is authorized.

## System roles

- **INFERRED:** Fitssey should remain the operational source of truth for clients, bookings/visits, pricing entitlements, contracts, purchases, and revenue, subject to status-code and finance reconciliation.
- **INFERRED:** HubSpot should become the engagement source of truth for contacts, approved lifecycle state, segmentation, communications, consent-aware marketing operations, and a denormalized view of Fitssey status.
- **CONFIRMED:** Meta is the source of truth for campaigns, ad sets, ads, lead forms, media spend, delivery, and platform-attributed actions.
- **CONFIRMED:** GA4 website stream URL `https://hotyogapilawa.pl`, Measurement ID `G-P4P791087B`, and Stream ID `15766835455` have been created. GA4 was attached to the existing Google tag already used by the studio’s Google Ads account. Creation/attachment does not confirm reliable event collection, consent behavior, Consent Mode v2, Google Ads linkage/configuration, conversion definitions, or duplicate-event handling.
- **INFERRED:** A small external analytical layer is appropriate for append-only cross-system events, reconciliation, retention/cohort analysis, and attribution joins.

## Target data flow

```text
Meta lead/events -----> controlled ingestion -----> HubSpot contact/acquisition summary
        |                         |
        v                         v
analytical layer <----- identity crosswalk <----- Fitssey read-only extracts
        ^                                           |
        |                                           v
GA4 website events (unvalidated)          HubSpot operational summaries
```

- **INFERRED:** Initial production flows should be one-way: Meta to HubSpot, Fitssey to HubSpot, and all sources to analytics.
- **INFERRED:** HubSpot-to-Fitssey writes are unnecessary for the first implementation and should remain disabled.
- **BUSINESS DECISION REQUIRED:** Meta audience uploads, offline conversions, or CRM-to-Meta feedback are separate future capabilities requiring explicit approval and privacy review.

## Integration boundaries

- **TECHNICAL FOLLOW-UP REQUIRED:** Use environment variables, dedicated least-privilege credentials, GET-only clients during build validation, and separate read/write code paths.
- **TECHNICAL FOLLOW-UP REQUIRED:** Preserve source IDs and source timestamps; checkpoint pagination; handle `Retry-After`; implement idempotency and replay-safe backfill.
- **TECHNICAL FOLLOW-UP REQUIRED:** Logs must contain counts, timings, status codes, and masked errors—not access tokens or raw contact fields.
- **TECHNICAL FOLLOW-UP REQUIRED:** Add automated assertions that reject outbound non-GET requests until a future write phase is explicitly enabled.
- **TECHNICAL FOLLOW-UP REQUIRED:** Use a dead-letter/conflict queue for ambiguous identities rather than creating or merging records automatically.

## Update frequency proposal

- **BUSINESS DECISION REQUIRED:** Meta lead ingestion target: near-real-time or frequent polling, subject to consent and operational SLA.
- **BUSINESS DECISION REQUIRED:** Fitssey current-state summaries: hourly or daily depending on follow-up and retention use cases.
- **INFERRED:** Historical visits, sales, and Meta insights can refresh daily; late-arriving data should be re-read over a rolling window.
- **TECHNICAL FOLLOW-UP REQUIRED:** Validate Fitssey rate budgets before selecting frequency; the documented ceiling includes 200 requests per five minutes.

## Website analytics and GA4 planning

### GA4 Measurement ID

- **CONFIRMED:** `.env.example` defines the non-secret values `GA4_MEASUREMENT_ID=G-P4P791087B` and `GA4_STREAM_ID=15766835455`.
- **CONFIRMED:** The GA4 website stream URL is `https://hotyogapilawa.pl`, Measurement ID is `G-P4P791087B`, and Stream ID is `15766835455`; the stream was attached to the existing Google tag already used by the studio’s Google Ads account.
- **UNKNOWN / NOT AUDITED:** Reliable live event collection, event taxonomy, consent/banner behavior, Google Consent Mode v2 configuration, Google Ads linkage/configuration, Search Console, HubSpot website tracking, conversion definitions, duplicate-event behavior, retention settings, and Google Signals configuration.

### Website analytics

- **BUSINESS DECISION REQUIRED:** Define a minimal event taxonomy before treating the stream as validated or using it for reporting: page view, lead-form start/submit, booking start/complete, purchase handoff/complete, and consent update are candidates, not approved events.
- **INFERRED:** Do not send names, emails, phone numbers, health-adjacent form text, or Fitssey raw identifiers in GA4 events or URLs.

### UTM standards

- **BUSINESS DECISION REQUIRED:** Approve controlled lowercase values for `utm_source`, `utm_medium`, `utm_campaign`, `utm_content`, and `utm_term`, plus immutable Meta IDs where available.
- **INFERRED:** Recommended campaign token pattern is `market_offer_audience_yyyymm`; creative content should carry a stable version token. Exact Polish/English vocabulary remains a business choice.
- **TECHNICAL FOLLOW-UP REQUIRED:** Enforce URL validation and store both the original raw UTM touch and normalized reporting value.

### HubSpot website tracking

- **UNKNOWN:** Current HubSpot tracking-code deployment, cookie behavior, domain configuration, and form tracking were not inspected.
- **BUSINESS DECISION REQUIRED:** Decide which website events belong in HubSpot versus GA4 and prevent duplicate form/conversion events.

### Consent and Google Consent Mode v2

- **CONFIRMED:** Google states Consent Mode consumes choices from a consent banner and does not provide the banner itself; advanced mode may transmit cookieless pings under denied consent: <https://support.google.com/analytics/answer/10000067>.
- **BUSINESS DECISION REQUIRED:** Choose a consent-management approach and obtain Polish/EU legal review for default states, categories, notices, withdrawal, evidence, and tag behavior.
- **TECHNICAL FOLLOW-UP REQUIRED:** When authorized, test `analytics_storage`, `ad_storage`, `ad_user_data`, and `ad_personalization` in all banner paths before production.

### Future attribution integration

- **INFERRED:** GA4 should contribute web-touch events to the analytical layer, not overwrite Fitssey conversion truth or Meta delivery truth.
- **BUSINESS DECISION REQUIRED:** Decide whether consented client/user IDs may be used for cross-device or offline joins; default to pseudonymous, minimized identifiers.

## Security, privacy, and governance

- **CONFIRMED:** GDPR requires purpose limitation, minimization, accuracy, storage limitation, lawful processing, transparency, processor controls, security, and compliant international transfers: <https://eur-lex.europa.eu/eli/reg/2016/679/oj/eng>.
- **BUSINESS DECISION REQUIRED:** Complete a data-processing inventory, processor/subprocessor review, retention schedule, access matrix, and transfer assessment before enabling cross-system writes or ad feedback.
- **UNKNOWN:** Whether a DPIA is legally required; assess this with qualified counsel based on final scope, profiling, sensitive data, minors, scale, and tracking design.
