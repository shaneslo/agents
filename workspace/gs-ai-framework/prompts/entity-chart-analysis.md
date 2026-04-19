# Prompt: Entity / structure chart analysis

**Workflow:** Orienting to a new institutional client's legal-entity structure — producing a narrative walk-through, a list of likely tax-relevant touchpoints, and a questions-for-the-deal-team list.

**Tool fit:** Prop-GPT for narration and taxonomy. Copilot BizChat + SharePoint for locating any prior-year structure work.

**Risk level:** Low-medium. The AI narrates and hypothesizes; it never determines classification or concludes on treatment.

---

## Goal

Given a structure chart (or a textual description of one — never upload a real client chart until policy is explicit), produce:
1. A plain-English walk-through of the structure.
2. Probable entity classifications by jurisdiction, **flagged as hypotheses to verify**.
3. A list of likely tax-relevant touchpoints: withholding nodes, CFC/PFIC-relevant entities, pass-through vs. opaque entities, treaty-relevant jurisdictions, UBTI-relevant entities if fund context, etc.
4. A questions-for-the-deal-team list — everything I would need to confirm before acting on any of the above.
5. A "what's unusual here" flag list.

## System prompt

> You assist a Goldman Sachs tax Senior Associate with orientation on institutional-client entity structures. You describe and hypothesize — you never determine. Every entity classification must be labeled "hypothesized — to verify with [source]." Every tax-relevant flag must be framed as a question, not a conclusion. If the user's description is ambiguous, ask for the clarifying detail rather than guessing. Never invent jurisdictions, entity types, or relationships that the user did not describe. Prefer a shorter, more-flagged output over a longer, more-confident one.

## User-prompt template

```
Structure description (generic, no client names): {DESCRIPTION}
Known facts:
  - Apex entity type and jurisdiction: {e.g. "Cayman exempted company"}
  - Key intermediate entities: {LIST}
  - Investor profile: {e.g. "mix of US-tax-exempt and foreign institutional"}
  - Economic activity footprint (jurisdictions): {LIST}
  - Any known elections: {LIST}
Context: {e.g. "fund formation" | "acquisition vehicle" | "restructuring diligence" | "routine advisory"}
What I want:
  - Narrative walk-through
  - Probable classifications (hypothesized)
  - Tax-relevant touchpoint list
  - Questions for the deal team
  - "Unusual" flags
```

## Example (fully synthetic)

> Description: Apex Cayman exempted company → Delaware LLC (check-the-box election?) → three jurisdiction-specific operating subsidiaries (Lux, Singapore, Delaware). Investor base: mix of US-taxable, US-tax-exempt, and foreign institutional.

Expected shape (illustrative):

```
Narrative:
  The apex Cayman vehicle holds a Delaware LLC, which in turn holds three operating subs in Lux, Singapore, and Delaware. The structure is consistent with a fund-of-one or a holding vehicle for a single transaction.

Hypothesized classifications (to verify):
  - Cayman exempted company: typically treated as a foreign corporation for US federal tax purposes. Verify whether CTB election was made.
  - Delaware LLC: default classification depends on # of members; assume partnership default unless otherwise elected.
  - Lux/Singapore/Delaware operating subs: each needs confirmation — hypotheses only.

Tax-relevant touchpoints (as questions):
  - Is the Delaware LLC treated as a partnership or disregarded? If partnership, is it engaged in a US trade or business?
  - Does the Cayman apex qualify for any treaty benefits anywhere in the chain? (Typically not.)
  - Any entities triggering CFC / PFIC lookthrough for US investors?
  - UBTI exposure for US-tax-exempt investors?
  - Withholding at any payment node between subs and apex?
  - Is there a blocker entity to address ECI for foreign investors?

Questions for deal team:
  1. Has a CTB election been made on the Delaware LLC?
  2. What is the economic activity profile of each operating sub?
  3. Investor profile percentages?
  4. Expected income character at each sub?

Unusual flags:
  - Three-jurisdiction operating footprint suggests a non-trivial treaty / withholding map worth diagramming.
```

## Known failure modes

1. **Confident classification.** Model says "this is a CFC" before we know the investor profile percentages. Strip all determinations; reframe as hypotheses.
2. **Inventing entities.** If the description is sparse, the model fills in a plausible-but-fabricated structure. Always cross-check the output against what you actually said.
3. **Missed touchpoints.** UBTI, ECI, CFC/PFIC, and withholding are the usual four; the model sometimes misses one. Verify the list covers all four plus treaty.
4. **No questions list.** The output is useless without a clean list of things to ask the deal team. Insist on it.
5. **Over-narration.** The model writes three paragraphs of prose. One is enough.

## Eval rubric

- [ ] **Classification discipline.** All hypothesized, none determined. (0/1/2)
- [ ] **Entity fidelity.** No invented entities or relationships. (0/1/2)
- [ ] **Touchpoint completeness.** UBTI/ECI/CFC/PFIC/withholding/treaty covered. (0/1/2)
- [ ] **Questions list quality.** Actionable, specific. (0/1/2)
- [ ] **"Unusual" flag utility.** Catches the non-obvious. (0/1/2)

Target: ≥ 1.6 average across five uses.
