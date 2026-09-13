# Fitssey Finance Reconciliation

Audit date: 2026-09-13. Scope: Fitssey API v4 finance-report GET requests only, covering 2025-01-01 through 2026-09-13.

## Result

FINANCE EXTRACTION RECONCILED for documented API pagination and exact duplicate removal.

This means the API result is internally reproducible and its monetary fields balance after deduplication. It does not mean accounting close, currency confirmation, refund completeness, or Fitssey BackOffice/export agreement has been validated.

## Methodology

1. Requested report/finance/sales with explicit page 1 and count 1,000.
2. Followed the documented page count exactly; page sizes were 1,000 and 86.
3. Compared returned rows to totalCount.
4. Grouped rows by source-native sale GUID.
5. Compared commercial fields within repeated-GUID groups.
6. Removed exact repeated rows by retaining one row per sale GUID.
7. Queried report/finance/zero-sales separately with explicit count 1,000.
8. Reconciled itemPrice, discountAmount, itemTotalPrice, itemNetPrice, and itemTaxAmount arithmetically.

## Counts

| Measure | Result |
| --- | ---: |
| Sales endpoint totalCount | 1,086 |
| Returned sales rows | 1,086 |
| Page sizes | 1,000; 86 |
| Unique sale GUIDs | 1,076 |
| Repeated rows beyond one per GUID | 10 |
| Repeated GUID groups | 5 |
| Zero-sales totalCount | 275 |
| Returned zero-sales rows | 275 |
| Unique zero-sale order GUIDs | 275 |
| Zero-sale duplicate rows | 0 |

Each of the five repeated-GUID groups contained two to four rows with one identical commercial signature and one item name. They are exact report duplicates, not different line items. The pre-dedup row count still matches totalCount; totalCount therefore counts the duplicated report rows.

Phase 1's 1,164 versus 1,082 mismatch came from the earlier extraction method, not the current endpoint result. Explicit count/page pagination now returns a self-consistent 1,086 rows. The four-row change from the prior reported total is compatible with new sales between audit dates.

## Date range

- Deduplicated sales rows: 2025-08-21 through 2026-09-13.
- Zero-sales rows: 2025-08-26 through 2026-09-10.

## Monetary interpretation

All 1,076 deduplicated sale rows contain the same tax factor, 1.08, which Fitssey documents as 8% tax. Values are integers in the smallest currency unit.

| Field | Deduplicated minor-unit sum | Major-unit sum | Interpretation |
| --- | ---: | ---: | --- |
| itemPrice | 32,414,600 | 324,146.00 | price before the reported discount |
| discountAmount | 90,000 | 900.00 | reported discount |
| itemTotalPrice | 32,324,600 | 323,246.00 | post-discount line total |
| itemNetPrice | 29,930,260 | 299,302.60 | net component |
| itemTaxAmount | 2,394,340 | 23,943.40 | tax component |

The equations reconcile exactly:

- itemPrice minus discountAmount equals itemTotalPrice.
- itemNetPrice plus itemTaxAmount equals itemTotalPrice.

The extraction therefore supports 323,246.00 major currency units as the deduplicated sales-report total for this date range. It is not labeled PLN or accounting revenue because the response contains no currency field and no accounting control was compared.

## Zero-value and discount semantics

The separate zero-sales endpoint is documented by Fitssey as orders fully discounted to zero, including voucher redemption examples. It returned 275 unique records. These records are not added to the monetary total above. Their item-name distribution includes vouchers, bonus passes, family/friend passes, and other zero-value entitlements.

The sales endpoint's discountAmount is a monetary amount. Its 900.00 major-unit sum bridges pre-discount itemPrice to post-discount itemTotalPrice. Discount-rate values are present but should not be summed as a financial measure.

## Status, void, and refund limits

- The sales and zero-sales report rows expose no order-status field, void reason, refund flag, or reversal identifier.
- No monetary field in the sales report was negative.
- Paid, free-of-charge, void, cancelled, rejected, failed, refunded, and reversed distributions therefore cannot be established from these two report endpoints.
- Fitssey documents order statuses on client-order resources, but a full per-client order-status extraction was not required for pagination reconciliation and would materially increase API volume.
- The absence of negative rows does not prove there were no refunds or reversals; it shows only that the sales report did not expose them as negative rows in this window.

## Currency

UNKNOWN. Fitssey provides smallest-unit semantics but no currency in the finance response or pricing-template response. Many offer names contain zł and both HubSpot and Meta use PLN, making PLN likely, but that remains an inference. OWNER/UI CONFIRMATION REQUIRED.

## Remaining controls

- Compare the deduplicated 323,246.00 major-unit post-discount total and 275 zero-sales records to a Fitssey BackOffice/export control using the same dates and timezone.
- Confirm configured currency.
- Confirm whether voids, refunds, reversals, and chargebacks appear in another Fitssey UI/export or accounting system.
- Approve whether reporting should use sale date, payment date, or accounting/posting date.
- Preserve sale GUID and zero-sale order GUID in future extracts; never sum returned rows before exact duplicate control.
