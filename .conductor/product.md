# Product Vision

## Product Overview

**Name:** Credit Governance Kit

**Tagline:** Monitor, budget, and optimize your Notion agent credits before the billing clock starts.

**Description:**
Credit Governance Kit is a Notion-native monitoring and optimization system for workspace admins running Custom Agents on Business or Enterprise plans. It gives teams a structured way to track agent credit consumption, estimate per-run costs, reduce unnecessary spend through proven prompt patterns, and enforce light governance before the May 4, 2026 usage-based billing transition makes every run count.

## Problem Statement

### The Problem

Notion's May 4, 2026 billing transition moves Custom Agents from an unlimited-use beta to metered, credit-based pricing. Workspace admins are responsible for controlling costs, but the Notion admin dashboard offers only aggregate usage data — no per-agent breakdowns, no historical trending, no threshold alerts, and no cost-reduction guidance. Admins are flying blind heading into a live billing event.

### Current Solutions

- Manual spot-checks of the Notion admin dashboard (no history, no automation)
- Ad hoc spreadsheet tracking by individual admins (inconsistent, not shared)
- No commercial product targets this gap as of April 2026

### Why They Fall Short

Manual dashboard checks provide no trending data and require remembering to look. Spreadsheets are disconnected from the agents themselves and degrade quickly. No existing template or tool surfaces optimization guidance — most admins don't know which prompt changes produce the largest credit savings.

## Target Users

### Primary Users

Workspace Admins on Notion Business or Enterprise

- **Who:** IT leads, ops managers, and technical co-founders who own agent rollouts and will receive the credit bill
- **Goals:** Stay within budget, avoid surprise invoices, demonstrate responsible AI usage to leadership
- **Pain Points:** No native alerting, no per-agent cost visibility, no formal process for governing which agents run and how often
- **Technical Proficiency:** Moderate — comfortable with Notion databases and admin settings; not necessarily developers

### Secondary Users

Solopreneurs and Small Team Operators

- **Who:** Founders and operators who built several Custom Agents for their own workflows
- **Goals:** Understand their cost exposure and reduce it before paying real money
- **Relationship to Primary:** Same pain, smaller scale — they may not have an IT function, so they are both the admin and the end user

## Core Value Proposition

### Key Benefits

1. **Instant cost visibility** — A structured tracking database and cost calculator replace dashboard guesswork with a running record of credit consumption by agent, month, and model tier
2. **Proven savings** — 10 optimization skills cut per-run credit spend through shorter instructions, step limits, cheaper-model routing, and output constraints; each skill includes a before/after example and an estimated savings percentage
3. **Audit-ready governance** — An agent registry, monthly review checklist, and ownership assignment template give admins a defensible paper trail before the billing transition

### Differentiators

- First commercial product targeting Notion credit governance — no direct competition as of April 2026
- Optimization skill library is independent of native monitoring improvements; value persists even if Notion ships better dashboards
- Positioned explicitly as a companion to any agent framework (AgentCore OS, Role Agent Library, or hand-built agents) rather than a standalone system

### Value Statement

> The kit that turns the May 4 billing transition from a threat into a managed event — so you walk in knowing your costs, your owners, and your levers, not scrambling after your first invoice arrives.

## Success Metrics

### Key Performance Indicators

| Metric | Target | Measurement Method |
| --- | --- | --- |
| Units sold in first 30 days | 50 | Gumroad/Lemon Squeezy sales dashboard |
| Email list signups (pre-launch + launch) | 200 | Email platform subscriber count |
| Refund rate | <5% | Platform refund reports |
| Cost reduction reported by buyers | ≥20% projected savings | Post-purchase survey (30-day follow-up) |

### North Star Metric

Workspace admins who completed the monthly review checklist report ≥20% projected credit savings before the May 4 billing date.

### Leading Indicators

- Pre-launch waitlist sign-up rate (target: 50 before launch)
- Video completion rate on dashboard walkthrough (target: ≥60%)

### Lagging Indicators

- 60-day repurchase rate for AgentCore OS bundle (validates trailhead function)
- Net Promoter Score from 30-day buyer survey

## Out of Scope

### Explicitly Not Included

- Real-time native Notion alerting (platform limitation; workaround is documented as optional P1)
- Automatic credit top-ups or billing integrations
- Cross-workspace credit aggregation
- Per-user credit breakdowns (not exposed by Notion admin dashboard as of April 2026)

### Future Considerations

- V1.1: Native alerting guide if Notion ships per-agent credit breakdowns mid-2026
- V2: Scheduled autonomous monitoring via MCP + Claude Desktop (Hybrid MCP CoWork Blueprint pattern)
- Bundle: Credit Governance Kit + AgentCore OS at $119–$129

### Non-Goals

- Replacing the Notion admin dashboard
- Supporting Free or Plus plan workspaces (Custom Agents require Business or Enterprise)
