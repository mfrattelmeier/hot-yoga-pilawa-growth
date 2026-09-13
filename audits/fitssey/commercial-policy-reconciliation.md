# Fitssey Commercial-Policy Reconciliation

Audit date: 2026-09-13. Scope: Fitssey API v4 documentation/schema and GET-only studio data. Historical rules are context only and are not treated as current.

## Policy evidence

| Policy area | API evidence | Current conclusion |
| --- | --- | --- |
| Booking cutoffs | Schedule events expose isAvailableForBookingAhead and isAvailableBeforeStartTime booleans. No duration or cutoff rule is exposed. | OWNER/UI CONFIRMATION REQUIRED |
| Waitlists | Events expose waiting-list capacity and booked waiting-list spots; visit status 8 is documented as waiting list. No waiting-list visits appeared in the report and the current schedule had zero booked waiting-list spots. | Technical states exist; promotion, expiry, notification, and priority rules require OWNER/UI CONFIRMATION. |
| Cancellation windows | Visit statuses distinguish early cancel, self early cancel, late cancel, and self late cancel. The API does not expose the time boundary between early and late. | OWNER/UI CONFIRMATION REQUIRED |
| Minimum enrollment | Events expose total capacity and current booked spots but no minimum-attendance threshold. | OWNER/UI CONFIRMATION REQUIRED |
| Class cancellation | Visit status 7 means class cancelled and event objects have isCancelled. No event in the current window was cancelled. | State is confirmed; decision and notification rules require OWNER/UI CONFIRMATION. |
| No-show handling | Visit status 2 means absent. The API does not expose penalties, fees, warnings, or escalation. | OWNER/UI CONFIRMATION REQUIRED |
| Pass deduction | Client pricing-option instances expose remaining sessions, but the read API does not state which cancellation/absence states consume or restore a session. | OWNER/UI CONFIRMATION REQUIRED |
| Pass activation and expiry | Pricing templates expose expiration type: 0 sale date, 1 first visit, 2 always valid, 3 calendar month, 4 specific date. Client instances expose activatedAt and expiresAt. | Technical date semantics confirmed; each product's intended validity length and exceptions require OWNER/UI CONFIRMATION. |
| Freeze / suspension | Client and contract-instalment schemas include suspension fields and the API documents write endpoints for suspend/resume, which were not called. Template-level freeze allowance and limits are not exposed. | OWNER/UI CONFIRMATION REQUIRED |
| Make-up rules | No current configuration field was found. | OWNER/UI CONFIRMATION REQUIRED |
| Transferability / sharing | Client pricing-option instances expose isShared, but product-level eligibility, household scope, and transfer rules are not exposed. | OWNER/UI CONFIRMATION REQUIRED |
| Refunds / reversals | The sales report exposes sale lines but no order status, void reason, or refund/reversal field. Order objects document void status, but a complete order audit was outside this phase. | OWNER/UI CONFIRMATION REQUIRED; accounting control also required. |
| Staff override | Backoffice booking source and staff-side mutation endpoints exist, but allowed override policy is not represented in read configuration. | OWNER/UI CONFIRMATION REQUIRED |

## Current evidence versus historical material

Historical conversations describe changing cancellation deadlines, minimum-attendance expectations, pass freezes, extensions, make-ups, transfers, vouchers, refunds, and owner-managed exceptions. Those statements conflict by date and context. None is elevated to current policy by this audit.

The current API evidence narrows the data model: cancellation and absence outcomes can be distinguished reliably by visit status, and pricing activation/expiry can be represented using source timestamps. It does not authorize any customer-facing policy statement or automation.

## Michael/Kat review checklist

- Approve the early/late cancellation boundary and whether actor-specific statuses have different consequences.
- Approve what status 2 absence means commercially and operationally.
- Confirm pass deduction/restoration behavior for each cancellation and absence state.
- Confirm booking-ahead, booking-close, waitlist-promotion, and minimum-enrollment rules.
- Confirm freeze, expiry-extension, make-up, sharing/transfer, refund, and exception policies.
- Define which staff roles may override each rule and what audit trail is required.
- Reconcile the approved rules with Fitssey BackOffice settings and customer-facing terms before any CRM messaging is built.
