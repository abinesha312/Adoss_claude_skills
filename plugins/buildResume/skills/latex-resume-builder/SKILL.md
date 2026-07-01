---
name: latex-resume-builder
description: >-
  Builds Abinesh Haridoss's resume as raw LaTeX (.tex) tailored to a job description.
  Use ONLY when the user wants LaTeX, .tex, or Overleaf output.
  Do NOT use for Word, .docx, Microsoft Word, Workday, or strict-ATS requests — use word-resume-builder instead.
  Triggers: LaTeX resume, tex resume, Overleaf, ATS optimize LaTeX.
---

# LaTeX Resume Builder — Abinesh Haridoss

## START HERE

### WHEN TO USE THIS SKILL

- User asks for **LaTeX**, **.tex**, or **Overleaf** output
- User says "compile in Overleaf" or "give me the tex file"
- Triggers: LaTeX resume, tex resume, Overleaf, ATS optimize LaTeX

### WHEN NOT TO USE

- User wants **Word**, **.docx**, or **Microsoft Word** → use **word-resume-builder**
- User mentions **Workday**, **Taleo**, **iCIMS**, **Greenhouse**, **SuccessFactors**, or "strict ATS format" by name → use **word-resume-builder** (specialized for strict-ATS parsers)
- User wants PDF only without LaTeX source → ask if they want `.tex` (this skill) or `.docx` (Word skill)

### NON-NEGOTIABLES

1. All **7 sections** in fixed order (Contact → Summary → Experience → Internships → Projects → Education → Technical Skills)
2. Fixed job titles, companies, dates, and **locations** — never invent or change
3. **No fabrication** — reframe real experience only
4. **Bold metrics only** in body bullets (e.g., `\textbf{85\%}`) — not tool names
5. **≤4 projects** from the pool in candidate profile
6. Exactly **2 pages** when compiled — no page 3, no trailing whitespace
7. Preserve LaTeX preamble, `\jobentry` macro, 1in margins, Helvetica 11pt

### IF JD MISSING

**STOP.** Ask the user to paste the job description (or URL). Do not tailor without a JD.

---

## Reference files (read when tailoring)

| When | Read |
| --- | --- |
| Before any edit | `../shared/candidate-profile.md` — fixed fields, experience index, project pool |
| Bullet editing | `../shared/bullet-strategy.md` — Step 0, edit vs add, verbs, page fill |
| Before output | `../shared/checklist.md` — single pre-output checklist |
| LaTeX structure | `references/baseline.tex` — full starting template |
| LaTeX rules | `references/formatting.md` — macros, anti-patterns, ATS |

---

## Primary Workflow

When the user provides a **job description** and wants LaTeX output:

### Step 0 — JD gate

**STOP** if no JD — ask user to paste it.

### Step 1 — READ candidate profile

**READ** `../shared/candidate-profile.md`. Do not invent roles, dates, locations, or employers.

### Step 2 — READ baseline template

**READ** `references/baseline.tex`. Start from this file for every request. Preserve LaTeX structure; modify Summary, bullets, Projects (≤4), and Technical Skills only.

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

### Step 7 — OUTPUT NOW

**OUTPUT NOW:** Return the **complete raw LaTeX** from `\documentclass` through `\end{document}`.

- No markdown fences
- No commentary unless user asks
- User compiles in Overleaf with `pdflatex`

---

## User trigger phrases

- "Give me LaTeX for Overleaf for this JD"
- "Update my LaTeX resume"
- "Tailor my resume in tex"
- "ATS optimize my LaTeX resume"

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
- LaTeX preamble, `\jobentry`, margins, font
- Fabricated experience or metrics

---

## LaTeX essentials (details in references/formatting.md)

### Job header

Title left, dates **right-aligned** on the same line via `\hfill` inside `\jobentry`:

```latex
\jobentry{Full Stack Developer}{Tanishq \& ProwessIQ Private Limited — Chennai, India}{Mar 2020 -- Sept 2021}
\begin{itemize}
\item Crisp bullet — bold metrics only, e.g., achieving \textbf{99.9\%} uptime.
\end{itemize}
```

Never put dates inline after the title (e.g., `\textbf{Title} — Dates`). Always pass dates as the **third** `\jobentry` argument.

### Spacing rules

- **Never** `\vspace` inside `\begin{itemize}`
- Use `\jobentry` for every role and education entry
- No trailing spaces on any output line

### Bold rule

**Metrics only:** `\textbf{85\%}`, `\textbf{300ms}`. Do **not** bold PyTorch, Kubernetes, or other tools in body bullets.

---

## Page fill strategy (quick reference)

**Too much white space:** Add crisp bullets across roles — do not pad with `\vspace` or long paragraphs.

**Over 2 pages:** Trim Tanishq → LTIMindtree → … first. Shorten wording; keep Action + Result.

Full rules: `../shared/bullet-strategy.md`

---

## DELIVER — final checklist

Run `../shared/checklist.md` internally, then confirm:

- [ ] All 7 sections present in order
- [ ] Locations preserved from candidate profile
- [ ] ≤4 JD-relevant projects
- [ ] Bold metrics only in bullets
- [ ] `\jobentry` headers; no `\vspace` in `itemize`
- [ ] Exactly 2 pages when compiled
- [ ] Raw LaTeX output — no markdown fences

---

## Output format

**Default:** Raw LaTeX only — full document, no fences, no preamble explanation.

**If user asks for explanation:** After LaTeX, optionally append a keyword mapping table (JD term → where added).

---

## ATS rules

**DO:** Standard `\item` bullets, single column, exact JD keywords where truthful, `\textbf{}` on metrics only, text PDF via pdflatex.

**DON'T:** Layout tables, photos, fabricated experience, change section order, wrap output in markdown code blocks.
