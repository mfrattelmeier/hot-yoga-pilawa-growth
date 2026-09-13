# Fitssey Current-State Reconciliation

Audit date: 2026-09-13. Scope: aggregate-only Fitssey API v4 GET reads. The entitlement sweep covered every record in the 467-client default/current collection, used 935 GET requests at a conservative rate, checkpointed only aggregate counts, and received no rate-limit response.

## Client population

| Measure | 2026-09-12 Phase 1 | 2026-09-13 Phase 1A | Change |
| --- | ---: | ---: | ---: |
| Default/current client list | 466 | 467 | +1 |
| Including deleted-filter population | 476 | 477 | +1 |
| Inferred deleted difference | 10 | 10 | 0 |

The documented Fitssey deletion filter continues to behave as an inclusion switch: supplying it returns current plus deleted records rather than only deleted records. Production extraction must retain this tested behavior as a vendor-specific rule and monitor it.

## Current-client contact completeness

| Measure | Count | Share of 467 |
| --- | ---: | ---: |
| Valid email | 408 | 87.37% |
| Valid phone | 443 | 94.86% |
| Neither | 24 | 5.14% |
| Unique normalized phones | 403 | — |
| Duplicate email groups | 0 | 0 records |
| Duplicate/shared phone groups | 20 | 40 records |

When the 10 deleted records are included, the population has 414 records with email, 453 with phone, four duplicate-email groups covering eight records, and 28 duplicate-phone groups covering 57 records. The broader counts match Phase 1 except for the one newly added record.

## Current entitlements

| Measure | Count |
| --- | ---: |
| Clients with at least one current-derived pricing entitlement | 67 |
| Clients with an active-derived contract | 5 |
| Clients with neither current pricing nor active contract | 400 |
| All pricing-option instances returned | 1,427 |
| Current-derived pricing-option instances | 124 |
| Expired pricing-option instances | 1,247 |
| Exhausted but unexpired limited-visit instances | 56 |
| Pricing instances without activatedAt | 7 |
| Pricing instances flagged unpaid | 30 |
| All client-contract instances returned | 6 |
| Active-derived client contracts | 5 |
| Terminated/expired contracts | 1 |

All five clients with an active-derived contract are among the 67 clients with a current-derived pricing instance, so the current-entitlement union is 67 clients and the neither count is 400.

### Classification method

The client-pricing-option collection exposes remaining sessions, session type, activatedAt, expiresAt, unpaid/shared flags, template reference, and instance GUID, but it does not return a status field. Current-derived means the instance is not expired and, for limited-visit instances, has more than zero remaining visits. Expired means expiresAt is before the audit boundary. Exhausted-unexpired means a limited-visit instance has zero remaining visits while its expiry is not past.

Contract active-derived means startsAt is reached and neither endsAt nor the effective termination date is past. These are reproducible technical classifications, not approved lifecycle or billing rules.

## Current pricing-entitlement distribution

| Pricing-option ID | Instance label / current relationship | Current-derived instances |
| --- | --- | ---: |
| E28EB1CE-8AC9-417B-A78E-6557589C190E | Członkostwo OPEN FLOW | 59 |
| FEB2D006-D7B5-4A32-8E26-82833F5A7F01 | 8 x zajęcia; 10 instances use current 47 zł label and one retains older 45 zł label | 11 |
| 4E919D28-A2E9-4461-9EA6-3628EFEF8077 | Karnet Premium 3 mies. (36 zajęć) | 9 |
| C15B12F4-812F-45D1-854B-FC8FBC2428F3 | 4 x zajęcia (60 zł wejście) | 8 |
| 026485DB-07D3-4051-BF5F-57605E55375F | Karnet zajęcia grafikowe | 7 |
| FCEF9872-FFE8-4A60-8225-C4FD5712BC89 | PIĄTKI SĄ DLA PRZYJACIÓŁ | 6 |
| D30308D2-71E5-441F-A825-C245D5767820 | 12 x zajęcia (41 zł wejście) | 5 |
| 8F607920-DD44-4BED-B328-0DB89A501A1B | Karnet (rodzina i przyjaciele) | 4 |
| E62202DD-4918-4BB4-8775-2F0B5AB5776F | WRZEŚNIOWE WYZWANIE 20/30 | 3 |
| C0678943-4D9A-401B-8970-76A7360D52D9 | SENIOR - 8 wejść - miesiąc | 3 |
| C762FD0F-9C5C-4F70-B891-FA3D5B295D56 | 10 x zajęcia (2 miesiące ważności) | 2 |
| 05ACAE38-2ABC-447C-8ABC-E24D84E06DA7 | KARNET STUDENCKI | 2 |
| 3A330117-414F-49E0-84A5-8AF7FEA0E20E | 1 x zajęcia (65 zł wejście) | 1 |
| EB72432A-FC80-4E69-9A8D-F112D2C63DC0 | Karnet 24 wejścia (3 miesiące) | 1 |
| B48B6C13-0D25-4F90-B36E-B7A84AD6F3D0 | TEAM PASS – Karnet Instruktorski | 1 |
| D964703C-7E5B-4DDF-BACB-49F54C18357D | PREMIUM 36 x zajęcia; template ID not in current 45-option catalog | 1 |
| 2256F9F3-23B4-4D4B-948B-242118714720 | 4 zajęcia kursowe; template ID not in current 45-option catalog | 1 |

The two template IDs absent from the current catalog and the retained older display label demonstrate why historical instance identifiers and names must be preserved even when templates are renamed or removed.

## Contract distribution

- Six client-contract instances were returned.
- Five are active-derived and all reference contract B83C7E7C-839A-476F-A5C6-AD6BEE9E9F1C, Członkostwo OPEN FLOW.
- One is expired/terminated.
- Across all contract instances, 13 instalments are processed and 59 are scheduled.

The second sold-online contract template, OPEN START, had no active-derived client contract in this population at audit time. This does not establish that the product has never been sold or should be removed.

## Visit and finance comparison

- Visit-report rows increased from 8,137 to 8,283 because Phase 1A extends the requested boundary through 2026-10-31 and includes future booked rows. The two totals are not a same-window trend measure.
- Visit status meanings are now confirmed in visit-status-map.md.
- Finance pagination is now internally reconciled at 1,086 returned rows and totalCount 1,086, with 1,076 unique sale GUIDs after removing 10 exact duplicate rows. See finance-reconciliation.md.

## Decisions narrowed

- Fitssey user GUID remains the preferred operational identity key; client UUID remains useful for report relationships.
- Lifecycle can now distinguish booked status 0, present status 1, absent status 2, early cancellations 3/4, late cancellations 5/6, class cancellation 7, waiting list 8, and unconfirmed 9.
- Retention logic can use current-derived entitlement and expiry evidence, but thresholds and treatment of unpaid, not-activated, shared, free, staff, and event records remain business decisions.
- Historical template names cannot be discarded during synchronization because active instances can retain superseded labels or reference templates absent from the current catalog.

No lifecycle threshold, merge, marketing segment, CRM property, or automation is authorized by this reconciliation.
