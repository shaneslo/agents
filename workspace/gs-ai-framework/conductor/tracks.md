# tracks.md — Workstream registry

Active tracks for the Goldman Sachs AI framework. Modeled on the Conductor pattern (see `plugins/conductor/skills/context-driven-development/SKILL.md`).

## Status legend

- `pending` — not started
- `active` — currently running
- `blocked` — waiting on input (dependency noted)
- `done` — complete, archived

## Active tracks

| ID | Track | Status | Owner | Target | Link |
|----|-------|--------|-------|--------|------|
| T-001 | 30/60/90 onboarding plan | pending | me | Day 90 | [../tracks/30-60-90-plan.md](../tracks/30-60-90-plan.md) |
| T-002 | Tax prompt library v1 | pending | me | Day 60 | [../prompts/](../prompts/) |
| T-003 | Copilot rollout framework (team-level) | pending | me + manager | Day 90 | [../tracks/copilot-rollout.md](../tracks/copilot-rollout.md) |
| T-004 | Adoption KPI proposal | pending | me | Day 90 | [../tracks/adoption-kpis.md](../tracks/adoption-kpis.md) |
| T-005 | Internal training kit (tax lens) | pending | me | Day 75 | [../training/](../training/) |
| T-006 | Learning journal (daily) | active | me | continuous | [../journal/TEMPLATE.md](../journal/TEMPLATE.md) |

## Dependencies

- T-002 depends on T-001 (Day-30 workflow mapping).
- T-003 depends on T-001 (manager alignment in Week 2–4) and T-004 (KPIs inform rollout design).
- T-005 depends on T-002 (prompts seed training content).

## Update cadence

- T-001 — review weekly Weeks 1–4, then monthly.
- T-002 — add a prompt whenever a workflow recurs ≥ 3 times.
- T-003 — update on any material change in GS Copilot rollout status.
- T-004 — one full pass Week 8, refined Week 12.
- T-005 — assembled Week 10–12.
- T-006 — daily entries when actively in the role; weekly otherwise.

## Completed tracks

_(none yet)_
