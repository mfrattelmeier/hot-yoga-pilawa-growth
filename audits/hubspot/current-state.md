# HubSpot Current-State Audit

Audit date: 2026-09-12. Scope: authenticated GET requests only. No record, schema, workflow, list, campaign, or account mutation was attempted. Counts are point-in-time.

## Access and account

- **CONFIRMED:** The service credential authenticated to portal `146937704`; account metadata returned HTTP 200.
- **CONFIRMED:** Account timezone is `Europe/Warsaw`, company currency is `PLN`, and data hosting is `eu1`.
- **CONFIRMED:** Contact objects, contact property definitions and groups, lifecycle pipeline metadata, and owners were readable with HTTP 200.
- **CONFIRMED:** Two active owners and no archived owners were returned; owner names were not retained in this audit.
- **CONFIRMED:** Lists, forms, workflows, marketing emails, and imports each returned HTTP 403 because the credential lacks one or more required scopes.
- **UNKNOWN:** The number, configuration, quality, and active state of lists, forms, workflows, marketing emails, and imports cannot be established from this credential.
- **TECHNICAL FOLLOW-UP REQUIRED:** Review missing read scopes with the account owner only if the business decides those assets must be audited. Do not add scopes automatically.

## Contact inventory and data quality

- **CONFIRMED:** A complete paginated read returned 382 contacts created from 2025-07-15 through 2026-09-12.
- **CONFIRMED:** Email is populated on 381/382 contacts; the 381 populated values passed a basic format check.
- **CONFIRMED:** Phone or mobile phone is populated on 382/382 contacts; 11 populated phone values do not begin with `+`.
- **CONFIRMED:** First name is populated on all 382 contacts; last name is missing on 231 contacts (60.5%).
- **CONFIRMED:** Exact normalized-email analysis found no duplicate groups.
- **CONFIRMED:** Normalized-phone analysis found two duplicate groups covering four contacts; the largest group contains two records.
- **CONFIRMED:** No contact is missing both email and phone.
- **CONFIRMED:** No contact was older than 365 days at the audit date; this is expected given the earliest creation date.
- **INFERRED:** Phone format inconsistency and the two shared-phone groups make phone unsafe as an automatic unique key without conflict handling.
- **TECHNICAL FOLLOW-UP REQUIRED:** Before synchronization, define Polish phone normalization, validate country codes, and review the four records in duplicate-phone groups without exporting their values.

## Properties and schema

- **CONFIRMED:** The contact schema exposes 432 current property definitions across 16 property groups; 38 definitions are calculated.
- **CONFIRMED:** The largest groups are Contact information (181), Email information (42), Contact lifecycle (34), Contact activity (30), Lead Ad Properties (30), Conversion information (26), and Web analytics history (24).
- **CONFIRMED:** Thirty properties are grouped under `lead_ads`; their names correspond to questions collected by Meta lead forms.
- **CONFIRMED:** HubSpot-supplied property names are predominantly English technical identifiers, while portal-specific lead-form fields preserve Polish question text; there is no single portal-wide naming convention.
- **CONFIRMED:** Representative fields populated on all 382 contacts include `firstname`, phone, creation date, first/recent conversion fields, channel/source drill-downs, and HubSpot web-analytics session fields.
- **CONFIRMED:** 333 of the 432 definitions were blank across this contact population; most are unused HubSpot standard fields, so this count is not a deletion recommendation.
- **CONFIRMED:** The three most-used lead-form question properties are each populated on 187 contacts (49.0%); the next two are each populated on 132 (34.6%), and another is populated on 119 (31.2%). Remaining event-specific questions are sparse.
- **CONFIRMED:** No property whose name contains `fitssey` exists in the retrieved schema.
- **CONFIRMED:** HubSpot Facebook click ID and Facebook ID are blank on all 382 contacts, while broad source/conversion fields are populated.
- **UNKNOWN:** The API response did not expose a trustworthy standard-versus-custom count. Mutability metadata cannot safely be treated as proof that a property is portal-created.
- **INFERRED:** Repeated event-specific form questions have produced a wide, sparse contact schema that will become difficult to govern if each new form creates more properties.
- **TECHNICAL FOLLOW-UP REQUIRED:** Build a property dictionary with owner, purpose, lawful-use category, allowed values, source, and retention rule before any cleanup. Do not delete or alter properties during that exercise.

## Lifecycle and source behavior

- **CONFIRMED:** All 382 contacts have lifecycle stage `lead`.
- **CONFIRMED:** All 382 contacts have blank Lead Status (`hs_lead_status`).
- **CONFIRMED:** The standard lifecycle pipeline contains Subscriber, Lead, Marketing Qualified Lead, Sales Qualified Lead, Opportunity, Customer, Evangelist, and Other.
- **CONFIRMED:** All 382 contacts have original source `PAID_SOCIAL`, latest source `PAID_SOCIAL`, and record creation source `FORM`.
- **CONFIRMED:** First/recent conversion and source drill-down fields are populated on all 382 contacts, but converting-campaign properties and Facebook click identifiers are blank.
- **INFERRED:** HubSpot is currently functioning as a landing area for paid-social form leads, not as an operational lifecycle system: no audited contact has progressed beyond Lead and no Lead Status is in use.
- **INFERRED:** Source coverage is strong at channel level but insufficient for deterministic campaign-to-revenue attribution because campaign/ad/form identifiers are not consistently available as durable contact keys.
- **BUSINESS DECISION REQUIRED:** Approve lifecycle definitions and ownership before any lifecycle automation is designed.

## Integrations and operational risk

- **CONFIRMED:** All 78 Meta lead records currently retrievable through the audited Page forms matched a HubSpot contact by normalized email; all 78 also matched by normalized phone.
- **CONFIRMED:** One of the 78 Meta leads matched more than one HubSpot target when email and phone candidates were combined, consistent with the duplicate-phone risk.
- **CONFIRMED:** An email-only HubSpot-to-Fitssey comparison matched 107 of 382 HubSpot contacts; 275 had no email match in active Fitssey clients.
- **UNKNOWN:** Whether an installed native HubSpot/Meta connector, advertising account connection, or form automation is configured could not be directly audited through the available HubSpot scopes.
- **UNKNOWN:** Phone-based HubSpot-to-Fitssey match coverage was not completed because the Fitssey read-rate window was exhausted after the full inventory; no immediate retry was attempted.
- **INFERRED:** Meta-to-HubSpot lead delivery is operating for the currently retrievable Meta history, but no evidence shows that Fitssey customer status, attendance, membership, purchase, or revenue is synchronized into HubSpot.
- **TECHNICAL FOLLOW-UP REQUIRED:** Add durable external identifiers only after the proposed data model, conflict policy, and backfill plan are approved.

## Sources and limitations

- **CONFIRMED:** Contact reads used HubSpot's date-versioned CRM contacts endpoint and property metadata; the current API reference documents the `2026-03` object paths: <https://developers.hubspot.com/docs/api-reference/latest/crm/objects/contacts/get-contact>.
- **CONFIRMED:** Raw contact values and credentials were processed in memory only and were not written to this repository.
- **UNKNOWN:** Marketing asset findings remain incomplete because the credential returned 403 rather than because those assets were absent.
