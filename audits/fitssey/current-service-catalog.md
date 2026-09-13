# Fitssey Current Service Catalog

Audit date: 2026-09-13. Source: Fitssey API v4 GET requests only. Point-in-time catalog; owner approval is required before marketing or CRM use.

## Classification method

Fitssey returned 45 service records: 28 classroom and 17 course. The public class-service object supplies GUID, name, internal name, description, category, experience-level reference, and service type. It does not expose active/archive, online-visibility, bookability, duration, capacity, room, or instructor fields. Those operational fields appear on schedule events instead.

- ACTIVE AND CURRENTLY SCHEDULED means the service has at least one event in the 2026-09-13 through 2026-10-31 request.
- UNKNOWN STATUS means the record exists but has no event in the returned window and the API exposes no active/archive flag.
- No service can be classified safely as ACTIVE BUT NOT CURRENTLY SCHEDULED or INACTIVE / ARCHIVED from this API evidence alone.

Thirteen services were scheduled; 32 had unknown status. Forty records had a public description and five did not. Catalog categories were: Bez kategorii 21, Joga 11, Pilates 3, Kursy 2, Poziom 1 2, and one each in Dzieci, Poziom 2, Poziom 3, Warsztaty, Zajęcia dla firm/grup, and Zajęcia indywidualne. Three experience-level IDs were present across the catalog, but their localized labels were not normalized in this audit.

## Service register

| Fitssey ID | Current name | Type | Classification | Events in window | Description |
| --- | --- | --- | --- | ---: | --- |
| 39DAFF02-0E6F-46CF-A8F8-F696BF54535A | Inferno Hot Pilates (HIIT) | classroom | ACTIVE AND CURRENTLY SCHEDULED | 8 | yes |
| 60E4B2E4-C109-46E0-9107-35BD7528403D | Sivananda Joga | classroom | UNKNOWN STATUS | 0 | yes |
| 28CE19BF-AB8D-4008-B928-9750E8B34F6D | Joga powięziowa (Yin) REGENERACJA | classroom | ACTIVE AND CURRENTLY SCHEDULED | 5 | yes |
| 56090513-2A7B-4001-8938-D5D5085FA38B | KURS JOGI OD PODSTAW | course | UNKNOWN STATUS | 0 | yes |
| F56C1666-826C-4D7D-A2CD-29E9BBB2645E | Zajęcia indywidualne 1:1 | classroom | UNKNOWN STATUS | 0 | yes |
| A43748FF-EBF4-4BEB-A061-B65497256C01 | Oferta dla firm/zorganizowanych grup | classroom | UNKNOWN STATUS | 0 | yes |
| 7EF0B6AB-7330-4892-8ACC-61EB1F3AA55C | Joga od podstaw (kurs) | classroom | UNKNOWN STATUS | 0 | yes |
| FB885A77-7045-4BED-8F46-13912DD3DD8F | KURS JOGI OD PODSTAW POZIOM 2 wrzesień | course | UNKNOWN STATUS | 0 | no |
| 4880DCAA-64BE-4804-A0A4-247020002A3B | HOT JOGA | classroom | UNKNOWN STATUS | 0 | yes |
| B7F10E0A-7264-4DFC-B628-0DE3EC279428 | Bikram Joga (26&2) | classroom | ACTIVE AND CURRENTLY SCHEDULED | 14 | yes |
| 69DC9DCC-8D4C-41B8-ADF3-8025C1ECF5A3 | Koncert dźwiękowy mis i gongów (relaksacja) | classroom | UNKNOWN STATUS | 0 | yes |
| C70F3821-932E-4304-9BC3-AD926536BBC4 | Kurs jogi od podstaw - kontynuacja | course | UNKNOWN STATUS | 0 | yes |
| FD1A6F28-FDB5-4ACE-86B5-B3978F2E2EFE | Mobility | classroom | ACTIVE AND CURRENTLY SCHEDULED | 2 | yes |
| 0BB1CA7D-D05F-4B6F-AB17-0B1D14004C12 | ZDROWY KRĘGOSŁUP - Joga dla osób dojrzałych | course | UNKNOWN STATUS | 0 | yes |
| 096356E9-0F1D-4BFD-9C99-E6961DD172C9 | Kurs HOT PILATES | course | UNKNOWN STATUS | 0 | yes |
| EA4FEC2A-7D8D-411D-991F-C25C033D3053 | Vinyasa joga (początkujący) | classroom | ACTIVE AND CURRENTLY SCHEDULED | 1 | yes |
| 53CF03ED-77AF-4DAA-BD8A-9FC61DFE3F40 | Joga dla dzieci 4-8 lat | classroom | UNKNOWN STATUS | 0 | yes |
| 2B1BEF93-B264-428D-9A50-DD1B4DC416F5 | Joga dla nastolatków (12-18 lat) | classroom | UNKNOWN STATUS | 0 | no |
| 08982CA0-DA7B-45E9-B4EC-B855DD808C35 | Kurs Jogi dla dzieci (4-8 lat) | course | UNKNOWN STATUS | 0 | yes |
| 88F5F8CA-1CCD-4BA6-94A0-6E15DBB50BFB | PRZEDŚWIĄTECZNY RELAKS – kobiecy warsztat | course | UNKNOWN STATUS | 0 | yes |
| 14C1E8A5-5898-4987-99D0-83E2577E137F | Iyengar Joga | classroom | ACTIVE AND CURRENTLY SCHEDULED | 2 | yes |
| A0BFD1AB-4A18-4F40-91BF-9C7DC423C5C9 | Hatha Joga dla początkujących | classroom | ACTIVE AND CURRENTLY SCHEDULED | 3 | yes |
| 64DA9C4C-A9B4-446F-BCF9-4939ACCCDF73 | Zdrowy kręgosłup/ Delikatna praktyka jogi | classroom | ACTIVE AND CURRENTLY SCHEDULED | 5 | yes |
| 9A3655FE-328A-4F64-ADF0-E2050EF66996 | Hot Pilates (START) | classroom | ACTIVE AND CURRENTLY SCHEDULED | 5 | yes |
| AE075AD9-0706-4CA5-AD25-C44B2F483D67 | Joga dla dzieci | classroom | UNKNOWN STATUS | 0 | yes |
| 995E6424-E16F-4326-A6D7-7555A4E3BDC6 | Nowy Rok - Nowa Energia (wydarzenie dla kobiet) | course | UNKNOWN STATUS | 0 | yes |
| 6FE17A14-9348-4D64-B5E5-5F362CD017EF | ZDROWY KRĘGOSŁUP - zajęcia wzmacniające | classroom | UNKNOWN STATUS | 0 | yes |
| 026BB8F1-073A-4FDD-BC29-E97EBB5C72A5 | Joga dla początkujących | classroom | UNKNOWN STATUS | 0 | yes |
| 8CB3907B-F90C-40D8-BCEC-15F756711354 | HOT HIIT '45 | classroom | UNKNOWN STATUS | 0 | yes |
| C2354C64-7557-44D1-B7E0-A22270177FC1 | ROZKWITAM - DZIEŃ KOBIET W HOT YOGA PILAWA | course | UNKNOWN STATUS | 0 | yes |
| 996020A1-13FB-4933-A115-CDCA63F36409 | Warsztaty “POCZUJ SIEBIE” z Rafałem Wereżyńskim | course | UNKNOWN STATUS | 0 | yes |
| 818F5023-7B95-4D03-88F9-9D56E1D6D449 | Klasyczny PILATES na macie od podstaw | classroom | ACTIVE AND CURRENTLY SCHEDULED | 2 | yes |
| 4051564A-F78F-4149-8C88-31125280188E | Joga dla początkujących + automasaż twarzy | classroom | UNKNOWN STATUS | 0 | yes |
| 6C073693-6C67-4F1F-AE80-069101429108 | Koncert Mis i Gongów z Anuta OdNowa | course | UNKNOWN STATUS | 0 | yes |
| A6296358-D8FA-4778-B8D1-6F975073E032 | Trening funkcjonalny | classroom | UNKNOWN STATUS | 0 | yes |
| 8AE3E5E5-5A46-414A-802D-36CFD23AA3E5 | Ćwiczenia oddechowe i techniki relaksacyjne | classroom | ACTIVE AND CURRENTLY SCHEDULED | 1 | yes |
| 194DE962-9EB5-44E9-9962-D982B3001883 | DETOX Joga | classroom | UNKNOWN STATUS | 0 | yes |
| 19488D42-44F0-406C-8158-222FB4A41B61 | KĄPIEL W DŹWIĘKACH | course | UNKNOWN STATUS | 0 | yes |
| C4A9DD8F-60A3-492C-A317-BADA21EA00B1 | Weekend integracyjny Józefów | course | UNKNOWN STATUS | 0 | no |
| E34F0824-C8AA-47CE-A1D1-2EB4371BA52F | Spotkanie integracyjne - Odskocznia | course | UNKNOWN STATUS | 0 | no |
| 4560333F-FBD9-40B4-8842-911D30F932AB | Sobolew (sobota cały dzień) | course | UNKNOWN STATUS | 0 | yes |
| C80DB6C4-A658-4922-A454-0A544BA8B2FB | Sobolew - letni weekend 3-5 lipca | course | UNKNOWN STATUS | 0 | yes |
| F7199138-B091-4810-8A57-FEB9BF499197 | Sobolew - letni weekend 3-5 lipca | classroom | UNKNOWN STATUS | 0 | no |
| 26CA2178-6E19-4C0F-AB69-4ABD52A8B130 | Stretching (głębokie rozciąganie) | classroom | ACTIVE AND CURRENTLY SCHEDULED | 2 | yes |
| BE89AE3F-DF06-44A7-9D69-6F81D6D9C21C | Warsztat o emocjach z Anitą Wojdyłą | course | ACTIVE AND CURRENTLY SCHEDULED | 1 | yes |

## Operational metadata

Schedule-derived duration, capacity, room, instructor, online-bookability, cancellation, and current-booking evidence for the 13 scheduled services is in current-schedule-structure.md. Those event-level attributes must not be projected onto the 32 unscheduled records.

### Category and experience-level references

| Fitssey service ID | Category | Experience-level ID |
| --- | --- | --- |
| 39DAFF02-0E6F-46CF-A8F8-F696BF54535A | Pilates | 833EF78C-384E-4C91-9C46-DB17A2128EEF |
| 60E4B2E4-C109-46E0-9107-35BD7528403D | Joga | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| 28CE19BF-AB8D-4008-B928-9750E8B34F6D | Joga | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| 56090513-2A7B-4001-8938-D5D5085FA38B | Poziom 1 | 658D14C9-DBD1-4A2F-BFE1-323906B103E6 |
| F56C1666-826C-4D7D-A2CD-29E9BBB2645E | Zajęcia indywidualne | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| A43748FF-EBF4-4BEB-A061-B65497256C01 | Zajęcia dla firm/grup | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| 7EF0B6AB-7330-4892-8ACC-61EB1F3AA55C | Kursy | 658D14C9-DBD1-4A2F-BFE1-323906B103E6 |
| FB885A77-7045-4BED-8F46-13912DD3DD8F | Poziom 2 | 833EF78C-384E-4C91-9C46-DB17A2128EEF |
| 4880DCAA-64BE-4804-A0A4-247020002A3B | Joga | 833EF78C-384E-4C91-9C46-DB17A2128EEF |
| B7F10E0A-7264-4DFC-B628-0DE3EC279428 | Joga | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| 69DC9DCC-8D4C-41B8-ADF3-8025C1ECF5A3 | Warsztaty | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| C70F3821-932E-4304-9BC3-AD926536BBC4 | Poziom 3 | 833EF78C-384E-4C91-9C46-DB17A2128EEF |
| FD1A6F28-FDB5-4ACE-86B5-B3978F2E2EFE | Bez kategorii | 833EF78C-384E-4C91-9C46-DB17A2128EEF |
| 0BB1CA7D-D05F-4B6F-AB17-0B1D14004C12 | Bez kategorii | 658D14C9-DBD1-4A2F-BFE1-323906B103E6 |
| 096356E9-0F1D-4BFD-9C99-E6961DD172C9 | Bez kategorii | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| EA4FEC2A-7D8D-411D-991F-C25C033D3053 | Joga | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| 53CF03ED-77AF-4DAA-BD8A-9FC61DFE3F40 | Joga | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| 2B1BEF93-B264-428D-9A50-DD1B4DC416F5 | Joga | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| 08982CA0-DA7B-45E9-B4EC-B855DD808C35 | Bez kategorii | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| 88F5F8CA-1CCD-4BA6-94A0-6E15DBB50BFB | Bez kategorii | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| 14C1E8A5-5898-4987-99D0-83E2577E137F | Bez kategorii | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| A0BFD1AB-4A18-4F40-91BF-9C7DC423C5C9 | Joga | 658D14C9-DBD1-4A2F-BFE1-323906B103E6 |
| 64DA9C4C-A9B4-446F-BCF9-4939ACCCDF73 | Joga | 658D14C9-DBD1-4A2F-BFE1-323906B103E6 |
| 9A3655FE-328A-4F64-ADF0-E2050EF66996 | Pilates | 658D14C9-DBD1-4A2F-BFE1-323906B103E6 |
| AE075AD9-0706-4CA5-AD25-C44B2F483D67 | Dzieci | 658D14C9-DBD1-4A2F-BFE1-323906B103E6 |
| 995E6424-E16F-4326-A6D7-7555A4E3BDC6 | Bez kategorii | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| 6FE17A14-9348-4D64-B5E5-5F362CD017EF | Bez kategorii | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| 026BB8F1-073A-4FDD-BC29-E97EBB5C72A5 | Joga | 658D14C9-DBD1-4A2F-BFE1-323906B103E6 |
| 8CB3907B-F90C-40D8-BCEC-15F756711354 | Bez kategorii | 833EF78C-384E-4C91-9C46-DB17A2128EEF |
| C2354C64-7557-44D1-B7E0-A22270177FC1 | Bez kategorii | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| 996020A1-13FB-4933-A115-CDCA63F36409 | Bez kategorii | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| 818F5023-7B95-4D03-88F9-9D56E1D6D449 | Pilates | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| 4051564A-F78F-4149-8C88-31125280188E | Kursy | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| 6C073693-6C67-4F1F-AE80-069101429108 | Bez kategorii | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| A6296358-D8FA-4778-B8D1-6F975073E032 | Bez kategorii | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| 8AE3E5E5-5A46-414A-802D-36CFD23AA3E5 | Bez kategorii | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| 194DE962-9EB5-44E9-9962-D982B3001883 | Joga | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| 19488D42-44F0-406C-8158-222FB4A41B61 | Bez kategorii | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| C4A9DD8F-60A3-492C-A317-BADA21EA00B1 | Bez kategorii | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| E34F0824-C8AA-47CE-A1D1-2EB4371BA52F | Bez kategorii | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| 4560333F-FBD9-40B4-8842-911D30F932AB | Poziom 1 | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| C80DB6C4-A658-4922-A454-0A544BA8B2FB | Bez kategorii | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| F7199138-B091-4810-8A57-FEB9BF499197 | Bez kategorii | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| 26CA2178-6E19-4C0F-AB69-4ABD52A8B130 | Bez kategorii | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |
| BE89AE3F-DF06-44A7-9D69-6F81D6D9C21C | Bez kategorii | 0326FB7C-3365-4C9E-9561-CFA3C4441B8E |

## Owner review

- Confirm which of the 32 UNKNOWN STATUS records are active but unscheduled, private/appointment-only, seasonal, superseded, or archived.
- Confirm whether duplicate/near-duplicate families such as HOT JOGA versus Bikram Joga, beginner-course variants, children variants, Pilates variants, sound events, and Sobolew variants should remain distinct.
- Confirm the customer-facing level labels and which services are approved entry routes for beginners.
- Confirm which internal or historical names should be excluded from marketing.
