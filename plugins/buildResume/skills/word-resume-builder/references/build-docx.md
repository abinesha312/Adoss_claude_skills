# Build Word Document (.docx)

**Deliverable:** `.docx` only — never PDF, never LaTeX, never markdown pretending to be the resume. This document is specialized for **Workday / strict-ATS** parsing — read `references/ats-strict-rules.md` first; every rule there is mandatory here too.

## Setup

```bash
pip install python-docx
```

## Build steps

1. Start from `references/baseline-content.md` (structured starting text, already in `Month YYYY` date format).
2. Apply all tailoring edits to the document object in memory.
3. **Save** to `plugins/buildResume/Abinesh-Haridoss-Resume.docx` (or a user-specified path ending in `.docx`).
4. **Run the Notepad-test verification** (below) before returning.
5. Return **only the full file path** — that is the deliverable.

## Document setup (do not change)

| Setting | Value |
| --- | --- |
| Application | Microsoft Word (.docx) |
| Body font | Calibri 11 pt (or Arial 11 pt) |
| Name / contact | Calibri 16–18 pt bold, centered |
| Section headings | Calibri 12 pt bold, literal text (see `ats-strict-rules.md`) |
| Margins | 1 inch all sides |
| Line spacing | Multiple 1.08–1.15 |
| Page size | US Letter (8.5" × 11") |
| Layout | **Single column** — no tables, no text boxes, no headers/footers |
| Dates | `Month YYYY` (e.g., `December 2025`), `Present` for current role |

## Full build script skeleton

Adapt this end-to-end skeleton rather than writing python-docx calls from scratch — it already encodes every ATS-safety rule (no tables, no header/footer content, tab-stop job headers, working hyperlinks).

```python
from docx import Document
from docx.shared import Inches, Pt, RGBColor
from docx.enum.text import WD_TAB_ALIGNMENT, WD_ALIGN_PARAGRAPH
from docx.enum.style import WD_STYLE_TYPE
from docx.oxml.ns import qn
from docx.oxml import OxmlElement
from docx.opc.constants import RELATIONSHIP_TYPE as RT


def add_hyperlink(paragraph, url, text, bold=False):
    """python-docx has no native hyperlink API — this is the standard OXML workaround."""
    part = paragraph.part
    r_id = part.relate_to(url, RT.HYPERLINK, is_external=True)
    hyperlink = OxmlElement("w:hyperlink")
    hyperlink.set(qn("r:id"), r_id)
    run = OxmlElement("w:r")
    rpr = OxmlElement("w:rPr")
    if bold:
        rpr.append(OxmlElement("w:b"))
    color = OxmlElement("w:color")
    color.set(qn("w:val"), "0563C1")
    rpr.append(color)
    underline = OxmlElement("w:u")
    underline.set(qn("w:val"), "single")
    rpr.append(underline)
    run.append(rpr)
    text_el = OxmlElement("w:t")
    text_el.text = text
    run.append(text_el)
    hyperlink.append(run)
    paragraph._p.append(hyperlink)
    return hyperlink


def add_job_header(document, title, dates, company_location):
    """ATS-safe job header: paragraph + right tab stop — never a table."""
    p = document.add_paragraph()
    p.paragraph_format.tab_stops.add_tab_stop(Inches(6.5), WD_TAB_ALIGNMENT.RIGHT)
    p.paragraph_format.space_after = Pt(0)
    title_run = p.add_run(title)
    title_run.bold = True
    p.add_run(f"\t{dates}")
    company_p = document.add_paragraph()
    company_p.paragraph_format.space_after = Pt(4)
    company_run = company_p.add_run(company_location)
    company_run.italic = True
    return p, company_p


def add_bullet(document, text_segments):
    """text_segments: list of (text, is_bold) tuples — bold ONLY on metrics."""
    p = document.add_paragraph(style="List Bullet")
    for text, is_bold in text_segments:
        run = p.add_run(text)
        run.bold = is_bold
    return p


def add_section_heading(document, heading_text):
    """Literal, ATS-recognized heading text — never a creative alternative."""
    p = document.add_paragraph()
    p.paragraph_format.space_before = Pt(10)
    p.paragraph_format.space_after = Pt(4)
    run = p.add_run(heading_text)
    run.bold = True
    run.font.size = Pt(12)
    return p


def build_document():
    document = Document()

    # Margins + page size (US Letter, 1in all sides)
    for section in document.sections:
        section.top_margin = Inches(1)
        section.bottom_margin = Inches(1)
        section.left_margin = Inches(1)
        section.right_margin = Inches(1)
        # Defensive: ensure header/footer carry NO content (Workday strips them anyway,
        # but leaving stray text there is a common silent bug).
        section.header.is_linked_to_previous = True
        section.footer.is_linked_to_previous = True
        for p in list(section.header.paragraphs):
            p.text = ""
        for p in list(section.footer.paragraphs):
            p.text = ""

    # Base font
    style = document.styles["Normal"]
    style.font.name = "Calibri"
    style.font.size = Pt(11)

    # Contact header — MUST be in the body, first lines (never header/footer)
    name_p = document.add_paragraph()
    name_p.alignment = WD_ALIGN_PARAGRAPH.CENTER
    name_run = name_p.add_run("Abinesh Haridoss")
    name_run.bold = True
    name_run.font.size = Pt(18)

    contact_p = document.add_paragraph()
    contact_p.alignment = WD_ALIGN_PARAGRAPH.CENTER
    contact_p.add_run("+1 346-823-9553 | ")
    add_hyperlink(contact_p, "mailto:abinesha312@gmail.com", "abinesha312@gmail.com")
    contact_p.add_run(" | ")
    add_hyperlink(contact_p, "https://github.com/abinesha312", "github.com/abinesha312")
    contact_p.add_run(" | ")
    add_hyperlink(contact_p, "https://linkedin.com/in/aharido/", "linkedin.com/in/aharido/")
    contact_p.add_run(" | ")
    add_hyperlink(contact_p, "https://abineshharidoss.web.app", "abineshharidoss.web.app")

    # ... Summary, Professional Experience, Internships, Projects, Education,
    #     Technical Skills sections follow the same helper functions above,
    #     built from the tailored content (see baseline-content.md as the source
    #     structure and shared/bullet-strategy.md for bullet edits).

    return document


def notepad_test(document) -> str:
    """Concatenate all body paragraph text in document order for the flow check
    described in ats-strict-rules.md. Also asserts header/footer are empty."""
    for section in document.sections:
        for p in section.header.paragraphs:
            assert not p.text.strip(), "Header must stay empty — Workday strips it anyway."
        for p in section.footer.paragraphs:
            assert not p.text.strip(), "Footer must stay empty — Workday strips it anyway."
    return "\n".join(p.text for p in document.paragraphs if p.text.strip())


if __name__ == "__main__":
    doc = build_document()
    print(notepad_test(doc))  # manually eyeball top-to-bottom order before saving
    doc.save("plugins/buildResume/Abinesh-Haridoss-Resume.docx")
```

## python-docx style mapping (quick reference)

| Element | Approach |
| --- | --- |
| Contact block | Centered paragraph, bold name, `add_hyperlink()` for email/URLs — **never** in a header |
| Section title | `add_section_heading()` — literal ATS-recognized text, bold 12pt |
| Job title line | `add_job_header()` — paragraph + right tab stop at 6.5in, never a table |
| Company line | Italic paragraph; append location (e.g., `EXLServices — Texas, US`) |
| Bullets | `add_bullet()` — `List Bullet` style, one achievement each, bold on metric segments only |
| Metrics bold | Pass `(text, True)` only for numeric metrics (85%, 99.9%) in `add_bullet()` |
| Project links | `add_hyperlink()` to GitHub URLs |
| Skills | `List Bullet`; category label bold + colon + plain skills text |

## Formatting anti-patterns

```
❌ Empty paragraph between each bullet
❌ Tables or text boxes for job-header layout or skills grid
❌ Contact info, name, or page numbers in header/footer
❌ Multiple fonts or colors
❌ Title — Dates inline after em dash (must be right-aligned via tab stop)
❌ Abbreviated dates ("Dec 2025") — use Month YYYY ("December 2025")

✅ List Bullet style, consecutive items, no blank paragraphs
✅ Job header → bullets → 6pt gap → next job header
✅ Bold only on metrics: reducing manual intervention by 85%
✅ Header/footer left empty; all content in document body
```

## Page length

- Max **2 pages** in Word — no page 3, no trailing whitespace
- See `../shared/bullet-strategy.md` for fill/trim strategy

## Word safety rules

- Dates: `Month YYYY` everywhere (`December 2025 – Present`), never abbreviated or numeric
- Company names with `&` as plain text
- Hyperlinks via `add_hyperlink()` only — never plain-text URLs that look like links but aren't clickable, and never inside header/footer
- Save as `.docx` (Office Open XML) — not legacy `.doc`
- Filename: `Abinesh-Haridoss-Resume.docx`

## ATS rules

**DO:** List Bullet paragraphs, single column, bold metrics only, exact JD keywords where truthful, deliver `.docx`, run the Notepad-test check, keep header/footer empty.

**DON'T:** PDF, tables, text boxes, header/footer content, photos, fabricated experience, markdown instead of file, creative section header names.

Full Workday/strict-ATS rationale and checklist: `references/ats-strict-rules.md`.
