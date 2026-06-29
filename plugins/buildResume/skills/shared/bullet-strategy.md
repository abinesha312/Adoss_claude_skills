# Bullet & Content Strategy

Work top-down: **parse the JD first, write the Summary, then edit bullets to support it.**

## Step 0 — Parse the JD before touching any bullet

Extract from the job description:

1. **Role title** — mirror in Summary (e.g., "Lead AI/ML Engineer", "GenAI Engineer").
2. **Priority-1 keywords** — must-haves named 2+ times or in title/requirements (Kubernetes, RAG, PyTorch). Must appear in final resume.
3. **Priority-2 keywords** — nice-to-haves mentioned once (Terraform, gRPC). Include where natural.
4. **3–4 focus themes** — narrative the JD sells (scalable inference, MLOps automation, agentic systems).

## Decision rule — edit existing vs. add new

| Situation | Action |
| --- | --- |
| Keyword concept already in a bullet, just unnamed | **Minimal edit** — weave keyword into existing bullet |
| Keyword concept missing but candidate has done it | **New bullet** — add to most recent/relevant role |
| Candidate has never done it | **Do not fabricate** — Technical Skills only if defensible, else skip |

Prefer editing over adding. New bullets only for true gaps with real accomplishments.

## Pattern 1 — Minimal edit

JD wants **Kubernetes** and **microservices**; bullet describes work but doesn't name them.

```
Before: Architected fully autonomous LLM agent workflows for healthcare systems using FastAPI...
After:  Architected autonomous LLM agent workflows as Kubernetes microservices using FastAPI, achieving 99.9% uptime on GKE.
```

## Pattern 2 — New bullet (true gap)

JD wants **RAG**; no bullet mentions retrieval, but candidate built RAG pipelines. Add to most relevant role (usually EXLServices):

```
Built production RAG pipelines with LangChain and vector retrieval on GCP, cutting knowledge lookup latency by 40%.
```

New bullets go to the **highest-relevance role**, distributed across roles — never stack all in one job.

## Bullet formula — Action + Task/Method + Result

One crisp line (~1–2 lines in PDF, never 3 sentences).

| Component | Include | Examples |
| --- | --- | --- |
| **Action** | Strong past-tense verb | Architected, Deployed, Engineered, Optimized, Led, Built |
| **Task** | What + scope | LLM agent workflows for healthcare; eval across 80+ departments |
| **Method** | Tools, systems, approach (plain text — no bold on tools) | using FastAPI on GKE; via PyTorch |
| **Result** | Quantified or clear qualitative win (**bold metrics only**) | **99.9%** uptime; latency down **40%** |

## Strong verbs (by category)

**Building:** Authored, Conceptualized, Constructed, Devised, Formulated, Pioneered, Programmed, Spearheaded

**Deploying:** Executed, Integrated, Launched, Migrated, Operationalized, Provisioned, Shipped, Systematized

**Scaling:** Accelerated, Amplified, Automated, Modernized, Overhauled, Refactored, Scaled, Slashed, Transformed

**Data/AI:** Analyzed, Audited, Diagnosed, Evaluated, Forecasted, Quantified, Resolved, Troubleshot, Validated

**Leading:** Advocated, Championed, Coordinated, Directed, Facilitated, Mentored, Steered

## Weak verbs (avoid)

**Bystander:** Contributed to, Part of a team that, Collaborated on (as opener), Supported, Aided

**Duty traps:** Tasked with, Duties included, Handled, In charge of, Served as, Responsible for

**Vague:** Utilized/Used (as opener), Made/Did, Fixed (alone), Looked at/Explored, Maintained (without metric), Updated

### Weak verb audit — "How and What" pivot

- ❌ _Responsible for_ the cloud migration → ✅ **Orchestrated** migration of 50+ microservices to AWS, reducing costs by **20%**
- ❌ _Worked on_ the ML model → ✅ **Trained and fine-tuned** a custom LLM using PyTorch, improving accuracy by **15%**

## Good vs. bad bullets

```
✅ GOOD: Deployed AI agents with automated error recovery on GKE, reducing manual intervention by 85% while maintaining HIPAA audit trails.

❌ BAD:  I was responsible for deploying AI agents. I worked on implementing automated task tracking. This helped reduce manual intervention by 85%.
```

```
✅ GOOD: Engineered a vector-retrieval layer with pgvector, standardizing knowledge access across 6 agent services.

❌ BAD:  Used PyTorch TensorFlow Kubernetes Docker Terraform GCP AWS RAG LangChain FastAPI for AI agent deployment.
```

## Readability rules

- **One achievement per bullet** — no compound run-on sentences.
- **Bold metrics only** — e.g., **85%**, **99.9%**, **300ms**. Never bold tool names or keywords in body bullets.
- **Weave keywords naturally** — no keyword stuffing.
- **Quantify when you can; qualify when you can't** — concrete qualitative outcome beats a fake number.
- **Lead with the verb** — never start with "I", "Responsible for", or a noun.

## Bullet count targets (fill exactly 2 pages)

| Role type | Bullets | Notes |
| --- | --- | --- |
| Full-time (recent) | 5–7 | Most JD-relevant role gets most depth |
| Full-time (older) | 4–5 | Trim as roles age |
| Internship | 3–5 | Keep tight |

Distribute new bullets across roles. If page 2 is thin, add to mid-tenure roles before padding the most recent.

## Summary ↔ Bullets alignment

1. Write Summary first — JD role title + 3–4 themes.
2. Every Experience and Internship bullet supports the Summary narrative.
3. Projects and Technical Skills reinforce the same themes.

> Test: read Summary, then each bullet. If a bullet feels like a different resume, rewrite or cut it.

## Page fill strategy

**When last page has space:**
1. Do NOT lengthen bullets into paragraphs
2. Do NOT pad with empty lines or `\vspace` inside lists
3. Do add crisp bullets distributed evenly across roles
4. Prioritize JD-relevant roles first
5. Reframe real baseline work — never fabricate

**When content exceeds 2 pages:**
1. Trim oldest/least JD-relevant roles first (Tanishq → LTIMindtree → …)
2. Shorten bullets — keep Action + Result core
3. Never drop any of the 7 mandatory sections
