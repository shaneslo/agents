# workflows.md — Recurring tax / institutional-client workflows

Inventory of the workflows that are most frequent in a tax Senior Associate's week, scored for AI-leverage and mapped to the right tool.

## Scoring rubric

Each workflow gets four scores, 1–5:

- **F** — Frequency (how often it happens)
- **T** — Time cost per instance
- **E** — Error cost if it goes wrong
- **A** — AI suitability (how well current tools handle the task)

**Leverage = F × T × A ÷ E'** where E' penalizes tasks with catastrophic downside (sign-off-level tax positions, anything client-facing-final).

Target the top 3 by Leverage for the first 60 days. Everything else is stretch.

## Inventory

### Research & synthesis workflows

| Workflow | F | T | E | A | Tool fit | Notes |
|----------|---|---|---|---|----------|-------|
| Internal precedent search (prior memos, prior deliverables) | 5 | 3 | 2 | 5 | Prop-GPT + SharePoint Copilot | High pull, low risk; fastest early win. |
| External tax-authority synthesis (IRS / Treas / OECD / case law) | 4 | 4 | 4 | 4 | Prop-GPT (if corpus includes) + specialty platform | Must cite and verify every authority. |
| Comparative jurisdictional analysis | 3 | 5 | 4 | 3 | Prop-GPT for scaffolding; manual verification mandatory | Hallucination risk on foreign law is non-trivial. |
| Market / industry context for a client | 3 | 3 | 2 | 4 | Copilot BizChat + external data tools | Good for briefing prep. |

### Drafting workflows

| Workflow | F | T | E | A | Tool fit | Notes |
|----------|---|---|---|---|----------|-------|
| Tax memo first draft (structure + issue spotting) | 4 | 5 | 4 | 4 | Prop-GPT for scaffold, Word+Copilot for prose | Never ship without full human edit + reviewer pass. |
| Client email drafting / follow-ups | 5 | 2 | 3 | 5 | Outlook + Copilot | Huge time-save; voice tuning needed. |
| Internal status updates, deal-team comms | 5 | 2 | 1 | 5 | Teams + Copilot | Lowest-risk use of AI. |
| Engagement-letter or SOW drafting | 2 | 4 | 4 | 3 | Word + Copilot over approved templates | Template adherence critical. |

### Analytical / numerical workflows

| Workflow | F | T | E | A | Tool fit | Notes |
|----------|---|---|---|---|----------|-------|
| Schedule / allocation analysis | 3 | 4 | 5 | 3 | Excel + Copilot | Only on synthetic or sanctioned data; always cross-check formulas. |
| Reconciliation (book-tax differences, true-ups) | 3 | 4 | 5 | 3 | Excel + Copilot | AI assists formula authoring, not numerical conclusions. |
| Entity / structure chart interpretation | 2 | 3 | 3 | 4 | Prop-GPT | Useful for narration, not determination. |

### Review & QC workflows

| Workflow | F | T | E | A | Tool fit | Notes |
|----------|---|---|---|---|----------|-------|
| "What am I missing?" second-read of my own draft | 5 | 1 | 3 | 5 | Prop-GPT | My highest-value daily use. |
| Consistency check across a working-paper set | 3 | 3 | 4 | 4 | Copilot BizChat + SharePoint | Cite-everything rule applies. |
| Citation / authority verification | 4 | 2 | 5 | 2 | **Do not** trust AI here — manual lookup | AI can surface, humans must verify. |

### Knowledge / onboarding workflows

| Workflow | F | T | E | A | Tool fit | Notes |
|----------|---|---|---|---|----------|-------|
| Getting up-to-speed on a new product area | 2 | 5 | 2 | 5 | Prop-GPT as Socratic tutor | Ask for a progression, not a conclusion. |
| Finding the right internal subject-matter expert | 4 | 2 | 2 | 4 | Copilot BizChat over people/directory | Beats cold-emailing. |
| Understanding a new client's prior-year footprint | 3 | 4 | 3 | 4 | Prop-GPT + SharePoint | Start here for every new matter. |

### Operations workflows (Copilot-rollout angle)

| Workflow | F | T | E | A | Tool fit | Notes |
|----------|---|---|---|---|----------|-------|
| Meeting capture and action-item extraction | 5 | 1 | 2 | 5 | Teams Copilot | Zero controversy, universal pull. |
| Inbox triage after PTO / off-hours | 3 | 3 | 2 | 5 | Outlook Copilot | The showcase demo for a workshop. |
| Status-reporting to senior reviewers | 5 | 2 | 2 | 5 | Teams + Word Copilot | Worth templating once. |
| Document version reconciliation | 3 | 3 | 3 | 4 | Word Compare + Copilot | Fewer errors than manual diffing. |

## Top 3 focus workflows for Days 1–60

(Assumptions — refresh after Week 2 based on actual work.)

1. **"What am I missing?" review** — highest F, lowest risk, immediate personal leverage.
2. **Internal precedent search via prop-GPT** — highest team-pull potential, easiest to demo to peers.
3. **Outlook triage + draft** — universal, fastest path to reclaimed hours, easiest workshop material.

## Workflow → prompt mapping

Each top workflow gets a dedicated file in `../prompts/`:

| Workflow | Prompt file |
|----------|-------------|
| Tax memo scaffolding | [`../prompts/tax-memo-scaffold.md`](../prompts/tax-memo-scaffold.md) |
| Internal precedent search | [`../prompts/research-synthesis.md`](../prompts/research-synthesis.md) |
| Client email draft | [`../prompts/client-email-draft.md`](../prompts/client-email-draft.md) |
| Entity / structure narration | [`../prompts/entity-chart-analysis.md`](../prompts/entity-chart-analysis.md) |
| Schedule summarization (e.g. K-1 review) | [`../prompts/k1-summarization.md`](../prompts/k1-summarization.md) |

## Maintenance

- Revisit this file at the end of each month — scores drift as I learn the real distribution.
- A workflow that stays at low A for three months means either the tooling matured or my prompt needs an overhaul.
- Anything that moves from "interesting" to "indispensable" graduates to its own entry in the prompt library.
