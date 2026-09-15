# Michael Review Summary — D01 / D08 / D09

Owner interview completed with Katarzyna in Polish on 2026-09-14 and 2026-09-15. This English summary covers current offer truth, commercial policies, and the beginner promise only. No external system was changed.

Repository numbering warning: this interview uses D01/D08/D09 as requested in the interview brief. The current `docs/open-decisions.md` uses D13/D14/D15 for the closely related offer, commercial-policy, and beginner topics. Reconcile the identifiers before updating the central register.

## What Katarzyna Approved

### Current offer

- Core regular services: Stretching; Bikram Joga (26&2); advanced Inferno Hot Pilates; Zdrowy kręgosłup/ Delikatna praktyka jogi; Hot Pilates START; beginner Hatha; Yin REGENERACJA; Iyengar; classical mat Pilates; and Mobility.
- Occasional Sunday services: beginner Vinyasa and Sivananda, approximately monthly.
- Private 1:1 and 2:1 sessions are real by-arrangement services. Corporate/group work is also possible by arrangement but has not been marketed or validated.
- The current standalone breath/relaxation class is paused; related practices are included in Yin.
- HOT JOGA is a genuine shortened Bikram format, currently absent but potentially returning.
- The September emotion workshop is a one-off current event. Old workshops, sound events, integrations, and retreats are historical editions even when the format may return.

Core public passes are current: PLN 65 single; PLN 240/4; PLN 380/8; PLN 500/12; and PLN 550/10 with two-month validity. The owner intends all to activate on first use; the 1-, 4-, 8-, and 12-visit passes last one month.

OPEN START is approved at PLN 690 per billing period for up to three months, with no minimum commitment: cancellation before the next payment prevents that payment. OPEN FLOW is PLN 590 per billing period, requires three paid months, and then has one full billing-period notice. OPEN START must not auto-convert to OPEN FLOW without explicit agreement.

Current special products include SENIOR 8/PLN 360, student 7/PLN 299, public TEAM PASS 10/PLN 349, and an internal PLN 0 family/friend entitlement. WRZEŚNIOWE WYZWANIE 20/30 is the current seasonal offer. PIĄTKI SĄ DLA PRZYJACIÓŁ is active and gives each newly registered companion one free Friday visit with an active-pass customer.

### Booking and commercial rules

- Publish the next monthly timetable around the 20th; use a 28-day rolling booking window.
- Customer self-booking closes 10 minutes before class; staff may add a valid customer until class starts if capacity remains.
- More than 6 hours before class: a cancelled visit returns to a limited pass. Within 6 hours or on no-show: the limited-pass visit is lost.
- New intended OPEN rule: PLN 30 for late cancellation or no-show. There is currently no OPEN consequence, so this is not yet implemented.
- Minimum attendance is provisionally five. Mark the class at risk 6 hours before start and make the final decision 3 hours before start. Five remains financially unvalidated.
- Studio cancellation restores every entry, including late-cancelled entries. Extend a pass when studio cancellations prevent use before expiry.
- Only Katarzyna currently authorizes exceptions. Małgosia joins from October for management, customer service, and marketing support; her override authority is undefined.
- Introduce a first-in, first-out waitlist. Auto-promote with notice more than 6 hours before class; within 6 hours, require acceptance before confirmation.
- Ordinary passes are personal and non-transferable. There is no make-up entitlement in the open timetable and no standard refund; serious cases remain owner exceptions.
- Monthly passes and the two-month/10-visit pass may freeze for up to 7 days for illness or travel. OPEN START has no standard freeze. OPEN FLOW may freeze for 14 days per rolling 12 months after the first three paid months, once or as 2 x 7 days; billing/access dates move with the freeze.

### Beginner promise

- A structured beginner course is the preferred future onboarding route but is not running and will not be mandatory.
- Current strongest entry options: beginner Hatha, Yin REGENERACJA, Zdrowy kręgosłup/ Delikatna praktyka jogi, Hot Pilates START, Stretching, and Iyengar.
- Bikram is an owner-preferred first option when the customer tolerates heat, accepts 90 minutes, and has no issue requiring individual guidance.
- The only current class not recommended as a first class is the advanced Inferno Hot Pilates group.
- Approved messages: no experience or flexibility required; practise at an individual pace; modifications and instructor help are available; do not compare yourself with others.
- Heat messaging may positively reflect Katarzyna’s extensive teaching experience and attributed customer experiences, but must not become a guaranteed medical, injury-prevention, or “better than physiotherapy” claim.
- Customers who are pregnant, returning after injury/accident, have chronic conditions, take relevant medication, have mobility limitations, or are uncertain about heat should consult an appropriate professional and contact the studio.

## What Changed From Assumptions or History

- Old fixed-group yoga and Hot Pilates courses are not current. Today’s model is an open timetable, although Katarzyna believes a beginner course produced stronger onboarding and retention.
- Old back-care names are naming/course predecessors of the current Zdrowy kręgosłup/ Delikatna praktyka jogi class.
- Children’s yoga was discontinued; the teen group never launched. HOT HIIT '45 never launched. Józefów never ran.
- Historical Premium, 24-visit, and non-contract OPEN products are retired. Old multi-month prepaid offers were underpriced and caused extension/cash-timing problems.
- Event pricing products with an online-sale API flag are hidden when the event is hidden; the API flag alone does not establish current customer visibility.
- Current heated classes are Bikram and advanced Inferno Hot Pilates. Hot Pilates START is not currently heated.

## What Remains Unresolved

- SENIOR age/eligibility and student proof requirements.
- GOLD PASS current visibility and keep/retire decision.
- Financial validation of the five-person class threshold, private-session prices, and membership economics.
- Private-session and retreat cancellation/refund rules; future-event credit validity and price differences.
- Exact Fitssey behavior for booking horizon/close, cancellation, activation, expiry, freeze, billing, waitlist, and the new OPEN charge.
- Małgosia’s authority for refunds, overrides, cancellations, and Fitssey changes.
- Final legal review of membership terms, refund wording, event withdrawal rights, pricing labels, and public health-oriented claims.
- Timing, schedule, pricing, and recruitment for a relaunched beginner course.

Katarzyna did not reserve any business item as a mandatory joint Michael/Katarzyna decision, but Michael can support the validations above.

## Fitssey Cleanup / Configuration Later

- Verify the single-entry activation mismatch: API evidence suggests sale-date activation, while owner policy is first use.
- Configure/verify 28-day booking, 10-minute booking close, 6-hour cancellation boundary, automatic restoration, and the provisional five-person/three-hour cancellation process.
- Test whether Fitssey can support the PLN 30 OPEN late/no-show charge, payment block, approved freeze mechanics, and waitlist acceptance flow.
- Archive or remove customer visibility from historical course, child/teen, event, retreat, seasonal, and retired pricing records without deleting history or identifiers.
- Consolidate obsolete back-care and course naming; keep Hatha, Vinyasa, HOT JOGA, and Bikram conceptually distinct.
- Consider removing rounded “per class” amounts from the 8- and 12-visit product names.
- Confirm that TEAM PASS remains intentionally public, while internal family/friend and correction products remain private.
- Reconcile the approved rules across Fitssey, FrontOffice, the website, and customer terms before enforcement or publication.
