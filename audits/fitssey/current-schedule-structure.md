# Fitssey Current Schedule Structure

Audit date: 2026-09-13. Source: Fitssey API v4 GET requests only. This is a point-in-time structural view, not a permanent timetable.

## Window and coverage

- Requested window: 2026-09-13 through 2026-10-31.
- Fitssey returned 49 date buckets and 51 schedule events, all dated 2026-09-13 through 2026-09-30. The absence of October events means only that no October events were returned at audit time.
- Thirteen of 45 catalog services appeared in the returned schedule.
- All 51 events were marked online-bookable; none was hidden, free, live-streamed, or cancelled.
- Aggregate booked spots at extraction time: 136. This is a point-in-time sum across occurrences, not a unique-client count or an approved occupancy KPI.
- Returned events used the Sala do jogi room at the Hot Yoga Pilawa facility. Capacities varied by event from 11 to 18.

## Scheduled service structure

| Service ID | Service | Occurrences | Cancelled | Booked spots | Capacity pattern | Room | Instructor coverage |
| --- | --- | ---: | ---: | ---: | --- | --- | --- |
| 26CA2178-6E19-4C0F-AB69-4ABD52A8B130 | Stretching (głębokie rozciąganie) | 2 | 0 | 14 | 13 × 2 | Sala do jogi | Kamila G. × 2 |
| B7F10E0A-7264-4DFC-B628-0DE3EC279428 | Bikram Joga (26&2) | 14 | 0 | 30 | 13 × 14 | Sala do jogi | Katarzyna Rattelmeier × 14 |
| 39DAFF02-0E6F-46CF-A8F8-F696BF54535A | Inferno Hot Pilates (HIIT) | 8 | 0 | 25 | 13 × 3; 16 × 5 | Sala do jogi | Kamila G. × 1; Katarzyna Rattelmeier × 7 |
| 64DA9C4C-A9B4-446F-BCF9-4939ACCCDF73 | Zdrowy kręgosłup/ Delikatna praktyka jogi | 5 | 0 | 2 | 11 × 5 | Sala do jogi | Kamila G. × 1; Katarzyna Rattelmeier × 4 |
| 9A3655FE-328A-4F64-ADF0-E2050EF66996 | Hot Pilates (START) | 5 | 0 | 6 | 13 × 5 | Sala do jogi | Kamila G. × 2; Katarzyna Rattelmeier × 3 |
| A0BFD1AB-4A18-4F40-91BF-9C7DC423C5C9 | Hatha Joga dla początkujących | 3 | 0 | 19 | 13 × 2; 16 × 1 | Sala do jogi | Anita Laskowska × 3 |
| 28CE19BF-AB8D-4008-B928-9750E8B34F6D | Joga powięziowa (Yin) REGENERACJA | 5 | 0 | 20 | 13 × 2; 16 × 1; 18 × 2 | Sala do jogi | Anita Laskowska × 3; Kamila G. × 1; Katarzyna Rattelmeier × 1 |
| 14C1E8A5-5898-4987-99D0-83E2577E137F | Iyengar Joga | 2 | 0 | 5 | 14 × 2 | Sala do jogi | Agnieszka Lesiak × 2 |
| 818F5023-7B95-4D03-88F9-9D56E1D6D449 | Klasyczny PILATES na macie od podstaw | 2 | 0 | 2 | 13 × 2 | Sala do jogi | Klaudia Rękawek × 2 |
| FD1A6F28-FDB5-4ACE-86B5-B3978F2E2EFE | Mobility | 2 | 0 | 5 | 14 × 2 | Sala do jogi | Ania Barcikowska × 2 |
| EA4FEC2A-7D8D-411D-991F-C25C033D3053 | Vinyasa joga (początkujący) | 1 | 0 | 4 | 13 × 1 | Sala do jogi | Anita Laskowska × 1 |
| BE89AE3F-DF06-44A7-9D69-6F81D6D9C21C | Warsztat o emocjach z Anitą Wojdyłą | 1 | 0 | 4 | 13 × 1 | Sala do jogi | generic Fitssey instructor record × 1 |
| 8AE3E5E5-5A46-414A-802D-36CFD23AA3E5 | Ćwiczenia oddechowe i techniki relaksacyjne | 1 | 0 | 0 | 13 × 1 | Sala do jogi | Ada Jankowska × 1 |

Eleven services recur at least twice in the returned window. The workshop and breathing/relaxation service each appear once. This supports a repeated-class-plus-event structure; it does not establish a permanent weekly timetable.

## Current course structure

One course resource was returned:

- Course GUID C3E47B32-3D83-4F76-B9F4-260CB3EF1E74, Warsztat o emocjach z Anitą Wojdyłą.
- It links to class-service GUID BE89AE3F-DF06-44A7-9D69-6F81D6D9C21C.
- It contains one event on 2026-09-20.
- Booking behavior code 2 is documented by Fitssey as allow booking single dates only.

## Instructors and staff

- Fitssey returned 14 staff/member records.
- Eight distinct staff/instructor records appear on events in the current schedule window: Agnieszka Lesiak, Ada Jankowska, Ania Barcikowska, Anita Laskowska, Kamila G., Katarzyna Rattelmeier, Klaudia Rękawek, and the generic Instruktor/ Instruktorka record.
- Six returned staff records do not appear on events in this window: Ania Piesio, Anna Płóciennik, Justyna Ochnik, Małgorzata Piętka, Michael Rattelmeier, and Nagranie/ zoom/ online.
- Fitssey role-filtered reads returned one manager, 12 teachers, and one host. The 14 unfiltered records therefore reconcile to the three documented IAM role filters. Eight distinct records appeared on this schedule; role membership is still not inferred from names alone.

Staff absence from this finite window does not establish inactivity. The generic instructor and online/recording records require owner review before they are treated as people in CRM or reporting.

## Catalog items absent from the schedule

Thirty-two catalog services returned no events in this window. They are listed in current-service-catalog.md as UNKNOWN STATUS because the service schema exposes no active/archive or online-visibility flag. Absence from this schedule does not mean abandoned, unavailable, or safe to market.

## Owner/UI confirmation required

- Whether the returned schedule is fully published beyond 2026-09-30.
- Whether capacities are operational room limits, event-specific sales limits, or both.
- Staff IAM role membership and which generic/system records should be excluded from people reporting.
- Booking-ahead cutoffs, minimum enrollment, cancellation thresholds, and staff override rules.
- Whether services absent from this window are inactive, seasonal, appointment-only, private, corporate, course-only, or awaiting publication.
