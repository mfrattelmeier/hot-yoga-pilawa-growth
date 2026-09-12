# Meta Current-State Audit

Audit date: 2026-09-12. Scope: Graph API v26.0 GET requests only. No campaign, ad set, ad, form, Page, audience, or account mutation was attempted. Counts are point-in-time.

## Access and account

- **CONFIRMED:** The credential can read Business `155572145764580`, Ad Account `1339768977067748`, and Page `644853172034596`; all three checks returned HTTP 200.
- **CONFIRMED:** The ad account is enabled, uses `PLN`, and is configured for `Europe/Warsaw`.
- **CONFIRMED:** The Page is categorized as a Yoga Studio and had 664 followers/fans at audit time.
- **CONFIRMED:** Granted permissions returned by Meta are `ads_management`, `ads_read`, `business_management`, `leads_retrieval`, `pages_manage_ads`, `pages_read_engagement`, `pages_show_list`, and `public_profile`; none were reported declined.
- **INFERRED:** The credential has broader write-capable permissions than a read-only audit needs, even though this audit issued GET requests only.
- **BUSINESS DECISION REQUIRED:** After the audit, decide whether a dedicated least-privilege read integration identity should replace the current credential. Do not change permissions without approval.

## Campaign, ad set, and ad inventory

- **CONFIRMED:** The account contains 16 campaigns: 15 with objective `OUTCOME_LEADS` and one with `OUTCOME_ENGAGEMENT`.
- **CONFIRMED:** Two campaigns are active and 14 are paused.
- **CONFIRMED:** Campaigns were created from 2025-07-15 through 2026-06-29.
- **CONFIRMED:** One active engagement campaign has a `start_time` of 1970-01-01 despite a 2025 creation date.
- **CONFIRMED:** The account contains 15 ad sets: 13 configured paused and two configured active; effective status is 13 paused, one active, and one campaign-paused.
- **CONFIRMED:** Ad-set optimization goals are Lead Generation (7), Quality Lead (6), and Offsite Conversions (2); all bill on impressions.
- **CONFIRMED:** Eleven ad sets use 1-day click attribution, two use 7-day click plus 1-day view, and two returned no attribution specification.
- **CONFIRMED:** The account contains 50 ads: 44 configured paused and six active; effective status is 44 paused, four active, and two ad-set-paused.
- **CONFIRMED:** Ad creatives reference 12 distinct lead-form IDs.
- **INFERRED:** Campaign and ad names are understandable to operators but lack a stable taxonomy for objective, offer, audience, geography, date, and creative version; copy markers and inconsistent capitalization appear repeatedly.
- **TECHNICAL FOLLOW-UP REQUIRED:** Correct or explain the 1970 campaign start time before time-based reporting trusts that field.
- **BUSINESS DECISION REQUIRED:** Approve a future naming standard before new campaigns are built; no existing names should be changed during the audit.

## Performance and conversion tracking

- **CONFIRMED:** Maximum-range campaign insights returned 15 campaign rows totaling PLN 12,486.78 spend, 849,283 impressions, 18,659 clicks, and 5,374 inline link clicks.
- **CONFIRMED:** Campaign-level reach sums to 142,936, but this is non-deduplicated across campaigns and must not be presented as unique account reach.
- **CONFIRMED:** Insights report 400 `lead` actions and 400 grouped onsite lead actions.
- **CONFIRMED:** One Meta Pixel (`716236981220835`) is available and last fired on 2026-09-11; no custom conversions were returned.
- **UNKNOWN:** The semantic relationship among the multiple action names reporting 400 must be validated before summing actions; they appear to represent the same lead events.
- **UNKNOWN:** Pixel event quality, event parameters, deduplication, domain configuration, consent state, and downstream purchase/attendance signal quality were not established by this object-level audit.
- **INFERRED:** Meta can optimize and report lead generation, but it has no audited closed-loop signal for Fitssey revenue or attendance.

## Lead forms and history

- **CONFIRMED:** Fourteen lead forms were returned and all are active; creation dates range from 2025-07-15 through 2026-06-29.
- **CONFIRMED:** A system-user token could not directly read Page lead forms and returned HTTP 400 `(#190)`; a Page access token was then retrieved in memory through an authorized GET and used only for Page/form GET requests.
- **CONFIRMED:** The Page token was not printed or persisted.
- **CONFIRMED:** All 14 form lead-history reads returned HTTP 200, but only 78 lead records are currently retrievable: 72 from one general form and six from one workshop form.
- **CONFIRMED:** All 78 currently retrievable leads have email and phone, and all 78 match HubSpot contacts by both normalized fields.
- **CONFIRMED:** Meta insights report 400 lead actions while current Page-form lead reads return 78 records, a gap of 322.
- **CONFIRMED:** Thirteen forms collect an email/phone identity pair using a mix of Polish and English field keys; one automated-chat form contains two custom questions and no standard identity fields.
- **CONFIRMED:** Form schemas repeatedly encode event-specific eligibility, schedule, motivation, and attendance questions as unique field keys.
- **INFERRED:** Historical form-lead availability is incomplete relative to insights. Retention, deletion, form behavior, or another delivery path may explain the gap, but the audit did not prove which.
- **INFERRED:** Form-field variation is the likely source of the 30-field HubSpot Lead Ad Properties group and its sparse utilization.
- **TECHNICAL FOLLOW-UP REQUIRED:** Obtain an approved historical export/backfill source if person-level analysis of the missing 322 lead actions is required; do not assume the Graph endpoint can supply them.
- **BUSINESS DECISION REQUIRED:** Standardize a small reusable lead-form identity schema and decide which event-specific answers belong in contact properties versus submission/event history.

## Attribution and identity gaps

- **CONFIRMED:** Eight of the 78 currently retrievable Meta leads match an active Fitssey client by normalized email; 70 do not.
- **CONFIRMED:** All eight Meta-to-Fitssey email matches also match HubSpot.
- **UNKNOWN:** Phone-based Meta-to-Fitssey matching was not completed after the Fitssey rate window was exhausted; the eight matches are therefore a lower bound, not a full conversion count.
- **INFERRED:** Existing history can link a subset of recent Meta leads to Fitssey, but a complete lead-to-booking/purchase view is not available from current person-level history alone.
- **TECHNICAL FOLLOW-UP REQUIRED:** Future ingestion should preserve Meta lead ID, form ID, campaign ID, ad-set ID, ad ID, submission time, and normalized UTM/click identifiers before retention windows close.
