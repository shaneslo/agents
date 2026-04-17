# Prompt: Internal precedent & research synthesis

**Workflow:** I need to understand how the firm has previously handled a tax issue, or synthesize external tax authority into a usable brief, before drafting my own analysis.

**Tool fit:** Goldman Sachs proprietary GPT (RAG-grounded) as primary. Copilot BizChat over SharePoint as secondary for pure firm-precedent search. Specialty tax research platform as third leg.

**Risk level:** Medium. AI-surfaced authority must always be verified against the primary source.

---

## Goal

Produce a structured research brief with:
1. Issue statement (1–2 lines).
2. Relevant authorities with citations.
3. Key holdings / principles extracted.
4. Tensions, splits, or open questions.
5. Firm-internal precedents if surfaced.
6. Explicit "unknowns" list.

Output is always a **draft for my review**, never a substitute for reading the authorities.

## System prompt (prop-GPT)

> You are assisting a Goldman Sachs tax Senior Associate with research synthesis on institutional-client matters. For every piece of authority or firm precedent you surface, you must include a citation with enough specificity that a human can locate and verify the source in one step. If you cannot cite with that level of specificity, say "not cited" and flag it. Never summarize a source you have not actually retrieved. If the corpus does not contain relevant material, say so explicitly rather than generalizing from training data. Preserve ambiguity where it exists. Flag any split authority or unsettled area.

## User-prompt template

```
Issue: {ISSUE_STATEMENT}
Context (non-identifying): {GENERIC_FACT_PATTERN}
Jurisdictions in scope: {JURISDICTIONS}
Time horizon of authority: {e.g. "last 10 years; earlier if foundational"}
Type of synthesis wanted: {"narrow brief" | "broad survey" | "comparison"}

Please produce:
1. A one-sentence issue framing.
2. Up to {N} most relevant authorities, each with: cite, holding in one sentence, relevance in one sentence.
3. Any firm-internal precedents from the indexed corpus, with their cite and a one-sentence relevance note.
4. Tensions / splits / unsettled areas — with cites.
5. An "unknowns" list of what I would need to confirm before relying on this.
6. A suggested next-step research plan if gaps remain.

Do not provide a recommendation or conclusion. I will form that after verifying sources.
```

## Example (fully synthetic)

> Issue: Whether a particular income item received by a foreign institutional client through a U.S. partnership is ECI.
>
> Context: Widely-held foreign institutional investor; U.S. partnership with mixed portfolio including trading activity.
>
> Jurisdictions in scope: U.S. federal.
>
> Type: narrow brief.

Expected shape of output (illustrative):

```
Issue framing: ...
Authorities (5):
  1. [Cite] — Holding: ... — Relevance: ...
  2. ...
Firm-internal precedents (2): ...
Tensions: ...
Unknowns: [1] whether the partnership's trading activity rises to the level of a US trade or business; [2] ...
Suggested next steps: ...
```

## Known failure modes

1. **Fabricated citations.** Most common failure. Always click through to the cited source; if the link is broken or the page doesn't say what the summary claims, the citation is dead. One single fabricated cite invalidates the whole brief in reviewer's eyes.
2. **Confident synthesis of a splittable issue.** Ask for tensions explicitly (step 4). If the model says "it is well established that…" on a genuinely contested area, push back.
3. **Corpus gaps masquerading as absence of authority.** The prop-GPT RAG corpus may not include every relevant source. Verify with the specialty research platform before treating silence as meaning.
4. **Over-generalization across jurisdictions.** Ask explicitly which jurisdiction each authority is from.
5. **Stale authority.** Ask for the year of each authority; be alert to subsequent legislation or case law.

## Eval rubric

For any use of this prompt, score the output 0–2 on each:

- [ ] **Citation integrity** — every cite resolves to the claimed source. (0 = any fabrication; 2 = all verified)
- [ ] **Coverage** — relevant major authority surfaced. (0 = missing something an SA would know; 2 = complete)
- [ ] **Calibration** — ambiguity preserved, splits flagged. (0 = false certainty; 2 = honest)
- [ ] **Relevance filtering** — off-topic authority excluded. (0 = padding; 2 = tight)
- [ ] **Usability** — I could hand this to my reviewer as a starting point. (0 = no; 2 = yes)

Target: average ≥ 1.6 across five uses before treating the prompt as stable.
