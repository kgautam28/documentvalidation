# Research appendix 5: Gambling and cannabis license verification sources (US)

Compiled 2026-09-18. "Verified" means the page, file, or API was fetched and inspected. Unconfirmed items are collected at the end.

## 1. Gambling regulators: public licensee lists

Key finding: most regulators publish operator lists as dated PDFs or HTML pages with no license number, no status, and no expiry. Only a minority (Illinois, Massachusetts vendor list, West Virginia, North Carolina, Indiana, Louisiana, Tennessee, Kentucky) expose a license number or dates. Legal-entity names are usually present alongside brands, but brand-only lists exist (New York, Massachusetts operators, Michigan).

| State / regulator | What is published | Form | Legal entity vs brand | License number, status, expiry | Cadence | Source |
|---|---|---|---|---|---|---|
| Nevada GCB | Location list, restricted/nonrestricted report, active registrations report | Pages render empty to a non-JS fetcher | Unconfirmed | Unconfirmed | Unconfirmed | https://www.gaming.nv.gov/about-us/statistics-and-publications/ |
| New Jersey DGE | Internet Gaming Permit Holders PDF (404 when fetched); Enterprise Active Vendors Report (PDF and XLS, 21,800 rows) | XLS for vendors | Vendor XLS: Applicant Name (legal) only | Vendor XLS: status code, license type code, Vendor ID, address, phone; no expiry | Vendors report updated daily at 10 PM | https://www.njoag.gov/about/divisions-and-offices/division-of-gaming-enforcement-home/vendor-licensing-reports/ ; https://www.nj.gov/oag/ge/docs/Reports/active_vendor.xls ; https://www.nj.gov/oag/ge/docs/Reports/info_keys.pdf |
| Pennsylvania PGCB | Licensed Interactive Gaming Certificateholders PDF/DOCX; sports wagering equivalent; Gaming Service Provider PDFs | PDF / DOCX | Both, e.g. "Bally's Pennsylvania, LLC d/b/a Bally's Casino" | Operator list: no number, no expiry. GSP Registered list has business name with DBA, city, phone, service description, expiration | Dated snapshots; GSP list as of 9/17/2026 | https://gamingcontrolboard.pa.gov/licensing/expanded-gaming-information-and-links ; https://pgcb.pa.gov/files/licensure/Reports/Application_Status_Vendors_Approved_Registered.pdf |
| Michigan MGCB | Authorized Online Gaming and Sports Betting Tribes/Casinos and Platform Providers | XLSX (downloaded) | Platform provider is brand only ("DraftKings"); no legal entity, no number, no dates | None | Undated | https://www.michigan.gov/mgcb/-/media/Project/Websites/mgcb/Internet-Gaming-and-Fantasy-Contests/Resources/Authorized_Online_Gaming_Sports_Betting_Operators_Providers.xlsx |
| New York Gaming Commission | Mobile sports wagering page: 9 brand names | HTML | Brand only | None | Undated | https://gaming.ny.gov/sports-wagering |
| Illinois IGB | Sports wagering applicant and licensee lists (Master, Supplier, MSP, Tier 2) | HTML with CSV export | Business name plus d/b/a | License status, wagering status (Approved, Provisionary, Suspended), effective date; no number | Live | https://igb.illinois.gov/sports-wagering/sports-lists.html |
| Colorado Division of Gaming | Gaming License Verification search by name, DBA, license number | HTML search (JS app) | Search supports DBA and number | Result fields unconfirmed | Live | https://sbg.colorado.gov/gaming-license-verification ; https://codor.mylicense.com/DOG_Verification/ |
| Ohio Casino Control Commission | Sports gaming applicant PDF (Dec 2024) plus eLicense lookup | PDF plus JS app | Applicants | Application status; "Licenses issued to a proprietor or services provider does not indicate licensure of any listed partners" | PDF stale | https://elicense.ohio.gov/oh_verifylicense?board=Casino+Control+Commission |
| Massachusetts MGC | Sports wagering licensees page; Sports Wagering Master Vendor List PDF | HTML; PDF | Operators: brand plus host casino; vendors: legal name with brand in quotes | Vendor PDF: License No. (SWV-0001...), expiration, status, address. Operator page: none | Vendor list as of 9/9/2026 | https://massgaming.com/about/sports-wagering-in-massachusetts/sports-wagering-licensees/ ; https://massgaming.com/wp-content/uploads/SW-Vendor-List-9-9-26.pdf |
| Arizona Department of Gaming | Approved operators page | 403 to every fetch | Unconfirmed | Unconfirmed | Unconfirmed | https://gaming.az.gov/ewfs/general-information |
| Virginia Lottery | Approved permit holders (11), suppliers (16), vendors PDF (Aug 2026) | HTML plus PDF | Yes: "Crown Virginia Gaming, LLC (Draft Kings)" | No number, status, or expiry | Current | https://www.valottery.com/aboutus/casinosandsportsbetting/sportsbetting |
| Tennessee SWC | Operators (9), vendors (60+), fantasy sports licensees (15) | HTML | Yes: "Crown TN Gaming LLC (DraftKings)" | Initial license and renewal dates; no number | Unstated | https://www.tn.gov/swac/licensees-registrants.html |
| Indiana IGC | Sports wagering vendor licensing table | HTML | Sportsbook name plus legal name | Platform, website, COA holder, initial license date, current license expiration; no number | As of 7/27/2026 | https://www.in.gov/igc/sports-wagering-and-paid-fantasy-sports/swvendors/ |
| Louisiana LGCB | Licensed platforms | HTML | Yes: "American Wagering, Inc. d/b/a Caesars Sportsbook (B016503431)" | License identifier shown; no status or expiry | Undated | https://lgcb.dps.louisiana.gov/licensed-platforms/ |
| Maryland Lottery and Gaming | Approved sports wagering contractor licenses PDF | PDF (not inspected) | Unconfirmed | Unconfirmed | Dated | https://www.mdgaming.com/maryland-sports-wagering/sports-wagering-licensing/ |
| Connecticut DCP | eLicense lookup, 800+ license types including gaming | HTML search plus rosters | Unconfirmed for gaming | Status generally shown | Live | https://portal.ct.gov/dcp/verify-a-license |
| West Virginia Lottery | MSP and supplier license dates PDF | PDF | Legal name plus DBA ("Crown WV Gaming, LLC" / "DraftKings") | License No (SWP 003), interim and annual dates, expiration | Dated | https://assets.ctfassets.net/nm98451qj5dg/7lTFDzTClQRpAauHBroZkL/59afddefe3aa372f59524ec05d1b7a73/Sports_Wagering_License_List.pdf |
| Kansas KRGC | Certified suppliers and sports wagering registrants | HTML name lists | Company name, sometimes DBA | No number, status, or expiry | As of 8/19/2026 | https://krgc.kansas.gov/regulated-info/licensing-security/certified-suppliers/ |
| Kentucky KHRG | Licensee search: operators, service providers, labs | HTML search | Licensee name | License number, issue and expiration dates; statuses Active, Denied, Inactive, Pending, Revoked | Live | https://khrc.ky.gov/Search/List_Licensees.aspx |
| North Carolina Lottery Commission | Approved licensees: interactive operators (7), service providers (4), suppliers (23) | HTML tables | Brand plus operator legal entity | License numbers NCO-0001, NCSP-, NCS-; no status or expiry | Undated | https://ncgaming.gov/approved-licensees/ |

Timeliness: Illinois shows Suspended; Kentucky exposes Revoked and Denied; Massachusetts notes non-renewals in prose; most PDF lists (PA, OH, MD, WV) are point-in-time snapshots that omit lapsed licensees, so a document naming a lapsed licensee will fail to match rather than be flagged as revoked.

## 2. Affiliate and vendor registration for gambling marketing

| State | Requirement | Public list of registered affiliates? | Source |
|---|---|---|---|
| New Jersey | Vendor Registration (free) or Ancillary CSIE license; sub-affiliates must also be licensed to receive compensation | Yes, in the daily Enterprise Active Vendors Report by legal name with status code; not tagged as "affiliate" | https://www.igbaffiliate.com/en/articles/regulation-compliance/the-licence-lowdown-which-us-states-are-worth-it-for-affiliates/ ; https://www.law.cornell.edu/regulations/new-jersey/N-J-A-C-13-69A-5-11 |
| Pennsylvania | Gaming Service Provider, registered or certified | Yes, the Approved Registered GSP PDF lists entries whose service description is literally "Affiliate marketing", with DBA and expiration | https://pgcb.pa.gov/files/licensure/Reports/Application_Status_Vendors_Approved_Registered.pdf |
| Massachusetts | Marketing affiliates must submit a Sports Wagering Registration Form | Yes, Master Vendor List PDF with license number, expiration, status | https://massgaming.com/licensing/vendor-licensing-and-registration/ |
| Colorado | Vendor Minor or Major license | Verification search; no bulk list found | https://sbg.colorado.gov/gaming-license-verification |
| Indiana | Sports wagering registrant | No affiliate registrant list found | https://www.in.gov/igc/sports-wagering-and-paid-fantasy-sports/swvendors/ |
| Michigan | Vendor registration (secondary sources); page 403 | Not confirmed | https://www.bettingusa.com/affiliate/ |
| Virginia | Sports betting vendor registration (11VAC5-70-80) | Approved vendors PDF, contents not inspected | https://law.lis.virginia.gov/admincode/title11/agency5/chapter70/section80/ |
| Kansas | Sports wagering registrants category | Name-only list | https://krgc.kansas.gov/regulated-info/licensing-security/certified-suppliers/ |
| Tennessee | No license for CPA affiliates per secondary source; vendor registrant list published | Names plus dates | https://www.tn.gov/swac/licensees-registrants.html |
| Arizona, West Virginia, Louisiana | Ancillary or non-gaming supplier permits (secondary sources only) | Not confirmed | https://www.bettingusa.com/affiliate/ |
| Illinois, Connecticut, New York | No distinct affiliate category found | No | https://igb.illinois.gov/sports-wagering/sports-vendors.html |

Implication: an affiliate advertiser can be matched against a regulator list only in NJ, PA, MA, and partially CO, KS, TN, VA. Elsewhere the affiliate holds no verifiable state credential, and Google's policy requires proof of relationship to a licensed operator instead.

## 3. Tribal gaming
- NIGC offers an interactive casino map and references PDFs listing gaming tribes; PDF URLs could not be extracted. Entries are framed by tribe and facility; it is not confirmed that an operating entity is named. https://www.nigc.gov/map
- Tribal operations are licensed by the tribe's own gaming commission under an NIGC-approved ordinance; a "tribal gaming license" upload is generally not verifiable against any single federal list. Michigan's MGCB spreadsheet is the clearest state-level substitute (tribe plus casino plus platform provider).

## 4. Google Ads gambling certification (US)
Policy: https://support.google.com/adspolicy/answer/15132179?hl=en ; August 26, 2026 update: https://support.google.com/adspolicy/answer/17258294?hl=en

Verified policy text (US):
- Allowed with certification: state lotteries (state-run only), horse racing, lottery couriers, sports betting, online casinos. "Advertisers of horse racing, sports betting and online casinos must be licensed by the state entity in certain states where legal."
- "Advertisers of online gambling-promoting content can only target specific U.S. states, as outlined in the certification form." Affiliate and aggregator content is certifiable, state-restricted; destinations "must not offer gambling services themselves or link to gambling services they own."
- DFS: state license where required; lottery couriers licensed in at least one state.
- No targeting under 21 or outside licensed states; addiction warning and help info required.

August 2026 certification changes:
- "You must hold a valid local license for every region you intend to target and provide evidence of that licence."
- "If the relationship of an advertiser to a licensee is unclear, advertisers must submit documentation which clearly describes the relationship between the advertising entity, the gambling entity, and the associated domain."
- Affiliates "must link exclusively to fully licensed and authorized gambling entities in the targeted geographic region"; footer must state that outbound links go only to licensed entities.
- Destination footer must show "licensee name, license number and a privacy policy"; separate application per country; recertify on material change.
- The application form (https://support.google.com/google-ads/contact/gambling) is JS-gated; whether it asks for a license number versus a document upload is unconfirmed from Google's own page. Secondary sources claim per-website certification and PA/NJ affiliates being asked for GSP or vendor credentials: https://www.fortismedia.com/en/articles/google-ads-gambling-policy/ ; https://richads.com/blog/google-ads-gambling-policy-guide/ (unverified).

## 5. Cannabis license databases

| State | Access form | Fields (verified) | License number format | Suspended or revoked visible? | Cadence | Source |
|---|---|---|---|---|---|---|
| California DCC | UI at search.cannabis.ca.gov. Undocumented public JSON API behind it: `GET https://as-dcc-pub-cann-w-p-002.azurewebsites.net/licenses/filteredSearch?pageSize=N&pageNumber=1&searchQuery=<text or number>`; lookups `/licensestatuses`, `/licensetypes`. Bulk CSV: `GET https://fa-dcc-pub-vip-cann-ww-p-001.azurewebsites.net/api/ExportAll?searchQuery=` returned a 7.6 MB CSV of all 20,902 records. Nothing on data.ca.gov. | licenseNumber, licenseStatus, licenseStatusDate, licenseType, licenseDesignation, issueDate, expirationDate, licensingAuthority, businessLegalName, businessDbaName, businessOwnerName, businessStructure, premise address, email, phone, dataRefreshedDate | `C10-0000123-LIC` (verified: returns "Emerald Pharms Resource Center", Surrendered) | Yes: Active, Canceled, Expired, Revoked, Suspended, Surrendered, Limited Operations | Daily (dataRefreshedDate 2026-09-18) | https://search.cannabis.ca.gov/ ; https://search.cannabis.ca.gov/config.js |
| Colorado MED | Per-type Google Sheets exportable as CSV, plus mylicense verification tool | License Number, Facility Name (legal), DBA, Facility Type, address, Expiration Date, Date Updated | `402-01197` (medical store); retail prefix inferred, not verified | Licensed facilities only; revoked not shown | Monthly | https://med.colorado.gov/licensee-information-and-lookup-tool/licensed-facilities ; https://docs.google.com/spreadsheets/d/1PqYThJJwGEsrwWvciu9vXosuC0BzAw4YtD03RvlSKzE/export?format=csv ; https://codor.mylicense.com/MED_Verification/ |
| Michigan CRA | Accela public portal (search only); licensing reports page has no visible export link | Unconfirmed | Not confirmed | Unconfirmed | Unconfirmed | https://aca-prod.accela.com/MIMM/Cap/CapHome.aspx?module=Adult_Use ; https://www.michigan.gov/cra/verify-a-license-1 |
| Washington LCB | XLSX "Cannabis License Applicants" | Tradename, License (6-digit), UBI, address, Privilege Status (e.g. ACTIVE (ISSUED), CLOSED (PERMANENT)), phone; legal name only on a secondary sheet. Page warns of a known data transfer issue. | 6-digit numeric | Yes | File dated 09-15-2026 | https://lcb.wa.gov/records/frequently-requested-lists ; https://lcb.wa.gov/sites/default/files/2026-09/CannabisApplicants09152026.xlsx |
| Massachusetts CCC | Socrata at opendata.mass-cannabis-control.com; dataset IDs hmwt-yiqy (licenses) and n6qz-us6r (applications) from search results; API calls failed from the research environment | Catalog says license number, legal name, DBA, type, status, expiry, address; self-reported by licensees | Not verified | Unconfirmed | Unconfirmed | https://masscannabiscontrol.com/open-data/data-catalog/ ; https://opendata.mass-cannabis-control.com/w/hmwt-yiqy/default |
| New York OCM | Socrata jskf-tt3q; SODA `https://data.ny.gov/resource/jskf-tt3q.json` | License Number, Type, Status, Issued/Effective/Expiration, Entity Name, DBA, address, website, Operational Status, contact | `OCM-RETL-25-000306` (verified) | Status field present | Weekly | https://data.ny.gov/Economic-Development/Current-OCM-Licenses/jskf-tt3q |
| Oregon OLCC | Socrata q32u-cmam on data.oregon.gov | Address, Tier, County, SOS Registration Number, Inactive Date, Expiration, Type, Business Licensee, Business Name, License Status, Closed flag, Endorsements, License Number | Not inspected | Status plus inactive date plus closed flag | Updated 2026-09-02 | https://data.oregon.gov/d/q32u-cmam |
| Illinois IDFPR | Combined PDF (39 pages) | License Holder (legal), Dispensary Name (brand), address, issue date, credential number | `284.000001-AUDO` (verified) | Active only | Updated January 2026 | https://idfpr.illinois.gov/content/dam/soi/en/web/idfpr/licenselookup/adultusedispensaries.pdf |
| Nevada CCB | HTML tables plus XLSX plus interactive search | Business name, address, type (Adult Use / Medical), license number, delivery flag | Not inspected | Active only | As of 09/01/2026 | https://ccb.nv.gov/list-of-licensees/ |
| Arizona DHS | PDF stale (June 2021); current data in ADHS GIS app | Status, 20-char certificate number, establishment name, DBA, address | 20-char alphanumeric | Operating status only | Stale | https://www.azdhs.gov/gis/adhs-licensed-facilities/index.php |
| New Jersey CRC | HTML tables with per-business permit PDFs | Business name, types, locations, expiration year or INACTIVE; no license numbers | n/a | Inactive flag | Unstated | https://nj.gov/cannabis/businesses/permitted/index.shtml |
| Florida OMMU | HTML MMTC table | Name, phone, email, Authorization Status, License Number | Not inspected | Status only | Unstated | https://knowthefactsmmj.com/mmtc/ |
| Missouri DCR | Interactive table plus ArcGIS map | License number, entity name, DBA, phone, address, Approval-to-Operate status, website | Not inspected | ATO status | Monthly | https://health.mo.gov/business-professionals/cannabis-regulation/licensee-compliance-guidance/licensed-facilities |
| Maryland MCA | Dashboard; the XLSX extract is sales data, not a roster | Unconfirmed | Unconfirmed | Unconfirmed | Monthly | https://cannabis.maryland.gov/Pages/Industry_Licensees_and_Registrants.aspx |
| Ohio DCC | Dispensary licenses page plus map; not visible to fetcher | Unconfirmed | Unconfirmed | Unconfirmed | Unconfirmed | https://com.ohio.gov/wps/portal/gov/com/divisions-and-programs/cannabis-control/about-dcc/licenses/dispensaries/dispensary-licenses |

Timeliness: CA daily via API, NY weekly, CO and MO monthly, WA per dated file, IL and AZ PDFs stale. Suspended or revoked visibility: CA, OR, WA, NY, NJ show status; most PDF lists omit lapsed licensees rather than marking them.

## 6. Fraud patterns and regulator warnings
- Forged regulator credentials: California Gambling Control Commission advisory (Jan 15, 2026): an illegal operation used the Commission's name and logo on forged fee notices; "The Commission does not issue, nor has it ever issued, licenses to California Scratch Card". https://www.cgcc.ca.gov/documents/enabling/2026/Advisory_California_Scratch_Card-FINAL.pdf
- Spoofing licensed casinos: Iowa Racing and Gaming Commission (Sep 2025): fraudulent sites "often use official logos and branding to appear legitimate or spoof real Iowa casinos". https://irgc.iowa.gov/news-release/2025-09-03/online-gambling-scams-and-illegal-operators
- Scale: BBB counted nearly 200 scam reports and 10,000+ complaints on online gambling 2022 to mid-2025. https://www.29news.com/2026/07/08/bbb-warns-sports-bettors-about-unlicensed-sportsbooks-online-gambling-scams/
- Unlicensed operators presenting as legitimate: Tennessee SWC (Oct 2025) enforcement; "Access to a website or an app does not mean the sportsbook has been licensed." https://www.tn.gov/swac/about/tennessee-sports-wagering-council-newroom/2025/10/23/three-more-illegal-sports-gaming-entities-stop-operations-in-tennessee.html
- Fake cannabis retailer listings: Vermont CCB (May 2025). https://ccb.vermont.gov/notice-public-fake-cannabis-retailer-scams
- License-number hijacking (using a real licensee's public number on a fake site or ad): no regulator notice documenting this pattern was found for US cannabis or gambling. California's consumer guidance relies on QR codes on displayed certificates and the license search. https://www.cannabis.ca.gov/consumers/whats-legal/ ; https://real.cannabis.ca.gov/
- Design implication: because operator lists are public and name-matchable, a forged document that copies a real licensee's legal name and number passes a naive "does the number exist" check. The check must also bind the advertiser's legal entity and domain to the licensee, and require relationship evidence for affiliates.

## 7. Could not confirm
1. Nevada GCB licensee list format.
2. New Jersey Internet Gaming Permit Holders PDF (404).
3. Arizona Department of Gaming operators list and affiliate registry (403).
4. Michigan MGCB vendor page and list (403); Michigan CRA export files and number format.
5. Ohio eLicense and Colorado mylicense result fields.
6. Maryland sports wagering PDF contents; Maryland cannabis roster format.
7. Massachusetts CCC Socrata dataset IDs and columns.
8. NIGC tribe list PDF URLs and whether entries name an operating entity.
9. Google's actual certification form fields.
10. Any documented case of a real US license number hijacked on a fake ad or site.
11. Whether the California DCC ExportAll and filteredSearch endpoints are officially supported or rate-limited.
