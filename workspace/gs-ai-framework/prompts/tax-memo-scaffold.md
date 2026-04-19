# Prompt: Tax memo scaffolding

**Workflow:** Producing the structural first draft of a tax memo for an institutional client — outline, issue list, analytical framework, open-questions list — before I write the substantive content myself.

**Tool fit:** Prop-GPT for the scaffold; Word + Copilot for subsequent prose work.

**Risk level:** Medium. The AI is never writing tax positions — only proposing structure and raising issue candidates for me to vet.

---

## Goal

Produce a memo skeleton that includes:
1. Issue list, framed as questions.
2. Standard sections a tax memo of this type typically has.
3. Framework of analysis for each issue (not the analysis itself).
4. Facts I would need to confirm or gather.
5. A list of cross-cutting considerations (withholding, reporting, treaty, state, timing).
6. A risk-flag list for the reviewer.

Output is a **scaffold only**. Substantive analysis is my job.

## System prompt

> You are assisting a Goldman Sachs tax Senior Associate on an institutional-client memo. You produce structural scaffolds, not legal conclusions. Never state a tax position. Never say "the better view is…". Surface issues as questions. Surface frameworks as "the analysis typically considers…". When you cite authority, cite with sufficient specificity that a human can verify in one step; if you cannot, label it "illustrative — to verify." Flag any issue you suspect is contested or has recent legislative change.

## User-prompt template

```
Memo type: {e.g. "internal technical memo" | "client-facing position memo" | "issue list for partner review"}
Audience: {e.g. "reviewing VP" | "client tax counsel" | "deal team"}
Subject matter: {GENERIC_SUBJECT}
Key fact pattern (non-identifying, reframed generically): {FACTS}
Transaction type (if applicable): {e.g. "acquisition structure" | "fund formation" | "restructuring"}
Jurisdictions: {JURISDICTIONS}
Length target: {SHORT/MEDIUM/LONG}

Please produce:
1. A proposed section outline with estimated length per section.
2. The issue list — each issue as a question.
3. For each issue, a 1-paragraph "framework of analysis" noting which doctrines, statutes, or lines of authority typically apply.
4. A "facts to confirm" list — what I would need from the client or deal team before analyzing.
5. Cross-cutting considerations (withholding, reporting, state/local, treaty, timing, elections).
6. A "risk flags for reviewer" list — anything where I should pre-warn my VP.

Do not state any tax conclusion. Do not assert that a position is more likely than another.
```

## Example (fully synthetic)

> Memo type: internal technical memo.
>
> Audience: reviewing VP.
>
> Subject matter: U.S. federal tax treatment of a novel derivative instrument issued by a foreign affiliate to institutional investors.
>
> Facts: {generic facts};
>
> Jurisdictions: U.S. federal; foreign issuer jurisdiction.
>
> Length: medium.

Expected shape (illustrative):

```
Outline: I. Summary. II. Facts. III. Issues. IV. Analysis. V. Conclusion. VI. Open questions.
Issue list:
  1. How is the instrument characterized for US federal income tax purposes?
  2. If treated as debt, what withholding regime applies?
  3. ...
Frameworks:
  1. Characterization typically considers [factor list], with analogies to [categories]. Recent Treasury guidance [if any] to verify.
  2. ...
Facts to confirm: term, payment profile, embedded optionality, holder profile, issuer jurisdiction tax classification.
Cross-cutting: FATCA, treaty eligibility, state conformity if relevant, timing of income recognition.
Risk flags: [possibly contested characterization]; [any recent legislative change to verify].
```

## Known failure modes

1. **Smuggled conclusions.** The model wraps a conclusion in framework language ("the analysis generally results in…"). Strip any language that implies a position.
2. **Stale framework.** Tax doctrine evolves. Treat every framework paragraph as a hypothesis; check against current authority.
3. **Missing cross-cutting.** Reviewers often care most about what was *omitted*. The "cross-cutting" step catches this.
4. **Issue-list inflation.** Model lists 15 issues when 5 are real. Rank them; defer the non-critical ones.
5. **Authority name-dropping without verification.** If a statute or case is named, verify before building anything on it.

## Eval rubric

- [ ] **No conclusions.** (0 = any normative claim; 2 = pure scaffold)
- [ ] **Issue coverage.** Would my VP ask about any issue the scaffold missed? (0 = yes; 2 = no)
- [ ] **Framework accuracy.** Frameworks map to real doctrine. (0 = invented; 2 = recognizable)
- [ ] **Cross-cutting completeness.** (0 = missed withholding / treaty / state / reporting; 2 = caught)
- [ ] **Risk-flag utility.** (0 = useless; 2 = at least one flag worth raising)

Target: ≥ 1.6 average across five uses.
