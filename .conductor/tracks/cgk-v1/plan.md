# Implementation Plan: Credit Governance Kit — V1

## Overview

**Track ID:** cgk-v1
**Spec:** [spec.md](./spec.md)
**Estimated Effort:** 2–3 weeks solo (14–18 working days)
**Target Completion:** 2026-05-01 (3 days before Notion billing transition)

## Progress Summary

| Phase | Status | Progress |
| --- | --- | --- |
| Phase 1: Foundation & Research | pending | 0% |
| Phase 2: Calculator & Skill Library | pending | 0% |
| Phase 3: Governance & Alerting | pending | 0% |
| Phase 4: Video, Polish & Launch Prep | pending | 0% |

---

## Phase 1: Foundation & Research

**Objective:** Resolve all open unknowns from the spec, then build the Credit Tracking Database and Agent Registry so everything downstream has a validated data model.
**Estimated Duration:** Days 1–4

### Tasks

- [ ] **1.1 Resolve open questions (FR-1, FR-2 dependencies)**
  - [ ] Log into a Notion Business workspace admin panel; document exactly what credit data is exposed (aggregate only vs. per-agent breakdown)
  - [ ] Source official Notion credit rates per model tier per run; screenshot and date-stamp the source
  - [ ] Test Zapier's Notion connector: confirm whether admin dashboard data is accessible or only workspace API data (determines P1 workaround scope)
  - [ ] Document findings in a `research-notes.md` file in this track directory

- [ ] **1.2 Build Credit Tracking Database**
  - [ ] Create Notion database with schema: Entry Date, Month Label, Workspace Credits Used, Per-Agent Estimates (multi-text), MoM Delta (formula), Notes
  - [ ] Create Monthly Entry Template with guided data-entry checklist (where to find the data in admin dashboard, how to estimate per-agent split)
  - [ ] Build 3-month comparison view (filter: last 3 monthly entries, grouped by Month Label)
  - [ ] Test: log 3 mock monthly entries; confirm MoM Delta formula resolves correctly

- [ ] **1.3 Build Agent Registry**
  - [ ] Create Notion database with schema: Agent Name, Owner, Purpose/Trigger, Model Tier (select), Connectors Enabled (multi-select), Estimated Monthly Credits (number), Last Reviewed (date), Status (active/paused/decommissioned)
  - [ ] Create default view filtered to Status = active, sorted by Estimated Monthly Credits descending
  - [ ] Add 3 sample entries (Inbox Manager, Product Feedback Triager, Meeting Prep) to demonstrate schema
  - [ ] Test: confirm registry loads and filters correctly in a fresh workspace duplication

### Verification

- [ ] Research notes document answers to all 3 open questions from spec
- [ ] Tracking DB logs 3 mock entries with correct MoM Delta formulas
- [ ] Agent Registry displays 3 sample agents in the active filtered view

### Checkpoint

```
Commit: [cgk-v1] checkpoint: phase 1 complete — foundation and research done
```

---

## Phase 2: Calculator & Skill Library

**Objective:** Build the Agent Cost Calculator using validated rate data from Phase 1, then write all 10 optimization skills.
**Estimated Duration:** Days 5–9
**Dependencies:** Phase 1 complete (credit rates and admin data structure confirmed)

### Tasks

- [ ] **2.1 Build Agent Cost Calculator**
  - [ ] Create a Notion database or formula page with inputs: Model Tier (select), Page Scope (select: small/medium/large), Step Count (number), Runs Per Day (number)
  - [ ] Implement per-run credit estimate formula using rates sourced in Phase 1
  - [ ] Add page-scope multipliers: small (<5 pages) = 1×, medium (5–20) = 2×, large (>20) = 3.5× (adjust based on Notion documentation)
  - [ ] Add output fields: Credits Per Run, Projected Monthly Credits, Projected Monthly Cost (at published Notion credit price)
  - [ ] Validate against 5 test scenarios using known-cost agent runs; document results in research-notes.md

- [ ] **2.2 Write Optimization Skills 1–5**
  - [ ] Skill 1: Shorter system instructions — trigger: instructions >500 words; before/after; savings estimate
  - [ ] Skill 2: Explicit step limits — trigger: open-ended multi-step agents; before/after; savings estimate
  - [ ] Skill 3: Cheaper-model routing — trigger: agents using premium tier for low-complexity tasks; before/after; savings estimate
  - [ ] Skill 4: Page-scope narrowing — trigger: agents with broad database or workspace access; before/after; savings estimate
  - [ ] Skill 5: Output-length constraints — trigger: agents producing long summaries or reports; before/after; savings estimate

- [ ] **2.3 Write Optimization Skills 6–10**
  - [ ] Skill 6: Conditional skip logic — trigger: agents that run even when no new input exists; before/after; savings estimate
  - [ ] Skill 7: Result reuse / caching — trigger: agents re-fetching unchanged data on every run; before/after; savings estimate
  - [ ] Skill 8: Batching — trigger: agents triggered per-item rather than per-batch; before/after; savings estimate
  - [ ] Skill 9: Deferred execution — trigger: agents running on a tight schedule regardless of demand; before/after; savings estimate
  - [ ] Skill 10: Scope-confirmation prompt — trigger: any agent with ambiguous task boundaries; before/after; savings estimate
  - [ ] Build skill library as a Notion table with Name, Trigger, Before, After, Savings columns + expandable toggle for full detail

### Verification

- [ ] Calculator returns estimates within ±20% for all 5 validation scenarios
- [ ] All 10 skills have complete fields (trigger, before, after, savings %)
- [ ] Skill library table renders correctly and toggles expand in Notion

### Checkpoint

```
Commit: [cgk-v1] checkpoint: phase 2 complete — calculator and skill library done
```

---

## Phase 3: Governance Templates & Alerting Workaround

**Objective:** Build the Monthly Review Checklist and governance policy templates; write the P1 alerting workaround guide. Complete end-to-end internal test.
**Estimated Duration:** Days 10–13
**Dependencies:** Phase 2 complete

### Tasks

- [ ] **3.1 Build Monthly Review Checklist**
  - [ ] Create a Notion checklist page with the following steps: (1) Open admin dashboard, log this month's credit total into Tracking DB; (2) Update Agent Registry — add new agents, change status of decommissioned ones; (3) Sort Registry by Estimated Monthly Credits; review top 3; (4) Apply ≥1 optimization skill to each of the top 3 agents; (5) Update Last Reviewed date for all agents touched; (6) Note any anomalies or open questions in the Notes field
  - [ ] Add time-target annotations per step (total target: <30 min)
  - [ ] Link checklist to Tracking DB, Agent Registry, and Skill Library via Notion inline links

- [ ] **3.2 Build Owner Assignment Workflow**
  - [ ] Write a 1-page Notion document: how to assign an agent owner, what owner responsibilities include (monthly review, optimization, decommission decisions), and how to communicate ownership to the team
  - [ ] Include a sample Slack message template for ownership announcements

- [ ] **3.3 Write Kit Index Page & Assemble Workspace**
  - [ ] Create a top-level Kit Index page with: product tagline, getting-started checklist (4 steps), navigation links to all kit components, and a "What's next" section pointing to Role Agent Library and AgentCore OS
  - [ ] Assemble all components (Tracking DB, Calculator, Registry, Skill Library, Monthly Review Checklist, Owner Workflow, Index) into a clean Notion workspace hierarchy
  - [ ] Internal test: duplicate the workspace into a fresh account; follow the getting-started checklist cold; time the first monthly review; confirm <30 min target is met

- [ ] **3.4 Write Alerting Workaround Guide (P1)**
  - [ ] Based on Phase 1 findings, write a step-by-step guide for either: (a) Zapier scheduled check on Notion admin dashboard data, or (b) Zapier scheduled check on the Tracking DB for threshold breach (fallback if admin data not accessible)
  - [ ] Document as a Notion page within the kit; frame explicitly as "optional external workaround" and explain platform limitation
  - [ ] Include Notion API token scoping instructions (read-only, minimum permissions)

### Verification

- [ ] End-to-end internal test: fresh workspace duplication → kit setup → first monthly review → <30 minutes confirmed
- [ ] Kit Index page links to all components without broken references
- [ ] Alerting workaround guide is completable by a non-developer admin in <60 minutes

### Checkpoint

```
Commit: [cgk-v1] checkpoint: phase 3 complete — governance templates and alerting done
```

---

## Phase 4: Video, Polish & Launch Prep

**Objective:** Record the dashboard walkthrough video, finalize all documentation, run a complete buyer-journey QA test, and prepare the sales page copy.
**Estimated Duration:** Days 14–18
**Dependencies:** Phase 3 complete

### Tasks

- [ ] **4.1 Record Dashboard Walkthrough Video**
  - [ ] Outline video chapters: (1) Intro & kit overview ~5 min; (2) Notion admin dashboard tour ~10 min; (3) Kit setup walkthrough ~10 min; (4) First monthly review live demo ~15 min; (5) Applying 3 optimization skills live ~10 min; (6) Q&A / what's next ~5 min
  - [ ] Record screen capture with narration (Loom or equivalent); target runtime 45–60 min
  - [ ] Review recording: confirm all dashboard views are legible, audio is clear, no sensitive workspace data visible
  - [ ] Add auto-generated captions; review and correct errors
  - [ ] Publish (unlisted); add timestamps/chapters; link from Kit Index page

- [ ] **4.2 Write Sales Page Copy**
  - [ ] Headline + subheadline (problem-focused, urgency-driven — reference May 4 date)
  - [ ] Problem section: what admins face without the kit (billing surprise, no visibility, no process)
  - [ ] Solution section: what the kit delivers (5 components, each described in 1–2 sentences)
  - [ ] What's included: formatted component list with benefit annotations
  - [ ] Pricing block: $49 one-time, 30-day refund guarantee
  - [ ] FAQ: 5 questions (requires Business plan? / what if Notion ships native monitoring? / how long to set up? / does this work with AgentCore OS? / is any coding required?)
  - [ ] CTA: "Get the Credit Governance Kit — $49"

- [ ] **4.3 Full Buyer Journey QA**
  - [ ] Simulate complete buyer path: sales page → purchase → workspace duplication → kit index → getting-started checklist → first monthly review → optimization skill applied
  - [ ] Confirm: no broken links, no placeholder text remaining, video loads correctly, duplication delivers all components
  - [ ] Fix any issues found; re-test affected paths

### Verification

- [ ] Video runtime 45–60 min, chapters/timestamps present, captions reviewed
- [ ] Sales page copy complete (all 6 sections)
- [ ] Full buyer journey test passed with no blockers
- [ ] No placeholder text or broken links in delivered workspace

### Checkpoint

```
Commit: [cgk-v1] checkpoint: phase 4 complete — kit ships-ready
```

---

## Final Verification

### Quality Gates

- [ ] All 5 P0 acceptance criteria from spec met
- [ ] End-to-end monthly review completable in <30 minutes (tested cold)
- [ ] Cost Calculator validated against ≥5 known-cost scenarios
- [ ] All 10 optimization skills have complete fields
- [ ] Video published with captions and timestamps
- [ ] Full buyer journey QA passed

### Documentation

- [ ] Kit Index page is the single entry point for all components
- [ ] research-notes.md documents all Phase 1 findings (credit rates, data granularity, alerting feasibility)
- [ ] Each component page has a brief description at the top explaining its purpose

### Launch Readiness

- [ ] Workspace duplication link tested in a fresh account
- [ ] Sales page draft complete and ready for review
- [ ] Email list / waitlist mechanism in place before public announcement
- [ ] "What's next" page points to Role Agent Library (next portfolio release)

---

## Deviations Log

| Date | Task | Deviation | Reason | Resolution |
| --- | --- | --- | --- | --- |
| — | — | — | — | — |

## Notes

**Key constraint:** The May 4, 2026 billing transition is a hard deadline. Phase 1 research must be completed by Day 4 at the latest — if credit rate data or admin dashboard structure is materially different from what the spec assumes, the calculator scope needs to be adjusted immediately rather than discovered at Phase 2.

**Fallback positioning:** If Notion ships native per-agent credit monitoring before launch, reposition the kit as a "governance and optimization playbook" rather than a monitoring gap filler. The skill library and governance templates retain full standalone value in that scenario.

**Bundle note:** This kit is designed as a trailhead into the AgentCore OS ($89) and Role Agent Library ($59) products. The "What's next" page in the kit is a functional part of the portfolio strategy, not optional copy.

---

**Plan Created:** 2026-04-16
**Last Updated:** 2026-04-16
