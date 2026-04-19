# Prompt: Schedule / K-1 summarization

**Workflow:** Producing a structured summary of a partnership schedule (e.g., a K-1, a foreign-equivalent schedule, or a fund-manager report) — line-item narrative, unusual items, follow-up question list — before I use the actual numbers in any analysis.

**Tool fit:** Excel + Copilot (on synthetic or explicitly-sanctioned data only). Prop-GPT if the schedule is accompanied by narrative documents.

**Risk level:** High. K-1-level data is often client-identifiable. **Do not feed real client data to any tool that has not been explicitly sanctioned for that data classification.** Default to synthetic data for prompt development, and only use real data once policy is confirmed.

---

## Goal

Given a schedule (text-extracted or structured, never an uploaded PDF of real client data until policy is explicit), produce:
1. A plain-English narrative summary of what the schedule shows.
2. A list of line items grouped by tax character (ordinary, capital, Section-specific items, foreign, state-specific).
3. An "unusual items" list — anything that would not appear on a typical schedule for this entity type.
4. A follow-up-questions list — gaps, inconsistencies, possibly missing items.
5. A downstream-relevance list — what this schedule implies for the investor's own return.

## System prompt

> You assist a Goldman Sachs tax Senior Associate in summarizing partnership schedules (K-1s or equivalents). You narrate and categorize; you do not compute tax liabilities or state conclusions about investor-level treatment. If line-item totals do not reconcile, surface the inconsistency as a question rather than "fixing" it. Never infer missing data. If a line is ambiguous (e.g., a partner-specific allocation without basis information), flag it rather than assuming. Preserve all figures exactly as provided; do not round silently.

## User-prompt template

```
Schedule type: {e.g. "K-1 (partnership)" | "foreign partnership equivalent" | "manager report"}
Entity profile: {e.g. "US partnership; institutional investor is limited partner"}
Investor profile: {e.g. "foreign pension" | "US tax-exempt" | "US taxable corporation"} — this affects what's relevant
Data classification: {SYNTHETIC / INTERNAL-SAMPLE / SANCTIONED-CLIENT-DATA} — if unclear, stop
Schedule content (pasted or referenced): {CONTENT}

Please produce:
1. Narrative summary (1 paragraph).
2. Line items grouped by character (ordinary / capital / Section-specific / foreign / state).
3. Unusual items list.
4. Follow-up questions.
5. Downstream-relevance list for this investor profile.

Preserve all figures exactly. Do not compute the investor-level tax impact.
```

## Example (fully synthetic)

> Schedule type: K-1 (partnership).
>
> Entity profile: US investment partnership; limited partner is a foreign pension.
>
> Data classification: SYNTHETIC.
>
> Content: {synthetic line items}.

Expected shape (illustrative):

```
Narrative: The K-1 shows allocations from a US investment partnership to a limited partner, with ordinary income, short- and long-term capital gains, a Section 1231 item, and foreign-source interest. Box 20 codes include {codes}.

Line items by character:
  Ordinary: [items]
  Capital: ST [items]; LT [items]
  Section-specific: [items with section references]
  Foreign: [items]
  State: [items]

Unusual items:
  - Box 20 code [Z/AH/etc.] is present — confirm partner has the detailed statement.
  - [item] is a line not typically seen on this entity type; worth confirming.

Follow-up questions:
  1. Is a supplemental statement attached for Box 20 code X?
  2. Does the foreign-source interest qualify for any treaty reduction?
  3. Does the partnership have a US trade or business that would generate ECI for this LP?

Downstream relevance for a foreign pension LP:
  - ECI determination is the dominant question.
  - FDAP withholding for any US-source interest.
  - Treaty-based claim possibilities.
  - Whether any state-specific filings are triggered.
```

## Known failure modes

1. **Silent reconciliation.** The model quietly "fixes" a line that doesn't add up. This is the worst failure — it destroys reviewer trust. Insist on surfacing inconsistencies as questions.
2. **Figure drift.** Rounding or re-formatting corrupts numbers. Add "preserve figures exactly" to the system prompt and double-check.
3. **Unauthorized computation.** The model computes "estimated tax impact" without being asked. Strip.
4. **Character misclassification.** A line labeled as one character when the code clearly indicates another. Spot-check every non-obvious classification.
5. **Data-classification drift.** Someone pastes real client data into a synthetic-only prompt cycle. This is a policy incident, not a prompt failure — but the prompt should remind the user at the top.

## Eval rubric

- [ ] **Figure fidelity.** All numbers preserved exactly. (0/1/2)
- [ ] **No inferred data.** (0/1/2)
- [ ] **Character accuracy.** Spot-checks of 5 line items all correct. (0/1/2)
- [ ] **Unusual-items utility.** Catches at least one real anomaly. (0/1/2)
- [ ] **Questions list actionable.** (0/1/2)

Target: ≥ 1.8 average. This prompt touches data; the bar is higher.

## Policy reminder (read before each use)

Before every use of this prompt:

1. What is the data classification of the schedule I am about to paste?
2. Is the tool I am using sanctioned for that classification?
3. If the answer to either is unclear, **do not use this prompt**. Ask compliance.
