# Goldman Sachs Enterprise AI Framework

A personal framework for a Senior Associate in Tax / institutional clients joining Goldman Sachs in the next 2–3 months, at the moment the firm is deploying (a) a proprietary GPT and (b) Microsoft 365 Copilot for operations.

**Bias:** tax deliverables first, AI leverage second, evangelism third. Deliverables build trust; trust buys the room to teach.

**This is a personal template.** Nothing in this directory contains Goldman Sachs data, client information, or firm-specific system names. It is designed to be copied to a personal drive, refined in the first 90 days on the job, and used as a living document.

---

## How to use this framework

### Before day one

1. Read `conductor/role.md` end-to-end. Edit the stakeholder table and success metrics to match what you already know about the role.
2. Read `conductor/tools.md`. Convert every "assumption" into a question you'll ask in Week 1.
3. Read `tracks/30-60-90-plan.md`. Pressure-test the timeline. Nothing here is sacred; it's a starting scaffold.

### Week 1

1. Don't publish anything. Listen.
2. Fill in the "Confirmed" columns in `tools.md` from official documentation, not assumptions.
3. Start daily journal entries using `journal/TEMPLATE.md`.

### Weeks 2–4

1. Score the workflows in `conductor/workflows.md` against what you actually see on the job.
2. Refine the prompt templates in `prompts/` against real (but fully generic) use-cases.
3. Confirm rules-of-engagement with compliance before any AI use with sensitive content.

### Days 31–90

Follow the 30/60/90 plan. Don't sprint ahead to Day 60 work during Week 2.

---

## Directory map

```
gs-ai-framework/
├── README.md                          ← you are here
├── conductor/                         ← project-context scaffold (Conductor pattern)
│   ├── role.md                        ← who I am, who my stakeholders are, what "good" means
│   ├── tools.md                       ← prop-GPT + Copilot + third-party inventory
│   ├── workflows.md                   ← recurring tax workflows, scored for AI leverage
│   └── tracks.md                      ← workstream registry
├── tracks/                            ← proposal-posture artifacts for team/org
│   ├── 30-60-90-plan.md               ← personal onboarding plan
│   ├── copilot-rollout.md             ← staged-rollout framework proposal
│   └── adoption-kpis.md               ← measurement framework proposal
├── prompts/                           ← tax-flavored prompt library
│   ├── research-synthesis.md          ← prop-GPT research pattern
│   ├── tax-memo-scaffold.md           ← structural scaffold, not substance
│   ├── client-email-draft.md          ← Outlook + Copilot pattern
│   ├── entity-chart-analysis.md       ← orientation to a new client structure
│   └── k1-summarization.md            ← schedule summarization (synthetic data only)
├── training/                          ← workshop materials
│   ├── copilot-101-tax.md             ← 30-min Copilot workshop for the team
│   └── proprietary-gpt-101-tax.md     ← 30-min prop-GPT workshop for the team
└── journal/
    └── TEMPLATE.md                    ← daily / weekly / monthly entry templates
```

---

## Recommended plugin stack (this marketplace)

This framework was built using and can be extended with the following plugins from the `claude-agents` marketplace. Load in this order:

| Order | Plugin | What it's for |
|-------|--------|--------------|
| 1 | [`plugins/conductor`](../../plugins/conductor) | Knowledge-base spine. `context-driven-development` skill scaffolds `conductor/`; `conductor-validator` audits for gaps. |
| 2 | [`plugins/llm-application-dev`](../../plugins/llm-application-dev) | `prompt-engineer` agent for prompt authoring; `prompt-engineering-patterns` and `llm-evaluation` skills. |
| 3 | [`plugins/agent-orchestration`](../../plugins/agent-orchestration) | `/improve-agent` command models the staged-rollout pattern adapted in `tracks/copilot-rollout.md`. |
| 4 | [`plugins/code-documentation`](../../plugins/code-documentation) | `docs-architect` for SOP drafting; `tutorial-engineer` for workshop material. |
| 5 | [`plugins/business-analytics`](../../plugins/business-analytics) | `business-analyst` agent and `kpi-dashboard-design` skill informed `tracks/adoption-kpis.md`. |
| 6 | [`plugins/documentation-standards`](../../plugins/documentation-standards) | HADS (Human-AI Document Standard) for any document that might later be indexed by a RAG system. |

Explicitly **out of scope**: deployment/infrastructure plugins, vector-database tuning, platform-engineering material. You are a power-user and enabler, not the platform team.

---

## Governance, baked in

Every artifact in this directory honors the same four rules:

1. **Human review is non-negotiable.** AI produces drafts. Humans ship.
2. **Citations are the deliverable.** Sources without a verifiable cite are assumptions.
3. **Classification lives in the user's head, not the tool.** The tool doesn't know what's sensitive. You do.
4. **No Goldman data, ever, in this directory.** Real work happens in sanctioned tooling with sanctioned data classifications. This directory is templates and patterns only.

---

## What to do with this on day one

1. Clone or copy this directory to a **personal** drive. Nothing here goes on a GS device until you've confirmed it's a personal-template-only document and your manager is comfortable with that.
2. Read `conductor/role.md`, `conductor/tools.md`, and `tracks/30-60-90-plan.md` on the morning of day one.
3. Start the journal. That's the single most important habit to establish.
4. At day 30, 60, and 90, snapshot the whole directory — you'll want to see how your understanding shifted.

---

## What this framework is not

- A set of rules for Goldman Sachs. It's a set of patterns for you.
- A Morgan Stanley playbook transplanted wholesale. It's a set of hypotheses to verify.
- A pitch. It's a private operating system.
- A substitute for being excellent at tax. It's an amplifier.
