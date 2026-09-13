# Fitssey Identity Follow-Up

Audit date: 2026-09-13. Scope: aggregate-only GET comparison of Fitssey clients and HubSpot contacts. No cross-system links were created, no records were changed, and no names, emails, phones, addresses, notes, or customer identifiers were persisted.

## Method

- Primary Fitssey population: 467 records in the current/default list. A secondary comparison includes 10 additional deleted records.
- HubSpot population: 383 non-archived contacts.
- Email normalization: trim and lowercase; only syntactically valid addresses used.
- Phone normalization: digits only, remove a leading 00 international prefix, and add Poland country code 48 to nine-digit values.
- A deterministic candidate requires the normalized value to occur exactly once in each system.
- Email and phone candidates were evaluated separately. No ambiguous value was auto-resolved.

The HubSpot count is reconciled with the Phase 1 total of 382. A fresh complete paginated GET returned 383 non-archived contacts, and exactly one contact was created on 2026-09-13 after the Phase 1 audit commit boundary. The change is therefore one newly created contact, not a pagination discrepancy. Account metadata plus four contact pages returned HTTP 200; only aggregate count and creation-time evidence was retained, with no contact ID or PII.

## Current Fitssey completeness and duplication

| Measure | Count | Share of 467 |
| --- | ---: | ---: |
| Records with valid email | 408 | 87.37% |
| Records with valid phone | 443 | 94.86% |
| Records with neither | 24 | 5.14% |
| Unique normalized phone values | 403 | — |
| Duplicate email groups | 0 | 0 records |
| Duplicate/shared phone groups | 20 | 40 records |

When deleted records are included, the population is 477: 414 have email, 453 have phone, four duplicate-email groups cover eight records, and 28 duplicate-phone groups cover 57 records. These broader counts are one record higher for email and phone than Phase 1 because the Fitssey population increased from 476 to 477; the broader duplicate counts are unchanged.

## HubSpot/Fitssey candidate matches

| Candidate evidence | HubSpot contacts |
| --- | ---: |
| Unique email match | 107 |
| Unique phone match | 124 |
| Both unique signals point to the same Fitssey record | 100 |
| Unique email only | 7 |
| Unique phone only | 24 |
| Unique email and phone point to different Fitssey records | 0 |
| Reached by at least one unique signal | 131 |

These are deterministic technical candidates, not approved identity links. The 107 unique-email count reproduces Phase 1's active-client email match using stricter one-to-one normalization while adding complete phone analysis.

Two shared-household-like phone groups covering four current Fitssey records were detectable: multiple Fitssey records have distinct emails but share a phone also present in HubSpot. Including deleted records produces three groups covering six Fitssey records. This pattern is compatible with household, parent-child, or spouse relationships but does not prove one.

## Owner input

Michael states that all current HubSpot contacts were created from Meta lead generation and none were manually added. This is owner-provided context, not an API finding.

Michael intends to review duplicate and conflict groups with Kat. Shared household, parent-child, and spouse cases are plausible. Future integration should prevent avoidable new duplicates but must not auto-merge ambiguous existing records. Fitssey native identifiers should remain preferred over phone-only matching.

## Recommended identity policy for approval

- Preserve Fitssey user GUID as the preferred operational join key and retain the internal client UUID where needed.
- Use a unique email or unique normalized phone only to propose a candidate link.
- Treat matching email plus phone as stronger evidence, but still retain source IDs and an audit trail.
- Route shared values and any future signal conflict to Michael/Kat review.
- Never merge solely because two people share a phone.
- Model guardian/household relationships explicitly if the business needs them; do not collapse people into one contact.
- Run a dry-run crosswalk and reviewed exception queue before any synchronization or HubSpot schema change.

No crosswalk, merge, or CRM write is authorized by this document.
