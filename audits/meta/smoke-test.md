# Meta Read-Only Smoke Test

## Test Summary

- Date: 2026-09-12
- Mode: Read-only
- Authentication: Success
- Overall result: Passed
- Graph API version requested and reported by Meta: `v26.0`

## Permissions Tested

- Request: `GET /me/permissions?fields=permission,status`
- HTTP status: `200 OK`
- Granted permissions reported: `ads_management`, `ads_read`, `business_management`, `leads_retrieval`, `pages_manage_ads`, `pages_read_engagement`, `pages_show_list`, `public_profile`

## Resources Tested

### Business

- Request: `GET /v26.0/{META_BUSINESS_ID}?fields=id`
- HTTP status: `200 OK`
- Access: Confirmed for the configured business ID.

### Ad Account

- Request: `GET /v26.0/act_{META_AD_ACCOUNT_ID}?fields=id,account_id`
- HTTP status: `200 OK`
- Access: Confirmed for the configured ad account ID.

### Page

- Request: `GET /v26.0/{META_PAGE_ID}?fields=id`
- HTTP status: `200 OK`
- Access: Confirmed for the configured page ID.

## Missing Access and Follow-Up

- Missing access: None detected for the three tested resources.
- Resolution: The earlier unversioned ad-account request returned OAuth error `2635`. Explicitly using Graph API `v26.0` resolved the versioning failure.
- No permission expansion or write request was attempted.

## Safety

- All requests used `GET`.
- No ads, campaigns, leads, audiences, pages, or other Meta resources were created or modified.
- No secret value is included in this document.
