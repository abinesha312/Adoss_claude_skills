# Resume Builder Plugin

Two skills for tailoring Abinesh Haridoss's resume to a job description:

| Skill | Output |
| --- | --- |
| `latex-resume-builder` | Raw LaTeX (`.tex`) for Overleaf |
| `word-resume-builder` | Microsoft Word (`.docx` only — never PDF) |

If the user does not specify format, ask: **LaTeX (.tex) or Word (.docx)?**

## Skills in this plugin

- **latex-resume-builder** → `.tex` / Overleaf
- **word-resume-builder** → `.docx` only (never PDF)

Shared reference files live under `skills/shared/` (candidate profile, bullet strategy, checklist).

## After updating

```bash
claude plugin update build-resume@adoss-claude-skills
```

Then in Claude Code:

```
/reload-plugins
```

Verify both skills appear:

```bash
claude plugin list
```

Expected: `build-resume` shows **both** `latex-resume-builder` and `word-resume-builder`.

## Routing tests

| User request | Expected skill |
| --- | --- |
| "Tailor my resume in Word for this JD: …" | `word-resume-builder` → saves `tailored_resume.docx` |
| "Give me LaTeX for Overleaf for this JD: …" | `latex-resume-builder` → raw LaTeX |
| "Tailor my resume" (no format) | Ask LaTeX vs Word before proceeding |

## Compliance checks

Output must include: all 7 sections, fixed locations, ≤4 projects, metrics-only bold, exactly 2 pages.
