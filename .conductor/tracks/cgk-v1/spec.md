# Track Specification: Credit Governance Kit — V1

## Overview

**Track ID:** cgk-v1
**Type:** feature
**Priority:** critical
**Created:** 2026-04-16
**Author:** shaneslo

### Description

Build and ship the V1 Credit Governance Kit: a Notion-native system for monitoring, budgeting, and optimizing Custom Agent credit usage ahead of Notion's May 4, 2026 metered-billing transition. Deliverables are a Notion workspace template (databases + pages), an optimization skill library, a governance policy set, and a dashboard walkthrough video.

### Background

Notion Business/Enterprise workspaces transition from unlimited Custom Agent usage to credit-based billing on May 4, 2026. The #1 new-buyer objection in April 2026 is credit-cost anxiety. No commercial product targets this gap. The kit is positioned as a low-cost ($49 one-time) trailhead that builds an email list ahead of the AgentCore OS flagship launch. Build time is 2–3 weeks. Portfolio rank: #3 (ship first by urgency).

## Functional Requirements

### FR-1: Credit Tracking Database

A Notion database with monthly entry templates that allow admins to log agent credit usage from the Notion admin dashboard and view 90-day rolling trends.

**Acceptance Criteria:**

- [ ] Database schema includes: Entry Date, Workspace Credits Used, Per-Agent Estimates (manual), Month-over-Month Delta (formula), and Notes fields
- [ ] Monthly entry template pre-fills the current month and includes a guided data-entry checklist
- [ ] A rollup or formula view surfaces 90-day trend (3-month comparison table)
- [ ] Documented clearly that per-agent breakdown requires manual estimation if Notion dashboard only exposes aggregate totals

### FR-2: Agent Cost Calculator

A formula-based Notion page or database that estimates per-run credit cost from three inputs: model tier, page scope (small/medium/large), and step count.

**Acceptance Criteria:**

- [ ] Covers all three model tiers available in Notion Custom Agents (e.g., GPT-5.4 Mini/Nano, standard, premium — mapped to documented Notion credit rates)
- [ ] Page scope options (small: <5 pages, medium: 5–20 pages, large: >20 pages) produce distinct multipliers
- [ ] Step count input (1–10 steps) scales estimate linearly
- [ ] Output shows estimated credits per run AND projected monthly cost at N runs/day
- [ ] Validated against published Notion credit documentation; accuracy target ±20%

### FR-3: Optimization Skill Library

Ten prompt-engineering patterns that reduce per-run credit consumption, each with a trigger condition, before/after instruction example, and estimated savings percentage.

**Acceptance Criteria:**

- [ ] Exactly 10 skills delivered at V1 (target: 15 for V1.1)
- [ ] Each skill has: name, trigger condition ("Use when…"), before example (wasteful pattern), after example (optimized pattern), and estimated savings (e.g., "~15–25% fewer credits")
- [ ] Skills cover at minimum: shorter system instructions, explicit step limits, cheaper-model routing, page-scope narrowing, output-length constraints, conditional skip logic, result reuse/caching, batching, deferred execution, and scope-confirmation prompt
- [ ] Skills are presented as a scannable Notion table with expandable detail toggles

### FR-4: Governance Policy Templates

An agent registry database, a monthly review checklist, and an owner assignment workflow that allow one admin to conduct a complete governance review in under 30 minutes.

**Acceptance Criteria:**

- [ ] Agent Registry database includes: Agent Name, Owner, Purpose/Trigger, Model Tier, Connectors Enabled, Estimated Monthly Credits, Last Reviewed date, and Status (active/paused/decommissioned)
- [ ] Monthly Review Checklist page covers: log new usage entries, update agent registry, review top 3 credit consumers, apply ≥1 optimization skill to each high-cost agent, update owner assignments
- [ ] Owner Assignment Workflow explains how to set and communicate agent ownership in the registry
- [ ] End-to-end review (fresh admin, no prior context) completable in <30 minutes per internal test

### FR-5: Dashboard Walkthrough Video

A 45–60 minute screen-recorded video walking through the Notion admin dashboard, the kit setup flow, a complete monthly review, and the optimization skill application process.

**Acceptance Criteria:**

- [ ] Video covers: navigating to the Notion admin credit dashboard, interpreting available data, transferring data into the Tracking DB, running the Cost Calculator for 2 example agents, applying 3 optimization skills live, completing a monthly review using the checklist
- [ ] Video is hosted (Loom or equivalent) and linked from the kit's index page
- [ ] Chapters/timestamps provided for non-linear navigation
- [ ] Runtime 45–60 minutes; target completion rate ≥60% for first 20 minutes

## Non-Functional Requirements

### Compatibility

- Requires Notion Business or Enterprise plan (Custom Agents not available on Free/Plus)
- Compatible with any existing Notion workspace structure — no required database relations to external plugins

### Accessibility

- All databases include descriptive property names and helper-text in page descriptions
- Video includes captions (auto-generated + reviewed)

### Scalability

- Tracking DB designed to hold 24+ months of entries without formula degradation
- Agent Registry supports up to 50 agents without view-performance issues

### Security

- No external API keys or credentials stored in the Notion template
- Zapier/Make alerting workaround (P1) documented with read-only Notion API token scoping instructions

### Performance

- Monthly review checklist completable in <30 minutes with no Notion automation lag
- Cost Calculator formula resolves in <2 seconds for all valid inputs

## Acceptance Criteria

### Must Have (P0)

- [ ] Credit Tracking DB with monthly entry template and 90-day trend view functional
- [ ] Agent Cost Calculator covers all three model tiers and returns plausible estimates
- [ ] ≥10 optimization skills with before/after examples and savings estimates
- [ ] Agent Registry + Monthly Review Checklist complete and tested end-to-end
- [ ] Dashboard walkthrough video (45–60 min) published and linked from kit index page

### Should Have (P1)

- [ ] Zapier or Make alerting workaround guide (step-by-step, free tier, non-developer admin can complete in <60 min)
- [ ] Sales page copy draft (headline, problem/solution, what's included, pricing, FAQ)

### Nice to Have (P2)

- [ ] V1.1 update guide if Notion ships native per-agent credit monitoring before launch
- [ ] Email nurture sequence draft (3 emails: pre-launch waitlist → launch → 7-day follow-up)

## Scope

### In Scope

- Notion workspace template: Credit Tracking DB, Agent Cost Calculator, Agent Registry, Monthly Review Checklist, Optimization Skill Library, Kit Index page
- Dashboard walkthrough video (P0)
- Zapier/Make alerting workaround guide (P1)
- Sales page copy draft (P1)

### Out of Scope

- Real-time native Notion alerting (platform limitation)
- Automatic credit top-ups or billing API integrations
- Cross-workspace or multi-account aggregation
- Per-user credit attribution (not exposed by Notion admin dashboard)
- Mobile-optimized Notion views
- Custom Agent configuration (this kit governs agents, not builds them)

### Future Considerations

- V1.1: Extended skill library (15 skills), native alert guide if Notion ships the feature
- V2: Scheduled autonomous monitoring via MCP + Claude Desktop
- Bundle play: Credit Governance Kit + AgentCore OS at $119–$129

## Dependencies

### Upstream Dependencies

| Dependency | Type | Status | Notes |
| --- | --- | --- | --- |
| Notion credit rates (official) | Research | Open question | Must confirm exact credits/run per model tier before building calculator |
| Notion admin dashboard data structure | Research | Open question | Must confirm whether per-agent breakdown is available or only aggregate totals |
| Notion workspace (Business plan) | Environment | Required | Need active Business workspace to build and test template |

### Downstream Impacts

| Component | Impact | Mitigation |
| --- | --- | --- |
| AgentCore OS launch | Credit Governance Kit builds email list; delay impacts AgentOS audience size | Ship CGK by April 30 to capture pre-billing urgency window |
| Role Agent Library | CGK buyers are natural Role Agent Library upsell candidates | Include "what's next" page in kit pointing to Role Agent Library |

### External Dependencies

- Loom (or equivalent) for video hosting
- Zapier or Make free tier for alerting workaround guide (P1)
- Gumroad or Lemon Squeezy for sales/delivery

## Risks

### Technical Risks

| Risk | Probability | Impact | Mitigation |
| --- | --- | --- | --- |
| Notion admin dashboard exposes only aggregate credit totals, not per-agent breakdown | High | Medium | Design Tracking DB for workspace-level totals; document limitation transparently; per-agent estimates become manual calculator inputs |
| Notion credit rates change between now and May 4 | Low | Medium | Version-stamp the calculator with the rate source date; note in kit that rates should be reverified against official docs |
| Zapier cannot read Notion admin dashboard API (only workspace API) | Medium | Low | If confirmed, reposition P1 workaround as "scheduled Notion database check" rather than "admin dashboard alert"; still valuable |

### Business Risks

| Risk | Probability | Impact | Mitigation |
| --- | --- | --- | --- |
| Notion ships native credit monitoring before May 4 | Low | High | Optimization skill library and governance templates retain full value regardless; reposition kit as "governance playbook" rather than "monitoring gap filler" |
| Custom Agent workspace transfer friction limits plug-and-play promise | Low | Low | Kit is documentation + DB templates, not agent configs — no transfer friction issue |
| Audience too small to reach 50-unit target | Medium | Medium | Pre-launch waitlist via Twitter/LinkedIn posts targeting Notion Power Users group and r/Notion |

### Unknowns

- [ ] Does the Notion admin dashboard expose per-agent credit breakdowns, or only workspace-level totals?
- [ ] What are the exact credit consumption rates per model tier as of May 4, 2026? (Need official Notion pricing documentation)
- [ ] Can Zapier trigger on Notion admin dashboard data, or only on Notion database/page changes via the workspace API?

## Open Questions

- [ ] **Credit granularity:** Confirm per-agent vs. aggregate-only data in admin dashboard before finalizing Tracking DB schema
- [ ] **Model tier rates:** Source official Notion credit rates per run per model tier; validate calculator against at least 5 known-cost scenarios
- [ ] **Alerting feasibility:** Test whether Zapier's Notion connector can access admin-level data or only workspace API; determines P1 workaround scope
- [ ] **Transfer mechanics:** Confirm workspace duplication flow for Notion databases to validate delivery method (duplication link vs. manual recreation instructions)

## References

- Notion Custom Agents launch announcement (March 2026)
- Notion Custom Skills launch (March 20, 2026)
- Notion billing transition documentation (May 4, 2026 credit transition)
- AgentOS (Gumroad, 4.9/5, 76 reviews) — price anchor validation at $89
- Remote case study: inbox triage agent saving 20 hours/week — demand validation

---

**Approved By:** shaneslo
**Approval Date:** 2026-04-16
