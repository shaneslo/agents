# tools.md — AI & productivity tooling inventory

> Fill in the **Confirmed** columns during your first week. Everything below is a hypothesis until verified with GS documentation, tax-technology team, or compliance. **Never test policy questions by trying things with real client data.**

## Tool 1 — Goldman Sachs Proprietary GPT

### Assumptions (verify day one)

| Dimension | Likely | Needs confirmation |
|-----------|--------|--------------------|
| Underlying model | Frontier LLM (Claude / GPT-class) wrapped with internal guardrails | Which model, which version, update cadence |
| Grounding | RAG over internal docs (research, policies, SOPs, possibly historical deliverables) | Scope of corpus, refresh frequency, which tax-specific content is indexed |
| Data classification | Likely allows firm-internal; unclear on client-identifiable data | Rules of engagement — confirm with compliance and tax-tech |
| Surfaces | Web UI at minimum; possibly API, Excel add-in, Teams bot | Which entry points and what each supports |
| Audit | Prompts and outputs logged centrally | Retention period, who sees logs, user-facing logs |
| Citations | Source links in RAG responses | How to validate citation authenticity |

### Day-one checklist

- [ ] Request access to all available prop-GPT modes / surfaces.
- [ ] Read the official user documentation end-to-end (not just the quickstart).
- [ ] Find and join any internal power-user channel or office hours.
- [ ] Identify the escalation path for bugs, hallucinations, and access issues.
- [ ] Confirm redaction / classification rules in writing.

### How I will use it — tax lens

- Research synthesis across internal tax memos, IRS / Treasury / OECD commentary, and firm positions.
- Scaffolding — structure-of-the-memo, outline-of-the-response, checklist-of-considerations.
- Review assistance — "what am I missing from this analysis?" as a second reader.
- Onboarding — rapidly orient to unfamiliar product areas (derivatives tax, partnership tax, structured products, etc.) to the level a Senior Associate needs.

### What I will not use it for (until policy is explicit)

- Any content containing client-identifiable information.
- Final-form client deliverables without a full human review pass.
- Generating tax positions that are not explicitly grounded in cited internal/external authority.

---

## Tool 2 — Microsoft 365 Copilot

### Surfaces and tax-role fit

| Surface | Expected use | Tax-specific angle |
|---------|--------------|---------------------|
| **Outlook** | Summarize threads, draft responses, catch-up after PTO | Client email triage, follow-up drafting, internal deal-team comms |
| **Word** | Draft memos, rewrite sections, compare versions | First-draft tax memo structure, citation insertion, format conversion |
| **Excel** | Formula generation, pivot summaries, data explanations | Schedule analysis, reconciliations, allocation waterfalls (synthetic / internal-only data only) |
| **Teams** | Meeting summaries, action items, chat search | Deal-team status captures, cross-functional status updates |
| **SharePoint / OneDrive** | Content discovery across shared libraries | Finding prior-year deliverables, template retrieval |
| **Copilot Chat (BizChat)** | Cross-app synthesis | "What did I commit to in that Client X meeting last week?" |
| **Copilot Pages / Notebook** | Collaborative doc with grounded context | Working-paper scaffolding |

### Morgan Stanley carry-over — concrete lessons to import

Use this section to capture specific MS observations in generic form (no MS-confidential material):

- [ ] **Adoption curve** — what the persona mix looked like at 30/60/90/180 days.
- [ ] **Failure modes** — where Copilot burned trust early (hallucinated summaries, wrong-file grounding, formatting regressions).
- [ ] **Winning use-cases** — the two or three that created pull rather than push.
- [ ] **Training that worked** — format, length, cadence, who led it.
- [ ] **Training that did not work** — and why.
- [ ] **Governance patterns** — what compliance required, what was ignored, what became best-practice.
- [ ] **Measurement** — which KPIs were tracked and which actually moved decisions.

Treat each bullet as a **hypothesis to confirm at GS**, not a rule to apply. The firms will differ.

### Day-one checklist

- [ ] Confirm which Copilot surfaces are licensed for my role.
- [ ] Get the official "rules of engagement for Copilot" document.
- [ ] Test each surface with synthetic / public data to calibrate quality.
- [ ] Identify the Copilot champion network (if one exists) and join.

---

## Tool 3 — Third-party / specialty tools (placeholder)

Add rows as I learn what GS Tax actually uses:

| Tool | Purpose | AI integration? | Policy notes |
|------|---------|-----------------|--------------|
| _(e.g. tax research platform)_ | _(research)_ | _(native AI? Copilot via M365? standalone?)_ | _(what I can and cannot do with it)_ |
| _(e.g. document management system)_ | _(working papers, deliverables)_ | _(search? summarization?)_ | |
| _(e.g. Bloomberg / CapIQ / internal deal systems)_ | _(market data, deal context)_ | _(any GenAI overlay?)_ | |

---

## Tool 4 — Claude Code / Claude.ai / external assistants

- Almost certainly **blocked** on the managed device. Do not assume access.
- Can still be used on **personal device** for this framework and for non-GS learning.
- **Zero GS data** ever leaves a GS-sanctioned boundary. Non-negotiable.

---

## Integration map (to draw in Week 2)

Sketch of how the tools fit together, once I know what is actually available:

```
[ Client email / request ]
        │
        ▼
[ Outlook + Copilot ] ──► triage / first draft
        │
        ▼
[ Prop-GPT ] ──► tax-specific research / synthesis with internal grounding
        │
        ▼
[ Word + Copilot ] ──► memo scaffolding / formatting
        │
        ▼
[ Excel + Copilot ] ──► numerical work (synthetic / internal only until policy clear)
        │
        ▼
[ Human review by me + senior reviewer ]
        │
        ▼
[ Client deliverable ]
```

## Governance mental model

Default stance on any AI use:

1. **Is the data allowed in this tool?** If unclear, stop and ask.
2. **Is the output cited / verifiable?** If not, treat as a draft only.
3. **Would I be comfortable if this interaction appeared in an audit log?** If not, reconsider.
4. **Would a partner sign off on this without a human pass?** If yes, my review was insufficient.
