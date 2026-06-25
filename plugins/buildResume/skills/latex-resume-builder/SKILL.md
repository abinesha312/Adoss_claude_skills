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
6. **Fill exactly 2 pages** — no trailing blank space at the bottom of page 2, no overflow to page 3. If white space remains, add bullets **evenly across roles** (see Page Fill Strategy). Never pad by turning every bullet into a long paragraph.
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
- LaTeX preamble, packages, margins, spacing commands, section order
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
- Keep `\vspace{1mm}` after each `\item`
- Use `\vspace{5mm}` after each employer block in Professional Experience
- Use `\vspace{3mm}` between Internship employer blocks

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

## LaTeX Formatting Standards

### Document class and packages

```latex
\documentclass[a4paper,10pt]{article}
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

### Margins and spacing (do not change)

```latex
\geometry{left=0.3in, right=0.3in, top=0.3in, bottom=0.1in}
\setlength{\parindent}{0pt}
\setlength{\parskip}{0pt}
\titlespacing\section{0pt}{5pt plus 2pt minus 2pt}{3pt plus 2pt minus 2pt}
\setlist[itemize]{noitemsep, topsep=0pt}
\newcommand{\location}[2]{\hfill #1 \hfill #2}
\titleformat{\section}{\bfseries\large}{}{0em}{}[\titlerule]
```

### Section order (fixed)

1. Name & Contact
2. Summary
3. Professional Experience (roles 1–4)
4. Internships (roles 5–8)
5. Projects
6. Education
7. Technical Skills

### Page length — exactly 2 pages

The resume must **fill exactly 2 pages** when compiled to PDF:
- **No trailing whitespace** — page 2 should end flush with content (Technical Skills or last section item), not half-empty
- **No page 3** — if content overflows, trim lowest-priority bullets or tighten wording before removing JD keywords
- **No orphaned lines** — avoid a section header alone at the top of page 2 with nothing below it

### Page fill strategy

When page 2 has unused space at the bottom:

1. **Do NOT** lengthen existing bullets into multi-sentence paragraphs
2. **Do** add new crisp bullets distributed **evenly across roles** — e.g., 1 bullet to EXLServices, 1 to Trans Union, 1 to LTIMindtree, 1 to an internship
3. Prioritize roles most relevant to the JD for extra bullets first
4. New bullets must use real work themes from the baseline — reframe, don't fabricate
5. Fine-tune `\vspace` only as a last resort (±1mm) — prefer content over spacing hacks

When content exceeds 2 pages:

1. Trim bullets from oldest/least JD-relevant roles first (Tanishq → LTIMindtree → …)
2. Shorten bullets — remove filler words, keep Action + Result core
3. Never drop Summary, Education, or Technical Skills sections

### LaTeX safety rules

- Escape special characters: `\&` for &, `\%` for %, `\_` for _ in text
- Use `\\` for line breaks after title/company lines (not a lone `\`)
- Use `\vspace{-3pt}` not `\vspace{-3px}` (px is invalid in standard LaTeX)
- Percent signs in metrics must be escaped: `\textbf{99.9\%}`
- Do not wrap output in markdown code fences

---

## Baseline LaTeX Template

Start from this template for every tailoring request. **Modify Summary, all Experience/Internship bullet content, Projects bullets (if needed), and Technical Skills.** Preserve LaTeX structure, spacing commands, and all fixed fields. Rewrite every bullet to align with the tailored Summary — do not leave baseline wording unchanged.

```latex
\documentclass[a4paper,10pt]{article}
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

% Page geometry settings
\geometry{left=0.3in, right=0.3in, top=0.3in, bottom=0.1in}
\setlength{\parindent}{0pt}
\setlength{\parskip}{0pt}

% Customizing section formatting
\titlespacing\section{0pt}{5pt plus 2pt minus 2pt}{3pt plus 2pt minus 2pt}
\titleformat{\section}{\bfseries\large}{}{0em}{}[\titlerule]

% Custom header settings
\fancypagestyle{plain}{
\fancyhf{}
\fancyfoot[C]{\thepage} 
\renewcommand{\headrulewidth}{0pt} 
}

% Reduce space between list items
\setlist[itemize]{noitemsep, topsep=0pt}

% Helper for right-aligning date and location
\newcommand{\location}[2]{\hfill #1 \hfill #2}


\begin{document}

% Name and Contact Info
\begin{center}
    {\LARGE \textbf{Abinesh Haridoss}} \\
    +1 346-823-9553 \textbar\ \href{mailto:abinesha312@gmail.com}{abinesha312@gmail.com} \textbar\ \href{https://github.com/abinesha312}{github.com/abinesha312} \textbar\ \href{https://www.linkedin.com/in/aharido/}{linkedin.com/in/aharido/} \textbar\ \href{https://abineshharidoss.web.app/}{abineshharidoss.web.app}
\end{center}

\vspace{-1mm}

\section*{Summary}
\vspace{1mm}
\textbf{Lead AI/ML Engineer} with a Master's and Bachelor's in Computer Science and built robust, fair, and interpretable \textbf{generative AI systems}. I specialize in \textbf{LLM safeguards}, \textbf{fairness evaluation}, \textbf{bias mitigation}, and \textbf{alignment techniques} including RLHF and DPO. I've deployed production-grade \textbf{foundation models} on distributed infrastructure, conducted rigorous \textbf{toxicity analysis} and \textbf{robustness benchmarks}, and led cross-functional efforts to embed \textbf{trustworthy AI principles} throughout the model lifecycle.


% Experience Section
\section*{Professional Experience}
\textbf{Lead Assistant Manager/Consultant - II} \location{Dec 2025 – Present} \\
\textit{EXLServices} \hfill \textit{} \\
\begin{itemize}
\vspace{1mm}
\item Architected fully autonomous \textbf{LLM agent workflows} for healthcare systems using \textbf{FastAPI} with a \textbf{three-tier fail-safe architecture}, implementing production-grade exception handling and achieving \textbf{99.9\% uptime} across distributed microservices on \textbf{Google Kubernetes Engine (GKE)}.
\vspace{1mm}

\item Orchestrated end-to-end workflow automation with \textbf{Apache Airflow DAGs}, integrating \textbf{BigQuery} for data warehousing and \textbf{Google Cloud Redis} for sub-\textbf{300ms inference latency}, processing \textbf{20GB+ per request} with real-time monitoring via \textbf{JIRA dashboards}.
\vspace{1mm}

\item Deployed \textbf{AI agents} with automated task tracking and error recovery, reducing manual intervention by \textbf{85\%} while maintaining built-in compliance and audit trails for healthcare workflows.
\vspace{1mm}

\item Implemented distributed caching strategies with \textbf{Redis} on \textbf{GCP}, optimizing high-throughput LLM inference pipelines and reducing backend query, while maintaining HIPAA-compliant data handling and encryption standards.
\vspace{1mm}

\item Architected and deployed \textbf{production-grade Agentic App} components using \textbf{MCP servers} and \textbf{LangGraph}, translating product goals into actionable engineering plans with end-to-end CI/CD observability.
\vspace{1mm}

\item Collaborated cross-functionally with \textbf{Product and Engineering} teams to deliver \textbf{customer-centric features}, communicating technical trade-offs to leadership and mentoring junior engineers on \textbf{agentic system design}.
\end{itemize}

\textbf{Associate Software Developer} \location{Feb 2023 – Jul 2023} \\
\textit{TransUnion} \hfill \textit{} \\
\begin{itemize}
\vspace{1mm}
\item Developed \textbf{fairness-aware ML models} for credit risk assessment, implementing \textbf{bias mitigation} and \textbf{fairness evaluation} metrics to ensure equitable predictions across demographic groups, improving approval fairness by \textbf{70\%}.
\vspace{1mm}
\item Designed \textbf{robustness benchmarks} for credit-scoring ML models using \textbf{PyTorch}, achieving real-time fraud detection with \textbf{99.8\% robustness} and \textbf{25\%} improved anomaly recall under adversarial conditions.
\vspace{1mm}
\item Established \textbf{evaluation protocols} and monitoring dashboards for model safety, integrating \textbf{toxicity} and \textbf{bias metrics} to track model drift and maintain trustworthy AI standards across production systems.
\vspace{1mm}
\item Collaborated across product, data science, and compliance teams to embed \textbf{fairness principles} throughout the ML lifecycle, reducing regulatory risk and ensuring \textbf{responsible AI} governance by \textbf{30\%}.
\vspace{1mm}
\item Implemented \textbf{interpretability} techniques for model predictions, providing stakeholders with transparent decision explanations and enabling faster model explainability reviews by \textbf{40\%}.
\end{itemize}
\vspace{5mm}

\textbf{Software Engineer} \location{Oct 2021 – Feb 2023} \\
\textit{Larsen and Toubro Infotech Mindtree} \hfill \textit{} \\
\begin{itemize}
\vspace{1mm}
\item Built \textbf{evaluation frameworks} for ML models with comprehensive metrics tracking, ensuring \textbf{fairness}, \textbf{robustness}, and \textbf{safety} compliance; achieved \textbf{92.4\% test coverage} with bias and regression detection.
\vspace{1mm}
\item Implemented \textbf{MLOps pipelines} with automated \textbf{model evaluation} and \textbf{bias auditing} gates, enabling rapid experimentation with alignment techniques and reducing model deployment time by \textbf{28\%}.
\vspace{1mm}
\item Engineered distributed ML infrastructure with \textbf{PyTorch} supporting foundation model experimentation, enabling fine-tuning, \textbf{RLHF}, and safety-focused model development across \textbf{10-node GPU clusters}.
\vspace{1mm}
\item Established monitoring and alerting for model safety metrics including toxicity, bias drift, and robustness scores, reducing mean-time-to-detection (\textbf{MTTD}) for model failures by \textbf{42\%} and maintaining \textbf{99.9\%} uptime.
\vspace{1mm}
\item Collaborated with cross-functional teams on model governance, documenting fairness trade-offs and safety constraints to embed \textbf{responsible AI principles} throughout the development and deployment lifecycle.
\end{itemize}
\vspace{5mm}

\textbf{Full Stack Developer} \location{Mar 2020 – Sept 2021} \\
\textit{Tanishq \& ProwessIQ Private Limited} \hfill \textit{} \\
\begin{itemize}
\vspace{1mm}
\item Implemented secure ML model serving infrastructure with comprehensive \textbf{audit logging}, \textbf{explainability} APIs, and access controls, ensuring model transparency and regulatory compliance across enterprise systems.

\vspace{1mm}
\item Designed infrastructure for responsible data handling and model evaluation, establishing automated \textbf{bias detection} and \textbf{fairness monitoring} pipelines that improved data governance by \textbf{40\%} and reduced security incidents by \textbf{30\%}.
\vspace{1mm}
\item Orchestrated ML infrastructure with automated testing and evaluation gates, supporting \textbf{fairness} and \textbf{safety assessments} before production deployment, reducing model-related incidents by \textbf{60\%} and ensuring \textbf{trustworthy AI} delivery.

\vspace{1mm}
\item Established monitoring systems for model performance and safety metrics, enabling real-time detection of fairness degradation and robustness issues, reducing \textbf{MTTR} for model failures by \textbf{42\%} and maintaining enterprise SLAs.
\vspace{1mm}

\end{itemize}
\vspace{3mm}

\section*{Internships}

\vspace{3mm}
\textbf{AI/ML Software and Web Development Intern} \location{Sept 2025 – Jan 2026} \\
\textit{Essential Knowledge Systems, LLC} \hfill \textit{} \\
\begin{itemize}
     \item Developed a knowledge distillation pipeline for the \textbf{GPT-OSS} model using \textbf{Qwen-3 1.5B}, implementing custom loss functions at the PyTorch layer for efficient model inference.
     \item Designed a web-based wizard at automating the end-to-end distillation workflow, enabling users to configure and trigger model compression directly from dataset inputs through an intuitive multi-step UI.

\end{itemize}
\vspace{3mm}

\textbf{Graduate-level research intern} \location{Sept 2025 – Feb 2026} \\
\textit{Turing} \hfill \textit{} \\
\begin{itemize}
\item Designed \textbf{LLM fine-tuning} workflows with automated \textbf{fairness evaluation} and \textbf{bias auditing} mechanisms, improving labeling consistency by \textbf{25\%} and reducing annotation errors by \textbf{30\%} through rigorous quality gates.
\vspace{1mm}
\item Orchestrated multi-modal \textbf{LLM training pipelines} using \textbf{PyTorch} and \textbf{HuggingFace Transformers}, implementing \textbf{instruction tuning} and \textbf{alignment protocols} to enhance model safety and reduce harmful outputs by \textbf{35\%}.
\vspace{1mm}
\item Conducted \textbf{bias audits} and \textbf{fairness evaluations} on training data, identifying and mitigating demographic disparities to improve model safety by \textbf{25\%}.
\vspace{1mm}
\end{itemize}

\vspace{3mm}
\textbf{Summer Intern/AI-ML Engineer} \location{Jul 2025 – September 2025} \\
\textit{Worlds Enterprise Inc.} \hfill \textit{} \\
\begin{itemize}
\item Implemented \textbf{red teaming pipelines} to systematically identify adversarial inputs and safety gaps in \textbf{foundation models}, enabling proactive \textbf{robustness} evaluation and iterative model hardening.
\vspace{1mm}

\item Developed \textbf{bias mitigation strategies} for anomaly detection systems, conducting \textbf{bias audits} and achieving \textbf{25\%} improvement in fairness across demographic groups.
\vspace{1mm}
    \item Architected \textbf{explainability} frameworks for LLM-driven workflows, integrating \textbf{interpretability} techniques to provide transparent reasoning and audit trails, improving user trust and regulatory compliance.
\end{itemize}
\vspace{4mm}

\textbf{AI Engineer/Student Assistant} \location{May 2024 – May 2025} \\
\textit{University of North Texas} \hfill \textit{} \\
\hfill  \hfill 
\begin{itemize}

\item Deployed \textbf{foundation model evaluation frameworks} across \textbf{80+ departments}, implementing \textbf{robustness benchmarks}, \textbf{toxicity analysis}, and \textbf{fairness assessment protocols} to ensure safe model deployment.
\vspace{1mm}
\item Configured and deployed \textbf{multi-modal foundation models} (LLaMA 3.2 90B) on GPU infrastructure, implementing \textbf{prompt engineering} best practices and \textbf{instruction tuning} to enhance model alignment and reduce hallucinations.
\vspace{1mm}
\item Designed \textbf{rigorous evaluation protocols} with custom \textbf{bias audit frameworks}, measuring model fairness across protected attributes and toxicity thresholds, reducing failure rates by \textbf{30\%} and improving model trustworthiness.
\vspace{1mm}
\item Conducted systematic \textbf{red teaming} to identify model vulnerabilities, documenting adversarial examples and safety edge cases, informing iterative model improvements and safeguard development for \textbf{responsible AI}.
\vspace{1mm}
\item Fine-tuned \textbf{foundation models} using \textbf{PyTorch} with domain-specific, bias-balanced datasets, improving model safety and fairness while maintaining \textbf{15\%} reduction in demographic bias and \textbf{20\%} improvement in task performance.

\end{itemize}

\vspace{-3pt}

\section*{Projects}

\vspace{3mm}
\begin{minipage}[t]{\textwidth}
\textbf{Fraud Folio} \textbar\ \textit{AI, Fraud Detection, Meta Llama 3} \hfill  \hfill \href{https://github.com/abinesha312/hack_unt_financial_fraud.git}{\faExternalLink}

\end{minipage}

\begin{itemize}
\item Engineered a custom \textbf{anomaly detection pipeline} utilizing \textbf{Meta Llama 3} with CUDA optimization for real-time fraud detection, demonstrating expertise in production-ready LLM systems.
\end{itemize}

\vspace{3mm}

\begin{minipage}[t]{\textwidth}
    \textbf{Hybrid Vision Transformer for Small-Scale Image Classification} \textbar\ \textit{PyTorch, Transformers, MixUp, CutMix} \hfill \href{https://github.com/abinesha312/vision-transformer-cifar}{\faExternalLink}
\end{minipage}
\begin{itemize}
    \item Developed a \textbf{Hybrid Vision Transformer} combining CNNs and transformers for CIFAR-10 classification, improving feature extraction and model interpretability through attention visualization. 
\end{itemize}

\section*{Education}
\vspace{3mm}
\textbf{Master of Science in Computer Science} \location{Aug. 2023 – 2025} \\
\textit{University of North Texas} \hfill \textit{} \\ 
Relevant Courses: Machine Learning, Algorithms, AI Software Development, Information Retrieval, Big Data and Data Science

\vspace{1mm}

\textbf{Bachelor of Engineering in Information Science and Engineering} \location{May. 2021} \\
\textit{Panimalar Engineering college Affiliated to Anna University } \hfill \textit{} \\ 
Relevant Courses: Operating Systems, Data Structures, DBMS, Computer Networks, Object Oriented Concepts, deep learning

\section*{Technical Skills}
\vspace{3mm}
\begin{itemize}
\item \textbf{Programming Languages:} Python, C++, JavaScript, TypeScript, Bash, PowerShell, Shell Scripting.
\item \textbf{ML/DL Frameworks:} PyTorch, TensorFlow, HuggingFace Transformers, ONNX, LangChain, OpenAI API
\item \textbf{Responsible AI \& Safety:} Fairness Evaluation, Bias Auditing, Toxicity Analysis, Red Teaming, Model Alignment, RLHF, DPO, Instruction Tuning, Explainability, Interpretability
\item \textbf{Distributed Training:} PyTorch (FSDP, DDP), Distributed Evaluation Frameworks, NVIDIA Nsight Systems
\item \textbf{Databases:} Redis, MongoDB, DynamoDB, Postgres, Databricks, MySQL
\item \textbf{Cloud \& DevOps:} AWS (Lambda, API Gateway, S3, ECS, EKS), Docker, Terraform, MLOps, Model Monitoring

\end{itemize}
\vspace{1mm}
\end{document}
```

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

### Step 4 — Balance to exactly 2 pages

1. Estimate page fill after all edits.
2. **Under 2 pages:** add bullets evenly across roles (1 per role, round-robin) — never bloat existing bullets.
3. **Over 2 pages:** trim oldest-role bullets first; tighten wording, don't drop P1 keywords.
4. Verify no trailing whitespace on page 2 and no content on page 3.

### Step 5 — Validate and output

Run the Quick Checklist, then output **only** the full `\documentclass...` through `\end{document}`.

---

## Output Format

**Default:** Return raw LaTeX only — no markdown fences, no preamble explanation.

**If user asks for explanation:** After the LaTeX, optionally append a short keyword mapping table showing which JD terms were added and where.

---

## Quick Checklist Before Output

- [ ] **Exactly 2 pages** — full page 2, no trailing whitespace, no page 3
- [ ] Summary written first; all bullets align with Summary themes and JD
- [ ] Every bullet is crisp (1–2 lines) — Action + Task/Method + Result where natural
- [ ] Strong action verbs; no "responsible for" / "helped" / "worked on"
- [ ] All P1 JD keywords covered at least once — readable, not keyword-dumped
- [ ] New bullets distributed evenly across roles (not stacked in one job)
- [ ] Margins unchanged (0.3in / 0.3in / 0.3in / 0.1in)
- [ ] Job titles, companies, dates unchanged
- [ ] `\textbf{}` on key technologies; `\%` escaped in metrics
- [ ] `\\` line breaks after title/company lines (not lone `\`)
- [ ] `\vspace{1mm}` between bullets; `\vspace{5mm}` between full-time employers
- [ ] Section order: Contact → Summary → Experience → Internships → Projects → Education → Skills
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
