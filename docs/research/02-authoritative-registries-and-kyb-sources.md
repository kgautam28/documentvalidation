# Research appendix 2: Authoritative sources for verifying US business documents

Compiled 2026-09-16 from official pages and live API probes. Vendor claims are marked as such. Unconfirmed items are collected at the end.

## 1. Secretary of State (SOS) business registries

### 1a. Official access by state

| State | Official API? | Bulk data? | Notes / source |
|---|---|---|---|
| Louisiana | Yes, official REST "Commercial API" (the only state found with one) | No | `https://commercialapi.sos.la.gov/` with `/api/Certificate/Validate`, `/api/Commercial/Search`, `/api/Commercial/Lookup`; token per request; free test token, paid yearly live token from https://subscriptions.sos.la.gov ; 18 calls/min; returns charter status, agents, officers. Guide: https://static.sos.la.gov/COAPI/Commercial_API_Guide.pdf . Live probe without a token returned the documented JSON schema (`IsValid`, `CertificateId`, `CertificateDate`, `EntityName`, `EntityNumber`). |
| Colorado | Socrata SODA API | Yes | https://data.colorado.gov/Business/Business-Entities-in-Colorado/4ykn-tg5h (entity id, status, addresses, registered agent). Live search https://www.coloradosos.gov/biz/BusinessEntityCriteriaExt.do |
| New York | Socrata SODA API | Yes | https://data.ny.gov/Economic-Development/Active-Corporations-Beginning-1800/n9v6-gdp6 (monthly); all filings https://catalog.data.gov/dataset/corporations-and-other-entities-all-filings |
| Florida | No API | Yes, free SFTP | Daily and quarterly files via `sftp.floridados.gov` (public credentials on page): https://dos.fl.gov/sunbiz/other-services/data-downloads/ ; layouts https://dos.fl.gov/sunbiz/other-services/data-downloads/corporate-data-file/ |
| Texas | No public API; SOSDirect web at $1/search | Paid bulk | Snapshots $1,350 to $1,750: https://direct.sos.state.tx.us/help/help-corp.asp?pg=bulk ; https://www.sos.state.tx.us/corp/sosda/index.shtml |
| California | No public API | Paid bulk | https://bizfileonline.sos.ca.gov/search ; bulk products https://www.sos.ca.gov/business-programs/business-entities/forms/business-records |
| Washington | No | Discontinued extract; CSV export from advanced search only | https://www.sos.wa.gov/corporations-charities/frequently-asked-questions-faqs/corporations-charities-filing-system-tools-resources ; https://ccfs-status.sos.wa.gov/ |
| Delaware | No API, no bulk | No | Free name search; $10 status, $20 extended status; officers not filed with the state. |
| Wyoming | No | Not found | https://wyobiz.wyo.gov/business/filingsearch.aspx (filing PDFs per entity) |
| Nevada | Unconfirmed third-party claims of bulk CSV and API; portal migrated to https://orion.nv.gov/ | ? | Unverified |
| Oregon, Connecticut, Hawaii | Socrata open data claimed by scraper vendors | | Dataset IDs not verified |

Everything else is an HTML or JS search UI. Several sit behind Cloudflare human checks (Michigan, Ohio returned 403 to curl). Cobalt notes Delaware live retrieval takes 2 to 3 minutes.

### 1b. Aggregators

| Vendor | What it returns | Pricing signal | Validates a certificate number? |
|---|---|---|---|
| OpenCorporates | 200M+ companies; search by jurisdiction; officers and filings "where available". Their own blog admits US officer, status history, and filing image coverage is inconsistent: https://blog.opencorporates.com/2025/09/15/sourcing-data-directly-from-us-state-registries/ . API: https://api.opencorporates.com/documentation/API-Reference | Self-serve plans roughly £2,250 to £12,000 per year for 200 to 1,000 calls/day (secondary source; official page 403'd) | No |
| Middesk | Searches all 50 states plus DC; officers; `Document` object returns filing documents retrieved from government sources: https://docs.middesk.com/reference/document ; https://docs.middesk.com/verify-business/registration | Not published | No (fetches its own fresh certificate; does not validate a supplied certificate ID) |
| Cobalt Intelligence | Live scrape of all states; status, filing history, officers vary by state; timestamped screenshots as evidence: https://blog.cobaltintelligence.com/post/secretary-of-state-api-instant-access-to-primary-source-documents | $0.50 to $5.00 per lookup per their guide: https://blog.cobaltintelligence.com/post/best-business-verification-apis-2026 | No |
| Persona | Business Registry Verification and Business Registrations Report: https://help.withpersona.com/articles/4CoTmwLAOugJst2XGScXgb/ | Subscription plus overage | No |
| Enigma | KYB API with `sos_name_verification`: https://documentation.enigma.com/kyb/response/ | Not published | No |
| Dun and Bradstreet Direct+ | Firmographics plus Corporate Linkage: https://directplus.documentation.dnb.com/html/pages/CorporateLinkageAPIs.html | GSA schedule: about $2.95 company search, $19.70 full family tree | No |
| Trulioo, LexisNexis, Sumsub, Socure, Alloy, Baselayer | Marketing pages only; no US SOS field docs found | Negotiated | No |

Bottom line: no aggregator validates a certificate authentication number. That must be done against each state's validator, and only Louisiana exposes it as an API.

### 1c. State certificate-of-good-standing validators (the key finding)

| State | URL | Input on certificate | Constraints |
|---|---|---|---|
| Delaware | https://corp.delaware.gov/authver | Entity file number plus authentication number | 1 year from issuance; certificates since July 2006 |
| Florida | https://services.sunbiz.org/Filings/CertificateOfStatus/CertificateAuthentication | Tracking number printed at bottom | Certificate of Status only |
| Texas | https://sosdirectws.sos.state.tx.us/pdfondemand/CertVerification.aspx | Document number at bottom | Certificates issued on or after Jan 2006 |
| California | https://bizfileonline.sos.ca.gov/verifycertificate | Certificate number | JS single-page app; needs a headless browser |
| Ohio | https://cogs.ohiosos.gov/filecheck.aspx | Validation number | 403 to non-browser clients |
| Nebraska | https://www.nebraska.gov/sos/corp/validation/index.cgi | Verification ID at bottom | Free; 12 months |
| Wyoming | https://wyobiz.wyo.gov/Business/ViewCertificate.aspx | Certificate ID | Returns a validation certificate PDF |
| Iowa | https://sos.iowa.gov/business/cert/ValidateCert.aspx | Certificate ID | |
| Colorado | https://www.coloradosos.gov/biz/CertificateSearchCriteria.do | Confirmation number | Also notary cert validation https://www.sos.state.co.us/notary/pages/public/verifyCert.xhtml ; "altered or page count inaccurate = void" |
| Illinois | https://apps.ilsos.gov/businessentitysearch/authentication.jsp | Authentication number | 1 year |
| Kansas | https://sos.ks.gov/eforms/BusinessEntity/CertifiedValidationSearch.aspx | Certificate number with dash | Confirmed via curl |
| Louisiana | API: `GET https://commercialapi.sos.la.gov/api/Certificate/Validate?Token&EmailAddress&CertificateId` returning `IsValid`, `CertificateDate`, `EntityName`, `EntityNumber`, `ValidationMessage` | Certificate ID | 18 req/min; paid live token |
| Massachusetts | https://corp.sec.state.ma.us/CorpWeb/Certificates/Verify.aspx | Certificate number on e-certificates | https://www.sec.state.ma.us/divisions/corporations/certificates/corporations-electronic-certificates.htm |
| Michigan | https://mibusinessregistry.lara.state.mi.us/verifycertificate | Certificate ID bottom left | Cloudflare human check |
| Virginia | https://cis.scc.virginia.gov/ValidateCertificate/Index | Not confirmed | Cookie-consent gate |
| Indiana | https://bsd.sos.in.gov/validatecertificate | Not confirmed | JS app |
| Nevada | SilverFlume "Verify Good Standing Certificates", portal migrated to orion.nv.gov | ? | Unconfirmed |
| Tennessee | Likely https://tnbear.tn.gov/Ecommerce/CertOfExistenceID.aspx | Verification number | Connection reset; unconfirmed |
| Maryland | Business Express says online certificates can be verified: https://dat.maryland.gov/businesses/Pages/Internet-Certificate-of-Status.aspx | ? | Exact URL not found |
| Connecticut | Verify only when logged into business.ct.gov | | Login required |
| Arizona | New Arizona Business Center (Jan 2026); certificates reportedly carry a QR code | QR | Unconfirmed |
| Not found | GA, PA, NJ, UT, MN, OR, NC, SC, OK, MO, AL, WA, NY (NY does not sell certificates of status online: https://dos.ny.gov/certificate-status) | | Absence in search is not proof of absence |

Design note: every validator returns at most "issued / not issued" plus entity name and date. The system must still compare entity name, number, and date on the uploaded PDF to the validator response and to the live registry record. Most validators expire after 12 months.

## 2. IRS: EIN letters and nonprofits

- No public EIN lookup exists. The IRS discloses EIN information only to the responsible party or an authorized representative. CP 575 is issued once; 147C is the replacement. No verification code appears on either letter.
- TIN Matching (https://www.irs.gov/tax-professionals/taxpayer-identification-number-tin-matching ; Pub 2108A https://www.irs.gov/pub/irs-pdf/p2108.pdf) is only for payers filing certain 1099 forms. Not a general KYB check.
- Format checks only: valid EIN prefix table https://irs.gov/businesses/small-businesses-self-employed/valid-eins ; useful only to reject impossible numbers.
- Vendors advertising "EIN verification" (e.g. https://www.middesk.com/blog/ein-verification-service) do not document their mechanism. Treat EIN letters as unverifiable against the issuer.
- Nonprofits: TEOS https://www.irs.gov/charities-non-profits/tax-exempt-organization-search ; bulk EO BMF by state https://www.irs.gov/charities-non-profits/exempt-organizations-business-master-file-extract-eo-bmf (includes EINs, so EIN to name can be cross-checked for exempt orgs only).

## 3. Federal and other registries

| Registry | Machine-readable? | Details |
|---|---|---|
| SAM.gov Entity Management API | JSON | `https://api.sam.gov/entity-information/v3/entities`; key from api.data.gov; 10 req/day for non-federal users without roles; public fields: legal name, UEI, CAGE, status, addresses, business types, dates, exclusions. https://open.gsa.gov/api/entity-api/ |
| SEC EDGAR | JSON | `data.sec.gov/submissions/CIK##########.json`, companyfacts, bulk zips; no key; 10 req/s and User-Agent required. https://www.sec.gov/search-filings/edgar-application-programming-interfaces ; full-text search https://efts.sec.gov/LATEST/search-index?q=... ; `company_tickers.json` |
| USPTO Open Data Portal | JSON | `api.uspto.gov`; key at https://data.uspto.gov/apis/key-management ; sign-in required from June 2026; patent file wrapper and assignments https://data.uspto.gov/apis/patent-file-wrapper/search |
| PatentsView | JSON | `https://search.patentsview.org/api/v1` with `X-Api-Key` https://search.patentsview.org/docs/ |
| TSDR (trademarks) | JSON / XML / PDF | `tsdrapi.uspto.gov`, header `USPTO-API-KEY`; 60 req/min. https://developer.uspto.gov/api-catalog/tsdr-data-api |
| Trademark Assignment API | XML | https://assignment-api.uspto.gov/documentation-trademark/ |
| FinCEN MSB Registrant Search | Excel download of all registrants, weekly | https://msb.fincen.gov/msbstateselector.php ; mirror https://www.opensanctions.org/datasets/us_fincen_msb/ |
| NMLS Consumer Access | HTML only; ToS forbids automated copying | https://www.nmlsconsumeraccess.org/Home.aspx/TermsOfUse ; vendor API via Comergence |
| DEA | Validation tool requires a DEA registration login | https://apps.deadiversion.usdoj.gov/webforms2/spring/validationLogin |
| FDA | Daily downloadable drug establishment registrations | https://www.fda.gov/drugs/drug-approvals-and-databases/drug-establishments-current-registration-site |
| FCC | JSON License View API | https://www.fcc.gov/reports-research/developers/license-view-api |

## 4. State cannabis license data

| State | Source | Form |
|---|---|---|
| California DCC | https://search.cannabis.ca.gov/ (updated daily) | JS search UI; CSV export from UI; no confirmed bulk endpoint |
| Colorado MED | https://med.colorado.gov/licensee-information-and-lookup-tool/licensed-facilities | Downloadable lists, monthly |
| Washington LCB | https://lcb.wa.gov/records/frequently-requested-lists | XLSX weekly; Socrata datasets on data.wa.gov |
| Oregon OLCC | https://www.oregon.gov/olcc/marijuana/pages/recreational-marijuana-licensee-reports.aspx | Interactive report; some addresses withheld |
| Michigan CRA | https://www.michigan.gov/cra/verify-a-license-1 | Blank search downloads entire database |
| Illinois IDFPR | https://idfpr.illinois.gov/content/dam/soi/en/web/idfpr/forms/cannabis/all-cannabis-licenses.pdf | PDF |
| Massachusetts CCC | https://opendata.mass-cannabis-control.com/ | Socrata (SODA API) |
| Nevada CCB | https://ccb.nv.gov/license-search/ | HTML |
| Arizona ADHS | https://www.azdhs.gov/documents/licensing/medical-marijuana/applications/licensed-marijuana-establishments.pdf | PDF |
| New York OCM | https://data.ny.gov/Economic-Development/Current-OCM-Licenses/jskf-tt3q | Socrata (SODA API) |
| New Jersey CRC | https://nj.gov/cannabis/businesses/permitted/index.shtml | HTML plus permit PDFs |
| Florida OMMU | https://knowthefactsmmj.com/mmtc/ | HTML list |

## 5. Contractor license boards

| Board | Lookup | API / bulk |
|---|---|---|
| California CSLB | https://www.cslb.ca.gov/onlineservices/dataportal/ | Master lists; no API |
| Florida DBPR | https://www2.myfloridalicense.com/construction-industry/public-records/ | Weekly CSV extracts |
| Texas TDLR | https://www.tdlr.texas.gov/LicenseSearch/ | Socrata dataset "TDLR All Licenses" https://data.texas.gov/dataset/TDLR-All-Licenses/7358-krk7 (JSON API) |
| Arizona ROC | https://azroc.my.site.com/AZRoc/s/contractor-search | Salesforce community; no API |

## 6. Notaries and e-signature verification

Commission lookups: NC https://www.sosnc.gov/online_services/Notary_Search/notary_search ; FL https://notaries.dos.state.fl.us/ ; PA https://www.notaries.pa.gov/pages/notarysearch.aspx ; OK https://www.sos.ok.gov/notary/search.aspx ; NY Socrata https://data.ny.gov/Economic-Development/Commissioned-NYS-Notaries-Public/rwbv-mz6z ; NJ https://www.nj.gov/treasury/revenue/notary.shtml ; MO https://s1.sos.mo.gov/business/notary/search/notarysearch.aspx ; TX https://direct.sos.state.tx.us/notaries/notarysearch.asp ; MN https://sos.mn.gov/notary-apostille/notary-help/verify-remote-online-notarization-authorization ; CO https://www.sos.state.co.us/notary/pages/public/verifyCert.xhtml . Not a 50-state inventory.

Paper notarizations have no central registry; only the commission (name, number, expiry, county) and seal format can be confirmed. Remote online notarization (RON) PDFs carry an X.509 notary signature validatable with a PAdES validator; Proof/Notarize has a verification portal requiring Proof ID and PIN: https://support.proof.com/hc/en-us/articles/360058800493-Verifying-the-Authenticity-of-Your-Document

DocuSign: no public envelope-ID lookup. "The Docusign envelope Id is not designed to be accessible by a third party" (https://community.docusign.com/esignature-111/how-can-i-verify-authenticity-of-signed-document-using-envelope-id-23892). Completed PDFs carry a "Signed by DocuSign, Inc." certification seal that can be validated locally.

Adobe Acrobat Sign: public verification page, enter the Transaction ID at https://secure.na1.adobesign.com/verify ; PDFs carry Adobe's tamper-evident seal: https://helpx.adobe.com/sign/using/sign-config-unauthenticated-access-to-audit-report.html

## 7. Corporate affiliation (parent/subsidiary, dealer, franchise)

- GLEIF (free, no key, JSON:API), confirmed live: `https://api.gleif.org/api/v1/lei-records/{LEI}/direct-parent`, `/ultimate-parent`, `/direct-children`, `/direct-parent-relationship` (returns relationship type, status, `corroborationLevel` such as `FULLY_CORROBORATED`, and a `corroborationReference` URL). Search `?filter[entity.legalName]=...`. Docs https://www.gleif.org/en/lei-data/gleif-api . Limitation: only entities with an LEI, mostly financial and large firms.
- SEC Exhibit 21 subsidiary lists: found via full-text search and the submissions API; no SEC-structured dataset. Free parsers: CorpWatch http://api.corpwatch.org/ ; OpenSanctions https://www.opensanctions.org/datasets/us_corpwatch/ ; commercial https://sec-api.io/docs/subsidiary-api . Public companies only.
- Dun and Bradstreet Corporate Linkage (paid).
- OpenCorporates has no reliable US ownership graph; officer overlap is the usable signal.
- Franchise (FDD) registries: NASAA EFD https://www.nasaaefd.org/ ; Minnesota CARDS https://cards.web.commerce.state.mn.us/franchise-registrations ; Wisconsin https://apps.dfi.wi.gov/apps/FranchiseSearch/MainSearch.aspx ; California DFPI (portal migration unconfirmed). FDD Item 20 lists franchisees, the best primary source for franchisee-to-franchisor claims.
- Dealer and affiliate letters: no registry exists. Usable corroboration: SOS officer, registered agent, and address overlap; USPTO trademark ownership (the dealer uses a mark owned by the claimed parent); GLEIF; Exhibit 21; FDD Item 20; SAM.gov immediate and highest owner fields.

## Could not find or confirm
1. Any aggregator that validates a certificate authentication number.
2. Validator input fields for Ohio, California, Virginia, Indiana, Michigan; Nevada after the portal migration; Maryland's exact URL; Tennessee; Arizona QR; validators for GA, PA, NJ, UT, MN, OR, NC, SC, OK, MO, AL, WA, NY.
3. Official OpenCorporates and Cobalt pricing; Sumsub, Socure, Baselayer, Alloy SOS specifics.
4. USPTO ODP official rate limits; GLEIF rate limit.
5. A bulk endpoint for California DCC; Colorado MED file format; Nevada bulk claims; Oregon, CT, HI Socrata dataset IDs.
6. Any verification number or IRS-side check for CP 575 or 147C letters (none appears to exist).
