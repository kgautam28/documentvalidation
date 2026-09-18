# Research appendix 6: Who already does this (competitive landscape)

Compiled 2026-09-18. Items marked unconfirmed come from secondary sources or could not be fetched (several vendor pages returned 403 or 404).

Headline: nobody sells the combined job as a product ("take the advertiser's uploaded document, check it for tampering, resolve it against the correct government registry, and decide affiliation or authorization"). The market splits into (a) manual-analyst certification bureaus that ad platforms and card networks outsource to, (b) KYB data and API vendors that do registry lookups but not document adjudication, (c) document-forensics vendors focused on financial documents, (d) niche license-data aggregators, and (e) AI compliance-agent vendors that are closest in method but sell to banks and fintechs.

## 1. Certification firms that ad platforms outsource to (manual-analyst model)

| Company | What it does | Evidence of success | What it does not do | Sources |
|---|---|---|---|---|
| LegitScript | Certifies pharmacy, telehealth, addiction treatment, CBD merchants; accepted by Google, Meta, Microsoft, Amazon, LinkedIn; Mastercard MMSP and Visa monitoring partner. Applicant uploads licenses; human analysts review; monitoring uses crawling plus an "Xray" AI platform (Mar 2025) with analyst review. | Named in Google's pharmacy policy in about 14 countries. Claims 60M+ merchants in database. Reseller pricing: healthcare about $975 application plus $2,150/yr per site; addiction treatment $1,395 to $1,595 plus $2,550 to $3,095/yr. | Publishes no timelines, error rates, or automation split. Certification, not verification-as-API; regulated verticals only. Criticised for pricing and opacity; PharmacyChecker antitrust suit survived summary judgment (Jan 2023). | https://support.google.com/adspolicy/answer/176031 ; https://www.legitscript.com/mmsp/ ; https://en.wikipedia.org/wiki/LegitScript ; https://www.rocketdigitalhealth.com/insights/what-legitscript-actually-is-and-isnt |
| G2 Risk Solutions | Google's mandated verifier for financial-services advertisers (India, Germany, and from July 23, 2026 24 EEA markets). Advertiser submits regulator license number and proof; G2 issues a code. Also merchant-risk monitoring for acquirers; Mastercard Brighterion AI partnership (Mar 2024). | Named by Google policy as the sole channel for those categories. | Publishes nothing on method, SLAs, or accuracy. A regulator-license lookup for one vertical. A remediation-consultant cottage industry exists, evidence of friction. | https://support.google.com/adspolicy/answer/17127726 ; https://g2risksolutions.com/financial-services/ |
| NABP | .pharmacy accreditation, accepted by Google for US and Canada. | Regulator-affiliated credibility. | Pharmacy only; manual; not an API. | https://support.google.com/adspolicy/answer/176031 |
| Evident ID | Google Local Services Ads: photo-ID upload and background-check intake. | Named in Google's LSA pages. | Google says it verifies licenses itself "to the extent practical"; Evident is intake, not the license adjudicator. | https://support.google.com/localservices/answer/6230381 ; https://evidentidsupport.zendesk.com/hc/en-us/articles/4403457817367 |

What they publish about method and error rates: nothing quantitative.

## 2. KYB platforms (registry data, not document adjudication)

| Company | What it does | Evidence | What it does not do | Sources |
|---|---|---|---|---|
| Middesk | US business identity API over "400+ government sources"; now sells AI agents that pull data, cross-reference, and document findings. | $77M raised; claims 7M businesses verified per year, 500+ customers including Shopify and Toast, Mercury, Brex, Ramp, Plaid. | Registry resolution, not adjudication of uploaded documents; no ad-platform customer named; match rates not published. | https://www.middesk.com/ ; https://www.insightpartners.com/ideas/leading-business-identity-platform-middesk-raises-57m-series-b-co-led-by-insight-partners-and-canapi-ventures/ |
| Cobalt Intelligence | Secretary of State API, all states, marketed as real-time. | No funding or named customers found; docs 403'd. | SOS only. | https://cobaltintelligence.com/secretary-of-state-business-search |
| Baselayer | Live SOS plus IRS EIN verification; fraud consortium. | Customers Oatfi, Fundbox; claims "60% more legitimate businesses identified vs competitors" (self-reported). | No document adjudication. | https://baselayer.com/solutions/business-identity-solutions/ |
| Enigma | KYB API blending SOS, TIN, card-transaction revenue, licenses, watchlists. | Customers Ramp, Findigs, Alloy, Capital One, Faire, Chase. Publishes production metrics: 92% match rate with person name, about 1.5s median; Ramp 94% match on 4,000 applications. | Data and match product, not document review. | https://www.enigma.com/solutions/onboarding-and-kyb/ |
| Persona | KYC plus KYB workflows. | $200M Series D at $2B (Apr 2025); customers OpenAI, Etsy, DoorDash, LinkedIn, Reddit, Square, Brex. | Marketplace customers use it for individual identity; no evidence of business-document or license verification use. | https://www.prnewswire.com/news-releases/persona-raises-200m-at-2b-valuation-to-build-the-verified-identity-layer-for-an-agentic-ai-world-302442649.html |
| Sumsub | KYB with automated AI reading of corporate documents plus a manual review service (about 15h turnaround); from $1.35 per verification. | Claims 15s automatic checks, 97% pass rate for combined flows. | Human-in-loop for corporate documents; no ad-platform customer; no independent evaluation. | https://sumsub.com/kyb/ |
| Trulioo | Global business verification with downloadable filings. | No customers named on product page. | Retrieval, not adjudication. | https://www.trulioo.com/product/business-verification |

## 3. Document fraud detection vendors

| Company | What it does | Evidence | What it does not do | Sources |
|---|---|---|---|---|
| Resistant AI | Document forensics (tamper and generation detection on "any document"); MVSI merchant-onboarding partnership (Dec 2025). | $25M Series B (Oct 2025), about $55M total; "150M+ documents verified"; breakeven Sep 2025; customers Dun and Bradstreet, Payoneer, AXA, PennyMac. | No registry lookup or content verification; no independent accuracy evaluation. | https://tech.eu/2025/10/13/resistant-ai-raises-25m-series-b-to-fortify-fintechs-and-ai-agents-against-financial-crime/ |
| Inscribe | "Agentic AI" for document fraud in financial services: bank statements, pay stubs, invoices. | Customers Bluevine, Plaid, Ramp, Mercari, Navan. No acquisition or exit news found for 2025 to 2026. | No formation docs, licenses, or permits. | https://www.inscribe.ai/why-inscribe |
| Ocrolus | Data capture and fraud signals on bank statements, pay stubs, tax docs. | Customers Enova, PayPal, SoFi, Square; "99+% accuracy" self-reported. | No business registration or license docs. | https://www.ocrolus.com/ |

Independent evaluations: none found for business-document fraud detection. NIST and iBeta benchmarks exist only for face and ID liveness.

## 4. Primary-source license verification (proof the registry-lookup model scales in one vertical)

| Company | What it does | Evidence | Limitation | Sources |
|---|---|---|---|---|
| Verifiable | Healthcare provider credentialing; connects "directly to the source via API whenever possible, eliminating errors caused by screen-scraping bots." | "6M+ verifications/month," 300+ license sources, ">97% verification success." | Healthcare professionals only; "whenever possible" implies scraping fallback. | https://verifiable.com/primary-source-verification |
| CAQH | Credentialing utility monitoring "500+ sources." | Industry utility. | Healthcare only. | https://www.relias.com/blog/caqh-primary-source-verification-and-more |
| Certemy, Medallion, symplr | Credentialing platforms. | Not deeply verified. | Same vertical. | https://certemy.com/solutions/primary-source-verification/ |
| Checkr | Professional license verification add-on. | Product page 404'd. | Individual licenses. | https://checkr.com/ |

## 5. Cannabis and gambling license data

| Company | What it does | Evidence | Limitation | Sources |
|---|---|---|---|---|
| Cannabiz Media | License database (60K+ cannabis, 43K+ hemp); Compliance Verification API returning status by state ID. | API customers Leaf Trade (marketplace buyer and seller verification), Shield Compliance. | Collection method not disclosed; primarily a sales CRM. | https://www.cannabiz.media/blog/cannabiz-media-launches-cannabis-and-hemp-business-verification-api |
| Simplifya Verified | 90K+ license records; in-house team manually collects from web pages, PDFs, spreadsheets, and open-records requests; about half the database changes weekly. | Honest about manual collection. | Not real time; no document adjudication. | https://www.simplifya.com/simplifya-verified/ |
| Metrc | State track-and-trace; no unified public licensee list. | | Not a verification vendor. | https://en.wikipedia.org/wiki/Marijuana_Enforcement_Tracking_Reporting_Compliance |
| GeoComply, GLI | Geolocation compliance; equipment certification. | Dominant in their niches. | Neither verifies operator licenses. | https://gaminglabs.com/services/ |

No gambling-license verification data vendor was found.

## 6. Ad impersonation and brand-abuse monitoring (detect after the fact, not verify)

| Company | What it does | Evidence | Limitation | Sources |
|---|---|---|---|---|
| Doppel | Threat graph across social, paid ads, domains; automated takedowns; claims brands surface only about 9% of confirmed fakes. | Customers ARK Invest, REA Group. | Detects impersonation on the open web; no document or authorization verification. | https://www.a16z.news/p/faking-a-brand-is-easy |
| Marcode, BrandVerity | Paid-search brand-bidding and affiliate compliance. | Marcode from $850/mo; BrandVerity acquired by Partnerize (2020). | Search ads only. | https://www.marcode.ai/brandverity-alternative |
| Red Points, MarqVision | Marketplace counterfeit and impersonation enforcement. | MarqVision "$90M+ raised." | Not paid-ad document verification. | https://www.marqvision.com/about |
| Memcyco, Bolster, Netcraft | Website spoofing and phishing takedown. | Memcyco $37M Series A (Jan 2026). | Not documents. | https://tracxn.com/d/companies/memcyco/__9Y8hGTtI3w458qhTKpdrocGdO_FF70sJhGq8YcCVK60 |

## 7. AI-agent startups closest in method (sell to banks, not trust and safety)

| Company | What it does | Evidence | Limitation | Sources |
|---|---|---|---|---|
| Parcha | Compliance AI agents; KYB agent claims "validation in under 20 seconds, visual verification of incorporation docs across all 50 US states," SOS records, proof of address; Alloy integration. | $6.75M raised; customers Airwallex, Pipe, Flutterwave, Brex; claims 45 min to under 3 min per case and "99%+ accuracy" (self-reported). | Fintech customers only; small. | https://blog.parcha.ai/the-audit-log-q2-2025/ |
| Bretton AI (formerly Greenlite) | AI agents for KYC and KYB review; Middesk and Alloy integrations; "70% manual review reduction via AI document analysis." | $75M Series B (Feb 2026); customers Robinhood, Mercury, Gusto, Ramp, Betterment. | Regulated FIs only. | https://www.amlintelligence.com/2026/02/latest-bretton-ai-raises-75m-for-compliance-platform-rebrands-from-greenlite-ai/ |
| Sardine | KYC and KYB agents (Feb 2025): automated resolution for over 50% of onboarding cases. | Unnamed customer. | KYC-centric. | https://www.sardine.ai/blog/kyc-agent |
| Unit21, Oscilar | Agentic triage, EDD, UBO mapping. | | Bank AML focus. | https://www.zyphe.com/resources/blog/ai-compliance-agents |

No startup was found that pitches "AI agent that verifies advertiser or merchant documents against government sources" for ad platforms or marketplaces.

## 8. Platforms' internal approaches
No engineering post from Google, Meta, Amazon, Shopify, Stripe, Airbnb, or Uber on automating business-document or advertiser verification was found. Google's policy pages outsource regulated verticals (LegitScript, NABP, G2RS, Evident plus D and B) and say Google checks LSA licenses "to the extent practical" (https://support.google.com/localservices/answer/6230381).

## Synthesis
1. The end-to-end job is unowned. Certification bureaus do it with humans for a few verticals; KYB vendors give data, not a decision on an uploaded document; forensics vendors say "tampered or not" on financial documents; nobody verifies affiliation or authorization letters at all.
2. Coverage is vertical-locked. Registry lookup at scale is proven in healthcare (Verifiable, CAQH) and cannabis (Simplifya, by hand). No gambling-license vendor; no general business-license layer.
3. The AI-agent wave sells to banks. Parcha, Bretton, Sardine, Middesk agents, and Sumsub are methodologically closest but target AML-mandated FIs. Middesk (Shopify, Toast), Enigma (Faire), and Inscribe (Mercari) show marketplaces buy pieces, but no vendor names an ad platform.
4. No independent evaluation exists anywhere. Every accuracy figure is self-reported; incumbents report nothing.
5. Incumbent weaknesses are structural: per-merchant fee models, opacity, single-vertical manual programs.

## Could not confirm
- Funding for Doppel, Bolster, Red Points, Netcraft, MarqVision beyond "$90M+".
- Any Inscribe acquisition or exit in 2025 to 2026.
- Cobalt Intelligence's retrieval method.
- Whether Pinkerton is still a Google LSA vendor.
- Checkr's license-verification method.
- Meta's own financial-services advertiser verification process.
