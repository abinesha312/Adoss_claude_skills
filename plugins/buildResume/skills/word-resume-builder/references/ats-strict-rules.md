# Strict ATS / Workday Compliance Rules

This skill is specialized to produce resumes that parse **cleanly and completely** in Workday and other strict ATS platforms (Taleo, iCIMS, Greenhouse, SuccessFactors). Apply every rule below in addition to `build-docx.md`. These are structural/parsing rules — they never override `../shared/candidate-profile.md` facts (titles, companies, dates, locations stay truthful).

## Why this matters

- Independent 2025–2026 benchmarks put Workday's **DOCX** parsing accuracy in the high-90% range vs. low-80s% for PDF. Always deliver `.docx` — never PDF.
- Workday reads the file in **strict top-to-bottom reading order** and maps extracted text into form fields (name, contact, employer, title, dates, skills). Anything outside that linear order — headers, footers, text boxes, tables — is frequently dropped, scrambled, or concatenated with the wrong field.
- A resume can look perfect visually and still fail silently: the upload succeeds but Workday shows fields as "[not detected]" or glues unrelated text together. These rules exist specifically to prevent that failure mode.

## Structural rules (never violate)

1. **Single column only** — no sidebars, no multi-column sections. Two-column layouts interleave sidebar text into the experience block.
2. **Contact info in the document body**, as the first 1–3 lines (name, phone, email) — **never** in a Word header or footer. Workday strips headers/footers on extraction; anything placed there disappears from the parsed profile.
3. **No text boxes, shapes, SmartArt, or floating objects.** Anything outside the main text flow is invisible to the parser.
4. **No tables anywhere** — not even for job-header layout. Use paragraph + tab-stop (see `build-docx.md`), never table cells. A 2-column skills grid fails to parse in the majority of tested ATS configurations.
5. **No skill-bar graphics, rating icons, or images containing text.**
6. **Standard section header tokens only** — literal text the parser's keyword scan expects:
   - `Professional Experience` (contains "Experience" — recognized)
   - `Internships` (recognized as experience-adjacent — do not rename)
   - `Education`
   - `Technical Skills`
   - `Projects`
   - Never use creative alternatives ("What I've Built", "Things I Know") — Workday cannot map them to form fields.
7. **Plain built-in Word bullets only** (`List Bullet` style, • character) — never custom glyphs, emoji, or Wingdings bullets.

## Formatting rules

- **Font:** Calibri or Arial, 11pt body (per `build-docx.md`).
- **Dates:** consistent `Month YYYY` format everywhere — e.g., `December 2025`, not `Dec 2025` or `12/25`. Use `Present` for the current role. This is a **display format** change only; the underlying date value in `../shared/candidate-profile.md` never changes (Dec 2025 and December 2025 mean the same date).
- **No underlines** except on hyperlinks.
- **Hyperlinks:** keep in the document body only (contact line, project links) — never inside a header/footer.
- **Filename:** save as `Abinesh-Haridoss-Resume.docx` — avoid generic names like `resume.docx`; Workday and recruiters both surface the filename.

## Build-time self-check ("Notepad test")

Before returning the file path, simulate copy-all-and-paste-into-Notepad:

1. Concatenate every paragraph's `.text` in document order (see verification snippet in `build-docx.md`).
2. Confirm it reads top-to-bottom exactly as intended: Name → Contact → Summary → Professional Experience → Internships → Projects → Education → Technical Skills.
3. Confirm no paragraph is empty where it shouldn't be, and no text is duplicated, truncated, or out of order.
4. Confirm `document.sections[0].header` and `.footer` contain **no** contact info or content — they must stay empty/default.

## Workday-specific gotchas

- Workday auto-fills application form fields from the parsed resume. Non-literal section headers or scrambled reading order leave fields blank even when the file looks fine visually — this hurts the application before a human ever reviews it.
- Broader strict-ATS platforms (Taleo, iCIMS, SuccessFactors, Greenhouse) share the same core constraints (single column, no tables/text boxes, contact in body). These rules keep the resume safe across all of them, not just Workday.
- Clean parsing beats visual polish. Workday weighs the parsed form fields more heavily than the uploaded file's appearance.

## Quick compliance table

| Rule | This skill's implementation |
| --- | --- |
| File format | `.docx` only, never PDF |
| Column layout | Single column — no tables/columns for layout |
| Contact location | Document body, first lines — never header/footer |
| Section headers | `Professional Experience` / `Internships` / `Projects` / `Education` / `Technical Skills` (literal) |
| Bullets | `List Bullet` style, plain • character |
| Dates | `Month YYYY` (e.g., `December 2025`), `Present` for current role |
| Tables / text boxes / graphics | None — paragraph + tab-stop layout only |
| Filename | `Abinesh-Haridoss-Resume.docx` |
