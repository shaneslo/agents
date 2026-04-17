# Copilot rollout framework — tax/operations lens

Adapted from the staged-rollout pattern in `plugins/agent-orchestration/commands/improve-agent.md` (alpha → beta → canary → full) and reframed for M365 Copilot adoption on a tax-operations team at a bulge-bracket firm.

**Posture:** this is a *proposal* from a Senior Associate to a manager, not a plan I own. I will not drive a rollout at the team level without explicit sponsorship.

---

## Why a staged approach beats a big bang

Observed at prior firm (generic, no confidential detail): Copilot rollouts that skip pilot phases create three failure modes.

1. **Trust crater** — early hallucination or grounding mishap poisons the well; users don't return for months.
2. **Invisible non-adoption** — licenses consumed, actual usage flat; no one tells you because there's no feedback loop.
3. **Policy whiplash** — a single high-profile incident forces blanket restrictions that slow the rollout for everyone.

Staged rollout converts each of those into a contained, recoverable event.

---

## The four stages

### Stage 1 — Alpha (Weeks 1–2)

- **Population:** me + 1–2 hand-picked peers who are both (a) high tool-tolerance and (b) credible internally.
- **Scope:** low-risk surfaces only — Teams meeting summaries, Outlook triage on internal threads, Word drafting on non-client docs.
- **Data:** internal-only; nothing client-identifiable; nothing sensitive.
- **Objective:** calibrate the tool's quality against our actual workflow. Find the failure modes before anyone else does.
- **Exit criterion:** at least 10 real uses per surface, documented quality assessment, no undisclosed issues.

### Stage 2 — Beta (Weeks 3–6)

- **Population:** the full immediate team (≈ 5–10 people) who opt in.
- **Scope:** expand to Excel (on synthetic data or firm-internal only), SharePoint search, Copilot BizChat for cross-app synthesis.
- **Data:** internal; explicit rules on what is off-limits.
- **Objective:** surface workflow-specific failure patterns; start collecting time-saved evidence; identify 2–3 signature use-cases.
- **Exit criterion:** ≥ 70% weekly active usage in the opt-in group; ≥ 3 documented signature use-cases; zero policy incidents.

### Stage 3 — Canary (Weeks 7–10)

- **Population:** broaden to one adjacent team (e.g., an ops team we work closely with). Still opt-in.
- **Scope:** everything proven in Beta, plus workshop-style onboarding.
- **Data:** as approved, no expansion.
- **Objective:** validate that the pattern transfers outside the initial bubble; identify new personas (ops analyst vs. reviewer vs. sign-off MD) and their different needs.
- **Exit criterion:** second team hits adoption metrics comparable to initial team within 3 weeks; no workflow regressions flagged by either team.

### Stage 4 — Full (Week 11+)

- **Population:** wider group, mandatory awareness, opt-in use.
- **Scope:** the patterns that survived stages 1–3. Resist scope creep.
- **Data:** as approved.
- **Objective:** institutionalize. Workshops become recurring. Prompt library becomes a shared resource. KPIs reported to leadership.
- **Exit criterion:** this is the steady state — there is no exit, only continuous iteration.

---

## Personas and their needs

| Persona | What they want from Copilot | What they fear | Rollout implication |
|---------|-----------------------------|----------------|---------------------|
| Junior analyst | Faster drafts, fewer rote tasks | Looking lazy; AI making them worse at fundamentals | Frame as scaffolding, not substitution. Pair with skill-building. |
| Senior Associate (my peers) | Hours reclaimed, higher-leverage work | Reviewer catching an AI-introduced error on their watch | Emphasize the review discipline; ship review prompts, not just draft prompts. |
| VP / ED (reviewers) | Consistent upstream quality, audit-friendly outputs | Output they can't trace; surprise at a partner meeting | Focus on review-assist, cite-everything patterns. |
| MD / partner (sign-off) | No downside; evidence of productivity lift | Any reputational event | Give them the KPI dashboard and the incident protocol, not tool demos. |
| Ops analyst | Meeting summaries, document discovery, report drafting | Being quietly measured and replaced | Frame as capacity expansion, not headcount discussion. |

## Signature use-cases to prioritize

Rank-ordered by "time-to-obvious-value":

1. **Meeting summaries with action items** (Teams) — universal pull, ~zero risk.
2. **Inbox catch-up after absence** (Outlook) — demo gold.
3. **Document and precedent search** (Copilot BizChat over SharePoint) — high-value, low controversy.
4. **"Second-reader" pass on my own draft** (Word + Copilot or prop-GPT) — quality angle.
5. **Excel formula generation and explanation** (Excel) — on synthetic or internal-only data; always verified.

Explicitly **deprioritize** at this stage:
- Client-facing email automation.
- Client-data analysis in Excel.
- Anything that drafts a tax position.

## Risk register

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|-----------|
| Hallucinated citation reaches a deliverable | Medium | High | Mandatory human verification of every authority, taught in every workshop. |
| Copilot grounding on wrong SharePoint file | Medium | Medium | Teach users to check the cited source before relying on a summary. |
| Policy violation via client data in prompt | Low (trained users) | Very High | Explicit red-line list; quick-reference card; report-and-rollback protocol. |
| "AI looked good, but" silent quality regression | Medium | Medium | KPI dashboard includes quality signal, not just volume. |
| Adoption theater (licensed but unused) | High | Low | Track weekly actives, not license count. Surface this to leadership. |
| Reviewer fatigue (AI-amplified volume) | Medium | Medium | Match draft tooling with review tooling; don't just double the reviewer's queue. |

## Training cadence

- **Onboarding session (30 min):** one surface at a time, live demo, one hands-on task, one policy red-line.
- **Office hours (30 min weekly):** drop-in, no agenda, bring your real work.
- **Signature-use-case workshops (45 min):** one per month, rotating through the five use-cases.
- **Reviewer-specific session (60 min):** review prompts, citation-verification discipline, audit-trail hygiene.

## Measurement — see `adoption-kpis.md`

Staged rollout reports against staged KPIs. Don't measure Stage 4 KPIs in Stage 1.

## What "done" looks like at each stage

| Stage | "Done" signal |
|-------|---------------|
| Alpha | I can describe the tool's real behavior — not the marketing behavior — on our workflows. |
| Beta | At least three peers voluntarily pulling patterns from the prompt library. |
| Canary | A team outside my own adopting without me babysitting. |
| Full | The framework outlives my sponsorship of it. Someone else is running the workshops. |
