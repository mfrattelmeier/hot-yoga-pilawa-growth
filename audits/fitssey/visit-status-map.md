# Fitssey Visit-Status Map

Audit date: 2026-09-13. Scope: Fitssey API v4 public documentation/schema and GET-only aggregate validation. No attendance or no-show rate is calculated here.

## Result

The public OpenAPI schema embedded in the [Fitssey API documentation](https://app.fitssey.com/docs/api) defines visit statuses 0 through 9. This resolves the Phase 1 numeric-code gap.

| Code | Documented meaning | Observed rows | Classification | Confidence | Evidence |
| --- | --- | ---: | --- | --- | --- |
| 0 | booked | 2,528 | booking | High | Fitssey OpenAPI enum; 125 future rows; sampled future events had bookedSpots exactly equal to status-0 rows while excluding cancelled rows. |
| 1 | present | 4,759 | attended | High | Fitssey OpenAPI enum; sampled completed event had 11 bookedSpots and 11 status-1 rows. |
| 2 | absent | 22 | no-show / absent | High for the label; owner confirmation required for commercial consequences | Fitssey OpenAPI enum. |
| 3 | early cancel | 26 | cancelled | High | Fitssey OpenAPI enum. The schema does not identify the actor. |
| 4 | self early cancel | 709 | cancelled | High | Fitssey OpenAPI enum; sampled events returned status-4 rows that were excluded from bookedSpots. |
| 5 | late cancel | 11 | cancelled | High | Fitssey OpenAPI enum. The schema does not identify the actor. |
| 6 | self late cancel | 228 | cancelled | High | Fitssey OpenAPI enum. |
| 7 | class cancelled | 0 | cancelled / excluded | High | Fitssey OpenAPI enum; not observed in the extracted visit window. |
| 8 | waiting list | 0 | waiting list / not booked | High | Fitssey OpenAPI enum; not observed in the extracted visit window. |
| 9 | unconfirmed | 0 | other / unconfirmed | High | Fitssey OpenAPI enum; not observed in the extracted visit window. |

Observed counts cover 8,283 report rows from 2025-01-01 through the requested future boundary of 2026-10-31. The endpoint returned nine cursor pages of 1,000 rows followed by 283. The report contains 8,274 unique visit GUIDs, so nine repeated GUID rows remain a report-level deduplication issue; the status counts above describe returned rows.

## Operational interpretation

- Status 0 is the current booking state.
- Status 1 is the reliable attendance state.
- Status 2 is the documented absence state and the correct technical candidate for no-show reporting.
- Statuses 3 and 4 are early cancellations.
- Statuses 5 and 6 are late cancellations.
- Status 7 is a class-level cancellation.
- Status 8 is waiting-list state and should not be counted as a confirmed booking.
- Status 9 is unconfirmed and should remain outside attended/cancelled/no-show metrics unless an approved business rule says otherwise.

The API resolves state names, but it does not resolve fees, pass deductions, allowed windows, staff overrides, or the studio's business response to each state. Those remain owner/UI confirmation items in commercial-policy-reconciliation.md.

## Verification controls

- All validation calls were HTTP GET.
- Five schedule-event samples contained only aggregate status counts; no client names, emails, phones, notes, or identifiers were persisted.
- In four sampled future events, bookedSpots equaled the number of status-0 rows and excluded status-4 rows.
- In one sampled completed event, bookedSpots equaled the number of status-1 rows and excluded a status-4 row.
