# Adoption KPI framework

Proposal-posture document. Designed with the `business-analyst` agent from `plugins/business-analytics/` and the `kpi-dashboard-design` skill as references. Do not populate with real GS numbers — this is a template only.

## Measurement principles

1. **Measure adoption, value, quality, and risk — in that order, but reported together.** Volume without value is theater. Value without quality is eventual pain. Quality without risk-tracking is a surprise waiting to happen.
2. **Leading indicators over lagging ones.** Weekly active users tells you something weeks before "hours reclaimed" does.
3. **Baselines first, deltas second.** Establish a pre-rollout baseline per workflow; measure delta, not absolute.
4. **Sample, don't surveil.** You don't need every user's every action; you need representative, explainable signal.
5. **Surface the bad news early.** A KPI framework that only shows green is broken.

## The four KPI tiers

### Tier 1 — Adoption (leading)

| Metric | Definition | Cadence | Target (illustrative) |
|--------|-----------|---------|-----------------------|
| Weekly active users | Distinct users with ≥ 1 Copilot invocation per week | Weekly | ≥ 70% of licensed in target group |
| Power users | Users with ≥ 10 invocations per week | Weekly | ≥ 20% of licensed |
| Surface breadth | Avg. number of distinct surfaces used per user | Monthly | ≥ 3 of {Outlook, Word, Excel, Teams, BizChat} |
| Time-to-first-value | Days from license provisioned to first genuine productivity use | Monthly cohort | ≤ 5 business days |

### Tier 2 — Value (lagging but real)

| Metric | Definition | Cadence | Target (illustrative) |
|--------|-----------|---------|-----------------------|
| Hours reclaimed per user per week | Self-reported or structured sample | Monthly | ≥ 2 hrs/user/week at steady state |
| Prompt reuse rate | % of invocations using a shared / documented prompt | Monthly | ≥ 30% |
| Signature-use-case penetration | % of target group using each of the top 5 use-cases | Monthly | ≥ 60% per use-case |
| Task-completion rate | % of initiated AI tasks that produced a used output | Sample-based | ≥ 70% |

### Tier 3 — Quality

| Metric | Definition | Cadence | Target (illustrative) |
|--------|-----------|---------|-----------------------|
| Error-attribution rate | % of deliverable errors traced to AI-generated content | Per incident | ≤ 1% of AI-assisted deliverables |
| Citation-verification rate | % of AI-surfaced citations that humans verified before relying | Audit sample | 100% for client-bound work |
| Reviewer satisfaction | "Is the AI-assisted draft easier or harder to review?" survey | Quarterly | Net positive |
| Rework rate | Drafts requiring substantive rework after AI first pass | Monthly | Trending down |

### Tier 4 — Risk

| Metric | Definition | Cadence | Target (illustrative) |
|--------|-----------|---------|-----------------------|
| Policy incidents | Disclosed mis-uses (wrong-data-in-prompt, etc.) | Ad hoc | Zero high-severity |
| Near-misses | Self-reported close calls | Monthly | Non-zero and trending down (reporting culture health) |
| Grounding-failure rate | AI outputs that cited a wrong or non-existent source | Audit sample | ≤ 2% and trending down |
| Shadow-tool usage | Staff using non-sanctioned AI tools for GS work | Quarterly survey | Zero |

## Reporting view

Proposed quarterly one-pager:

```
╭─────────────────────────────────────────────╮
│  Copilot Adoption — Tax / Institutional    │
│  QX 20XX                                    │
├─────────────────────────────────────────────┤
│  Adoption                                   │
│    WAU: __%  (target __%)      [▲/▼/—]     │
│    Power: __% (target __%)     [▲/▼/—]     │
│    Surfaces/user: _            [▲/▼/—]     │
│                                             │
│  Value                                      │
│    Hours reclaimed: ___h/user [▲/▼/—]      │
│    Prompt reuse: __%          [▲/▼/—]      │
│    Top 5 use-case penetration                │
│                                             │
│  Quality                                    │
│    Error attribution: _%     [▲/▼/—]       │
│    Reviewer NPS: +__         [▲/▼/—]       │
│                                             │
│  Risk                                       │
│    Incidents: _  Near-misses: _            │
│    Grounding failures: _%                  │
│                                             │
│  Top 3 learnings this quarter:              │
│    1.                                       │
│    2.                                       │
│    3.                                       │
╰─────────────────────────────────────────────╯
```

## Instrumentation — how to actually collect this

Most of this cannot be self-instrumented from my laptop. It needs tax-tech / IT / the Copilot admin team. The proposal I would take to my manager:

1. **Adoption tier** — from the M365 admin center and any internal usage dashboard (likely already exists).
2. **Value tier** — a light monthly self-report (3-minute form, 5 questions). Refuse to build a 20-field time-tracker.
3. **Quality tier** — a review-stage checkbox: *was this draft AI-assisted? if yes, did it help or hurt?* Requires buy-in from reviewers.
4. **Risk tier** — incident log owned by compliance; near-miss reporting normalized in office hours.

## Anti-patterns to reject

- **License count as success metric.** Licenses aren't usage.
- **"AI usage up 40%."** Up from what, for what, at what quality?
- **Single-number dashboards.** A good framework will sometimes have mixed-signal quarters; hide that and lose credibility.
- **Hours-reclaimed as the only value metric.** Quality and risk matter equally.
- **Leaderboards per user.** Surveillance culture kills the signal.

## Rollout of the measurement itself

Mirror the rollout stages:

- **Alpha/Beta:** manual tracking, n ≈ 10, journal-based evidence.
- **Canary:** lightweight monthly form, admin-center basics.
- **Full:** quarterly one-pager to leadership, monthly operational view for the team.

## What I would ask my manager to sponsor

Exactly one of these, not all:

1. A 3-minute monthly self-report across the immediate team.
2. A review-stage "AI-assisted?" flag in the team's existing review process.
3. An ops-side pilot of the top 2 use-cases with a baseline measurement before rollout.

Pick the one with the lowest org cost and highest signal. My bet: option 2.
