---
name: word-resume-builder
description: >-
  Builds Abinesh Haridoss's resume as a Microsoft Word file (.docx only, never PDF) tailored to a job description, specialized for Workday and other strict-ATS parsers (Taleo, iCIMS, Greenhouse, SuccessFactors).
  Use ONLY when the user wants Word, .docx, Microsoft Word, or Workday/strict-ATS output.
  Do NOT use for LaTeX, .tex, or Overleaf requests — use latex-resume-builder instead.
  Triggers: Word resume, docx resume, Microsoft Word resume, Workday resume, strict ATS resume, ATS optimize Word.
---

# Word Resume Builder — Abinesh Haridoss

Specialized for **Workday / strict-ATS parsing** (Taleo, iCIMS, Greenhouse, SuccessFactors) — not just generic "ATS-friendly" formatting.

## START HERE

### WHEN TO USE THIS SKILL

- User asks for **Word**, **.docx**, or **Microsoft Word** output
- User mentions **Workday**, **Taleo**, **iCIMS**, **Greenhouse**, **SuccessFactors**, or "strict ATS format"
- User says "build my resume in Word" or "save as docx"
- Triggers: Word resume, docx resume, Microsoft Word resume, Workday resume, strict ATS resume, ATS optimize Word

### WHEN NOT TO USE

- User wants **LaTeX**, **.tex**, or **Overleaf** → use **latex-resume-builder**
- User asks for PDF → deliver **.docx only**; never generate or suggest PDF export

### NON-NEGOTIABLES

1. All **7 sections** in fixed order (Contact → Summary → Experience → Internships → Projects → Education → Technical Skills)
2. Fixed job titles, companies, dates, and **locations** — never invent or change
3. **No fabrication** — reframe real experience only
4. **Bold metrics only** in body bullets (e.g., **85%**) — not tool names
5. **≤4 projects** from the pool in candidate profile
6. Exactly **2 pages** in Word — no page 3, no trailing whitespace
7. Calibri/Arial 11pt, 1in margins, List Bullet style
8. **Strict ATS / Workday structural rules** (`references/ats-strict-rules.md`) — single column, no tables/text boxes, contact in body (never header/footer), literal section headers, `Month YYYY` dates

### IF JD MISSING

**STOP.** Ask the user to paste the job description (or URL). Do not tailor without a JD.

---

## Reference files (read when tailoring)

| When | Read |
| --- | --- |
| Before any edit | `../shared/candidate-profile.md` — fixed fields, experience index, project pool |
| Bullet editing | `../shared/bullet-strategy.md` — Step 0, edit vs add, verbs, page fill |
| Before output | `../shared/checklist.md` — single pre-output checklist |
| Baseline content | `references/baseline-content.md` — structured starting text, `Month YYYY` dates |
| Build instructions | `references/build-docx.md` — full python-docx build script, hyperlink helper, tab-stop headers |
| **Strict ATS / Workday rules** | `references/ats-strict-rules.md` — structural rules, Notepad-test verification, compliance table |

---

## Primary Workflow

When the user provides a **job description** and wants Word output:

### Step 0 — JD gate

**STOP** if no JD — ask user to paste it.

### Step 1 — READ candidate profile

**READ** `../shared/candidate-profile.md`. Do not invent roles, dates, locations, or employers.

### Step 2 — READ baseline content and ATS rules

**READ** `references/baseline-content.md`. Start from this content for every request. Preserve structure; modify Summary, bullets, Projects (≤4), and Technical Skills only.

**READ** `references/ats-strict-rules.md` — apply every structural rule (single column, no tables/text boxes/headers-footers, literal section headers, `Month YYYY` dates) while building.

### Step 3 — WRITE Summary first

**WRITE Summary first** — mirror JD role title + 3–4 themes. Every Experience and Internship bullet must reinforce this narrative.

### Step 4 — EDIT bullets

**EDIT bullets** using priority:

1. **Minimal edit first** — weave missing JD keywords into existing bullets (one crisp line each)
2. **New bullet only** for true gaps where real work exists — add to most relevant role, distributed across roles
3. **Reorder Technical Skills** — JD tools first; candidate must actually use them

See `../shared/bullet-strategy.md` for Step 0 parsing, decision rules, and verb guidance.

### Step 5 — SELECT projects

**SELECT ≤4 projects** from the pool in `../shared/candidate-profile.md`. One crisp bullet per project with GitHub link.

### Step 6 — BALANCE to exactly 2 pages

**BALANCE to exactly 2 pages.** If short, add crisp bullets evenly across roles (reframe real work). If long, trim oldest/least JD-relevant roles first. Never drop a section.

### Step 7 — VERIFY ATS compliance

**VERIFY** against `references/ats-strict-rules.md` before building: no tables/text boxes planned, contact info goes in the body (never header/footer), section headers are literal (`Professional Experience`, `Internships`, `Projects`, `Education`, `Technical Skills`), dates are `Month YYYY`.

### Step 8 — RUN NOW (build .docx)

**RUN NOW:**

```bash
pip install python-docx
```

1. Build document with **python-docx** using the full skeleton in `references/build-docx.md` (includes hyperlink helper, tab-stop job headers, defensive header/footer clearing)
2. Run the **Notepad-test** verification (`notepad_test()` in `build-docx.md`) — confirm text flows top-to-bottom in order and header/footer are empty
3. **SAVE** to `plugins/buildResume/Abinesh-Haridoss-Resume.docx`
4. Return **only the full file path** — no markdown resume, no LaTeX, no PDF

---

## User trigger phrases

- "Tailor my resume in Word for this JD"
- "Build my resume in docx"
- "Update my Word resume"
- "ATS optimize my Word resume"
- "Build a Workday-ready resume"
- "Format my resume for Taleo/iCIMS/Greenhouse/SuccessFactors"

If user says "tailor my resume" **without naming format**, ask: **LaTeX (.tex) or Word (.docx)?**

### Required user input

```
I'm applying for this job:

[paste job description or URL]
```

Background is embedded in reference files. **Do not ask the user to re-paste work history** unless they want to change roles, dates, or add experience.

---

## Keyword tailoring (summary)

| Section | Action |
| --- | --- |
| Summary | Rewrite first — sets narrative |
| Experience / Internships | Align with Summary + JD; crisp single-line bullets |
| Projects | ≤4 JD-relevant from pool |
| Technical Skills | Reorder; add JD tools candidate actually uses |

### What NEVER to change

- Name, contact, URLs
- Job titles, companies, dates, locations
- Section order and all 7 sections
- Document styles, margins, font
- Fabricated experience or metrics

---

## Word essentials (details in references/build-docx.md and references/ats-strict-rules.md)

### Job header

```
[Bold] Full Stack Developer                    March 2020 – September 2021
[Italic] Tanishq & ProwessIQ Private Limited — Chennai, India
• Bullet with metric bold only — achieving 99.9% uptime on GKE.
```

Title left, dates **right-aligned** on the same line via paragraph tab stop (never a table — see `build-docx.md`). Dates use full `Month YYYY` format.

### Formatting rules

- `List Bullet` style — no empty paragraphs between bullets
- Tab stop for right-aligned dates — never a table for layout
- Contact info in the document **body**, first lines — **never** in a header/footer
- Literal section headers only (`Professional Experience`, `Internships`, etc.) — never creative alternatives
- Hyperlinks for email, GitHub, LinkedIn, portfolio — body only
- **Bold metrics only** — not tool names in bullets
- Dates in **`Month YYYY`** format everywhere (`December 2025`, not `Dec 2025`)

### Build method

| Element | python-docx |
| --- | --- |
| Bullets | `add_bullet()` — `List Bullet` style |
| Job header | `add_job_header()` — tab-stop paragraph, never a table |
| Metrics | Bold only on numeric segments |
| Links | `add_hyperlink()` — OXML helper, body only |

Full build script + hyperlink helper: `references/build-docx.md`. Structural ATS rules: `references/ats-strict-rules.md`.

---

## Page fill strategy (quick reference)

**Too much white space:** Add crisp bullets across roles — do not pad with empty paragraphs or long sentences.

**Over 2 pages:** Trim Tanishq → LTIMindtree → … first. Shorten wording; keep Action + Result.

Full rules: `../shared/bullet-strategy.md`

---

## DELIVER — final checklist

Run `../shared/checklist.md` internally, then confirm:

- [ ] All 7 sections present in order
- [ ] Locations preserved from candidate profile
- [ ] ≤4 JD-relevant projects
- [ ] Bold metrics only in bullets
- [ ] List Bullet style; no empty paragraphs between bullets
- [ ] Exactly 2 pages in Word
- [ ] **No tables, text boxes, or graphics anywhere in the document**
- [ ] **Contact info in the document body — header/footer left empty** (verified via `notepad_test()`)
- [ ] **Literal section headers** — `Professional Experience` / `Internships` / `Projects` / `Education` / `Technical Skills`
- [ ] **Dates in `Month YYYY` format** (e.g., `December 2025`), `Present` for current role
- [ ] Notepad-test passes — text flows top-to-bottom in order (see `references/build-docx.md`)
- [ ] Saved to `plugins/buildResume/Abinesh-Haridoss-Resume.docx`
- [ ] Returned file path only — **docx, never PDF**

---

## Output format

**Default:** Save `.docx` and return the file path. No markdown fences, no LaTeX, no PDF.

**If user asks for explanation:** After confirming file path, optionally append a keyword mapping table.

---

## ATS rules (Workday / strict-ATS specialized)

**DO:** List Bullet paragraphs, single column, exact JD keywords where truthful, bold metrics only, literal section headers, `Month YYYY` dates, contact in body, deliver `.docx`, run the Notepad-test.

**DON'T:** PDF, tables, text boxes, header/footer content, photos, fabricated experience, markdown instead of file, LaTeX output, creative section header names.

Full rationale and compliance table: `references/ats-strict-rules.md`.
