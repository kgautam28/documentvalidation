# Research appendix 1: Google Ads verification policy, fraud patterns, and dealer lookups (US)

Compiled 2026-09-16 from primary sources (Google policy pages, platform reports, press, and live inspection of manufacturer locator sites). Every claim carries a URL. Items that could not be confirmed are listed at the end.

## 1. Google Ads Advertiser Verification: accepted documents (US)

### Identity verification documents
Source: https://support.google.com/adspolicy/answer/9872280?hl=en&co=GENIE.CountryCode%3DUS

Organizations (one registration document showing legal name):
- Any document, notice, or letter issued or stamped by the IRS showing the organization name (examples: CP575, 147C, CP299, 988, 937, 1050, 5822).
- IRS forms only if a copy of the form is available on the IRS website (e.g. Forms 8871, 990).
- Certificate of Business Incorporation issued by the state where the business operates.
- Most recent SEC filing (10-K, 10-Q, 8-K).
- Business credit report from Experian, Equifax, or TransUnion.
- Official letter from a government agency on letterhead (for government/public agencies).
- Details must match the payments profile exactly.

Individuals / authorized representatives: US government photo ID (passport, state ID, driver's license, green card). Must be in color, clear, not a photocopy or screenshot.

Task types (https://support.google.com/adspolicy/answer/15577076?hl=en): organization questions, business operations questions, individual tasks (photo ID, phone code, SSN for US, video selfie with ID), organization tasks (D-U-N-S optional, documents, affiliation confirmation via SMS or organization email), agency tasks, billing tasks, industry tasks (gambling, healthcare, finance, elections).

D-U-N-S is optional. Google: "We can use your D-U-N-S number to confirm the information that you provide" (https://support.google.com/adspolicy/answer/13650402?hl=en).

Timelines (https://support.google.com/adspolicy/answer/15588490?hl=en): up to 5 business days, rarely up to 30 days. Agencies report decisions "within minutes" for common docs (https://www.oyova.com/blog/google-ads-verification-requirements/), consistent with an automated first pass, though Google does not say so.

Triggers and consequences (https://support.google.com/adspolicy/answer/9703665?hl=en): selection when behavior or ad content is "potentially suspicious", brand-related query ads, financial services, suspension appeals. False info is a Circumventing Systems violation. Google "uses its best efforts to review and verify the provided info"; no methodology stated.

### Business Operations Verification (BOV): the reseller/affiliate/dealer path
Source: https://support.google.com/adspolicy/answer/11938893

- Documents requested: business/governmental registrations; licenses for regulated verticals (healthcare, car rental, finance); government photo ID; proof-of-address docs issued within the last 90 days.
- Relationship evidence: "Documentation establishing proof of relationship with other brands or parties involved, such as an official agreement or contract" and "A document explaining the business relationship or brand owner on their company letterhead".
- Resellers/affiliates: provide details of the business delivering goods and services to the end customer, plus proof of relationship. Must identify agencies accessing the account, end service provider, and domain owner if different.
- Common failure: legal name mismatch including suffixes and punctuation; address mismatch.
- Formats: PDF, JPG, JPEG, PNG. "Screenshots and digital IDs: These are generally not accepted."

Design implication: the "letter on the brand owner's letterhead" is exactly the artifact most easily fabricated with generative AI, and Google gives no public detail on how it validates it.

### Trademark / "authorized reseller" in ad copy
Sources: https://support.google.com/adspolicy/answer/6118?hl=en ; https://support.google.com/adspolicy/answer/2562645?hl=en-GB

Trademark owners can file a 3rd-Party Authorization Request naming resellers. But authorization "isn't necessary in most scenarios": the Reseller and informational site policy allows trademark use if the landing page is primarily dedicated to selling the trademarked products with price info. Google largely checks page content, not dealer authorization.

### Third-party consumer technical support
Source: https://support.google.com/adspolicy/answer/13527027?hl=en

Third-party consumer tech support ads are not allowed. No current certification pathway for "authorized service providers" (the 2018 program at https://support.google.com/adspolicy/answer/9479396?hl=en is not referenced as active).

### Restricted categories (US)

| Category | Requirement | Source |
|---|---|---|
| Crypto exchanges and software wallets | Certification; advertiser registered with FinCEN as an MSB and with a state as a money transmitter, or a federal/state chartered bank. Hardware wallets need certification, no FinCEN. Prohibited: ICOs, DeFi protocols, crypto loans, unhosted wallets, trading signals. No public statement of what documents are uploaded. | https://support.google.com/adspolicy/answer/14009787?hl=en ; https://www.coindesk.com/markets/2021/06/02/google-will-only-take-ads-from-fincen-registered-or-chartered-crypto-exchanges-wallets |
| Financial services verification (G2) | US not in scope as of the April 2026 (Malaysia) and June 2026 (24 EEA markets) expansions. Where in scope, external partner G2 Risk Solutions collects service type, license status, registration number; resellers/brokers/affiliates of a licensed entity are not eligible. | https://support.google.com/adspolicy/answer/16888296?hl=en ; https://support.google.com/adspolicy/answer/17127726?hl=en ; https://g2risksolutions.com/financial-services/ |
| Debt services | US: only approved non-profit credit counseling agencies under 11 U.S.C. § 111. Credit repair banned. | https://support.google.com/adspolicy/answer/15189135?hl=en ; https://support.google.com/adspolicy/answer/2464998?hl=en |
| Gambling | Must be licensed by the state entity where legal; lotteries state-run only; DFS licensed in at least one state. | https://support.google.com/adspolicy/answer/6018017?hl=en |
| Pharmacies / telehealth | LegitScript or NABP certification plus Google healthcare certification. | https://support.google.com/adspolicy/answer/176031?hl=en |
| Addiction treatment | LegitScript addiction-services certification. | same |
| CBD / cannabis | US: only topical hemp-derived CBD at or below 0.3% THC, LegitScript-certified (product plus website), plus Google CBD Ads Certification form. No US allowance for dispensaries or hemp-derived THC; the cannabis pilot is Canada-only (Aug 2025 to Dec 2026). LegitScript lookup: https://www.legitscript.com/certification/website-certification-status/ (JS app, no API). | https://support.google.com/adspolicy/answer/16489299?hl=en ; https://support.google.com/adspolicy/answer/16430457?hl=en ; https://www.legitscript.com/google-cbd/ |

Implication for scope: a US "cannabis license" uploaded to Google Ads is, under current policy, not a path to approval at all. Any such upload is itself a signal.

### Local Services Ads (the only Google product that validates trade licenses)
Google states it "validates these licenses against the state or country databases"; insurance via certificate of insurance; background checks via partners (Pinkerton, then Evident ID per third parties). 3 to 4 weeks average. https://support.google.com/localservices/answer/6226575?hl=en ; https://support.google.com/localservices/answer/12174778?hl=en&co=GENIE.CountryCode%3DUS ; https://blusharkdigital.com/blog/local-service-ads-how-are-background-checks-changing/

## 2. Documented fraud and abuse patterns

Verified-but-impersonating advertisers (the core gap). Which? (Oct 2025): scam "Three UK" click-to-call ads ran from Google-verified accounts. Marcode co-founder Andy Cooney: "Google's verification only proves the account buying the ads is a real company. It doesn't prove they are associated with the brand they are pretending to be." https://www.which.co.uk/news/article/scammers-are-hiding-behind-googles-click-to-call-ads-aTnZB9C2aMjh . Verified-advertiser impersonation of Google Authenticator: https://www.malwarebytes.com/blog/news/2024/07/threat-actor-impersonates-google-via-fake-ad-for-authenticator ; https://cybernews.com/security/scammers-bypassing-google-impersonate-brands/

Hijacked verified accounts as the bypass instead of forged docs. Malwarebytes "great Google Ads heist" (Jan 2025): stolen advertiser accounts resold on forums. https://www.malwarebytes.com/blog/threat-intel/2025/01/the-great-google-ads-heist-criminals-ransack-advertiser-accounts-via-fake-google-ads ; https://thehackernews.com/2025/01/google-ads-users-targeted-in.html

Fake documents for identity verification (underground claims, unverified). A BlackHatWorld thread claims fake docs pass basic advertiser verification but not BOV because BOV is manually reviewed: https://www.blackhatworld.com/seo/google-ads-verification.1563902/ . Open market for "verified Google Ads accounts": https://yeezypay.io/blog/a-guide-to-google-ads-verification . Anecdotal.

Cloaking as the dominant moderation bypass. Meta sued a Vietnamese cloaking operator and others (Feb 2026): https://about.fb.com/news/2026/02/meta-takes-legal-action-against-scam-advertisers/

Meta internal documents (Reuters, Nov 2025 to Jan 2026): roughly 10% of 2024 revenue projected from scam and banned-goods ads; bans only at 95%+ fraud certainty; universal advertiser verification estimated to cost up to 4.8% of revenue. https://www.lawfaremedia.org/article/reuters-blows-lid-on-meta's-fraud-profit-scandal ; https://techcrunch.com/2025/11/06/meta-estimates-that-it-earns-10-of-its-revenue-from-scams-report-says/ ; https://www.blumenthal.senate.gov/download/2025-11-22_meta_ad_fraud_profiteering_letter ; https://www.emarketer.com/content/meta-expands-advertiser-verification-amid-scam-concerns

Fake FinCEN "licenses". FinCEN alert (Dec 2024): scammers self-register as MSBs and cite the public registry to appear legitimate; FinCEN "does not grant licenses nor endorse" MSBs. https://www.fincen.gov/system/files/2024-12/Alert-FinCEN-Scams-FINAL508.pdf ; registry https://msb.fincen.gov/ . A genuine registry hit is not proof of legitimacy.

Fake dispensaries: BBB alerts on fake delivery-only dispensaries, crypto payment, "delivery insurance" fees: https://www.bbb.org/article/scams/28080-bbb-scam-alert-marijuana-dispensary-scams-are-on-the-rise-heres-how-to-spot-one ; Vermont CCB: https://ccb.vermont.gov/notice-public-fake-cannabis-retailer-scams ; NY Governor urged Google and Meta not to promote unlicensed shops: https://www.marketingbrew.com/stories/2024/04/05/new-york-cannabis-marketing-laws

"Authorized service/dealer" impersonation ads: appliance-repair operators bidding on LG/Samsung/Whirlpool terms posing as authorized service (BBB): https://www.bbb.org/article/news-releases/20282-scam-alert-fridge-broken-be-careful-when-calling-for-repairs ; https://whnt.com/taking-action/bbb-consumer-alerts/looking-for-help-with-a-major-appliance-repair-watch-out-for-fake-service-providers/

Roofing/solar: contractor guides warn of loose "GAF certified" claims, outdated badges, lapsed annual certifications: https://www.affordableroofing.com/how-can-i-tell-if-a-roofing-contractor-is-truly-gaf-master-elite-certified/ . Solar sales practices under FTC/CFPB scrutiny: https://www.npr.org/2024/08/14/1244330369/solar-rooftop-panels-environment-fraud-deception

GenAI document forgery in KYC/KYB generally: Sumsub reports GenAI-made fakes went from 0% to 2% of detected fakes in a year and serial template reuse up 7x: https://sumsub.com/blog/ai-fake-id-challenge-for-kyc/ ; Middesk on synthetic business identities mixing real EINs with fake officers: https://www.middesk.com/blog/how-fraudsters-are-using-ai-to-bypass-traditional-kyb-checks ; G2 on OnlyFake-style generators: https://g2risksolutions.com/resources/blog/protect-your-business-from-ai-generated-fake-documents/

Google scale numbers: 2025 report, 8.3B ads removed, 24.9M accounts suspended, 602M scam ads, incorrect suspensions reduced 80%: https://blog.google/products/ads-commerce/2025-ads-safety-report/ . 2024 report: https://blog.google/products/ads-commerce/google-ads-safety-report-2024/

## 3. What platforms say they do

Google: no public description of document-review methodology. Named third parties: G2 Risk Solutions (financial services, non-US so far), LegitScript/NABP (health, CBD), Dun and Bradstreet (DUNS), Evident/Pinkerton (LSA, per third parties). Google Ads API exposes ADVERTISER_IDENTITY_VERIFICATION: https://developers.google.com/google-ads/api/docs/account-management/advertiser-identity-verification

Meta: accepted US docs are certificate/articles of incorporation, business registration/license, government-issued tax document (self-filed not accepted), business bank statement, utility bill. Must be unexpired, unmodified, in color. Up to 14 business days. https://www.facebook.com/business/help/2058515294227817 ; https://www.facebook.com/business/help/159334372093366 . March 2026 target: verified advertisers to drive 90% of ad revenue by end of 2026: https://about.fb.com/news/2026/03/meta-launches-new-anti-scam-tools-deploys-ai-technology-to-fight-scammers-and-protect-people/

TikTok: state certificate of incorporation, business license, IRS SS-4/EIN letter, IRS letters, SEC filing (from search summaries; page is JS-rendered): https://ads.tiktok.com/help/article/acceptable-documents-for-business-verification?lang=en

No platform publishes false positive or false negative rates for document review.

## 4. Manufacturer dealer and certification lookups (roofing and home services)

| Program | Public lookup | Tech / endpoint | Verdict |
|---|---|---|---|
| GAF Master Elite / Certified Plus / Certified | https://www.gaf.com/en-us/roofing-contractors/verify (by name or certification ID) and https://www.gaf.com/en-us/roofing-contractors/residential | Akamai returns 403 to non-browser clients on every path. | Needs headless browser or partner API; not confirmed |
| Owens Corning Preferred / Platinum | https://www.owenscorning.com/en-us/roofing/contractors | React app calling `https://mdms.owenscorning.com/api/v3/locations/roofing-contractors?lat=&lng=&radius=&units=mi&per_page=&c_code=en-us`. Live-tested, returns JSON with name, phone, website, address, membership_number, badges, tier_level. | Yes, programmatically queryable (unauthenticated) |
| CertainTeed SELECT ShingleMaster / ShingleMaster | https://www.certainteed.com/find-a-pro | Drupal plus Algolia index `prod_company_location` (search-only key embedded in page). Live-tested, 7,447 hits; records include certifications with qualification name and date achieved, phone, site, address, geo. | Yes, programmatically queryable |
| Carrier Factory Authorized Dealer | https://www.carrier.com/us/en/residential/carrier-factory-authorized-dealers/ embeds https://locator.ttdealers.carrier.com/ | Angular app; `api/dealer/` service with Bearer token; direct GET returned SPA shell. | Endpoint exists, auth handshake not reverse-engineered |
| Lennox Premier Dealer | https://www.lennox.com/residential/locate/ | `https://www.lennox.com/api/residential/v2/4rroifG/dealer-locator?postalCode=75001&radius=25`. Live-tested, JSON with dealerNumber, isPremier, isFactoryTrained, isNATE, address. | Yes, programmatically queryable |
| Generac Authorized Dealer | https://www.generac.com/dealer-locator/ | Vue app; `POST https://www.generac.com/DealerLocatorApi/GetDealers`; site behind Incapsula. | Endpoint identified, not exercised |
| Tesla Certified Installer | https://www.tesla.com/support/certified-installers | Akamai 403 to non-browser clients. | Not confirmed |
| LegitScript | https://www.legitscript.com/certification/website-certification-status/ | JS app, URL input, no API. | Manual or headless only |
| FinCEN MSB | https://msb.fincen.gov/ | Public registrant search. Existence is not legitimacy. | Usable as a negative check |

Typical "authorized dealer" evidence is a manufacturer-issued certificate or badge PDF plus a listing in the locator. The locator listing (and for CertainTeed and Owens Corning, the date achieved and tier) is the only independently checkable artifact. GAF certifications renew annually, so lapsed status is a real false-positive source.

## Could not find or confirm
- Any public statement by Google, Meta, or TikTok of how uploaded business documents are authenticated, or which vendor performs it.
- Any published false positive or false negative rates for document verification.
- Any court case, AG action, or news report specifically about forged affiliation or authorization letters or fake GAF/Owens Corning/Tesla/Carrier certifications submitted to an ad platform.
- A documented US case of a forged LegitScript certificate or fake cannabis license used to obtain Google certification.
- GAF and Tesla lookup page structure or APIs (blocked by Akamai).
- Whether Google's US crypto, gambling, and debt certification forms require document upload versus self-attested license numbers.
