# Research appendix 3: Detecting forged, tampered, template-generated, and AI-generated documents (state of the art, 2025 to 2026)

Compiled 2026-09-16. Vendor claims are reported as claims. Unconfirmed items are collected at the end.

## 0. Headline findings

1. Nobody has a validated, general-purpose "is this business document forged" model. The strongest evidence-based signals are (a) PDF structural and metadata forensics on native PDFs, (b) semantic consistency checks (arithmetic, dates, registry lookups), (c) provenance metadata (C2PA) when it survives, and (d) issuer verification portals. Pixel forensics degrade sharply on AI-edited documents and are destroyed by screenshots and photos.
2. Vision LLMs are strong on fully synthetic receipts because of arithmetic and logic errors, and near chance on localized AI inpainting. Claude Sonnet 4 F1 0.975 on GPT-4o receipts (https://arxiv.org/html/2603.11442); GPT-4o AUC 0.509 on Gemini-inpainted numeric fields (https://arxiv.org/html/2602.20569v1).
3. Document-specific forensic models collapse out of distribution: DocTamper goes from AUC 0.98 in-distribution to 0.563 on diffusion inpainting; TruFor 0.96 to 0.751. "No evaluated method works reliably out-of-the-box on diverse document types" (https://arxiv.org/html/2603.01433v2).
4. C2PA is present on ChatGPT/DALL-E, Firefly, and Imagen output but is stripped by screenshots and re-saves; SynthID is not third-party verifiable except via Google's waitlisted portal or a partner-preview Cloud API (https://c2paviewer.com/articles/verify-ai-generated-image-c2pa-synthid ; https://www.infoq.com/news/2026/05/google-synthid-content-detection/). Resistant AI's own framing: "80% of attempts will still be caught by standard metadata checks", so roughly 20% will not (https://resistant.ai/blog/chatgpt-document-fraud).
5. For US state certificates of good standing, template matching is the wrong primary tool: Delaware, Colorado, Kansas, Texas, and others expose authentication-number validators (see appendix 2); Colorado issues the official PDF for free and voids any altered copy (https://www.sos.state.co.us/pubs/business/FAQs/certGoodStanding.html).

## 1. Commercial vendors

"Arbitrary biz docs" means the API accepts a certificate, license, letter, or agreement, not just IDs or bank statements.

| Vendor | Signals claimed | Arbitrary biz docs / API | Published accuracy | GenAI named? |
|---|---|---|---|---|
| Resistant AI (Documents) | "500+" detectors on metadata, structure, fonts, visual inconsistencies; reused and template-farmed documents; AI document generator detector. https://resistant.ai/products/documents | Yes, "document-agnostic", lists business certificates; PDF/JPEG/PNG/TIFF; REST API; verdicts Trusted / Warning / High Risk | Marketing only ("99.2% accuracy", "<1% FP"); no methodology. Claims 90x rise in AI-generated doc fraud in 2025 | Yes: "ChatGPT, Gemini and all major models"; admits metadata alone catches about 80% |
| Inscribe | Font-based manipulation, text-editing patterns, document fingerprinting, template detection. https://www.inscribe.ai/2025-document-fraud-report | Financial docs (bank statements, payslips, invoices, tax forms); not marketed for certificates | "89% precision" for AI Fraud Analyst; AI-generated forgeries under 5% of lending doc fraud (Jan 2026) https://dev.to/haruodev/inscribe-says-ai-is-under-5-of-document-fraud-appzen-708-both-are-right-3cg3 | Generic |
| Ocrolus Detect | Altered metadata, inconsistent embedded fonts, rasterized text overlays, inserted image layers, compression anomalies. https://docs.ocrolus.com/docs/detect | No: only bank statements, pay stubs, W-2s today | None in docs; docs warn of false positives | Generic |
| Sardine | Behavioral and device risk; "enhanced document verification" Nov 2025 | Not documented | None | No |
| Alloy | Orchestration layer wrapping third-party doc verification. "Alloy DocVerify" does not appear to exist. https://developer.alloy.com/public/docs/document-verification-web-sdk | Via partners | None | No |
| Veriff (Proof of Address) | Document structure, metadata, fonts; reason codes such as `PDF_PROCESSED_BY_EDITOR`. https://devdocs.veriff.com/docs/proof-of-address-verification | Utility, bank, government letters; custom types via solutions engineer | None | No |
| Onfido / Entrust | ID-focused; digital forgeries 35% of doc fraud in 2025 https://www.entrust.com/company/newsroom/deepfake-attacks-strike-every-five-minutes-amid-244-surge-in-digital-document-forgeries | IDs | Relative claims only | Generic |
| Jumio | Watermarks, logos, security features; basic Doc Proof workflow labeled "(No fraud checks)" https://documentation.jumio.ai/docs/quickStart/docProof | "Limited coverage of commercial documents" | None | No |
| Persona | Check list behind login; blog 403 | Custom templates exist; checks unconfirmed | None | Unconfirmed |
| Socure DocV | IDs; ">98% first-attempt success" is a completion metric | IDs only | None | No |
| Mitek | Morphological artifacts, RGB/YCbCr discrepancies, repeated elements across documents (identical signatures, holograms). https://www.miteksystems.com/blog/ai-automated-document-fraud-detection-with-digital-manipulation-technology | IDs | None | Names OnlyFake-style ID farms |
| Sumsub | KYB: corporate docs including certificates of good standing get automated checks for graphic-editor modification plus manual legal-team review plus registry cross-check. https://docs.sumsub.com/docs/how-business-verification-works | Yes for KYB, partly manual | 2% of detected fake docs in 2025 made with GenAI | Names ChatGPT, Grok, Gemini as sources |
| Regula | Pattern, guilloche, microprint, font mismatch, "document liveness" (screenshots, printouts). https://regulaforensics.com/blog/document-authenticity-checks/ | IDs only | None | Generic |
| Hive | AI-generated image detection with source classification (about 80 classes including `4o`, `gemini`, `flux`); threshold 0.9 recommended. https://docs.thehive.ai/docs/ai-image-and-video-detection | Any image; not document-aware | None in docs | Yes |
| Sightengine | AI-image detection listing "OpenAI GPT image generation", "Nano Banana Pro", Flux, Midjourney; claims robustness to re-encoding; separate recapture detection. https://sightengine.com/docs/ai-generated-image-detection ; https://sightengine.com/docs/image-recapture-detection | Any image; public free tier | None | Yes |
| AI or Not | Self-audit of 16 generators, 75 attempts; 5 produced high-fidelity IDs (Nano Banana, ChatGPT Images 2.0, Recraft v4, Grok, Imagen 4 Ultra); ChatGPT refused in chat but complied via API. https://www.aiornot.com/blog/ai-fake-ids-kyc-audit-2026 | Images | Self-test, n=75 | Yes |
| AppZen (receipts) | Metadata, arithmetic validation, merchant cross-referencing, duplicates. 70.8% of flagged fraudulent expense receipts were AI-generated by May 2026, from 0% in Mar 2025. https://www.appzen.com/blog/catching-ai-generated-fake-receipts-with-ai | Receipts only | None | Generic |
| Truepic | Provenance at capture (C2PA-signed camera SDK); not a post-hoc detector. https://www.truepic.com/ | N/A | N/A | No |
| Reality Defender, Sensity | Deepfake media APIs; not document-specific | No | None public | Generic |

Takeaways: only Resistant AI, Sumsub KYB (partly manual), Veriff (by arrangement), and generic image-AI detectors (Hive, Sightengine) will take a state certificate or signed letter. Every published accuracy number is vendor-reported with no methodology. Expect ad-platform uploads of certificates to behave more like receipts (cheap, synthesized from scratch) than like bank statements (edited originals).

## 2. Forensic techniques: what works, limits, and what survives each capture path

### 2.1 Technique notes with evidence

- Error Level Analysis (ELA): JPEG-only; after repeated resaves "the ELA will return a black image"; false positives on high-contrast edges (https://fotoforensics.com/tutorial-ela.php). A 2026 multi-scale ELA approach reaches AUC 0.990 in-domain but 0.499 (chance) on copy-move (https://arxiv.org/html/2607.06615v2).
- JPEG quantization tables / double compression: editors use distinctive tables (https://29a.ch/2017/02/05/jpeg-forensics-in-forensically). Diffusion inpainting generates pixels directly without JPEG seams (https://arxiv.org/html/2602.20569v1).
- Noise residual / PRNU: PRNU needs a reference camera set; useless for anonymous uploads. TruFor drops to AUC 0.751 on AI-inpainted docs (https://arxiv.org/html/2607.01442).
- Copy-move: cross-document repeated elements (same signature or seal pixels across uploads) is a Mitek signal and cheap to do with perceptual hashing of seal and signature crops.
- Font, kerning, text-line alignment: Inscribe's top signal category; practical checks include multiple font dictionaries inside one text box and glyph spacing that breaks the baseline grid (https://dev.to/iurii_rogulia/detect-a-tampered-pdf-in-python-without-the-original-546o). Fully synthesized docs from one generator have consistent fonts, so this catches edits, not synthesis.
- PDF structure forensics: incremental updates (`startxref` count > 1), `/Producer` versus `/Creator` mismatch, `ModDate` before `CreationDate`, Info-dict versus XMP date disagreement, image objects layered over text, signature `/ByteRange` not covering EOF. Caveat: a from-scratch forgery has no post-creation modification to find; report intact / modified / inconclusive rather than binary (https://dev.to/iurii_rogulia/pdf-metadata-forensics-a-complete-field-by-field-reference-44oc). Concrete fingerprint: the Texas SOS sample certificate carries `Producer: Adobe PDF Library 22.3.98`, `Creator: Acrobat PDFMaker 22 for Word` (https://www.sos.state.tx.us/corp/status-example.pdf), so an issuer producer-string allowlist per state is feasible.
- EXIF/XMP: screenshots strip metadata entirely (https://fotoforensics.com/tutorial-mistakes.php).
- C2PA Content Credentials: embedded by ChatGPT image generation, DALL-E 3, Sora, Adobe Firefly, Google Imagen; not by Midjourney; Flux, Grok, Ideogram, Recraft not covered (https://c2paviewer.com/articles/ai-tools-c2pa-support). The manifest lives in the file container, so it is destroyed by screenshot and usually stripped by re-encoding. OpenAI joined the C2PA steering committee and committed to SynthID on May 19, 2026 (https://c2paviewer.com/articles/openai-google-c2pa-synthid-2026).
- SynthID: proprietary; verification only via the Gemini app, a waitlisted portal, or the SynthID Content Detection API on Google Cloud in partner preview as of May 2026 (https://www.infoq.com/news/2026/05/google-synthid-content-detection/ ; https://www.lumethic.com/en/articles/synthid-detector-portal).
- Recapture detection (photo of screen or print): moiré, sub-pixel, halftone artifacts; scanned docs are not recaptures (https://sightengine.com/docs/image-recapture-detection); domain generalization remains open (https://arxiv.org/pdf/2407.17170).

### 2.2 Robustness matrix

Strong = intact and discriminative; Partial = weakened; Gone = destroyed by that capture path.

| Signal | Native PDF upload | Screenshot | Photo of paper / print-scan | Notes |
|---|---|---|---|---|
| PDF incremental updates / xref layers | Strong | Gone | Gone | Only edits, not from-scratch fakes |
| /Producer, /Creator, Info vs XMP dates | Strong (issuer allowlist possible) | Gone | Gone | Forgeable by a sophisticated actor; still catches most |
| Font embedding / multiple font dicts / kerning | Strong | Partial (visual only) | Partial | Synthesis from one generator is font-consistent |
| Image-over-text overlay objects | Strong | Gone | Gone | |
| Digital signature /ByteRange | Strong where issuers sign (rare for US SOS certs) | Gone | Gone | |
| EXIF/XMP camera or editor metadata | n/a | Gone | Partial (EXIF of the photo) | |
| C2PA manifest | Present only if embedded image carries one (rare) | Gone | Gone | Absence proves nothing |
| SynthID watermark | Partial | Partial to Gone | Gone | Not verifiable without Google |
| ELA / double-JPEG / quantization tables | n/a for vector PDF; Strong for embedded JPEG | Gone | Gone | False positives on edges and text |
| Noise-residual localizers (TruFor, CAT-Net) | Partial | Partial | Weak | AUC 0.75 on AI inpainting |
| AI-image classifiers (Hive, Sightengine) | Partial (text-rich images are out of distribution) | Partial to Strong | Weak | Nothing published for text-rich certificates |
| Recapture / moiré detector | n/a | Strong | Strong | Tells you how it was uploaded, not whether forged |
| Arithmetic / date / logical consistency | Strong | Strong | Strong (OCR-dependent) | Best signal versus from-scratch GenAI; attackers can fix |
| Registry / issuer portal lookup | Strong | Strong | Strong | Best signal overall for SOS certificates |
| Seal/signature perceptual-hash reuse across uploads | Strong | Strong | Partial | Cheap; catches template farms |
| Layout / template match versus reference | Strong | Strong | Partial (perspective) | Needs per-state reference set |

## 3. AI-generated document detection research (2025 to 2026)

| Work | Data | Key numbers | Generalization |
|---|---|---|---|
| GPT4o-Receipt (https://arxiv.org/html/2603.11442 ; https://huggingface.co/datasets/Scam-AI/gpt4o-receipt) | 935 GPT-4o receipts plus 300 real | Binary F1: Claude Sonnet 4 0.975, Gemini 2.5 Flash 0.890, Grok 4 0.873 with FPR 90.3%, GPT-5 Nano 0.685; 30 humans F1 0.852. Dominant signal: arithmetic errors (97.2% of AI receipts flagged by Claude). "Adversarial hardening" (fixing sums) keeps top detectors above 94% via other inconsistencies | GPT-4o only; Feb 2026 snapshot |
| AIForge-Doc (https://arxiv.org/html/2602.20569v1) | 4,061 receipts and forms with numeric fields inpainted by Gemini 2.5 Flash Image and Ideogram | Zero-shot image AUC: TruFor 0.751, DocTamper 0.563 (versus 0.98 in-distribution), GPT-4o 0.509 | Median tampered region 0.92% of pixels; no JPEG seams |
| DocForge-Bench (https://arxiv.org/html/2603.01433v2) | 8 datasets, 14 methods | Pixel-AUC at or above 0.76 but near-zero pixel-F1 at default threshold; calibrating on 10 domain images recovers 39 to 55% of the gap | No VLMs evaluated; pre-GenAI datasets |
| VLMs for text manipulation (https://arxiv.org/html/2509.10278) | OSTF scene text plus FantasyID cards | GPT-4o F1 0.86 / 0.85; TruFor 0.65 / 0.71; forensic VLMs FakeShield 0.51, SIDA 0.34 to 0.47 | Specialized forensic VLMs do not transfer; resolution-limited |
| Forensics-Bench (https://arxiv.org/html/2503.15024) | 63k MCQs, 112 forgery types | GPT-4o 57.9%, Gemini 1.5 Pro 48.3%, Claude 3.5 Sonnet 33.8%; proprietary models "admit they cannot conclude" | Not document-specific |
| ID-document survey (https://arxiv.org/html/2607.01442) | SIDTD, IDNet, FantasyID, DocXPand | Zero-shot multimodal models EER above 45%; "detectors trained on one generation method fail against novel synthesis pipelines without retraining" | |
| FLiD (https://arxiv.org/html/2605.09089) | Field-localized ID forgery | Field cropping beats whole-document by 29 to 35 points | Supports a crop-the-seal-and-fields design |
| AI or Not audit (https://www.aiornot.com/blog/ai-fake-ids-kyc-audit-2026) | 16 generators, 75 attempts | 5 high-fidelity generators; ChatGPT refused in chat but complied via API | Self-audit |

Datasets: DocTamper (170k images, non-commercial, password-gated: https://github.com/qcf-568/DocTamper); OSTF; SIDTD (https://www.nature.com/articles/s41597-024-04160-9); Roboflow Receipt Fraud (527 images, tiny). No controlled longitudinal study of detector decay exists; proxies show DocTamper 0.98 to 0.563 across generator families. Plan for re-evaluation per major generator release.

## 4. Open-source tooling for a 2-week build (status as of Sep 2026)

| Tool | Use | Status |
|---|---|---|
| pikepdf | Low-level PDF object graph, XMP plus Info, built on qpdf | 10.13.0 (Sep 2026) https://pypi.org/project/pikepdf/ |
| pypdf | Metadata, text, signatures | 6.19.0 (Sep 2026) https://pypi.org/project/pypdf/ |
| pdfid.py / pdf-parser.py (Didier Stevens) | Object stats, incremental-update inspection | 0.2.10 / 0.7.13 (2025) https://blog.didierstevens.com/2025/08/31/update-pdf-parser-py-version-0-7-13/ |
| qpdf | `--check`, JSON dump | Underlies pikepdf |
| veraPDF | Strict parser surfaces malformed structures | 1.30.2 (Jun 2026) https://github.com/veraPDF/veraPDF-library/releases |
| exiftool | EXIF/XMP/ICC, JPEG quant tables | Widely maintained; version unverified |
| c2patool / c2pa-rs | Read and validate C2PA manifests | c2patool v0.27.22 (Sep 2025) from the c2pa-rs monorepo https://github.com/contentauth/c2pa-rs/releases |
| c2pa-python | Same, Python | Version and PDF support unconfirmed https://github.com/contentauth/c2pa-python |
| ImageHash | pHash/dHash for seal, signature, and template reuse | 4.3.2 https://pypi.org/project/ImageHash/ |
| Sherloq | ELA, JPEG ghost, PRNU, copy-move, noise | GUI-only, "not meant as an automatic tool" https://github.com/GuidoBartoli/sherloq . Port algorithms, do not depend on it |
| TruFor / CAT-Net / ManTraNet | Forgery localization with released weights | CAT-Net https://github.com/mjkwon2021/CAT-Net ; ManTraNet port https://github.com/RonyAbecidan/ManTraNet-pytorch . Recalibrate threshold on about 10 of your own docs |
| DocTamper model | Doc-specific localizer | Non-commercial license; likely unusable commercially |
| PaddleOCR | OCR plus PP-StructureV3 layout to Markdown/JSON | 3.7.0 (Jun 2026) https://github.com/PaddlePaddle/PaddleOCR |
| docTR | OCR, KIE, layout | v1.1.0 https://github.com/mindee/doctr |
| Sightengine / Hive | AI-image plus recapture detection as a service | Public docs; Sightengine has a free tier |

## 5. Vision LLMs as forgery judges

What the evidence supports:
- Strong on fully synthetic documents where the generator makes logical or arithmetic mistakes (Claude Sonnet 4 F1 0.975 on GPT-4o receipts; humans 0.852). The mechanism is semantic, not pixel forensics.
- Competitive with TruFor on ID text edits at high resolution (GPT-4o F1 0.85 versus TruFor 0.65 to 0.71).

Documented failure modes:
- Chance-level on localized AI inpainting (GPT-4o AUC 0.509 on AIForge-Doc).
- Over-flagging and hallucinated tampering: Grok 4 FPR 90.3% on real receipts; three of five MLLMs gave near-identical visual scores for real versus fake.
- Resolution sensitivity: use tiled or cropped inputs for small fields.
- Fine-tuned forensic VLMs do not transfer.
- Prompt injection via the document itself: OWASP LLM01:2025 (https://genai.owasp.org/llmrisk/llm01-prompt-injection/); invisible-text and steganographic image injections achieved 24.3% attack success across GPT-4V, Claude, and LLaVA (https://labs.cloudsecurityalliance.org/research/csa-research-note-image-prompt-injection-multimodal-llm-2026/). Mitigations: render PDF to pixels before the VLM (drops hidden text layers), diff OCR text versus the PDF text layer (a mismatch is itself a fraud signal), never let VLM output be the sole decider.
- Reproducibility: results are tied to a model snapshot.

No paper is framed as "LLM-as-judge for document authenticity". Design implication: use the VLM for structured extraction and consistency reasoning with a fixed schema, feed that into deterministic checks and registry lookups, and do not ask it "does this look tampered".

## 6. Template, seal, and signature verification and reference sources

- Stamp and seal detection: YOLOv8 to v11 on StaVer plus DDI-100; seal identity via multi-stage Siamese networks (https://www.techscience.com/CMES/v142n1/58997/html). Signature similarity: SigScatNet (https://arxiv.org/pdf/2311.05579). Layout matching: SIFT-based (https://arxiv.org/abs/2311.12663).
- Nothing published on embossed-seal, microprint, or watermark detection for US state business certificates.
- Cross-upload reuse: pHash of seal and signature crops plus FLiD-style field cropping.

Reference sources (portals beat templates):
- Delaware: 18 sample certificate types with images at https://corp.delaware.gov/sample-certificate-wording/ ; validator https://corp.delaware.gov/authver/ .
- Texas: official example https://www.sos.state.tx.us/corp/status-example.pdf ; https://www.sos.state.tx.us/corp/copies.shtml .
- Colorado: certificates issued free as PDFs; altered certificates or incorrect page counts are void (https://www.sos.state.co.us/pubs/business/FAQs/certGoodStanding.html).
- Kansas: https://www.sos.ks.gov/businesses/copies-and-certifications.html .
- DLA "Proof of Business Reference Sheet (Aug 2025)" claims examples per state (https://www.dla.mil/Portals/104/Documents/J3LogisticOperations/Brochures/50%20States%20-%20examples%20of%20Proof%20of%20Business%20(Aug%202025).pdf) but returned 403; unverified.
- Generic "certificate of good standing templates" from design sites (e.g. https://certifier.io/certificate-templates/good-standing) are what low-effort forgers use, so they are useful as negative references.

## 7. Could not find or confirm
- Any independent accuracy evaluation of Resistant AI, Inscribe, Ocrolus, Veriff, Persona, Mitek, IDVerse, Sumsub, or Regula on business documents.
- Vendor pricing beyond Reality Defender's free tier, Sightengine's public tiers, and third-party estimates.
- Persona's document-fraud check list; whether "Alloy DocVerify" exists (it appears not).
- OpenAI's first-party statements on C2PA persistence; Entrust 2026 report page.
- Whether Google's SynthID Content Detection API is generally available (preview as of May 2026).
- c2pa-python version and PDF manifest support.
- Any benchmark of AI-image detectors on text-rich certificate or letter images; print-scan robustness numbers for ELA or SynthID.
- Any published approach to embossed-seal, microprint, or watermark verification for US state business certificates.
