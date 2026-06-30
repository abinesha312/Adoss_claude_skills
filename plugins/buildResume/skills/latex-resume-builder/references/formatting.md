# LaTeX Formatting Reference

Read `baseline.tex` for full starting template. Apply tailoring to Summary, bullets, Projects (≤4), and Technical Skills only.

## Document class and packages (do not change)

```latex
\documentclass[11pt,a4paper]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage{helvet}
\renewcommand{\familydefault}{\sfdefault}
\usepackage{enumitem}
\usepackage{geometry}
\usepackage[hidelinks]{hyperref}
\usepackage{titlesec}
\usepackage{setspace}
\usepackage{fancyhdr}
\usepackage{fontawesome}
```

## Margins, spacing, and macros (do not change)

```latex
\geometry{left=1in, right=1in, top=1in, bottom=1in}
\setlength{\parindent}{0pt}
\setlength{\parskip}{0pt}
\setstretch{1.1}
\titlespacing\section{0pt}{8pt plus 2pt minus 2pt}{4pt plus 2pt minus 2pt}
\titleformat{\section}{\bfseries\large}{}{0em}{}[\titlerule]
\setlist[itemize]{leftmargin=*, itemsep=2pt, topsep=4pt, parsep=0pt, partopsep=0pt}

\newcommand{\jobentry}[3]{%
  \vspace{5pt}%
  \noindent\textbf{#1} \hfill #3\\%
  \textit{#2}%
}
```

## Job header pattern

**Title on the left, dates on the right** (same line). The `\jobentry` macro uses `\hfill` to push dates to the right margin. Company + location on the line below in italics.

Always use `\jobentry{Title}{Company — Location}{Start -- End}` — never put dates inline after the title.

```latex
\jobentry{Full Stack Developer}{Tanishq \& ProwessIQ Private Limited — Chennai, India}{Mar 2020 -- Sept 2021}
\begin{itemize}
\item Single crisp bullet — no \vspace inside this environment.
\end{itemize}
```

Renders as:

```
Full Stack Developer                                    Mar 2020 -- Sept 2021
Tanishq & ProwessIQ Private Limited — Chennai, India
```

The third argument (`Mar 2020 -- Sept 2021`) is always right-aligned via `\hfill`. Use `--` (LaTeX en-dash), not Unicode `–`.

## Section order (fixed)

1. Contact Header
2. Summary
3. Professional Experience (roles 1–5)
4. Internships (roles 6–8)
5. Projects
6. Education
7. Technical Skills

## Spacing anti-patterns (never do these)

```latex
❌ \begin{itemize}
   \vspace{1mm}
   \item Bullet text

❌ \textbf{Full Stack Developer} — Mar 2020 -- Sept 2021 \\   % dates inline, not right-aligned

❌ \textbf{Title} \location{Dates} \\
   \textit{Company} \hfill \textit{} \\

✅ \jobentry{Full Stack Developer}{Company — Location}{Mar 2020 -- Sept 2021}
   \begin{itemize}
   \item Bullet text
   \end{itemize}
```

## Typography & length

- Helvetica 11pt, 1-inch margins, `\setstretch{1.1}`
- Max **2 pages** when compiled — no page 3, no trailing whitespace on last page
- No photos, skill bars, or layout tables
- Export via `pdflatex` in Overleaf (user compiles; you deliver `.tex`)

## LaTeX safety rules

- Escape special characters: `\&`, `\%`, `\_`
- Use `--` for date ranges (en-dash), not Unicode `–`
- Percent in metrics: `\textbf{99.9\%}`
- **Bold metrics only** in bullets — not `\textbf{PyTorch}` or other tools
- Do not wrap output in markdown code fences

## ATS rules

**DO:** Standard `\item` bullets, single column, exact JD keywords where truthful, text-based PDF via pdflatex

**DON'T:** Tables for layout, photos, fabricated experience, change section order, markdown fences around LaTeX
