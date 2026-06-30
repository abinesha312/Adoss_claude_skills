# Pre-Output Checklist (run before delivering)

Execute tailoring in this order, then verify every item below.

## Tailoring sequence

1. **Parse JD** → Priority-1/2 keywords + 3–4 themes
2. **Gap analysis** — mark each P1 keyword Covered / Partial / Missing
3. **Write Summary first** — JD role title + themes
4. **Edit bullets** — minimal edit first; new bullet only for true gaps; blend with real experience
5. **Select projects** — **≤4** JD-relevant entries from candidate profile pool; one crisp bullet each
6. **Reorder Technical Skills** — JD tools first; candidate must actually use them
7. **Balance to exactly 2 pages** — see bullet-strategy.md Page fill strategy
8. **Run this checklist** → deliver output

## Content checks

- [ ] JD parsed: role title, Priority-1/2 keywords, 3–4 themes extracted
- [ ] Summary written **first**; all bullets align with Summary themes
- [ ] Summary role title mirrors JD title
- [ ] Every Priority-1 keyword appears ≥1× (Summary, bullets, or Skills)
- [ ] Each bullet follows Action + Task/Method + Result — single-line, no bloat
- [ ] **Bold metrics only** in body bullets — not tools or keywords
- [ ] New bullets in most-relevant roles, distributed — not stacked in one job
- [ ] Technical Skills lists only JD tools the candidate has actually used
- [ ] **≤4 projects** from pool — JD-relevant only

## Structure checks (both formats)

- [ ] All **7 mandatory sections** present in order: Contact → Summary → Experience → Internships → Projects → Education → Technical Skills
- [ ] Job titles, company names, dates, and **locations** unchanged from candidate profile
- [ ] No fabricated employers, roles, dates, locations, or metrics
- [ ] Exactly **2 pages** — no trailing whitespace, no page 3

## LaTeX-specific (latex-resume-builder only)

- [ ] No `\vspace` inside `itemize`; `\jobentry{}{}{}` for every role/education header; dates in arg 3 (right-aligned via `\hfill`)
- [ ] Margins 1in; Helvetica 11pt; `\setstretch{1.1}` unchanged
- [ ] Valid LaTeX — `\textbf{}`, `\href{}`, `\item`, `\\` syntax correct; no trailing spaces
- [ ] Output is **raw LaTeX only** — no markdown fences

## Word-specific (word-resume-builder only)

- [ ] List Bullet style; no empty paragraphs between bullets
- [ ] Job headers: bold title left, dates right-aligned (tab stop); italic company — location
- [ ] Margins 1in; Calibri/Arial 11pt; line spacing 1.08–1.15
- [ ] Saved to `plugins/buildResume/tailored_resume.docx` — return file path only
- [ ] **DOCX only** — never PDF
