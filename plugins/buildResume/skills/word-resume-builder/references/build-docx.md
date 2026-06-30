# Build Word Document (.docx)

**Deliverable:** `.docx` only — never PDF, never LaTeX, never markdown pretending to be the resume.

## Setup

```bash
pip install python-docx
```

## Build steps

1. Start from `plugins/buildResume/baseline_resume.docx` if it exists, or build from `references/baseline-content.md`.
2. Apply all tailoring edits to the document object in memory.
3. **Save** to `plugins/buildResume/tailored_resume.docx` (or user-specified path ending in `.docx`).
4. Return **only the full file path** — that is the deliverable.

## Document setup (do not change)

| Setting | Value |
| --- | --- |
| Application | Microsoft Word (.docx) |
| Body font | Calibri 11 pt (or Arial 11 pt) |
| Name / contact | Calibri 16–18 pt bold, centered |
| Section headings | Calibri 12 pt bold, optional bottom border |
| Margins | 1 inch all sides |
| Line spacing | Multiple 1.08–1.15 |
| Page size | US Letter (8.5" × 11") |
| Layout | Single column — no tables for layout |

## python-docx style mapping

| Element | Approach |
| --- | --- |
| Contact block | Centered paragraph, bold name, hyperlinks for email/URLs |
| Section title | `Heading 2` or bold 12 pt + 4 pt spacing after |
| Job title line | Bold title on left + tab + dates **right-aligned** at right margin (tab stop at 6.5 in) |
| Company line | Italic; append location from profile (e.g., `EXLServices — Texas, US`) |
| Bullets | `document.add_paragraph(text, style='List Bullet')` — one achievement each |
| Metrics bold | `run.bold = True` **only on numeric metrics** (85%, 99.9%) |
| Project links | Hyperlink runs to GitHub URLs |
| Skills | List Bullet; category label bold + colon + skills text |

## Job header pattern

```
[Bold] Full Stack Developer                              Mar 2020 – Sep 2021
[Italic] Tanishq & ProwessIQ Private Limited — Chennai, India
• First bullet — crisp one line, metric bold only (e.g., 99.9%).
• Second bullet — no empty paragraph between bullets.
```

Title on the **left**, dates on the **right** (same line). Never place dates inline after an em dash.

### python-docx tab stop (required for every job/education header)

```python
from docx.enum.text import WD_TAB_ALIGNMENT
from docx.shared import Inches

paragraph = document.add_paragraph()
paragraph.paragraph_format.tab_stops.add_tab_stop(Inches(6.5), WD_TAB_ALIGNMENT.RIGHT)
title = paragraph.add_run("Full Stack Developer")
title.bold = True
paragraph.add_run("\tMar 2020 – Sep 2021")
```

## Formatting anti-patterns

```
❌ Empty paragraph between each bullet
❌ Text boxes or tables for layout
❌ Multiple fonts or colors
❌ **Title** — Dates inline after em dash (dates must be right-aligned via tab stop)

✅ List Bullet style, consecutive items
✅ Job header → bullets → 6 pt gap → next job header
✅ Bold only on metrics: reducing manual intervention by 85%
```

## Page length

- Max **2 pages** in Word — no page 3, no trailing whitespace
- See `../shared/bullet-strategy.md` for fill/trim strategy

## Word safety rules

- En-dash in dates: `Dec 2025 – Present`
- Company names with `&` as plain text
- Hyperlinks: full URLs for GitHub, LinkedIn, portfolio, `mailto:` email
- Save as `.docx` (Office Open XML) — not legacy `.doc`

## ATS rules

**DO:** List Bullet paragraphs, single column, bold metrics only, exact JD keywords where truthful, deliver `.docx`

**DON'T:** PDF, layout tables, photos, fabricated experience, markdown instead of file
