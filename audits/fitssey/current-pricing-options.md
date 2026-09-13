# Fitssey Current Pricing Options and Contracts

Audit date: 2026-09-13. Source: Fitssey API v4 GET requests only. Point-in-time catalog; owner approval is required before marketing or CRM use.

## Interpretation

Fitssey returned 45 pricing-option templates: 39 limited-visit and six unlimited. Twenty-six are sold online, all 45 use tax factor 1.08, none is auto-assigned, and none is marked as an introductory offer.

The template schema does not expose active/archive status. Sold online is direct evidence of current FrontOffice availability, but a not-sold-online record may be staff-only, private, seasonal, legacy, or inactive. It is therefore classified as UNKNOWN STATUS rather than legacy.

Prices below convert the API's smallest-unit integers to major units. Fitssey did not expose a studio currency field. Some product names explicitly contain zł, but currency must still be confirmed in Fitssey/finance settings before reporting. The template supplies one price and a tax factor; it does not provide separate gross, net, and tax amounts, so no net value is inferred.

Expiration codes are documented as: 0 dates set at sale; 1 dates set on first booked visit; 2 always valid; 3 calendar month; 4 specific custom dates. The template response does not expose the duration behind sale/first-visit activation or the actual custom dates.

## Pricing-option register

| Fitssey ID | Current name | Session type | Visits/value | Price amount | Online | Expiration | Intro |
| --- | --- | --- | ---: | ---: | --- | --- | --- |
| 3A330117-414F-49E0-84A5-8AF7FEA0E20E | 1 x zajęcia (65 zł wejście) | limitedVisits | 1 | 65.00 | yes | sale date | no |
| C15B12F4-812F-45D1-854B-FC8FBC2428F3 | 4 x zajęcia (60 zł wejście) | limitedVisits | 4 | 240.00 | yes | first visit | no |
| FEB2D006-D7B5-4A32-8E26-82833F5A7F01 | 8 x zajęcia (47 zł wejście) | limitedVisits | 8 | 380.00 | yes | first visit | no |
| D30308D2-71E5-441F-A825-C245D5767820 | 12 x zajęcia (41 zł wejście) | limitedVisits | 12 | 500.00 | yes | first visit | no |
| 96A1F0C4-726D-4823-A357-820CAA8A8415 | Zajęcia indywidualne 1:1 | limitedVisits | 1 | 180.00 | yes | sale date | no |
| 5318C22A-96D5-4AE1-B57A-B006A878CFB2 | Voucher prezentowy na 1 zajęcia | limitedVisits | 1 | 0.00 | no | sale date | no |
| DE74A03C-AE7D-482D-8058-75A16F5A2AE4 | PAKIET 4 x zajęcia indywidualne 1:1 | limitedVisits | 4 | 660.00 | yes | sale date | no |
| 767ABC95-0EB9-4438-BBE0-C4DA969F2A22 | 8 x zajęcia indywidualne 1:1 | limitedVisits | 8 | 1200.00 | yes | sale date | no |
| 8F607920-DD44-4BED-B328-0DB89A501A1B | Karnet (rodzina i przyjaciele) | unlimited | -1 | 0.00 | no | sale date | no |
| C762FD0F-9C5C-4F70-B891-FA3D5B295D56 | 10 x zajęcia (2 miesiące ważności) | limitedVisits | 10 | 550.00 | yes | first visit | no |
| 026485DB-07D3-4051-BF5F-57605E55375F | Karnet zajęcia grafikowe | limitedVisits | 5 | 0.00 | no | sale date | no |
| 91B253B9-0AE1-4905-B1C5-6FD5F34B2747 | 4 x zajęcia Joga dla dzieci | limitedVisits | 4 | 180.00 | no | first visit | no |
| 4E919D28-A2E9-4461-9EA6-3628EFEF8077 | Karnet Premium 3 mies. (36 zajęć) 33 zł wejście | limitedVisits | 36 | 1200.00 | no | first visit | no |
| CB074DAB-6AA5-4936-83F5-4517A6DD7F9A | Karnet BONUS zajęcia | limitedVisits | 1 | 0.00 | no | sale date | no |
| 19CE80E9-B33C-4976-888E-557D1D9486DD | HOT 20 – Marcowe Wyzwanie | limitedVisits | 20 | 599.00 | no | specific date | no |
| 7E74F012-EBA0-4DA3-B2F5-974B2DA21BD3 | OPEN | unlimited | -1 | 599.00 | no | first visit | no |
| E8392EF1-24DB-43B1-8D24-10B3C2D9D0AB | Koncert Mis i Gongów | limitedVisits | 1 | 169.00 | yes | sale date | no |
| 1C4B57B9-C8DB-4B74-A305-5A5709BA9E51 | Koncert Mis i Gongów (osoba towarzysząca) | limitedVisits | 1 | 129.00 | yes | sale date | no |
| EB72432A-FC80-4E69-9A8D-F112D2C63DC0 | Karnet 24 wejścia (3 miesiące) 37 zł wejście | limitedVisits | 24 | 899.00 | no | first visit | no |
| 37AB6EDD-47DC-41A7-93D6-6260824DFA15 | Koncert Mis i Gongów (osoby spoza studia) | limitedVisits | 1 | 219.00 | no | sale date | no |
| DE636F31-F93C-4FBB-995D-7A6F2CCA0520 | GOLD PASS (6 miesięcy) 80 zajęć | limitedVisits | 80 | 2780.00 | no | first visit | no |
| E28EB1CE-8AC9-417B-A78E-6557589C190E | Członkostwo OPEN FLOW | unlimited | -1 | 590.00 | no | sale date | no |
| FFA0CE62-E9D7-4345-A4E0-A766253E04F8 | OPEN MAJ PASS | unlimited | -1 | 699.00 | no | first visit | no |
| 85004376-7F48-457C-8A24-A174DF922218 | OPEN MAJ PASS (uczestnicy wyzwania HOT20) | unlimited | -1 | 699.00 | no | first visit | no |
| C0678943-4D9A-401B-8970-76A7360D52D9 | SENIOR - 8 wejść - miesiąc | limitedVisits | 8 | 360.00 | yes | sale date | no |
| A64FDC9A-B0B7-405F-8E6C-4EEA5DD31C63 | Kąpiel w dźwiękach - cena regularna | limitedVisits | 1 | 159.00 | yes | sale date | no |
| 965C6B2A-EB91-4384-9200-86E1B3411BC9 | Kąpiel w dźwiękach - klienci/os. towarzysząca | limitedVisits | 1 | 119.00 | yes | sale date | no |
| 19E5DBFB-6B18-426D-B7DE-E7F945F1ACB8 | Kąpiel w dźwiękach - wejście dla 2 osób | limitedVisits | 1 | 239.00 | yes | sale date | no |
| 0870247F-D2C4-4699-A8FD-39CF7F591949 | Prezent na Dzień Matki | limitedVisits | 1 | 0.00 | no | specific date | no |
| ABAD05BB-5110-4167-BC52-D49A145CEA39 | Weekend Integracyjny Józefów | limitedVisits | 1 | 450.00 | no | first visit | no |
| 90C087C9-FFA6-4083-BEF9-92FE972DF7FA | Członkostwo OPEN START | unlimited | -1 | 690.00 | no | sale date | no |
| 8ABC2F6D-5A79-4B40-8F0F-3FF254CE2397 | Integracja - Odskocznia | limitedVisits | 1 | 65.00 | no | sale date | no |
| A2FDF633-A535-4C0A-8C12-DAC118937061 | Sobolew (sobota) klienci studia | limitedVisits | 1 | 299.00 | yes | sale date | no |
| 226259D7-676C-4B9B-BBEA-A66CFF9C1E02 | Sobolew (sobota) osoby spoza studia | limitedVisits | 1 | 369.00 | yes | sale date | no |
| BBC167BC-0586-47AD-B9E7-458E7807642C | Sobolew - letni weekend 3-5 lipca | limitedVisits | 3 | 749.00 | yes | sale date | no |
| CEB07B91-6D19-4524-A0B0-89049FD487F1 | Zajęcia indywidualne 2:1 (2 osoby) | limitedVisits | 1 | 260.00 | yes | sale date | no |
| 531AB425-B3F1-4ADE-9FC6-BA42CCE2A6EA | PAKIET 4 x zajęcia indywidualne 2:1 | limitedVisits | 4 | 920.00 | yes | sale date | no |
| 69751A49-4329-4C35-9A09-04E6F8715132 | HOT SUMMER PASS (18 zajęć - 7 tygodni) | limitedVisits | 18 | 699.00 | no | specific date | no |
| E62202DD-4918-4BB4-8775-2F0B5AB5776F | WRZEŚNIOWE WYZWANIE 20/30 | limitedVisits | 20 | 649.00 | yes | specific date | no |
| B48B6C13-0D25-4F90-B36E-B7A84AD6F3D0 | TEAM PASS – Karnet Instruktorski | limitedVisits | 10 | 349.00 | yes | sale date | no |
| 05ACAE38-2ABC-447C-8ABC-E24D84E06DA7 | KARNET STUDENCKI | limitedVisits | 7 | 299.00 | yes | first visit | no |
| FCEF9872-FFE8-4A60-8225-C4FD5712BC89 | PIĄTKI SĄ DLA PRZYJACIÓŁ | limitedVisits | 1 | 0.00 | yes | sale date | no |
| 2DBC5EB3-F245-491F-AFC8-DB4164617ABE | Warsztat o emocjach - klientki studia | limitedVisits | 1 | 169.00 | yes | sale date | no |
| F605F2CE-45BA-42FC-8065-86DB485668D2 | Warsztat o emocjach - instruktorki | limitedVisits | 1 | 149.00 | yes | sale date | no |
| D3BA71EC-F5B8-4521-B473-7B7FCF35B337 | Warsztat o emocjach - osoby spoza studia | limitedVisits | 1 | 199.00 | yes | sale date | no |

## Contracts / memberships

| Fitssey ID | Current name | Online sale | Template status | Instalment slots |
| --- | --- | --- | --- | ---: |
| B83C7E7C-839A-476F-A5C6-AD6BEE9E9F1C | Członkostwo OPEN FLOW | yes | UNKNOWN STATUS; sold online | 12 |
| D4607079-F49D-41D2-A3D2-E97319AFAD56 | Członkostwo OPEN START | yes | UNKNOWN STATUS; sold online | 3 |

Both templates have public descriptions and are sold online. OPEN FLOW contains 12 instalment slots, each linking pricing-option ID E28EB1CE-8AC9-417B-A78E-6557589C190E at 590.00 major units. OPEN START contains three instalment slots, each linking pricing-option ID 90C087C9-FFA6-4083-BEF9-92FE972DF7FA at 690.00 major units. The API does not attach dates or a billing-interval label to the template slots, so monthly frequency is not inferred. Client-contract records expose starts, ends, termination dates, instalments, next payment, next charge, and minimum instalment count to allow termination. Current aggregate client-contract counts are documented in current-state-reconciliation.md.

The public template response does not provide a normalized currency, a simple billing-interval field, cancellation wording, included-service list, location restrictions, or a directly stated commitment rule. Instalment counts suggest recurring structures but do not by themselves establish billing frequency. OWNER/UI CONFIRMATION REQUIRED before these memberships are marketed or represented in CRM.

## Restrictions and commercial gaps

The pricing template does not expose service/category restrictions, location restrictions, purchase limits, sharing/transfer rules, cancellation consequences, or the validity duration attached to expiration types 0 and 1. Product names are not a substitute for configuration. These items require owner/UI confirmation.

Four option records have promotion enabled: OPEN MAJ PASS as highlight; OPEN MAJ PASS for HOT20 participants as a 100.00-unit discount to 599.00; HOT SUMMER PASS as a highlight dated 2026-07-10 through 2026-07-31; and WRZEŚNIOWE WYZWANIE as a highlight. The summer record remains enabled after its dated end and three of the four options are not sold online, so promotion-enabled does not by itself establish a currently purchasable campaign. FrontOffice display and intended current use require owner/UI confirmation.
