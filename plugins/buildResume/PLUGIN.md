# Resume Builder Plugin

Two skills for tailoring Abinesh Haridoss's resume to a job description:

| Skill | Slash command | Output |
| --- | --- | --- |
| `latex-resume-builder` | `/latex-resume-builder` | Raw LaTeX (`.tex`) for Overleaf |
| `word-resume-builder` | `/word-resume-builder` | Microsoft Word (`.docx` only — never PDF) |

If the user does not specify format, ask: **LaTeX (.tex) or Word (.docx)?**

## Skills in this plugin

- **latex-resume-builder** → `.tex` / Overleaf
- **word-resume-builder** → `.docx` only (never PDF)

Shared reference files live under `skills/shared/` (not a skill — reference only).

## Fix stale "LaTeX Resume Builder" card (UI steps)

If the Plugins tab still shows the old **"LaTeX Resume Builder"** card, Claude is using a cached copy of an old marketplace entry. The repo is already fixed; you must re-sync:

1. Open **Directory → Plugins → Personal**.
2. Click **`...`** next to **Adoss_claude_skills**.
3. Choose **Remove** (or **Refresh / Sync** if available).
4. Click **`+`** and re-add the marketplace: `abinesha312/Adoss_claude_skills`.
5. The card should now read **"Resume Builder (LaTeX + Word)"** — click **`+`** to install.
6. Open **Directory → Skills** — confirm **both** appear:
   - `latex-resume-builder`
   - `word-resume-builder`

## After updating (CLI alternative)

```bash
claude plugin update build-resume@adoss-claude-skills
/reload-plugins
claude plugin list
```

Expected: `build-resume` v1.2.2 shows **both** skills.

## Routing tests

| User request | Expected skill |
| --- | --- |
| "Tailor my resume in Word for this JD: …" | `word-resume-builder` → saves `tailored_resume.docx` |
| "Give me LaTeX for Overleaf for this JD: …" | `latex-resume-builder` → raw LaTeX |
| "Tailor my resume" (no format) | Ask LaTeX vs Word before proceeding |

## Compliance checks

Output must include: all 7 sections, fixed locations, ≤4 projects, metrics-only bold, exactly 2 pages.
