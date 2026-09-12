# Repository Rules

1. Fitssey is expected to be the operational source of truth for bookings, attendance, purchases, memberships, and revenue, subject to audit confirmation.
2. HubSpot is intended to become the CRM and marketing source of truth for contacts, lifecycle, segmentation, communications, and attribution.
3. Meta is the advertising and lead-generation source.
4. No external system may be modified during the initial audit phase.
5. Before creating or modifying any HubSpot schema, document the proposed change in docs/data-model.md.
6. Before writing back to Meta, HubSpot, or Fitssey, explicit approval is required.
7. Never commit secrets, API keys, tokens, passwords, or .env files.
8. All integrations should use environment variables.
9. Favor least privilege.
10. The initial audit should be read-only.
11. Document assumptions separately from confirmed facts.
12. If technical behavior is uncertain, inspect the API rather than guessing.
13. Preserve identifiers that allow records to be matched across systems.
14. Identity matching, duplicate handling, and historical backfill must be designed before bulk synchronization.
15. Do not build marketing automation until the customer lifecycle and data model are approved.
