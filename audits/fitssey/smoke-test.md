# Fitssey Read-Only Smoke Test

## Test Summary

- Date: 2026-09-12
- Mode: Read-only
- Authentication: Success
- Overall result: Passed

## Resource Tested

- Request: `GET /{FITSEY_STUDIO_UUID}/api/v4/public/location/all?count=1&page=1`
- HTTP status: `200 OK`
- Validation: The response contained the expected studio location collection structure.
- Data handling: No location values or response records were written to disk or printed to diagnostic output.

## Permissions and Access

- Confirmed: Bearer-token API access for the configured studio UUID.
- Confirmed: Read access to the location resource.
- Missing access: None detected for the tested resource.
- Scope note: The tested endpoint did not enumerate a separate granular scope list.

## Safety

- No client, booking, attendance, membership, purchase, payment, or other write endpoint was called.
- No secret value is included in this document.
