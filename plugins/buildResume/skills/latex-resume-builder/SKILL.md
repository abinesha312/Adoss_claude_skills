---
name: latex-resume-builder
description: Tailors Abinesh Haridoss's LaTeX resume to a job description — rewrites Summary and crisp Action+Task+Method+Result bullets, fills exactly 2 pages with no trailing whitespace, and returns the full updated LaTeX document. Use when the user pastes a JD or asks to tailor/update/ATS-optimize their resume.
---

# LaTeX Resume Builder — Abinesh Haridoss

## Primary Workflow (Do This Every Time)

When the user provides a **job description** (or job URL) and asks for a tailored resume:

1. **Analyze the JD** — extract must-have skills, tools, responsibilities, and repeated ATS keywords.
2. **Compare against the baseline resume** (Section: Baseline LaTeX Template below).
3. **Identify missing keywords** — terms in the JD that are not yet reflected in Summary, Experience, Internships, Projects, or Technical Skills.
4. **Rewrite the Summary first** — set the narrative theme (role title + top JD focus areas). Every Experience and Internship bullet must reinforce this same theme.
5. **Tailor bullets using this priority order:**
   - **First choice:** Edit an existing bullet with a **minimal, crisp change** — weave the missing keyword in while keeping one sharp line.
   - **Second choice:** If a keyword cannot fit naturally, **add a new bullet** to the most relevant role.
   - **Also update:** Technical Skills to cover high-priority JD keywords the candidate actually uses.
6. **Fill up to 2 pages** — no overflow to page 3; no large trailing blank space on the last page. If white space remains, add bullets **evenly across roles** (see Page Fill Strategy). Never pad by turning every bullet into a long paragraph.
7. **Return the complete updated LaTeX document** — raw LaTeX only, no markdown fences, no commentary unless the user asks.

### User trigger phrases

- "Provide the updated LaTeX resume that should match with the Job description"
- "Tailor my resume for this job"
- "ATS optimize my resume"
- "Rewrite bullets for this JD"
- "Update my LaTeX resume"

### Required user input

```
I'm applying for this job:

[paste job description or URL]
```

Background is already embedded in this skill. **Do not ask the user to re-paste their work history** unless they explicitly want to change roles, dates, or add new experience.

---

## Candidate Profile (Fixed — Never Change)

| Field | Value |
|-------|-------|
| Name | Abinesh Haridoss |
| Phone | +1 346-823-9553 |
| Email | abinesha312@gmail.com |
| GitHub | github.com/abinesha312 |
| LinkedIn | linkedin.com/in/aharido/ |
| Portfolio | abineshharidoss.web.app |

### Experience Index (titles, companies, dates — NEVER change)

| # | Title | Company | Dates | Section |
|---|-------|---------|-------|---------|
| 1 | Lead Assistant Manager/Consultant - II | EXLServices | Dec 2025 – Present | Professional Experience |
| 2 | Associate Software Developer | Trans Union | Feb 2023 – Jul 2023 | Professional Experience |
| 3 | Software Engineer | LTIMindtree (Larsen and Toubro Infotech Mindtree) | Oct 2021 – Feb 2023 | Professional Experience |
| 4 | Full Stack Developer | Tanishq & ProwessIQ Private Limited | Mar 2020 – Sep 2021 | Professional Experience |
| 5 | AI/ML Software and Web Development Intern | Essential Knowledge Systems, LLC | Sep 2025 – Jan 2026 | Internships |
| 6 | Graduate-level research intern | Turing | Sep 2025 – Feb 2026 | Internships |
| 7 | Summer Intern/AI-ML Engineer | Worlds Enterprise Inc. | Jul 2025 – Sep 2025 | Internships |
| 8 | AI Engineer/Student Assistant | University of North Texas | May 2024 – May 2025 | Internships |

### Education (NEVER change)

- **Master of Science in Computer Science** — University of North Texas — Aug 2023 – 2025
- **Bachelor of Engineering in Information Science and Engineering** — Panimalar Engineering College (Anna University) — May 2021

### Default Projects (keep unless user asks to change)

- **Fraud Folio** — AI, Fraud Detection, Meta Llama 3 — github.com/abinesha312/hack_unt_financial_fraud
- **Hybrid Vision Transformer for Small-Scale Image Classification** — PyTorch, Transformers, MixUp, CutMix — github.com/abinesha312/vision-transformer-cifar

---

## Keyword Tailoring Rules

### What to change

| Section | Action |
|---------|--------|
| Summary | Rewrite first — sets the narrative all bullets must align with |
| Experience bullets | Rewrite to match Summary theme + JD keywords; crisp single-line bullets |
| Internship bullets | Same as experience — aligned with Summary, edit first, add if needed |
| Projects | Light keyword alignment only if JD-relevant |
| Technical Skills | Reorder categories and add JD tools the candidate actually uses |

### What NEVER to change

- Name, contact info, URLs
- Job titles, company names, employment dates
- Section order and all 7 mandatory sections
- LaTeX preamble, `\jobentry` macro, margins (1in), font (Helvetica 11pt)
- Fabricated experience — only reframe real work; never invent employers or metrics

### Bullet edit strategy

**Minimal edit example** — JD wants "Kubernetes" and "microservices":

```
Before: Architected fully autonomous LLM agent workflows for healthcare systems using FastAPI...
After:  Architected autonomous LLM agent workflows on Kubernetes microservices using FastAPI, achieving 99.9% uptime on GKE.
```

**New bullet example** — JD wants "RAG" with no existing mention:

```
Add to EXLServices (most recent, most relevant):
\item Built production RAG pipelines with LangChain and vector retrieval on GCP, cutting knowledge lookup latency by 40%.
```

**Good vs bad bullet style:**

```
✅ GOOD (crisp, one line):
\item Deployed AI agents with automated error recovery on GKE, reducing manual intervention by 85% while maintaining HIPAA audit trails.

❌ BAD (bloated, 3 sentences):
\item I was responsible for deploying AI agents. I worked on implementing automated task tracking and error recovery systems. This helped reduce manual intervention by 85% and also maintained compliance for healthcare workflows.
```

### Bullet writing formula — Action + Task/Method + Result

Every bullet should be **one crisp line** (~1–2 lines in PDF, never 3 sentences). Apply this structure when it fits naturally — do not force every element if the bullet reads better without one:

| Component | What to include | Examples |
|-----------|----------------|----------|
| **Action** | Strong past-tense verb opening the bullet | Architected, Deployed, Engineered, Optimized, Led, Built, Designed, Implemented |
| **Task** | What you did + scope (scale, team, domain) | LLM agent workflows for healthcare; evaluation across 80+ departments |
| **Method** | How — tools, systems, approach (bold key tech) | using `\textbf{FastAPI}` on `\textbf{GKE}`; via `\textbf{PyTorch}` and `\textbf{RLHF}` |
| **Result** | Quantified outcome | `\textbf{99.9\%}` uptime; reduced latency by `\textbf{40\%}`; `\textbf{85\%}` less manual work |

**Strong verbs — use:** Architected, Built, Deployed, Designed, Engineered, Implemented, Led, Optimized, Orchestrated, Reduced, Streamlined

**Weak verbs — avoid:** responsible for, helped, assisted, worked on, participated in, involved in

**Readability rules:**
- One achievement per bullet — no compound run-on sentences
- Bold 1–2 JD-aligned technologies per bullet: `\textbf{PyTorch}`
- Keywords woven in naturally — never keyword-dumped or unreadable
- If a Result metric doesn't exist for that bullet, a clear qualitative outcome is fine
- **Never** put `\vspace` inside `\begin{itemize}` — it causes blank lines and broken bullet spacing
- Use `\jobentry{}{}{}` for every role header; use `\setlist[itemize]` for bullet spacing
- Place `\vspace` only **between** employer blocks (outside itemize), via `\jobentry` macro

**Target bullet counts (adjust to fill 2 pages evenly):**
- Full-time roles: 4–7 bullets each (more for recent, fewer for older)
- Internships: 3–5 bullets each
- Distribute new bullets across roles — do not stack them all in one job

### Summary ↔ Bullets alignment (critical)

1. Write the **Summary first** after parsing the JD — pick the JD role title and 3–4 focus themes.
2. Every Experience and Internship bullet must **support the Summary narrative** — same domain language, same priority skills, same tone.
3. If the Summary emphasizes "MLOps pipelines," the EXLServices and LTIMindtree bullets should reflect pipeline/deployment language, not unrelated themes.
4. Projects and Technical Skills reinforce the same themes — clean and scannable, not loaded.

### Keyword coverage checklist (internal — do before output)

- [ ] Summary written first; all bullets align with Summary themes
- [ ] Every Priority-1 JD keyword appears at least once (Summary, bullets, or Skills)
- [ ] Summary role title aligns with JD title (e.g., "Lead AI/ML Engineer", "ML Engineer", "GenAI Engineer")
- [ ] Bullets follow Action + Task/Method + Result — crisp, single-line, no 3-sentence bloat
- [ ] Technical Skills section lists JD tools the candidate has actually used
- [ ] No keyword stuffing — readable, natural sentences
- [ ] Exactly 2 pages — no trailing whitespace, no page 3 overflow
- [ ] All `\textbf{}`, `\href{}`, `\item`, and `\\` syntax is valid LaTeX
- [ ] No trailing spaces at end of lines in LaTeX output

---

## US Resume Design Standards (always follow)

### Typography
- Use **Helvetica** (LaTeX: `helvet` package) — professional sans-serif, closest to Arial/Calibri on US resumes
- **11pt minimum** body text (`\documentclass[11pt,a4paper]{article}`)
- No decorative fonts, skill bars, or icons beyond project link arrows

### Spacing & margins
- **1-inch margins** on all sides (`\geometry{left=1in, right=1in, top=1in, bottom=1in}`)
- **1.0–1.15 line spacing** (`\setstretch{1.1}` via `setspace` package) — clean, not cramped
- Bullet spacing via `enumitem` only — **never** manual `\vspace` inside `itemize`

### Length & format
- **General US rule:** one page unless 10+ years of senior-level experience
- **Abinesh's baseline:** 8 roles + projects may compile to **2 pages** — trim lowest-priority bullets to stay within 2 pages max; never overflow to page 3
- **Export as PDF** (`pdflatex`) — preserves formatting for ATS and all devices
- **No photos** — not standard in US resumes; never add headshots

### Mandatory sections (never omit — match `baseline_resume.tex`)

Every output must include **all seven sections** in this exact order:

| # | Section | Content |
|---|---------|---------|
| 1 | **Contact Header** | Full name, phone, professional email, GitHub, LinkedIn, portfolio |
| 2 | **Summary** | 3–4 sentence elevator pitch — core expertise, passion, fit |
| 3 | **Professional Experience** | Roles 1–4, reverse chronological, action-verb bullets |
| 4 | **Internships** | Roles 5–8, same bullet style as experience |
| 5 | **Projects** | Fraud Folio + Vision Transformer (default) with GitHub links |
| 6 | **Education** | Degree, university, graduation dates, relevant courses |
| 7 | **Technical Skills** | Bulleted categories — tailor keywords from JD (6–10+ hard skills) |

**Technical Skills** serves as Skills & Core Competencies — reorder and keyword-align per JD, but keep all baseline categories unless user explicitly removes one.


## LaTeX Formatting Standards

### Document class and packages (do not change)

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

### Margins, spacing, and macros (do not change)

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

### Job header pattern (use for every role and education entry)

```latex
\jobentry{Job Title}{Company Name}{Start -- End}
\begin{itemize}
\item Single crisp bullet — no \vspace inside this environment.
\item Next bullet directly follows — enumitem controls spacing.
\end{itemize}
```

### Section order (fixed — all seven required)

1. Contact Header
2. Summary
3. Professional Experience (roles 1–4)
4. Internships (roles 5–8)
5. Projects
6. Education
7. Technical Skills

### Spacing anti-patterns (never do these)

```latex
❌ \begin{itemize}
   \vspace{1mm}          % causes blank line before first bullet
   \item Bullet text
   \vspace{1mm}          % causes unwanted gap / next-line spacing

❌ \textbf{Title} \location{Dates} \\   % broken two-arg macro with one arg
   \textit{Company} \hfill \textit{} \\ % empty italic hack adds space

✅ \jobentry{Title}{Company}{Dates}
   \begin{itemize}
   \item Bullet text
   \end{itemize}
```

### Page length — up to 2 pages, no page 3

The resume must **not exceed 2 pages** when compiled to PDF:
- **No trailing whitespace** — last page should end flush with Technical Skills
- **No page 3** — trim oldest-role bullets or tighten wording before dropping JD keywords
- **No orphaned lines** — avoid a section header alone at page bottom with nothing below it

### Page fill strategy

When the last page has unused space at the bottom:

1. **Do NOT** lengthen existing bullets into multi-sentence paragraphs
2. **Do NOT** add `\vspace` inside `itemize` to pad — it breaks bullet alignment
3. **Do** add new crisp bullets distributed **evenly across roles**
4. Prioritize roles most relevant to the JD for extra bullets first
5. New bullets must use real work themes from the baseline — reframe, don't fabricate

When content exceeds 2 pages:

1. Trim bullets from oldest/least JD-relevant roles first (Tanishq → LTIMindtree → …)
2. Shorten bullets — remove filler words, keep Action + Result core
3. Never drop any of the 7 mandatory sections

### LaTeX safety rules

- Escape special characters: `\&` for &, `\%` for %, `\_` for _ in text
- Use `--` for date ranges (en-dash), not Unicode `–`
- Use `\\` for line breaks after `\jobentry` title line (handled inside macro)
- Percent signs in metrics must be escaped: `\textbf{99.9\%}`
- Do not wrap output in markdown code fences

---

## Baseline LaTeX Template

Start from this template for every tailoring request. **Modify Summary, all Experience/Internship bullet content, Projects bullets (if needed), and Technical Skills.** Preserve LaTeX structure, spacing commands, and all fixed fields. Rewrite every bullet to align with the tailored Summary — do not leave baseline wording unchanged.

**Baseline bullets reflect Abinesh's actual work experience** (V75 resume): titles, companies, dates, and projects stay fixed; experience/internship bullets describe real roles and tools (e.g., scikit-learn/XGBoost at LTIMindtree, GKE/Airflow at EXLServices). When tailoring for a JD, reframe bullets — never invent employers, roles, or metrics not grounded in this baseline.

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

\geometry{left=1in, right=1in, top=1in, bottom=1in}
\setlength{\parindent}{0pt}
\setlength{\parskip}{0pt}
\setstretch{1.1}

\titlespacing\section{0pt}{8pt plus 2pt minus 2pt}{4pt plus 2pt minus 2pt}
\titleformat{\section}{\bfseries\large}{}{0em}{}[\titlerule]

\fancypagestyle{plain}{
  \fancyhf{}
  \fancyfoot[C]{\thepage}
  \renewcommand{\headrulewidth}{0pt}
}

\setlist[itemize]{leftmargin=*, itemsep=2pt, topsep=4pt, parsep=0pt, partopsep=0pt}

% Job header: title + right-aligned dates, then company on next line
\newcommand{\jobentry}[3]{%
  \vspace{5pt}%
  \noindent\textbf{#1} \hfill #3\\%
  \textit{#2}%
}

\begin{document}

\begin{center}
  {\LARGE \textbf{Abinesh Haridoss}}\\[4pt]
  +1 346-823-9553 \textbar\
  \href{mailto:abinesha312@gmail.com}{abinesha312@gmail.com} \textbar\
  \href{https://github.com/abinesha312}{github.com/abinesha312} \textbar\
  \href{https://www.linkedin.com/in/aharido/}{linkedin.com/in/aharido/} \textbar\
  \href{https://abineshharidoss.web.app/}{abineshharidoss.web.app}
\end{center}

\section*{Summary}
\textbf{Lead AI/ML Engineer} with a Master's and Bachelor's in Computer Science and built robust, fair, and interpretable \textbf{generative AI systems}. I specialize in \textbf{LLM safeguards}, \textbf{fairness evaluation}, \textbf{bias mitigation}, and \textbf{alignment techniques} including RLHF and DPO. I've deployed production-grade \textbf{foundation models} on distributed infrastructure, conducted rigorous \textbf{toxicity analysis} and \textbf{robustness benchmarks}, and led cross-functional efforts to embed \textbf{trustworthy AI principles} throughout the model lifecycle.

\section*{Professional Experience}

\jobentry{Lead Assistant Manager/Consultant - II}{EXLServices}{Dec 2025 -- Present}
\begin{itemize}
\item Architected fully autonomous \textbf{LLM agent workflows} for healthcare systems using \textbf{FastAPI} with a \textbf{three-tier fail-safe architecture}, implementing production-grade exception handling and achieving \textbf{99.9\%} uptime across distributed microservices on \textbf{Google Kubernetes Engine (GKE)}.
\item Orchestrated end-to-end workflow automation with \textbf{Apache Airflow DAGs}, integrating \textbf{BigQuery} for data warehousing and \textbf{Google Cloud Redis} for sub-\textbf{300ms} inference latency, processing large-scale workloads (\textbf{20GB+} per request) with real-time monitoring via \textbf{JIRA dashboards}.
\item Deployed \textbf{AI agents} with automated task tracking and error recovery, reducing manual intervention by \textbf{85\%} while maintaining built-in compliance and audit trails for healthcare workflows.
\item Implemented distributed caching strategies with \textbf{Redis} on \textbf{GCP}, optimizing high-throughput LLM inference pipelines and reducing backend query load while maintaining HIPAA-compliant data handling and encryption standards.
\item Architected and deployed \textbf{production-grade Agentic App} components using \textbf{MCP servers} and \textbf{LangGraph}, translating product goals into actionable engineering plans with end-to-end CI/CD observability.
\item Collaborated cross-functionally with \textbf{Product and Engineering} teams to deliver \textbf{customer-centric features}, communicating technical trade-offs to leadership and mentoring junior engineers on \textbf{agentic system design}.
\end{itemize}

\jobentry{Associate Software Developer}{TransUnion}{Feb 2023 -- Jul 2023}
\begin{itemize}
\item Developed \textbf{fairness-aware ML models} for credit risk assessment, implementing \textbf{bias mitigation} and \textbf{fairness evaluation} metrics to ensure equitable predictions across demographic groups, improving approval fairness by \textbf{70\%}.
\item Designed \textbf{robustness benchmarks} for credit-scoring ML models using \textbf{PyTorch}, achieving \textbf{99.8\%} accuracy under adversarial conditions and improving anomaly recall by \textbf{25\%}.
\item Established \textbf{evaluation protocols} and monitoring dashboards for model safety, integrating \textbf{toxicity} and \textbf{bias metrics} to track model drift and maintain trustworthy AI standards across production systems.
\item Collaborated across product, data science, and compliance teams to embed \textbf{fairness principles} throughout the ML lifecycle, improving AI governance compliance by \textbf{30\%}.
\item Implemented \textbf{interpretability} techniques for model predictions, providing stakeholders with transparent decision explanations and enabling faster model explainability reviews by \textbf{40\%}.
\end{itemize}

\jobentry{Software Engineer}{Larsen and Toubro Infotech Mindtree}{Oct 2021 -- Feb 2023}
\begin{itemize}
\item Built comprehensive \textbf{evaluation frameworks} for \textbf{ML classification and regression} models, implementing \textbf{fairness metrics}, robustness testing, and safety validation protocols; achieved \textbf{92.4\%} test coverage with automated bias detection and performance regression detection.
\item Implemented end-to-end \textbf{MLOps pipelines} with automated model training, validation, and deployment gates, incorporating \textbf{bias auditing} and fairness checks to enable rapid experimentation and reduce deployment cycles by \textbf{28\%}.
\item Developed scalable ML infrastructure using \textbf{scikit-learn}, \textbf{XGBoost}, and \textbf{LightGBM} for rapid prototyping and production deployment, supporting cross-validation, hyperparameter tuning, and \textbf{A/B testing} workflows across multiple model architectures.
\item Collaborated with data science and product teams on \textbf{model governance} and ethical AI standards, documenting model trade-offs, fairness constraints, and performance baselines to ensure \textbf{responsible ML} practices throughout the development and deployment lifecycle.
\end{itemize}

\jobentry{Full Stack Developer}{Tanishq \& ProwessIQ Private Limited}{Mar 2020 -- Sept 2021}
\begin{itemize}
\item Implemented secure ML model serving infrastructure with comprehensive \textbf{audit logging}, \textbf{explainability} APIs, and access controls, ensuring model transparency and regulatory compliance across enterprise systems.
\item Designed infrastructure for responsible data handling and model evaluation, establishing automated \textbf{bias detection} and \textbf{fairness monitoring} pipelines that improved data governance by \textbf{40\%} and reduced security incidents by \textbf{30\%}.
\item Orchestrated ML infrastructure with automated testing and evaluation gates, supporting \textbf{fairness} and \textbf{safety assessments} before production deployment, reducing model-related incidents by \textbf{60\%} and ensuring \textbf{trustworthy AI} delivery.
\item Established monitoring systems for model performance and safety metrics, enabling real-time detection of fairness degradation and robustness issues, reducing \textbf{MTTR} for model failures by \textbf{42\%} and maintaining enterprise SLAs.
\end{itemize}

\section*{Internships}

\jobentry{AI/ML Software and Web Development Intern}{Essential Knowledge Systems, LLC}{Sept 2025 -- Jan 2026}
\begin{itemize}
\item Developed a knowledge distillation pipeline for the \textbf{GPT-OSS} model using \textbf{Qwen-3 1.5B}, implementing custom loss functions at the \textbf{PyTorch} layer for efficient model inference.
\item Designed a web-based wizard to automate the end-to-end distillation workflow, enabling users to configure and trigger model compression directly from dataset inputs through an intuitive multi-step UI.
\end{itemize}

\jobentry{Graduate-level research intern}{Turing}{Sept 2025 -- Feb 2026}
\begin{itemize}
\item Designed \textbf{LLM fine-tuning} workflows with automated \textbf{fairness evaluation} and \textbf{bias auditing} mechanisms, improving labeling consistency by \textbf{25\%} and reducing annotation errors by \textbf{30\%} through rigorous quality gates.
\item Orchestrated multi-modal \textbf{LLM training pipelines} using \textbf{PyTorch} and \textbf{HuggingFace Transformers}, implementing \textbf{instruction tuning} and \textbf{alignment protocols} to enhance model safety and reduce harmful outputs by \textbf{35\%}.
\item Conducted \textbf{bias audits} and \textbf{fairness evaluations} on training data, identifying and mitigating demographic disparities to improve model safety by \textbf{25\%}.
\end{itemize}

\jobentry{Summer Intern/AI-ML Engineer}{Worlds Enterprise Inc.}{Jul 2025 -- September 2025}
\begin{itemize}
\item Implemented \textbf{red teaming pipelines} to systematically identify adversarial inputs and safety gaps in \textbf{foundation models}, enabling proactive \textbf{robustness} evaluation and iterative model hardening.
\item Developed \textbf{bias mitigation strategies} for anomaly detection systems, conducting \textbf{bias audits} and achieving \textbf{25\%} improvement in fairness across demographic groups.
\item Architected \textbf{explainability} frameworks for LLM-driven workflows, integrating \textbf{interpretability} techniques to provide transparent reasoning and audit trails, improving user trust and regulatory compliance.
\end{itemize}

\jobentry{AI Engineer/Student Assistant}{University of North Texas}{May 2024 -- May 2025}
\begin{itemize}
\item Deployed \textbf{foundation model evaluation frameworks} across \textbf{80+ departments}, implementing \textbf{robustness benchmarks}, \textbf{toxicity analysis}, and \textbf{fairness assessment protocols} to ensure safe model deployment.
\item Configured and deployed \textbf{multi-modal foundation models} (LLaMA 3.2 90B) on GPU infrastructure, implementing \textbf{prompt engineering} best practices and \textbf{instruction tuning} to enhance model alignment and reduce hallucinations.
\item Designed \textbf{rigorous evaluation protocols} with custom \textbf{bias audit frameworks}, measuring model fairness across protected attributes and toxicity thresholds, reducing failure rates by \textbf{30\%} and improving model trustworthiness.
\item Conducted systematic \textbf{red teaming} to identify model vulnerabilities, documenting adversarial examples and safety edge cases, informing iterative model improvements and safeguard development for \textbf{responsible AI}.
\item Fine-tuned \textbf{foundation models} using \textbf{PyTorch} with domain-specific, bias-balanced datasets, improving model safety and fairness while maintaining \textbf{15\%} reduction in demographic bias and \textbf{20\%} improvement in task performance.
\end{itemize}

\section*{Projects}

\noindent\textbf{Fraud Folio} \textbar\ \textit{AI, Fraud Detection, Meta Llama 3} \hfill \href{https://github.com/abinesha312/hack_unt_financial_fraud.git}{\faExternalLink}
\begin{itemize}
\item Engineered a custom \textbf{anomaly detection pipeline} utilizing \textbf{Meta Llama 3} with CUDA optimization for real-time fraud detection, demonstrating expertise in production-ready LLM systems.
\end{itemize}

\vspace{4pt}
\noindent\textbf{Hybrid Vision Transformer for Small-Scale Image Classification} \textbar\ \textit{PyTorch, Transformers, MixUp, CutMix} \hfill \href{https://github.com/abinesha312/vision-transformer-cifar}{\faExternalLink}
\begin{itemize}
\item Developed a \textbf{Hybrid Vision Transformer} combining CNNs and transformers for CIFAR-10 classification, improving feature extraction and model interpretability through attention visualization.
\end{itemize}

\section*{Education}

\jobentry{Master of Science in Computer Science}{University of North Texas}{Aug. 2023 -- 2025}
Relevant Courses: Machine Learning, Algorithms, AI Software Development, Information Retrieval, Big Data and Data Science

\jobentry{Bachelor of Engineering in Information Science and Engineering}{Panimalar Engineering college Affiliated to Anna University}{May. 2021}
Relevant Courses: Operating Systems, Data Structures, DBMS, Computer Networks, Object Oriented Concepts, deep learning

\section*{Technical Skills}
\begin{itemize}
\item \textbf{Programming Languages:} Python, C++, JavaScript, TypeScript, Bash, PowerShell, Shell Scripting.
\item \textbf{ML/DL Frameworks:} PyTorch, TensorFlow, HuggingFace Transformers, ONNX, LangChain, OpenAI API
\item \textbf{Responsible AI \& Safety:} Fairness Evaluation, Bias Auditing, Toxicity Analysis, Red Teaming, Model Alignment, RLHF, DPO, Instruction Tuning, Explainability, Interpretability
\item \textbf{Distributed Training:} PyTorch (FSDP, DDP), Distributed Evaluation Frameworks, NVIDIA Nsight Systems
\item \textbf{Databases:} Redis, MongoDB, DynamoDB, Postgres, Databricks, MySQL
\item \textbf{Cloud \& DevOps:} AWS (Lambda, API Gateway, S3, ECS, EKS), Docker, Terraform, MLOps, Model Monitoring
\end{itemize}

\end{document}
`

---

## Step-by-Step Tailoring Process

### Step 1 — Parse the JD

Extract into three buckets:

| Priority | What to extract |
|----------|----------------|
| P1 — Must-have | Required skills, years, degree, core tools (exact spellings) |
| P2 — Responsibilities | Verbs and outcomes the role owns (build, deploy, evaluate, monitor) |
| P3 — Nice-to-have | Bonus skills, domain terms, certifications |

### Step 2 — Gap analysis

For each P1 keyword, mark:
- **Covered** — already in baseline → optionally strengthen wording
- **Partial** — related term exists → minimal edit to add exact JD phrase
- **Missing** — not present → add via bullet edit or new bullet

### Step 3 — Write Summary, then align all bullets

1. Rewrite **Summary first** — JD role title + 3–4 focus themes that set the narrative.
2. Rewrite **every Experience and Internship bullet** to support the Summary — same keywords, same tone, crisp Action + Task/Method + Result format.
3. For each missing P1 keyword, try a **minimal edit** to the closest existing bullet.
4. If no bullet fits, add a **new crisp bullet** to the most relevant role.
5. Reorder **Technical Skills** so JD-relevant tools appear first.

### Step 4 — Balance to up to 2 pages

1. Estimate page fill after all edits.
2. **Under target length:** add bullets evenly across roles (1 per role, round-robin) — never bloat existing bullets.
3. **Over 2 pages:** trim oldest-role bullets first; tighten wording, don't drop P1 keywords.
4. Verify no trailing whitespace on the last page and no content on page 3.

### Step 5 — Validate and output

Run the Quick Checklist, then output **only** the full `\documentclass...` through `\end{document}`.

---

## Output Format

**Default:** Return raw LaTeX only — no markdown fences, no preamble explanation.

**If user asks for explanation:** After the LaTeX, optionally append a short keyword mapping table showing which JD terms were added and where.

---

## Quick Checklist Before Output

- [ ] **All 7 mandatory sections** present in correct order (Contact → Summary → Experience → Internships → Projects → Education → Technical Skills)
- [ ] **Up to 2 pages** — no trailing whitespace on last page, no page 3
- [ ] Summary written first; all bullets align with Summary themes and JD
- [ ] Every bullet is crisp (1–2 lines) — Action + Task/Method + Result where natural
- [ ] Strong action verbs; no "responsible for" / "helped" / "worked on"
- [ ] All P1 JD keywords covered at least once — readable, not keyword-dumped
- [ ] New bullets distributed evenly across roles (not stacked in one job)
- [ ] Margins unchanged (1in on all sides); Helvetica 11pt; `\setstretch{1.1}`
- [ ] Job titles, companies, dates unchanged
- [ ] `\textbf{}` on key technologies; `\%` escaped in metrics
- [ ] `\jobentry{}{}{}` for role headers — no `\location`, no `\vspace` inside `itemize`
- [ ] Valid LaTeX — compiles without errors; no trailing spaces on any line

---

## ATS Rules

### DO
- Standard `\item` bullets, single column
- Bold technologies inline with `\textbf{}`
- Exact JD keyword phrases where truthful
- Text-based PDF output

### DON'T
- Tables for layout, skill bars, photos
- Fabricate employers, titles, dates, or metrics
- Change LaTeX structure or section names
- Wrap final output in markdown code blocks (unless user explicitly asks)