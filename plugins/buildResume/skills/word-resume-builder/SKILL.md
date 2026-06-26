---
name: word-resume-builder
description: Tailors Abinesh Haridoss's Word resume to a job description — rewrites Summary and crisp Action+Task+Method+Result bullets, fills exactly 2 pages with no trailing whitespace, and saves the deliverable as .docx only (never PDF). Use when the user pastes a JD or asks for a Word/docx tailored resume.
---

# Word Resume Builder — Abinesh Haridoss

## Primary Workflow (Do This Every Time)

When the user provides a **job description** (or job URL) and asks for a tailored resume:

1. **Analyze the JD** — extract must-have skills, tools, responsibilities, and repeated ATS keywords and find what's missing.
2. **Compare against the baseline resume** (Section: Baseline Word Document Template below).
3. **Identify missing keywords** — terms in the JD that are not yet reflected in Summary, Experience, Internships, Projects, or Technical Skills.
4. **Rewrite the Summary first** — set the narrative theme (role title + top JD focus areas). Every Experience and Internship bullet must reinforce this same theme.
5. **Tailor bullets using this priority order:**
   - **First choice:** Edit an existing bullet with a **minimal, crisp change** — weave the missing keyword in while keeping one sharp line.
   - **Second choice:** If a keyword cannot fit naturally, **add a new bullet** to the most relevant role and blends with the buiness what I have worked it should be a different end to end changes it should blend with the current changes.
   - **Also update:** Technical Skills to cover high-priority JD keywords the candidate actually uses.
6. **Fill up to 2 pages** — no overflow stricly 2 pages only; no large trailing blank space on the last page. If white space remains, add bullets **evenly across roles based on the job description and requirements that blends with the current experience** (see Page Fill Strategy). Never pad by turning every bullet into a long paragraph most of the bullet points should be 1 line or max to max 2 lines that fits a standard Word page layout in Microsoft Word.
7. **Build and save the complete updated Word document** — save as `.docx` using `python-docx` (see Build Method below). No markdown fences around file content unless the user asks.

### User trigger phrases

- "Provide the updated Word resume that should match with the Job description"
- "Tailor my resume for this job"
- "ATS optimize my resume"
- "Rewrite bullets for this JD"
- "Update my Word resume"
- "Give me the updated resume"
- "Word resume" / "docx resume"
- "Build my resume in Word"

### Required user input

```
I'm applying for this job:

[paste job description or URL]
```

Background is already embedded in this skill. **Do not ask the user to re-paste their work history** unless they explicitly want to change roles, dates, or add new experience.

---

## Candidate Profile (Fixed — Never Change)

| Field     | Value                            |
| --------- | -------------------------------- |
| Name      | Abinesh Haridoss                 |
| Phone     | +1 346-823-9553                  |
| Email     | abinesha312@gmail.com            |
| GitHub    | https://github.com/abinesha312   |
| LinkedIn  | https://linkedin.com/in/aharido/ |
| Portfolio | https://abineshharidoss.web.app  |

### Experience Index (titles, companies, dates — NEVER change)

| # | Title | Company | Dates | Section |Location |
| --- | ----------------------------------------- | ------------------------------------------------- | ------------------- | ----------------------- | |  
| 1 | Lead Assistant Manager/Consultant - II | EXLServices | Dec 2025 – Present | Professional Experience |Texas, US |
| 2 | Associate Software Developer | Trans Union | Feb 2023 – Jul 2023 | Professional Experience |Chennai, India |
| 3 | Software Engineer | LTIMindtree (Larsen and Toubro Infotech Mindtree) | Oct 2021 – Feb 2023 | Professional Experience |Chennai, India
| 4 | Full Stack Developer | Tanishq & ProwessIQ Private Limited | Mar 2020 – Sep 2021 | Professional Experience |Chennai, India|
| 5 | AI/ML Software and Web Development Intern | Essential Knowledge Systems, LLC | Sep 2025 – Jan 2026 | Internships | Texas, US |
| 6 | Graduate-level research intern | Turing | Sep 2025 – Feb 2026 | Professional Experience | Texas, US |
| 7 | Summer Intern/AI-ML Engineer | Worlds Enterprise Inc. | Jul 2025 – Sep 2025 | Internships | Texas, US |
| 8 | AI Engineer/Student Assistant | University of North Texas | May 2024 – May 2025 | Internships | Texas, US |

### Education (NEVER change)

- **Master of Science in Computer Science** — University of North Texas — Aug 2023 – 2025
- **Bachelor of Engineering in Information Science and Engineering** — Panimalar Engineering College (Anna University) — May 2021

### Default Projects (keep unless user asks to change based on the projects and Job Decription fill whatever need to NOT MORE THAN 4 PROJECTS.)

- **Adoss_claude_skills** — Claude Code plugin marketplace — github.com/abinesha312/Adoss_claude_skills
- **mcp-unified** — MCP server for Gmail & LinkedIn integration — github.com/abinesha312/mcp-unified
- **ABB** — Agentic Banking Bot for transactions — github.com/abinesha312/ABB
- **medical_vlm** — Medical Vision-Language Model — github.com/abinesha312/medical_vlm
- **NeMo-Agent-Toolkit** — NVIDIA agent orchestration framework — github.com/abinesha312/NeMo-Agent-Toolkit
- **OGGAI** — Oracle Golden Gate automation — github.com/abinesha312/OGGAI
- **EKS_KD** — Knowledge distillation for LLM training — github.com/abinesha312/EKS_KD
- **MDPS** — Mortgage Default Prediction System — github.com/abinesha312/MDPS
- **SnapEye** — Interview support tool with NLP feedback — github.com/abinesha312/SnapEye
- **UNTGenAI** — UNT GenAI system — github.com/abinesha312/UNTGenAI
- **REPHUB** — Repository maintenance utility — github.com/abinesha312/REPHUB
- **LeetCode** — LeetCode problem solutions — github.com/abinesha312/LeetCode
- **blockchain_voter2** — Blockchain-based voting system — github.com/abinesha312/blockchain_voter2
- **GenAI_UNT** — ChainLit + Llama Stack integration — github.com/abinesha312/GenAI_UNT
- **vision-transformer-cifar** — Interpretable ViT with attention visualization on CIFAR-10 — github.com/abinesha312/vision-transformer-cifar
- **futuredynamic** — Adaptive memory management for LLM inference — github.com/abinesha312/futuredynamic
- **WalletFlowIO** — Digital wallet with blockchain backend — github.com/abinesha312/WalletFlowIO
- **LlamaStack2_0** — Llama 3.2 Vision with Llama Stack — github.com/abinesha312/LlamaStack2_0
- **GPT_Llama2** — Meta Llama2 with Gradio UI — github.com/abinesha312/GPT_Llama2
- **Job-Interview-Simulator** — Real-time NLP interview feedback tool — github.com/abinesha312/Job-Interview-Simulator-with-Real-time-Feedback

---

## Keyword Tailoring Rules

### What to change

| Section            | Action                                                                                           |
| ------------------ | ------------------------------------------------------------------------------------------------ |
| Summary            | Rewrite first — sets the narrative all bullets must align with                                   |
| Experience bullets | Rewrite to match Summary theme + JD keywords; crisp single-line bullets                          |
| Internship bullets | Same as experience — aligned with Summary, edit first, add if needed                             |
| Projects           | Light keyword alignment only if JD-relevant and pick the right project only not all the projects |
| Technical Skills   | Reorder categories and add JD tools the candidate actually uses                                  |

### What NEVER to change

- Name, contact info, URLs
- Job titles, company names, employment dates, location
- Section order and all 7 mandatory sections never miss anything
- Word document styles, job-header layout, margins (1in), font (Calibri 11pt)
- Fabricated experience — only reframe real work; never invent employers or metrics
- don't highligh /bold the text only hight for the metrics

## Bullet & Content Strategy

This is the core of resume tailoring. The goal: make every line earn its place by aligning with the target JD while staying truthful, crisp, and ATS-readable. Work top-down — **parse the JD first, write the Summary, then edit bullets to support it.**

---

### Step 0 — Parse the JD before touching any bullet

Before editing, extract from the job description:

1. **Role title** — the exact title to mirror in the Summary (e.g., "Lead AI/ML Engineer", "GenAI Engineer", "ML Platform Engineer").
2. **Priority-1 keywords** — must-have hard skills/tools named 2+ times or in the title/requirements (e.g., Kubernetes, RAG, PyTorch). These _must_ appear in the final resume.
3. **Priority-2 keywords** — nice-to-haves mentioned once (e.g., Terraform, gRPC). Include where natural.
4. **3–4 focus themes** — the narrative the JD is selling (e.g., "scalable inference", "MLOps automation", "agentic systems").

Everything downstream — Summary, bullets, skills — serves these four outputs.

---

### Decision rule — edit existing vs. add new

For each Priority-1 keyword, decide:

| Situation                                                     | Action                                                                           |
| ------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| Keyword's concept already in a bullet, just unnamed           | **Minimal edit** — weave the keyword into the existing bullet                    |
| Keyword's concept genuinely missing but candidate has done it | **New bullet** — add to the most recent/relevant role                            |
| Candidate has never done it                                   | **Do not fabricate** — surface in Technical Skills only if defensible, else skip |

Prefer editing over adding. New bullets are only for true gaps where a real accomplishment exists.

---

### Pattern 1 — Minimal edit (keyword woven in)

JD wants **"Kubernetes"** and **"microservices"**; the bullet already describes the work but doesn't name them.

```
Before:
Architected fully autonomous LLM agent workflows for healthcare
systems using FastAPI...

After:
Architected autonomous LLM agent workflows as Kubernetes
microservices using FastAPI, achieving 99.9% uptime on GKE.
```

Why it works: the keywords land naturally, scope (healthcare → implied), method (FastAPI/Kubernetes), and result (99.9% uptime) are all present in one line.

---

### Pattern 2 — New bullet (true gap)

JD wants **"RAG"**; no existing bullet mentions retrieval, but the candidate has built RAG pipelines. Add to the most recent, most relevant role.

```
Add to EXLServices (most recent):
• Built production RAG pipelines with LangChain and vector
retrieval on GCP, cutting knowledge lookup latency by 40%.
```

Rule: new bullets go to the **highest-relevance role**, not wherever there's space. Distribute additions across roles so no single job balloons.

---

### The bullet formula — Action + Task/Method + Result

Every bullet is **one crisp line** (~1–2 lines in the document, never 3 sentences). Apply the structure where it fits naturally; don't force every element if the line reads better without one.

| Component  | What to include                                | Examples                                                         |
| ---------- | ---------------------------------------------- | ---------------------------------------------------------------- |
| **Action** | Strong past-tense verb opening the bullet      | Architected, Deployed, Engineered, Optimized, Led, Built         |
| **Task**   | What you did + scope (scale, team, domain)     | LLM agent workflows for healthcare; eval across 80+ departments  |
| **Method** | How — tools, systems, approach (bold key tech) | using FastAPI on GKE; via PyTorch                                |
| **Result** | Quantified outcome (or clear qualitative win)  | **99.9%** uptime; latency down **40%**; **85%** less manual work |

**Strong verbs (use):** ### 🏗️ Building & Creating (Zero-to-One)

          *Use these when you built something from scratch, designed a new system, or introduced a novel solution.*

          * **Authored:** (Great for documentation, core libraries, or standard operating procedures)
          * **Conceptualized:** (Shows high-level system design thinking)
          * **Constructed:** (Good for data pipelines or infrastructure)
          * **Devised:** (Implies creative problem solving)
          * **Formulated:** (Ideal for algorithms, models, or strategies)
          * **Pioneered:** (Use sparingly for truly innovative, first-of-its-kind company projects)
          * **Programmed:** (Direct, unambiguous coding action)
          * **Spearheaded:** (Combines building with taking the initiative)

          ### 🚀 Executing & Deploying (Getting Things to Production)

          *Use these when the focus is on releasing software, managing infrastructure, or connecting systems.*

          * **Executed:** (Strong general action for completing complex tasks)
          * **Integrated:** (Perfect for APIs, third-party services, or merging microservices)
          * **Launched:** (High-impact verb for releasing features/products to users)
          * **Migrated:** (Crucial for cloud transitions, e.g., on-prem to AWS)
          * **Operationalized:** (Taking a prototype/model and making it production-ready)
          * **Provisioned:** (Excellent for DevOps, IaC, and cloud infrastructure)
          * **Shipped:** (Industry-standard term for delivering software)
          * **Systematized:** (Turning a manual process into a repeatable system)

          ### ⚡ Scaling & Improving (Making it Better/Faster/Cheaper)

          *Use these when you took an existing system and improved its performance, cost, or reliability.*

          * **Accelerated:** (For reducing latency, speeding up load times, or faster CI/CD)
          * **Amplified:** (For increasing revenue, user engagement, or throughput)
          * **Automated:** (A top-tier keyword for DevOps, QA, and MLOps)
          * **Modernized:** (Updating legacy codebases or architectures)
          * **Overhauled:** (A massive, fundamental rebuild of a system)
          * **Refactored:** (Specifically for code cleanup and improving maintainability)
          * **Scaled:** (Handling more users, data, or traffic)
          * **Slashed:** (Aggressive, high-impact verb for cutting costs, errors, or latency)
          * **Transformed:** (For major structural or workflow shifts)

          ### 📊 Data, AI & Problem Solving (Analyzing & Fixing)

          *Use these for ML, data engineering, debugging, and quality assurance bullets.*

          * **Analyzed:** (Extracting insights from large datasets)
          * **Audited:** (Checking systems for compliance, security, or performance)
          * **Diagnosed:** (Finding the root cause of complex system failures)
          * **Evaluated:** (A/B testing, model benchmarking, vendor selection)
          * **Forecasted:** (Predictive modeling and trend analysis)
          * **Quantified:** (Putting hard numbers to abstract problems)
          * **Resolved:** (Fixing critical bugs or production outages)
          * **Troubleshot:** (Hands-on problem solving)
          * **Validated:** (Ensuring data integrity, model accuracy, or user needs)

          ### 🤝 Leading & Managing (Taking Charge)

          *Use these to show soft skills, team leadership, and cross-functional alignment (even if you aren't a formal manager).*

          * **Advocated:** (Pushing for best practices, e.g., "Advocated for TDD...")
          * **Championed:** (Leading the adoption of a new tool or culture shift)
          * **Coordinated:** (Managing moving parts across different teams)
          * **Directed:** (Leading a specific project or squad)
          * **Facilitated:** (Running sprint plannings, post-mortems, or architecture reviews)
          * **Mentored:** (Upskilling junior developers or onboarding new hires)
          * **Steered:** (Guiding a project back on track or through ambiguity)

**Weak verbs (avoid):** Here is an expanded list of weak verbs and passive phrases to actively hunt down and eliminate from your resume.

These phrases are dangerous because they read like a generic HR job description rather than a list of personal achievements. They tell the recruiter what you were _supposed_ to do, but not what you _actually accomplished_, and they heavily dilute your ownership of the project.

### 🙈 The "Bystander" Phrases (Dilutes Ownership)

_These make it sound like you were just in the room while the real work was happening. If you were on a team, claim the specific piece of the project you owned._

- **Contributed to:** (What was your exact contribution? Did you write the API? Design the schema?)
- **Part of a team that:** (Remove this completely. Start with the action _you_ took on that team.)
- **Collaborated on:** (A great soft skill, but a weak bullet opener. Better: "Engineered X in collaboration with...")
- **Supported:** (Sounds like a secondary/admin role. Better: "Accelerated team delivery by...")
- **Aided:** (Too passive.)

### 📋 The "Job Description" Traps (Focuses on Duty, Not Impact)

_These phrases state your obligations instead of your victories. They are the fastest way to put a hiring manager to sleep._

- **Tasked with:** (Nobody cares what you were asked to do; they care what you delivered.)
- **Duties included:** (Instantly reads like a copy-pasted job posting.)
- **Handled:** (Too vague. Did you process data? Resolve tickets? Deploy servers?)
- **In charge of:** (Passive state of being. Better: "Directed," "Orchestrated," or "Led.")
- **Served as:** (Focuses on the title rather than the action.)

### 🥱 The "Low-Effort/Vague" Verbs (Lacks Precision)

_These words technically describe an action, but they are so generic that they waste valuable resume real estate._

- **Utilized / Used:** (Never open a bullet with this. Don't say "Utilized Python to build X." Say "Built X using Python.")
- **Made / Did:** (Too conversational. Use "Architected," "Developed," or "Executed.")
- **Fixed:** (Too simple for complex tech roles. Use "Diagnosed," "Resolved," or "Patched.")
- **Looked at / Explored:** (Use "Analyzed," "Evaluated," or "Audited.")
- **Maintained:** (Implies just keeping the lights on without making improvements. If you must use it, pair it with a metric: "Maintained 99.9% uptime by...")
- **Updated:** (A chore. Use "Modernized," "Refactored," or "Upgraded.")

---

### 🔄 How to perform a "Weak Verb" Audit

If you catch yourself using a weak phrase, use the **"How and What" pivot** to find the strong verb:

- **❌ Weak:** _Responsible for_ the cloud migration.
- _Pivot:_ **How** did you do it? **What** was the result?
- **✅ Strong:** **Orchestrated** the migration of 50+ microservices to AWS, reducing infrastructure costs by 20%.

- **❌ Weak:** _Worked on_ the new machine learning model.
- _Pivot:_ **What** part did you do?
- **✅ Strong:** **Trained and fine-tuned** a custom LLM using PyTorch, improving classification accuracy by 15%.

- **❌ Weak:** _Participated in_ daily code reviews.
- _Pivot:_ **What** was the impact of you doing that?
- **✅ Strong:** **Enforced** strict code quality standards across 4 engineering squads, dropping production bugs by 30%.

---

### Good vs. bad bullets

```
✅ GOOD — crisp, one line, formula applied:
• Deployed AI agents with automated error recovery on GKE,
reducing manual intervention by 85% while maintaining HIPAA
audit trails.

❌ BAD — bloated, weak verbs, 3 sentences:
• I was responsible for deploying AI agents. I worked on
implementing automated task tracking and error recovery systems.
This helped reduce manual intervention by 85% and also maintained
compliance for healthcare workflows.
```

```
✅ GOOD — qualitative result when no metric exists:
• Engineered a vector-retrieval layer with pgvector,
standardizing knowledge access across 6 agent services.

❌ BAD — keyword dump, unreadable:
• Used PyTorch TensorFlow Kubernetes Docker Terraform GCP AWS
RAG LangChain FastAPI for AI agent microservices deployment.
```

---

### Readability rules

- **One achievement per bullet** — no compound run-on sentences.
- **Bold only metrics** in bullets (e.g., **85%**, **99.9%**) — not tools or keywords (per What NEVER to change).
- **Weave keywords naturally** — a reader should never sense keyword-stuffing.
- **Quantify when you can; qualify when you can't** — a concrete qualitative outcome beats a fake number.
- **Lead with the verb** — never start a bullet with "I", "Responsible for", or a noun.

---

### Word formatting rules (these break the document if violated)

- **Never** insert empty paragraphs between bullet items — use Word's bullet list only.
- Use the **job header pattern** (title + dates, company + location) for every role.
- Use **List Bullet** style with tight spacing (0 pt before/after each item).
- Add **6 pt spacing** only **between** employer blocks (blank line or paragraph spacing), not between bullets.
- No trailing spaces at the end of any line in the document.

---

### Bullet count targets (to fill exactly 2 pages, evenly)

| Role type          | Bullets | Notes                                  |
| ------------------ | ------- | -------------------------------------- |
| Full-time (recent) | 5–7     | Most relevant role gets the most depth |
| Full-time (older)  | 4–5     | Trim as roles age                      |
| Internship         | 3–5     | Keep tight                             |

Distribute new bullets across roles — **do not stack them all in one job.** If page 2 is thin, add to mid-tenure roles before padding the most recent one further.

---

### Summary ↔ Bullets alignment (critical)

The Summary is the thesis; every bullet is supporting evidence. They must speak the same language.

1. **Write the Summary first**, right after parsing the JD. Lock in the JD role title + 3–4 focus themes.
2. **Every Experience and Internship bullet must support the Summary narrative** — same domain language, same priority skills, same tone.
3. If the Summary emphasizes "MLOps pipelines", then EXLServices and LTIMindtree bullets must use pipeline/deployment language — not unrelated side projects.
4. **Projects and Technical Skills reinforce the same themes** — clean and scannable, never loaded.

> Test: read the Summary, then read each bullet. If a bullet feels like it belongs to a _different_ resume, rewrite it to align or cut it.

---

### Pre-output checklist (run internally before generating)

- [ ] JD parsed: role title, Priority-1/2 keywords, and 3–4 themes extracted
- [ ] Summary written **first**; all bullets align with Summary themes
- [ ] Summary role title mirrors JD title
- [ ] Every Priority-1 keyword appears ≥1× (Summary, bullets, or Skills)
- [ ] Each edited/new bullet follows Action + Task/Method + Result — single-line, no bloat
- [ ] Bold metrics only in bullets; no keyword stuffing anywhere
- [ ] New bullets placed in most-relevant roles and distributed, not stacked
- [ ] Technical Skills lists only JD tools the candidate has actually used
- [ ] No empty paragraphs between bullets; job headers formatted correctly
- [ ] Exactly 2 pages — no trailing whitespace, no page-3 overflow
- [ ] Hyperlinks clickable; bullets use List Bullet style; no trailing spaces

---

## US Resume Design Standards (always follow)

### Typography

- Use **Calibri** or **Arial** — professional sans-serif standard for US Word resumes
- **11pt minimum** body text (Calibri 11 pt or Arial 11 pt)
- No decorative fonts, skill bars, text boxes for layout, or icons beyond hyperlink text

### Spacing & margins

- **1-inch margins** on all sides (Layout → Margins → Normal, or custom 1" all sides)
- **1.0–1.15 line spacing** (Line spacing: Multiple 1.08 or 1.15) — clean, not cramped
- Bullet spacing via Word list styles only — **never** manual blank lines between bullet items

### Length & format

- **General US rule:** one page unless 10+ years of senior-level experience
- **Abinesh's baseline:** 8 roles + projects may fit **2 pages** in Word — trim lowest-priority bullets to stay within 2 pages max; never overflow to page 3
- **Deliverable is always `.docx`** — never PDF, never ask the user to export PDF, never use `docx2pdf`
- **No photos** — not standard in US resumes; never add headshots

### Mandatory sections (never omit — match `baseline_resume.docx` structure)

Every output must include **all seven sections** in this exact order:

| #   | Section                     | Content                                                              |
| --- | --------------------------- | -------------------------------------------------------------------- |
| 1   | **Contact Header**          | Full name, phone, professional email, GitHub, LinkedIn, portfolio    |
| 2   | **Summary**                 | 3–4 sentence elevator pitch — core expertise, passion, fit           |
| 3   | **Professional Experience** | Roles 1–4, reverse chronological, action-verb bullets                |
| 4   | **Internships**             | Roles 5–8, same bullet style as experience                           |
| 5   | **Projects**                | ≤4 JD-relevant projects from Default Projects pool with GitHub links |
| 6   | **Education**               | Degree, university, graduation dates, relevant courses               |
| 7   | **Technical Skills**        | Bulleted categories — tailor keywords from JD (6–10+ hard skills)    |

**Technical Skills** serves as Skills & Core Competencies — reorder and keyword-align per JD, but keep all baseline categories unless user explicitly removes one.

## Word Document Formatting Standards

### Document setup (do not change)

| Setting          | Value                                                  |
| ---------------- | ------------------------------------------------------ |
| Application      | Microsoft Word (.docx)                                 |
| Body font        | Calibri 11 pt (or Arial 11 pt)                         |
| Name / contact   | Calibri 16–18 pt bold, centered                        |
| Section headings | Calibri 12 pt bold, with optional bottom border (1 pt) |
| Margins          | 1 inch on all sides                                    |
| Line spacing     | Multiple 1.08–1.15 (body text)                         |
| Alignment        | Single column — no tables for layout                   |
| Page size        | US Letter (8.5" × 11")                                 |

### Build method (always use)

Generate the resume with **python-docx**:

```bash
pip install python-docx
```

1. Start from `plugins/buildResume/baseline_resume.docx` if it exists, or build from the Baseline Word Document Template content below.
2. Apply all tailoring edits to the document object in memory.
3. **Save** to `plugins/buildResume/tailored_resume.docx` (or a user-specified path ending in `.docx`).
4. Tell the user the full path to the saved `.docx` file — **that is the only deliverable**.

**Do not** output LaTeX. **Do not** output markdown pretending to be the resume. **Do not** generate or mention PDF.

### python-docx style mapping

| Resume element    | python-docx approach                                                                         |
| ----------------- | -------------------------------------------------------------------------------------------- |
| Contact block     | Centered paragraph, bold name, hyperlinks for email/URLs                                     |
| Section title     | `paragraph.style = 'Heading 2'` or bold 12 pt + spacing after 4 pt                           |
| Job title line    | Bold title + tab + right-aligned dates (tab stop at right margin for dates)                  |
| Company line      | Italic company name; append location from Experience Index (e.g., `EXLServices — Texas, US`) |
| Bullets           | `document.add_paragraph(text, style='List Bullet')` — one achievement per paragraph          |
| Metrics bold      | `run.bold = True` only on numeric metrics (e.g., `85%`, `99.9%`)                             |
| Project links     | Hyperlink runs to GitHub URLs                                                                |
| Skills categories | List Bullet with category label bold + colon + skills text                                   |

### Job header pattern (use for every role and education entry)

```
[Bold] Lead Assistant Manager/Consultant - II          Dec 2025 – Present
[Italic] EXLServices — Texas, US
• First bullet — crisp one line, metric bold only (e.g., 99.9%).
• Second bullet — no empty paragraph between bullets.
```

### Section order (fixed — all seven required)

1. Contact Header
2. Summary
3. Professional Experience (roles 1–4)
4. Internships (roles 5–8)
5. Projects
6. Education
7. Technical Skills

### Formatting anti-patterns (never do these)

```
❌ Empty paragraph between each bullet     % creates unwanted gaps
❌ Text boxes or tables for layout         % breaks ATS parsing
❌ Multiple fonts or colors                % unprofessional
❌ Bold on every tool name in bullets      % bold metrics only

✅ List Bullet style, consecutive items
✅ Job header → bullets → 6 pt gap → next job header
✅ Bold only on metrics: reducing manual intervention by 85%
```

### Page length — up to 2 pages, no page 3

The resume must **not exceed 2 pages** when opened in Word:

- **No trailing whitespace** — last page should end flush with Technical Skills
- **No page 3** — trim oldest-role bullets or tighten wording before dropping JD keywords
- **No orphaned lines** — avoid a section header alone at page bottom with nothing below it

### Page fill strategy

When the last page has unused space at the bottom:

1. **Do NOT** lengthen existing bullets into multi-sentence paragraphs
2. **Do NOT** add empty paragraphs to pad — it breaks bullet alignment
3. **Do** add new crisp bullets distributed **evenly across roles**
4. Prioritize roles most relevant to the JD for extra bullets first
5. New bullets must use real work themes from the baseline — reframe, don't fabricate

When content exceeds 2 pages:

1. Trim bullets from oldest/least JD-relevant roles first (Tanishq → LTIMindtree → …)
2. Shorten bullets — remove filler words, keep Action + Result core
3. Never drop any of the 7 mandatory sections

### Word safety rules

- Use en-dash in dates: `Dec 2025 – Present` (Unicode en-dash or hyphen acceptable)
- Company names with `&` as plain text (Tanishq & ProwessIQ)
- Hyperlinks: full URLs for GitHub, LinkedIn, portfolio, email `mailto:`
- Percent signs in metrics: plain `85%` with bold on metric only
- Save as `.docx` (Office Open XML) — not legacy `.doc` format

---

## Baseline Word Document Template

Start from this template for every tailoring request. **Modify Summary, all Experience/Internship bullet content, Projects (select ≤4 from Default Projects pool per JD), and Technical Skills.** Preserve document structure, styles, margins, and all fixed fields. Rewrite every bullet to align with the tailored Summary.

**Baseline bullets reflect Abinesh's actual work experience:** titles, companies, dates, and locations stay fixed. When tailoring for a JD, reframe bullets — never invent employers, roles, or metrics not grounded in this baseline. Replace default Projects with JD-relevant picks from the Default Projects list (max 4).

### Contact Header (centered)

**Abinesh Haridoss**
+1 346-823-9553 | abinesha312@gmail.com | github.com/abinesha312 | linkedin.com/in/aharido/ | abineshharidoss.web.app

### Summary

Lead AI/ML Engineer with a Master's and Bachelor's in Computer Science and built robust, fair, and interpretable generative AI systems. I specialize in LLM safeguards, fairness evaluation, bias mitigation, and alignment techniques including RLHF and DPO. I've deployed production-grade foundation models on distributed infrastructure, conducted rigorous toxicity analysis and robustness benchmarks, and led cross-functional efforts to embed trustworthy AI principles throughout the model lifecycle.

### Professional Experience

**Lead Assistant Manager/Consultant - II** — Dec 2025 – Present
_EXLServices — Texas, US_
• Architected fully autonomous LLM agent workflows for healthcare systems using FastAPI with a three-tier fail-safe architecture, implementing production-grade exception handling and achieving **99.9%** uptime across distributed microservices on Google Kubernetes Engine (GKE).
• Orchestrated end-to-end workflow automation with Apache Airflow DAGs, integrating BigQuery for data warehousing and Google Cloud Redis for sub-300ms inference latency, processing large-scale workloads (20GB+ per request) with real-time monitoring via JIRA dashboards.
• Deployed AI agents with automated task tracking and error recovery, reducing manual intervention by **85%** while maintaining built-in compliance and audit trails for healthcare workflows.
• Implemented distributed caching strategies with Redis on GCP, optimizing high-throughput LLM inference pipelines and reducing backend query load while maintaining HIPAA-compliant data handling and encryption standards.
• Architected and deployed production-grade Agentic App components using MCP servers and LangGraph, translating product goals into actionable engineering plans with end-to-end CI/CD observability.
• Collaborated cross-functionally with Product and Engineering teams to deliver customer-centric features, communicating technical trade-offs to leadership and mentoring junior engineers on agentic system design.

**Associate Software Developer** — Feb 2023 – Jul 2023
_Trans Union — Chennai, India_
• Developed fairness-aware ML models for credit risk assessment, implementing bias mitigation and fairness evaluation metrics to ensure equitable predictions across demographic groups, improving approval fairness by **70%**.
• Designed robustness benchmarks for credit-scoring ML models using PyTorch, achieving **99.8%** accuracy under adversarial conditions and improving anomaly recall by **25%**.
• Established evaluation protocols and monitoring dashboards for model safety, integrating toxicity and bias metrics to track model drift and maintain trustworthy AI standards across production systems.
• Collaborated across product, data science, and compliance teams to embed fairness principles throughout the ML lifecycle, improving AI governance compliance by **30%**.
• Implemented interpretability techniques for model predictions, providing stakeholders with transparent decision explanations and enabling faster model explainability reviews by **40%**.

**Software Engineer** — Oct 2021 – Feb 2023
_LTIMindtree (Larsen and Toubro Infotech Mindtree) — Chennai, India_
• Built comprehensive evaluation frameworks for ML classification and regression models, implementing fairness metrics, robustness testing, and safety validation protocols; achieved **92.4%** test coverage with automated bias detection and performance regression detection.
• Implemented end-to-end MLOps pipelines with automated model training, validation, and deployment gates, incorporating bias auditing and fairness checks to enable rapid experimentation and reduce deployment cycles by **28%**.
• Developed scalable ML infrastructure using scikit-learn, XGBoost, and LightGBM for rapid prototyping and production deployment, supporting cross-validation, hyperparameter tuning, and A/B testing workflows across multiple model architectures.
• Collaborated with data science and product teams on model governance and ethical AI standards, documenting model trade-offs, fairness constraints, and performance baselines to ensure responsible ML practices throughout the development and deployment lifecycle.

**Full Stack Developer** — Mar 2020 – Sep 2021
_Tanishq & ProwessIQ Private Limited — Chennai, India_
• Implemented secure ML model serving infrastructure with comprehensive audit logging, explainability APIs, and access controls, ensuring model transparency and regulatory compliance across enterprise systems.
• Designed infrastructure for responsible data handling and model evaluation, establishing automated bias detection and fairness monitoring pipelines that improved data governance by **40%** and reduced security incidents by **30%**.
• Orchestrated ML infrastructure with automated testing and evaluation gates, supporting fairness and safety assessments before production deployment, reducing model-related incidents by **60%** and ensuring trustworthy AI delivery.
• Established monitoring systems for model performance and safety metrics, enabling real-time detection of fairness degradation and robustness issues, reducing MTTR for model failures by **42%** and maintaining enterprise SLAs.

### Internships

**AI/ML Software and Web Development Intern** — Sep 2025 – Jan 2026
_Essential Knowledge Systems, LLC — Texas, US_
• Developed a knowledge distillation pipeline for the GPT-OSS model using Qwen-3 1.5B, implementing custom loss functions at the PyTorch layer for efficient model inference.
• Designed a web-based wizard to automate the end-to-end distillation workflow, enabling users to configure and trigger model compression directly from dataset inputs through an intuitive multi-step UI.

**Graduate-level research intern** — Sep 2025 – Feb 2026
_Turing — Texas, US_
• Designed LLM fine-tuning workflows with automated fairness evaluation and bias auditing mechanisms, improving labeling consistency by **25%** and reducing annotation errors by **30%** through rigorous quality gates.
• Orchestrated multi-modal LLM training pipelines using PyTorch and HuggingFace Transformers, implementing instruction tuning and alignment protocols to enhance model safety and reduce harmful outputs by **35%**.
• Conducted bias audits and fairness evaluations on training data, identifying and mitigating demographic disparities to improve model safety by **25%**.

**Summer Intern/AI-ML Engineer** — Jul 2025 – Sep 2025
_Worlds Enterprise Inc. — Texas, US_
• Implemented red teaming pipelines to systematically identify adversarial inputs and safety gaps in foundation models, enabling proactive robustness evaluation and iterative model hardening.
• Developed bias mitigation strategies for anomaly detection systems, conducting bias audits and achieving **25%** improvement in fairness across demographic groups.
• Architected explainability frameworks for LLM-driven workflows, integrating interpretability techniques to provide transparent reasoning and audit trails, improving user trust and regulatory compliance.

**AI Engineer/Student Assistant** — May 2024 – May 2025
_University of North Texas — Texas, US_
• Deployed foundation model evaluation frameworks across 80+ departments, implementing robustness benchmarks, toxicity analysis, and fairness assessment protocols to ensure safe model deployment.
• Configured and deployed multi-modal foundation models (LLaMA 3.2 90B) on GPU infrastructure, implementing prompt engineering best practices and instruction tuning to enhance model alignment and reduce hallucinations.
• Designed rigorous evaluation protocols with custom bias audit frameworks, measuring model fairness across protected attributes and toxicity thresholds, reducing failure rates by **30%** and improving model trustworthiness.
• Conducted systematic red teaming to identify model vulnerabilities, documenting adversarial examples and safety edge cases, informing iterative model improvements and safeguard development for responsible AI.
• Fine-tuned foundation models using PyTorch with domain-specific, bias-balanced datasets, improving model safety and fairness while maintaining **15%** reduction in demographic bias and **20%** improvement in task performance.

### Projects

**Fraud Folio** | AI, Fraud Detection, Meta Llama 3 — github.com/abinesha312/hack_unt_financial_fraud
• Engineered a custom anomaly detection pipeline utilizing Meta Llama 3 with CUDA optimization for real-time fraud detection, demonstrating expertise in production-ready LLM systems.

**Hybrid Vision Transformer for Small-Scale Image Classification** | PyTorch, Transformers, MixUp, CutMix — github.com/abinesha312/vision-transformer-cifar
• Developed a Hybrid Vision Transformer combining CNNs and transformers for CIFAR-10 classification, improving feature extraction and model interpretability through attention visualization.

_(Replace with ≤4 JD-relevant projects from Default Projects pool when tailoring.)_

### Education

**Master of Science in Computer Science** — Aug 2023 – 2025
_University of North Texas_
Relevant Courses: Machine Learning, Algorithms, AI Software Development, Information Retrieval, Big Data and Data Science

**Bachelor of Engineering in Information Science and Engineering** — May 2021
_Panimalar Engineering College (Anna University)_
Relevant Courses: Operating Systems, Data Structures, DBMS, Computer Networks, Object Oriented Concepts, Deep Learning

### Technical Skills

• **Programming Languages:** Python, C++, JavaScript, TypeScript, Bash, PowerShell, Shell Scripting.
• **ML/DL Frameworks:** PyTorch, TensorFlow, HuggingFace Transformers, ONNX, LangChain, OpenAI API
• **Responsible AI & Safety:** Fairness Evaluation, Bias Auditing, Toxicity Analysis, Red Teaming, Model Alignment, RLHF, DPO, Instruction Tuning, Explainability, Interpretability
• **Distributed Training:** PyTorch (FSDP, DDP), Distributed Evaluation Frameworks, NVIDIA Nsight Systems
• **Databases:** Redis, MongoDB, DynamoDB, Postgres, Databricks, MySQL
• **Cloud & DevOps:** AWS (Lambda, API Gateway, S3, ECS, EKS), Docker, Terraform, MLOps, Model Monitoring

---

## Operational Tailoring Sequence

**Authoritative process:** Bullet & Content Strategy (Step 0 through Pre-output checklist) above. Do not duplicate those rules here — execute in this order:

1. **Parse JD** → Priority-1/2 keywords + 3–4 themes (Step 0).
2. **Gap analysis** — mark each P1 keyword Covered / Partial / Missing.
3. **Write Summary first** — JD role title + themes.
4. **Edit bullets** — minimal edit first; new bullet only for true gaps; blend with real experience.
5. **Select projects** — pick **≤4** JD-relevant entries from Default Projects pool; one crisp bullet each.
6. **Reorder Technical Skills** — JD tools first; candidate must actually use them.
7. **Balance to exactly 2 pages** — Page Fill Strategy below; strict 2-page cap in Word.
8. **Run Pre-output checklist** (in Bullet & Content Strategy) → build and save `.docx`.

---

## Output Format

**Default:** Save a `.docx` file and return the file path. **DOCX only** — never PDF. No markdown fences around document content, no LaTeX.

**If user asks for explanation:** After confirming the file path, optionally append a short keyword mapping table showing which JD terms were added and where.

---

## Final Validation (extends Pre-output checklist)

Run the **Pre-output checklist** in Bullet & Content Strategy first. Then confirm:

- [ ] All **7 mandatory sections** present (Contact → Summary → Experience → Internships → Projects → Education → Technical Skills)
- [ ] **≤4 projects** selected from Default Projects pool — JD-relevant only
- [ ] Job **locations** preserved from Experience Index (never change)
- [ ] **Bold only metrics** (e.g., **99.9%**) — not tools/keywords in body bullets (per What NEVER to change)
- [ ] Job headers formatted correctly; List Bullet style; no empty paragraphs between bullets
- [ ] Margins 1in; Calibri/Arial 11pt; line spacing 1.08–1.15 unchanged
- [ ] Valid `.docx` — opens in Word; hyperlinks work; no trailing spaces on any line
- [ ] Deliverable is `.docx` only — no PDF generated or suggested

---

## ATS Rules

### DO

- Standard Word **List Bullet** paragraphs, single column
- Bold **metrics** only in bullet runs (not general keyword bolding)
- Exact JD keyword phrases where truthful (plain text or natural phrasing)
- Deliver **`.docx` only** — the final ATS-ready file format for this skill
- Exact JD keyword phrases where truthful (plain text or natural phrasing)

### DON'T

- Output PDF or instruct the user to export to PDF

- Tables for layout, skill bars, photos
- Fabricate employers, titles, dates, locations, or metrics
- Change document structure, section names, or section order
- Return markdown instead of a `.docx` file (unless user explicitly asks for preview text)
