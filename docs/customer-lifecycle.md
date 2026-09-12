# Customer Lifecycle

Status: proposed framework based on audit evidence. No lifecycle automation is authorized.

## Confirmed current state

- **CONFIRMED:** All 382 HubSpot contacts are at Lead; Lead Status is blank for every contact.
- **CONFIRMED:** Fitssey has 466 active clients, visit history for 386 unique clients, and sales history for 288 unique clients.
- **CONFIRMED:** HubSpot and Fitssey therefore describe different slices of the population and are not currently a unified lifecycle view.
- **INFERRED:** HubSpot lifecycle cannot presently distinguish prospect, booked visitor, attendee, purchaser, active customer, or lapsed customer.

## Proposed lifecycle evidence model

| Stage/state | Minimum system evidence | Status |
| --- | --- | --- |
| New lead | New HubSpot/Meta acquisition event with usable contact method | **BUSINESS DECISION REQUIRED:** approve entry rule. |
| Contacting | Owned lead plus recorded outreach attempt | **BUSINESS DECISION REQUIRED:** approve SLA and outcome fields. |
| Connected | Two-way human response | **BUSINESS DECISION REQUIRED:** define acceptable channels. |
| Qualified | Approved fit/intent criteria | **BUSINESS DECISION REQUIRED:** define qualification without overusing sensitive data. |
| First booking | First qualifying future Fitssey booking | **TECHNICAL FOLLOW-UP REQUIRED:** map visit statuses. |
| First attended visit | First attended Fitssey visit | **TECHNICAL FOLLOW-UP REQUIRED:** confirm attended code. |
| First-time customer | First paid order or approved paid-attendance rule | **BUSINESS DECISION REQUIRED:** choose commercial definition. |
| Active customer | Valid entitlement and/or recent attendance | **BUSINESS DECISION REQUIRED:** define by product type and recency. |
| At-risk | Declining activity or entitlement approaching expiry | **BUSINESS DECISION REQUIRED:** choose thresholds. |
| Lapsed | No qualifying activity for an approved interval | **BUSINESS DECISION REQUIRED:** choose separate class/course/membership windows. |
| Reactivated | New attendance or purchase after lapse | **BUSINESS DECISION REQUIRED:** define reset/evidence rule. |
| Advocate | Explicit referral/review/ambassador evidence | **BUSINESS DECISION REQUIRED:** do not infer from spend alone. |

## HubSpot lifecycle versus studio status

- **INFERRED:** Keep HubSpot's standard lifecycle stage for broad relationship progression and add one controlled `studio_customer_status` for operational engagement state.
- **INFERRED:** A contact can remain `Customer` in HubSpot while moving between Active, At-risk, Lapsed, and Reactivated studio status.
- **BUSINESS DECISION REQUIRED:** Approve mapping from studio evidence to HubSpot Lead/MQL/SQL/Opportunity/Customer; do not equate a form submission automatically with MQL or a Fitssey account automatically with Customer.
- **BUSINESS DECISION REQUIRED:** Decide whether free visits, vouchers, staff/test accounts, guardians booking for children, and event-only buyers qualify as Customers.

## Ownership and service levels

- **CONFIRMED:** HubSpot exposes two active owners, but current ownership distribution and lead activities were not included in the audit output.
- **UNKNOWN:** Current manual lead-response process, response times, channels, and disposition vocabulary.
- **BUSINESS DECISION REQUIRED:** Assign default and backup owner, hours of operation, first-response target, attempt cadence, stop conditions, and mandatory outcomes.
- **BUSINESS DECISION REQUIRED:** Separate operational/service messages from marketing nurture and respect subscription/consent state.

## Automation prerequisites

- **TECHNICAL FOLLOW-UP REQUIRED:** Confirm Fitssey visit-status and finance semantics, build the identity crosswalk, and validate stage calculations on sampled records.
- **BUSINESS DECISION REQUIRED:** Approve lifecycle, field definitions, consent/legal basis, suppression rules, quiet hours, and exit criteria.
- **TECHNICAL FOLLOW-UP REQUIRED:** Design automations as disabled specifications with test cases and rollback paths before any activation request.
- **CONFIRMED:** Under repository rules, no marketing automation may be built until the lifecycle and data model are approved.
