---
name: latex-resume-builder
description: Generates and formats ATS-optimized LaTeX resumes with consistent structure, spacing, and keyword alignment for technical roles
---

# LaTeX Resume Builder

## When to Use This Skill
- User needs a LaTeX resume created or updated
- User pastes a Job Description and needs bullet points rewritten
- Resume needs ATS keyword optimization
- Formatting is inconsistent or missing LaTeX standards
- User says: "tailor my resume", "rewrite bullets", "ATS optimize", "update my LaTeX resume"

---

## LaTeX Document Setup

### Document Class
```latex
\documentclass[a4paper,10pt]{article}
```

### Required Packages
```latex
\usepackage[utf8]{inputenc}
\usepackage{enumitem}
\usepackage{geometry}
\usepackage[hidelinks]{hyperref}
\usepackage{titlesec}
\usepackage{parskip}
\usepackage{lmodern}
\usepackage{fancyhdr}
\usepackage{array}
\usepackage{multicol}
\usepackage{fontawesome}
```

---

## Margins

```latex
\geometry{left=0.3in, right=0.3in, top=0.3in, bottom=0.1in}
```

| Side | Value | Standard Min | Status |
|------|-------|-------------|--------|
| Left | 0.3in | 0.5in | ⚠️ Aggressive but functional |
| Right | 0.3in | 0.5in | ⚠️ Aggressive but functional |
| Top | 0.3in | 0.5in | ⚠️ Aggressive but functional |
| Bottom | 0.1in | 0.5in | ❌ Critically small |

> Note: These margins are intentionally tight for single-page density. Do not increase unless content fits comfortably within 1 page.

---

## Font Selection

### Family
- **Current:** `lmodern` (LaTeX Modern — serif-based)
- **ATS-Safe Alternatives:** Times New Roman (`\usepackage{times}`), Calibri, Arial

### Sizes

| Element | LaTeX Command | Approximate Size | Standard Range |
|---------|--------------|-----------------|----------------|
| Name | `\LARGE` | ~17-18pt | 16-20pt ✅ |
| Section Headers | `\bfseries\large` | ~12pt | 12-14pt ✅ |
| Body Text | `10pt` (doc class) | 10pt | 10-12pt ✅ |
| Minimum | — | 10pt | 10pt ✅ |

---

## Spacing

```latex
\setlength{\parindent}{0pt}
\setlength{\parskip}{0pt}
\titlespacing\section{0pt}{5pt plus 2pt minus 2pt}{3pt plus 2pt minus 2pt}
\setlist[itemize]{noitemsep, topsep=0pt}
```

| Element | Current Setting | Standard | Status |
|---------|----------------|----------|--------|
| Line Spacing | 1.0 (default) | 1.0–1.15 | ✅ |
| Space After Paragraphs | 0pt | 6-12pt | ⚠️ Tight |
| Section Spacing | 5pt before / 3pt after | 12-16pt | ⚠️ Compressed |
| Item Spacing | noitemsep (0pt) | Minimal | ⚠️ Tight |

> These are intentionally compressed for 1-page constraint. Acceptable for dense technical resumes.

---

## Section Formatting

```latex
\titleformat{\section}{\bfseries\large}{}{0em}{}[\titlerule]
```

### Standard Section Order
1. Name & Contact Information
2. Professional Summary
3. Professional Experience
4. Projects
5. Education
6. Technical Skills

### Section Header Style
- Bold + Large font + Horizontal rule beneath
- All sections use `\section*{Section Name}` (unnumbered)

---

## Contact Information Template

```latex
\begin{center}
    {\LARGE \textbf{Full Name}} \\
    Phone \textbar\ 
    \href{mailto:email@domain.com}{email@domain.com} \textbar\ 
    \href{https://github.com/username}{github.com/username} \textbar\ 
    \href{https://linkedin.com/in/username}{linkedin.com/in/username} \textbar\ 
    \href{https://portfolio.url}{portfolio.url}
\end{center}
```

### Include
- ✅ Full name
- ✅ Phone number
- ✅ Professional email
- ✅ GitHub URL
- ✅ LinkedIn URL
- ✅ Portfolio URL (if relevant)

### Exclude
- ❌ Full street address
- ❌ Photo
- ❌ Date of birth
- ❌ Personal social media

---

## Summary Section Template

```latex
\section*{Summary}
\vspace{1mm}
\textbf{[Role Title]} with a Master's and Bachelor's in [Field] and over [X] years of experience 
building [domain 1] and [domain 2] with [key trait]. Expertise in [skill 1], [skill 2], 
and [skill 3], with a strong focus on [focus area] and delivering [business impact].
```

### Rules
- Single paragraph only (no multi-paragraph summaries)
- 3–4 lines max
- Bold the role title
- ATS keywords from JD woven naturally

---

## Experience Section Template

```latex
\textbf{[Job Title]} \location{[Start Month Year] – [End Month Year / Present]} \\
\textit{[Company Name]} \hfill \textit{} \
\begin{itemize}
\item [Action verb] + [what] + [how/technology] + [quantified result]
\vspace{1mm}
\item [Action verb] + [what] + [how/technology] + [quantified result]
\vspace{1mm}
\item [Action verb] + [what] + [how/technology] + [quantified result]
\end{itemize}
\vspace{5mm}
```

### Helper Command
```latex
\newcommand{\location}[2]{\hfill #1 \hfill #2}
```

### Bullet Point Rules
- Start with strong action verb (Engineered, Deployed, Architected, Optimized, Implemented)
- Single line per bullet — no wrapping preferred
- End with quantified result: percentages, latency numbers, scale metrics
- Bold key technologies inline: `\textbf{AWS Bedrock}`
- 3–6 bullets per role (more for recent, fewer for older)
- `\vspace{1mm}` between each bullet
- `\vspace{5mm}` after each employer block

---

## Projects Section Template

```latex
\section*{Projects}
\vspace{3mm}
\begin{minipage}[t]{\textwidth}
    \textbf{[Project Name]} \textbar\ 
    \textit{[Tech Stack, Comma Separated]} \hfill \href{[URL]}{\faExternalLink}
\end{minipage}
\begin{itemize}
    \item [Single focused bullet describing what was built and its technical/business impact]
    \vspace{1mm}
    \item [Optional second bullet if needed]
\end{itemize}
\vspace{3mm}
```

### Rules
- 1–2 bullets per project
- Include GitHub link with `\faExternalLink` icon
- List tech stack in `\textit{}` after pipe separator
- Use `Stealth` if project is confidential

---

## Education Section Template

```latex
\section*{Education}
\vspace{3mm}
\textbf{[Degree Name]} \location{[Month Year] – [Year]} \\
\textit{[University Name]} \hfill \textit{} \\ 
Relevant Courses: [Course 1], [Course 2], [Course 3]
\vspace{1mm}
```

---

## Technical Skills Section Template

```latex
\section*{Technical Skills}
\vspace{3mm}
\begin{itemize}
\item \textbf{Programming Languages:} [Lang1], [Lang2], [Lang3]
\item \textbf{JavaScript Frameworks:} [Framework1], [Framework2]
\item \textbf{Back-End Technologies:} [Tech1], [Tech2]
\item \textbf{Python Libraries:} [Lib1], [Lib2]
\item \textbf{Deep Learning \& Distributed Training:} [Tool1], [Tool2]
\item \textbf{Databases:} [DB1], [DB2]
\item \textbf{Cloud \& DevOps:} [Service1], [Service2]
\end{itemize}
```

### Rules
- Bold category label
- Comma-separated values inline
- No columns (ATS risk)
- No skill bars or progress indicators

---

## ATS Formatting Rules

### DO ✅
- Use standard bullet points (`\item`)
- Bold key technologies within bullets
- Use single-column layout only
- Keep contact info in body (not header/footer)
- Use standard section names
- Save as text-based PDF

### DON'T ❌
- Use tables for layout
- Use multi-column sections
- Use text boxes
- Use images or icons for essential info
- Use color for critical text
- Use unusual fonts or emojis

---

## Page Length Rule
- **Under 10 years experience:** 1 page strictly enforced
- Compress bullets, reduce `\vspace`, tighten margins before adding a second page

---

## Bullet Rewrite Workflow (JD Tailoring)

### Step 1 — Analyze JD
Extract:
- Must-have skills (technical tools, languages, frameworks)
- Role responsibilities (action verbs used in JD)
- Quantitative language (scale, performance, throughput)
- ATS keywords (exact phrases repeated in JD)

### Step 2 — Map to Experience
For each employer:
- Match existing bullets to JD requirements
- Replace generic verbs with JD-aligned verbs
- Insert exact keyword matches from JD
- Preserve all real metrics and quantified results

### Step 3 — Rewrite Rules
- Maintain original employer names, job titles, and dates — NEVER change these
- Only rewrite bullet point content
- Keep same LaTeX structure and spacing
- Match bullet count per role (don't add or remove bullets without instruction)
- Bold the most critical JD-matched technology per bullet

### Step 4 — Output
- Deliver full LaTeX code only
- No explanation unless asked
- No format changes outside bullet text

---

## Output Format

Always return:

Full updated LaTeX document with only bullet points changed.
No commentary. No markdown wrapping. Raw LaTeX only.

---

## Quick Checklist Before Output

- ✅ Single page
- ✅ Margins preserved (left=0.3in, right=0.3in, top=0.3in, bottom=0.1in)
- ✅ Font: lmodern, 10pt body
- ✅ Section headers: \bfseries\large with \titlerule
- ✅ Bullets: action verb → technology → quantified result
- ✅ \vspace{1mm} between bullets, \vspace{5mm} between employers
- ✅ JD keywords bolded inline
- ✅ No personal info changed (names, titles, dates preserved)
- ✅ Summary: single paragraph, role title bolded
- ✅ Projects: minipage + faExternalLink format maintained
