# Attribution Model

Status: proposed measurement framework. It does not authorize tracking, uploads, schema changes, or automation.

## Confirmed baseline

- **CONFIRMED:** HubSpot labels all 382 contacts as original and latest source `PAID_SOCIAL`, created through `FORM`.
- **CONFIRMED:** Meta reports 400 lead actions and PLN 12,486.78 spend across 15 delivering campaign rows.
- **CONFIRMED:** Only 78 current Meta lead records are person-level retrievable; all match HubSpot, and eight match active Fitssey clients by email.
- **CONFIRMED:** HubSpot Facebook click ID and Facebook ID are blank on all 382 contacts.
- **CONFIRMED:** Meta ad sets use mixed attribution windows: mostly one-day click, with two using seven-day click plus one-day view.
- **UNKNOWN:** GA4 is not connected, and website/HubSpot tracking and consent behavior are not audited.

## Measurement layers

- **INFERRED:** Media delivery layer: Meta spend, impressions, clicks, form leads, and platform-attributed conversions.
- **INFERRED:** Acquisition layer: immutable lead/submission and web-touch events with campaign/form/ad identifiers.
- **INFERRED:** CRM layer: person, lifecycle, lead-handling outcomes, and first/latest acquisition summaries in HubSpot.
- **INFERRED:** Operational conversion layer: booking, attended first visit, first paid purchase, active entitlement, repeat attendance, and revenue in Fitssey.
- **INFERRED:** Analytical layer: joins and attribution calculations without forcing event history into CRM properties.

## Proposed conversion definitions

| Conversion | Evidence source | Status |
| --- | --- | --- |
| Lead captured | Meta lead ID or HubSpot form-created contact | **BUSINESS DECISION REQUIRED:** resolve duplicate/repeat submission counting. |
| Lead contacted | HubSpot activity/outcome | **BUSINESS DECISION REQUIRED:** define qualifying activity and SLA. |
| First booking | Earliest qualifying Fitssey visit/booking row | **TECHNICAL FOLLOW-UP REQUIRED:** map visit statuses. |
| First attendance | Earliest attended Fitssey visit | **TECHNICAL FOLLOW-UP REQUIRED:** confirm attendance status code. |
| First purchase | Earliest paid Fitssey order/sale | **TECHNICAL FOLLOW-UP REQUIRED:** reconcile finance pagination and void/refund behavior. |
| Active customer | Current Fitssey entitlement plus activity rule | **BUSINESS DECISION REQUIRED:** define membership/pass and recency thresholds. |
| Retained/reactivated | Repeat visit/purchase after approved interval | **BUSINESS DECISION REQUIRED:** choose windows. |

## First-touch and last-touch proposal

- **INFERRED:** First touch should be immutable: earliest eligible source/medium/campaign/form/ad or website touch associated with the person.
- **INFERRED:** Last touch should be the latest eligible touch before the selected conversion, not simply HubSpot's latest source at report time.
- **BUSINESS DECISION REQUIRED:** Select lookback windows and whether view-through credit is included; mixed Meta windows must be normalized or reported separately.
- **BUSINESS DECISION REQUIRED:** Decide whether direct traffic preserves the prior known campaign or receives last-touch credit.
- **INFERRED:** Report Meta platform attribution alongside an independently joined operational model; do not present them as identical measures.

## Required join keys

- **INFERRED:** Person: HubSpot contact ID + Fitssey user GUID/client UUID after approved identity resolution.
- **INFERRED:** Acquisition: Meta lead ID, form ID, campaign ID, ad-set ID, ad ID, submission time.
- **INFERRED:** Web: UTM tuple, landing URL, referrer, click IDs where lawfully collected, GA4 event/session keys when authorized.
- **INFERRED:** Operational: Fitssey visit GUID, order/sale GUID, pricing-option/contract GUID, service GUID, and event timestamps.
- **TECHNICAL FOLLOW-UP REQUIRED:** Keep source-native IDs as strings to avoid numeric precision loss.

## Historical limitations

- **CONFIRMED:** The 322-record difference between Meta lead actions and retrievable lead records prevents complete person-level historical attribution from the current Graph reads.
- **INFERRED:** The 107 HubSpot-to-Fitssey email matches are a conservative known bridge, not the total paid-social customer count.
- **UNKNOWN:** Phone matching may add legitimate links after rate reset, but duplicates may also introduce conflicts.
- **BUSINESS DECISION REQUIRED:** Decide whether to accept partial historical attribution, source an approved Meta/HubSpot export, or start a clean prospective model from an agreed date.

## Reporting guardrails

- **INFERRED:** Never sum duplicate Meta action aliases that represent the same lead.
- **INFERRED:** Never sum campaign reach and label it unique account reach.
- **INFERRED:** Never publish Fitssey revenue until row totals, currency, void/refund rules, zero-sales, and taxes reconcile.
- **BUSINESS DECISION REQUIRED:** Approve one canonical timezone (`Europe/Warsaw` is the current candidate) and reporting currency (likely PLN, pending Fitssey confirmation).
- **BUSINESS DECISION REQUIRED:** Define the authoritative dashboard owner and a monthly cross-system reconciliation process.
