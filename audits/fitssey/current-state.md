# Fitssey Current-State Audit

Audit date: 2026-09-12. Scope: Fitssey API v4 GET requests only. No client, tag, booking, visit, order, contract, membership, purchase, or studio mutation was attempted. Counts are point-in-time.

## Access and studio inventory

- **CONFIRMED:** The credential authenticated with Bearer access to studio UUID `HotYogaPilawa`; all 105 full-audit requests returned successful responses.
- **CONFIRMED:** One facility named Hot Yoga Pilawa is returned, with four rooms.
- **CONFIRMED:** The studio exposes 14 staff/member records, 45 class services (28 classroom and 17 course), two contract products, 45 pricing options, and no retail products.
- **CONFIRMED:** Both contract products are sold online; 26 pricing options are sold online, 39 are limited-visit, six are unlimited, and none is flagged as an introductory offer.
- **INFERRED:** The absence of an introductory-offer flag does not prove there is no commercial first-timer offer; offers may be represented by ordinary pricing options or handled operationally.

## Clients and identity quality

- **CONFIRMED:** The default client list reports 466 active/non-deleted clients. Supplying the documented deletion filter in any tested string form expands the total to 476, implying 10 additional deleted records.
- **CONFIRMED:** Retrieved activation/last-activity timestamps across the full 476-record inventory span 2025-06-30 through 2026-09-12; all 476 have both a user GUID and internal client UUID.
- **UNKNOWN:** An exact client creation timestamp was not present in the returned client-list schema, so client creation-date distribution could not be confirmed.
- **CONFIRMED:** Across the 476-record inventory, 413 have email, 452 have a phone, and 24 have neither email nor phone.
- **CONFIRMED:** Email normalization found four duplicate groups covering eight records; phone normalization found 28 duplicate groups covering 57 records, with a largest group of three.
- **CONFIRMED:** Sixty-three records have login disabled, none is suspended, 60 show Android app use, and 63 show iOS app use.
- **CONFIRMED:** Agreements are present structurally on all 476 records; notes and tags are unused in the returned client list.
- **UNKNOWN:** The deletion-filter parameter behaves as an inclusion switch when present, irrespective of the tested value; the exact vendor semantics should be confirmed before deleted-client synchronization.
- **INFERRED:** Fitssey GUIDs are the strongest system-native keys. Email is a useful cross-system key but not universally present or unique; phone is more complete but materially more ambiguous.
- **TECHNICAL FOLLOW-UP REQUIRED:** Establish a duplicate-review queue and never auto-merge Fitssey clients on phone alone.

## Bookings, attendance, and schedule

- **CONFIRMED:** The complete client-visit report returned 8,137 visit rows dated from 2025-08-28 through 2026-09-12 and covering 386 unique active client UUIDs.
- **CONFIRMED:** Payment state across visit rows is 7,375 paid, 652 free, 94 unpaid, and 16 blank/other.
- **CONFIRMED:** Booking sources are 3,006 backoffice, 2,766 frontoffice, and 2,365 mobile app.
- **CONFIRMED:** Visit status codes returned counts of `0`: 2,403; `1`: 4,748; `2`: 22; `3`: 26; `4`: 700; `5`: 10; and `6`: 228.
- **UNKNOWN:** The public report schema did not provide reliable human-readable labels for those visit status codes in the audited response; attendance, cancellation, and no-show totals must not be inferred from numeric codes without vendor confirmation.
- **CONFIRMED:** Appointment and entry reports returned zero rows for the historical window; operational activity is represented in client visits.
- **CONFIRMED:** The 2026-09-01 to 2026-10-31 schedule request returned 86 events, including three cancelled and 401 booked spots; returned events ended on 2026-09-30 at audit time.
- **CONFIRMED:** One course was bookable in the 2026-09-01 to 2026-12-31 course window.
- **TECHNICAL FOLLOW-UP REQUIRED:** Obtain/confirm Fitssey visit-status definitions before calculating attendance rate, cancellation rate, or no-show rate.

## Memberships, purchases, and revenue

- **CONFIRMED:** A deterministic 20-client relationship sample completed successfully: 14 had orders, 14 had pricing-option records, 16 had visits, and one had a contract.
- **CONFIRMED:** The sample contained 75 orders: 60 paid, 14 free of charge, and one void based on the documented order-status enumeration.
- **CONFIRMED:** The complete sales report read 1,164 rows dated from 2025-08-20 through 2026-09-11 and covering 288 unique client UUIDs; the endpoint simultaneously reported `totalCount` 1,082.
- **CONFIRMED:** A separate zero-sales report returned 275 fully discounted rows dated from 2025-08-25 through 2026-09-10.
- **CONFIRMED:** Fitssey documents monetary values as smallest currency units. The read rows summed to 34,949,200 minor units gross, 32,360,439 net, 2,588,761 tax, and 90,000 discount.
- **UNKNOWN:** Those finance sums are not approved financial totals because the collected row count disagrees with the endpoint-reported total and the response did not explicitly state currency.
- **INFERRED:** PLN is likely because the studio's HubSpot and Meta accounts use PLN and Fitssey pricing labels contain zł amounts, but currency must be confirmed in Fitssey before reporting.
- **TECHNICAL FOLLOW-UP REQUIRED:** Re-run the sales report after the rate window resets using the documented `count` parameter, deduplicate by sale GUID, reconcile `totalCount`, include zero-sales separately, and compare against Fitssey's UI/finance export.

## Entity relationships and source-of-truth assessment

- **CONFIRMED:** All 386 client UUIDs and user GUIDs referenced by visit rows match the client inventory.
- **CONFIRMED:** All 288 client UUIDs and user GUIDs referenced by sales rows match the client inventory.
- **CONFIRMED:** Stable relationships exist among user GUID, internal client UUID, visits, sales, pricing options, contracts, services, and location.
- **CONFIRMED:** An email-only comparison matched 107 active Fitssey clients to HubSpot contacts; 359 active Fitssey clients had no HubSpot email match.
- **UNKNOWN:** Phone-based cross-system matching is pending because the documented Fitssey rate limit returned HTTP 429 after the complete inventory; the audit respected the retry interval and did not continue.
- **INFERRED:** Fitssey is fit to remain the operational source of truth for client identity, bookings/visits, pricing entitlements, contracts, purchases, and revenue, subject to finance reconciliation and status-code confirmation.
- **INFERRED:** HubSpot should receive stable Fitssey identifiers and a small set of derived lifecycle/recency/value summaries, not a copy of every visit and order row.

## API constraints and privacy

- **CONFIRMED:** Fitssey documents API v4, Bearer authentication, GET report endpoints, a `count` pagination parameter, and rate limits of 10 requests/second, 200/5 minutes, 4,000/6 hours, and 10,000/day: <https://app.fitssey.com/docs/api>.
- **CONFIRMED:** The audit stayed under the 180-request safety cap but reached a later rate window during the separate identity follow-up; no retry storm occurred.
- **CONFIRMED:** Raw client PII and credentials were not written to this repository.
- **TECHNICAL FOLLOW-UP REQUIRED:** Production design must implement vendor pagination exactly, rate-aware scheduling, checkpointing, retry-after handling, idempotent reads, and aggregate-only logs.
