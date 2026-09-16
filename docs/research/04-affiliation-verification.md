# Research appendix 4: Verifying affiliation claims (dealer, installer, reseller, franchisee, subsidiary, licensee)

Compiled 2026-09-16 from published sources and direct probes of GLEIF, SEC EDGAR, RDAP, Wikidata, and about 20 manufacturer and franchise locator pages. Secondary sources (seller-consultant blogs, Apify listings) are labeled.

Core finding: every large platform that accepts "letter of authorization" (LOA) PDFs treats the document as a claim, not proof. Amazon "may try to validate your LOA by contacting the rights owner"; Walmart designed its reseller program so the brand, not Walmart, approves the reseller; Google Ads tells partners to "ask [the brand] to mention you on their website." The document is a pointer to an out-of-band check, and the out-of-band check should use contact channels discovered independently of the document, the same principle as FBI business email compromise guidance: call "previously known numbers, not the numbers provided in the e-mail request" (https://www.fbi.gov/news/stories/business-e-mail-compromise-on-the-rise).

## 1. How marketplaces and app stores verify "authorized reseller" today

### Amazon
- LOA elements per a consultant summary (Amazon's own page could not be fetched): licensor, licensee (must match the Seller Central legal entity exactly), grant and scope, geographic scope, term with dates. Accepted formats: signed PDF or scan, digital signature, company stamp, or an email from the brand's official domain. Common rejections: "signer lacks apparent corporate authority or uses free email domains"; licensee name does not match the account. Amazon "may try to validate your LOA by contacting the rights owner you name". https://amazonsellersappeal.com/amazon-letter-of-authorization-valid-requirements/
- Amazon community manager: reseller LOAs are handled by "Automated Brand Protection"; Amazon "may contact you [the brand] directly to verify if specific sellers are authorized". https://sellercentral.amazon.com/seller-forums/discussions/t/1dde62d5-e614-411d-8465-8428646a1dc2
- Not accepted as an LOA: invoices, distribution-rights or reseller agreements, receipts, purchase orders (secondary): https://brandsbro.com/how-to-get-brand-approval-on-amazon/
- An email screenshot is accepted "but the email must be sent from a brand domain": https://sellercentral.amazon.com/seller-forums/discussions/t/483cf7f0-4981-4017-bd55-cef6747fff94

What has failed at Amazon (forum evidence):
- LOA-as-a-service scam: a wholesaler charged a seller over $2,700 for a "manufacturer LOA" and vanished. https://sellercentral.amazon.com/seller-forums/discussions/t/14893b2b-2b7a-40e1-bed3-b5c04b0d7b7a
- Amazon's forgery notice text: "You have provided documents that appear to have been forged or manipulated to Amazon." Nobody discloses how manipulation was detected; the community view is that Amazon cross-checks supply chain against brand whitelists rather than document forensics. https://sellercentral.amazon.com/seller-forums/discussions/t/0d42948b-63b7-4a14-8aae-fe50fedacd70
- Distributor letters are rejected because the supplier being authorized is not the seller being authorized: https://sellercentral.amazon.com/seller-forums/discussions/t/2a510d40-c55e-4781-954b-3a35d1f2dd5b
- Off-platform LOA generators exist ("Create your LOA in minutes"), which shows how cheap a plausible letterhead PDF is: https://fivestarcommerce.com/amazon-letter-of-authorization-instant-generator/

### Walmart Marketplace (Brand Portal)
Brand registers with a live USPTO registration. A seller uploads "a letter of authorization or other evidence of their relationship to the brand"; the brand reviews and approves or denies. Out-of-band confirmation by construction. https://marketplacelearn.walmart.com/guides/Brand%20Portal/Getting%20started/brand-portal-overview ; https://marketplacelearn.walmart.com/guides/brand-manager-manage-brand-privileges

### eBay (VeRO)
A takedown program for rights owners; eBay does not pre-verify "authorized dealer" claims. https://www.ebay.com/help/policies/listing-policies/selling-policies/intellectual-property-vero-program?id=4349

### App stores
Apple guideline 5.2.1 and 5.2.2: "Authorization must be provided upon request"; standard advice for agencies is to be added to the client's developer team, so the brand acts rather than a letter. https://developer.apple.com/app-store/review/guidelines/ . Google Play Impersonation policy has no published documentation standard. https://support.google.com/googleplay/android-developer/answer/9888374?hl=en

### Banks
No bank-specific "authorized reseller" practice found. The transferable control is callback verification: https://www.ic3.gov/CrimeInfo/BEC ; https://www.jpmorgan.com/insights/cybersecurity/business-email-compromise/when-callbacks-go-wrong

## 2. Out-of-band confirmation, programmatically

### 2a. Manufacturer dealer, installer, and certification locators (probed 2026-09-16)
Caveats: locators are lead-gen tools, show trade names not legal entities, often lag real status, and many sit behind bot protection. None publishes a documented public API. Appendix 1 found working JSON endpoints for Owens Corning, CertainTeed (Algolia), and Lennox by inspecting the page JavaScript bundles; this probe did not find them in the raw HTML, which is consistent: they are undocumented, discovered by bundle inspection, and fragile.

| Brand / program | URL | Probe result |
|---|---|---|
| GAF | https://www.gaf.com/en-us/roofing-contractors | 403 (Akamai) even with browser UA; browser automation needed |
| Owens Corning | https://www.owenscorning.com/en-us/roofing/contractors | 200, JS app (JSON endpoint found separately, see appendix 1) |
| CertainTeed | https://www.certainteed.com/find-a-pro | 200, JS (Algolia index found separately, see appendix 1) |
| Tesla Certified Installer | https://www.tesla.com/support/certified-installers | 403 |
| Enphase Installer Network | https://enphase.com/installer-locator | 200, JS; only trained and certified installers appear per https://enphase.com/homeowners/enphase-installer-network |
| SolarEdge | https://www.solaredge.com/us/installer-locator | 403 |
| SunPower, Qcells | find-a-dealer pages | 404 |
| Carrier | https://www.carrier.com/us/en/residential/find-a-dealer/ | 200, JS; third-party scraper https://apify.com/spry_frame/carrier-dealer-scraper/api |
| Lennox | https://www.lennox.com/residential/locate/ | 200; server-rendered directory pages `/residential/locate/dealer-list`, `/dealer-state`, `/dealer-detail` |
| Trane Comfort Specialist | https://www.trane.com/residential/en/dealer-locator/ | 200; scraper claims JSON with `dealerType` https://apify.com/spry_frame/trane-dealer-scraper |
| Generac | https://www.generac.com/dealer-locator/ | 200, JS |
| Mitsubishi Diamond Contractor | https://www.mitsubishicomfort.com/find-a-contractor | Redirects to a lead form, not a lookup |
| Daikin Comfort Pro | https://daikincomfort.com/find-a-dealer | 200, JS |
| Rheem Pro | https://www.rheem.com/find-a-pro/ | reCAPTCHA-gated |
| Toyota dealers | https://www.toyota.com/dealers/ | 200; undocumented JSON hosts referenced |
| Ford dealers | https://www.ford.com/dealerships/ | HTTP/2 error, likely bot filter |
| Aggregator | https://apify.com/jungle_synthesizer/hvac-manufacturer-dealer-locator-aggregator-scraper/api | Commercial; ToS risk |

Auto: state dealer licensing is a real registry (e.g. TxDMV https://texasdmv.my.salesforce-sites.com/dealers). A state dealer license proves "licensed dealer", not "franchised by Brand X".

### 2b. Confirming via the brand's real domain
- RDAP is the structured successor to WHOIS. Probe: `https://rdap.org/domain/gaf.com` returned registration 1996-11-11, registrar CSC Corporate Domains. IANA bootstrap (https://data.iana.org/rdap/dns.json) covers 1,202 TLDs. https://www.arin.net/resources/registry/whois/rdap/
- Signals on the letterhead or sender domain: RDAP creation date (young domain is a red flag), registrar type (corporate registrars like CSC and MarkMonitor are typical for large brands), MX presence, SPF and DMARC records, and whether it matches the brand's canonical domain from Wikidata P856.
- Lookalike detection: dnstwist generates homoglyph, typo, TLD, and hyphenation permutations and checks DNS. Python API `dnstwist.run(domain=..., registered=True, format='null')`. https://github.com/elceef/dnstwist

### 2c. Is the signer a real employee with authority?
- LinkedIn has no public API for this.
- Public companies: Section 16 officers file Forms 3/4/5; DEF 14A proxies list executive officers. EDGAR submissions API `https://data.sec.gov/submissions/CIK##########.json` and full-text search `https://efts.sec.gov/LATEST/search-index?q=...`; 10 req/s and a User-Agent required: https://www.sec.gov/os/accessing-edgar-data . Only about 5 to 10 named officers per company; a regional dealer-program manager will not appear.
- State SOS records: roughly 35 states show officer names in free search (FL, TX, GA, KS, OH, OR, NC); CA, DE, NY, PA, WY do not or only partially. https://www.globaldatabase.com/secretary-of-state-business-search-free-state-by-state-guide-to-official-registries
- Commercial person enrichment (People Data Labs) is probabilistic, not authoritative: https://docs.peopledatalabs.com/docs/person-enrichment-api . Consent-based employment verification (Checkr, Truework) requires the individual's consent.
- Strongest practical check: send a challenge to the signer's address at the brand's independently resolved domain, or a callback per 2d.

### 2d. Phone verification
Call a number from the brand's official site, never the number printed on the letter. https://www.fbi.gov/how-we-can-help-you/scams-and-safety/common-frauds-and-scams/business-email-compromise

## 3. Franchise verification
- FTC Franchise Rule, 16 CFR 436.5(t): Item 20 discloses names, addresses, and phone numbers of all current franchisees. https://www.law.cornell.edu/cfr/text/16/436.5 ; https://www.ftc.gov/business-guidance/resources/amended-franchise-rule-faqs . The FDD Item 20 exhibit is the only systematic franchisor-attested list of franchisees.
- Registration-state lookups: California DFPI DOCQNET https://docqnet.dfpi.ca.gov/search/ (403 to curl); Minnesota CARDS https://cards.web.commerce.state.mn.us/franchise-registrations (403 to curl); Wisconsin https://apps.dfi.wi.gov/apps/FranchiseSearch/MainSearch.aspx (200); Indiana https://securities.sos.in.gov/public-portfolio-search/ (200, 2019+); Virginia https://scc.virginia.gov/regsearches/ ; Washington has no online search (https://dfi.wa.gov/franchises/franchises); New York AG has no online search; Illinois and Maryland not found.
- None of these registries indexes franchisees; names appear only inside the FDD PDF's Item 20 exhibit.
- No franchisor locator discloses the franchisee's legal entity; locators prove the outlet exists, not who owns it.

## 4. Parent and subsidiary proof

### GLEIF (probed)
- Base `https://api.gleif.org/api/v1`, no auth, 60 requests per minute per user (https://api.gleif.org/docs). Relationship links: `/lei-records/{lei}/direct-parent`, `/ultimate-parent`, `/direct-children`, `/ultimate-children`, and reporting-exception endpoints. Name lookup: `/lei-records?filter[entity.legalName]=...` and `/fuzzycompletions?field=entity.legalName&q=...`.
- Example: Carrier Global Corporation, LEI 549300JE3W6CWY2NAN77, has 126 ultimate children in GLEIF.
- Coverage: about 360,714 US records (golden copy 2026-09-16). LEIs concentrate in financial-market participants and large corporates; a small US dealer or subsidiary usually has none. Relationship data is self-reported on an accounting-consolidation basis. https://www.gleif.org/en/newsroom/blog/the-lei-in-numbers-active-lei-population-surpasses-3-million-in-q1-2026

### SEC EDGAR Exhibit 21 (probed)
- Regulation S-K Item 601(b)(21): may omit subsidiaries that in aggregate are not significant, so absence from Exhibit 21 is not proof of non-affiliation. https://corpgov.law.harvard.edu/2019/04/23/disclosure-simplification-round-two-a-deep-dive-into-secs-new-amendments/
- Fetch path: `https://efts.sec.gov/LATEST/search-index?q="<name>"&forms=10-K` returns hits with `file_type` `EX-21`; or `https://data.sec.gov/submissions/CIK##########.json` to the latest 10-K accession to `https://www.sec.gov/Archives/edgar/data/<cik>/<accession>/index.json`. The exhibit is HTML. OSS: https://github.com/wolfgang-aura/edgartools ; commercial https://sec-api.io/docs/subsidiary-api
- Wikidata carries P749 (parent organization), P856 (official website), P1278 (LEI). GAF (Q5512817) has P856 gaf.com and P749 but no LEI.

### OpenCorporates
API key required; default 200 requests per month and 50 per day; free keys only for public-benefit use. https://api.opencorporates.com/documentation/API-Reference

### State SOS shared officers, agent, address
Corroborative only. Registered agents are usually commercial services shared by unrelated companies, and virtual-office addresses are common, so shared agent or address is a very weak signal; shared named officers is moderately useful.

## 5. Letterhead and brand impersonation detection
- Canonical brand facts: Wikidata P856 official website (free), Google Knowledge Graph Search API (returns `url` but Google says it is "not suitable for use as a production-critical service": https://developers.google.com/knowledge-graph), and the brand site's own schema.org `Organization` markup and footer.
- Domain checks: RDAP creation date plus registrar; dnstwist permutations against the canonical domain.
- Post-signing edits: pyHanko's difference analysis rejects unjustified incremental updates by default, with the caveat that "correctly adjudicating incremental updates is inherently somewhat risky and ill-defined". https://docs.pyhanko.eu/en/latest/lib-guide/validation/diff-analysis.html
- Not found: any published, validated method for logo matching on letterheads.

## 6. Legal and policy meaning of "authorized dealer"
- First-sale doctrine: resale of genuine goods is lawful without the mark owner's consent, but the doctrine "does not protect resellers who use trademarks in a way that falsely implies they are authorized or favored dealers". https://www.grsm.com/insight/first-sale-doctrine-limitations-key-trademark-law-considerations-for-businesses/ . Design consequence: "we sell Brand X" needs no authorization; "we are an authorized or certified Brand X dealer" is a factual affiliation claim.
- Lanham Act 43(a)(1)(A): liability for representations likely to confuse as to "affiliation, connection, or association". https://sierraiplaw.com/false-designation-of-origin/
- FTC Impersonation Rule, 16 CFR 461.3 (effective April 2024): unlawful to "materially misrepresent, directly or by implication, affiliation with" a business, with civil penalties. https://www.law.cornell.edu/cfr/text/16/461.3
- Google Ads: Misrepresentation policy bars misleading statements about "identity, affiliations, or qualifications" https://support.google.com/adspolicy/answer/6020955?hl=en ; Misleading representation: "Implying affiliation with or endorsement by another organization, brand ... without their knowledge or consent" https://support.google.com/adspolicy/answer/15936666?hl=en ; Unacceptable business practices: "If you're an official or authorized partner of another brand, ask them to mention you on their website"; evidence for appeals is "contracts, written agreements, a link to a credible news article ... and any public statements (like a social media post) from the brand" https://support.google.com/adspolicy/answer/15938071?hl=en

## 7. Signature and e-signature verification
- DocuSign: the Certificate of Completion records envelope ID, signer names and emails, IP addresses, timestamps; completed PDFs carry a "Signed by Docusign, Inc." seal verifiable in Acrobat. The envelope ID is not independently verifiable by a third party. Seal CA changed from Entrust to DigiCert from June 2025. https://community.docusign.com/esignature-111/how-can-i-verify-authenticity-of-signed-document-using-envelope-id-23892 ; https://www.docusign.com/trust/alerts/update-new-entrust-certificate-published
- Adobe Acrobat Sign: public verifier at https://secure.na1.adobesign.com/verify with the transaction ID.
- Open tools: `pyhanko sign validate --pretty-print doc.pdf` checks integrity, chain, timestamps, post-signature modifications (https://docs.pyhanko.eu/en/latest/cli-guide/validation.html); `pdfsig` from poppler prints signer, time, and whether the whole document is covered (https://manpages.debian.org/bookworm/poppler-utils/pdfsig.1.en.html).
- Key limitation: a DocuSign or Adobe seal proves the platform processed a signature ceremony; it does not prove the signer's email belonged to Brand X. The signer email domain is the useful field.
- No data on how dealer agreements are signed. Expect a large share of uploaded "agreements" to be flattened scans with no verifiable signature.

## 8. Design implications
1. Treat any uploaded PDF as a claim; score it (letterhead domain resolvable, signer email on brand domain, seal present and chain-valid, PDF unmodified after signing) but never approve on it alone.
2. Resolve the brand's canonical domain and phone independently, then verify any domain on the letter: RDAP age and registrar, dnstwist distance, MX/SPF/DMARC.
3. Out-of-band ladder: (a) presence on the brand locator or certification page; (b) email challenge to the signer at the canonical domain or the brand's partner-program address; (c) callback to a number from the brand's site; (d) a page on the brand's domain naming the advertiser, which is Google's own advice and the strongest cheap evidence.
4. Franchisees: pull the franchisor's FDD Item 20 from CA, MN, WI, or IN and match the advertiser's legal name, address, and phone.
5. Subsidiaries: GLEIF ultimate children plus SEC Exhibit 21 plus SOS officer overlap; absence is not disproof.
6. Policy line: a bare "we sell Brand X" claim needs no authorization; "authorized, certified, official" is an affiliation claim.

## 9. Could not find or confirm
- Amazon's own help text on LOA requirements; how Amazon detects "forged or manipulated" documents.
- Any documented public JSON API for GAF, Tesla, Enphase, SolarEdge, Carrier, Trane, Generac locators.
- Online franchise registries for Illinois and Maryland; Virginia's FDD download scope.
- GLEIF breakdown of reporting exceptions versus actual parent links.
- Any franchisor locator that discloses franchisee legal-entity names.
- Statistics on e-signed versus wet-signed dealer agreements.
- Meta and TikTok brand-authorization-letter requirements.
- A validated technique for letterhead logo matching.
