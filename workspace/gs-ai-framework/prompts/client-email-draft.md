# Prompt: Client email draft

**Workflow:** Drafting or responding to client emails on tax matters — follow-ups, status updates, non-committal acknowledgments, next-step proposals.

**Tool fit:** Outlook + Copilot primarily. Prop-GPT as fallback for substance-heavy drafts that benefit from firm-grounded language.

**Risk level:** High visibility, medium substantive risk. Voice and precision matter; any substantive tax content requires a review pass.

---

## Goal

Produce a draft email that:
1. Matches the firm's tone for institutional-client correspondence — precise, measured, neither casual nor stiff.
2. Commits only to what I can deliver.
3. Never states a tax position that has not been reviewed.
4. Leaves the client with a clear next step.
5. Is short. Length is a feature, not a bug.

## System prompt

> You draft institutional-client email responses for a Goldman Sachs tax Senior Associate. Target length: 75–150 words unless otherwise specified. Tone: professional, precise, measured, collegial — never effusive, never casual, never stiff. Never state a tax position or conclusion; frame any substantive content as "our current thinking," "preliminary view," or "subject to confirmation." Always include a concrete next step with an owner and an approximate timeframe. Never promise outcomes, only process. Preserve client-side ambiguity rather than resolving it in the draft.

## User-prompt template

```
Relationship: {e.g. "existing client, ongoing matter" | "new relationship, first email"}
Client tone to match: {FORMAL / SEMI-FORMAL / COLLEGIAL} — infer from the thread if provided
Prior thread summary (non-identifying): {SUMMARY}
My role in this exchange: {"respond" | "initiate" | "follow up on unanswered" | "escalate politely"}
What I need to convey:
  - {POINT 1}
  - {POINT 2}
Commitments I am authorized to make: {LIST — be explicit about ceiling}
Do not commit to: {ANTI-LIST}
Desired next step: {e.g. "call on Thursday" | "deliverable by end of next week"}
Length: {concise / standard}

Please produce:
1. A subject line (6–10 words).
2. An email body of the target length.
3. An alternative last-line suggesting a different next-step phrasing.
4. A one-line note flagging anything I should double-check before sending.
```

## Example (fully synthetic)

> Relationship: existing institutional client, ongoing matter.
>
> Client tone: formal, corporate.
>
> Prior thread: client asked for a view on a structuring question raised in a call two days ago.
>
> My role: respond.
>
> Convey: we have begun analysis; preliminary concerns exist around one issue; full memo next week.
>
> Cannot commit to: a position, a timing earlier than next Friday, or any fee adjustment.
>
> Next step: short call Thursday to align.
>
> Length: concise.

Expected shape (illustrative):

```
Subject: Structuring question — initial thoughts and next steps

[Name],

Thank you for the call on Tuesday. We've begun working through the structuring question you raised and wanted to share an initial read. Our preliminary view is that the analysis will turn primarily on [neutral framing of the issue]; we'd like to confirm a handful of facts before taking a firmer position. We expect to have a full memo to you by end of day next Friday.

In the meantime, would a 20-minute call on Thursday suit you, so we can align on scope and any factual gaps?

Best regards,
[Me]

Alternate close: "Happy to hold a call this week if helpful — Thursday afternoon works on our end."
Check before sending: confirm Thursday calendar; confirm Friday deliverable with VP.
```

## Known failure modes

1. **Voice mismatch.** Copilot defaults to a generic corporate voice that reads slightly too warm for bulge-bracket institutional tone. Specify "measured, not effusive" explicitly.
2. **Implicit commitments.** Words like "we will have X" convert into firm commitments. Replace with "we expect to."
3. **Premature positions.** The draft sneaks in a view on the tax issue. Strip any sentence a reviewer has not seen.
4. **Over-explanation.** Institutional clients do not want a technical primer; they want a view and a next step. Cut.
5. **Hallucinated context.** If the thread summary is thin, the model invents context that was not in the email. Verify every specific reference.

## Eval rubric

- [ ] **Voice match.** Reads like a Senior Associate at a top-tier firm. (0/1/2)
- [ ] **Commitment discipline.** No over-promises. (0/1/2)
- [ ] **No un-reviewed positions.** (0/1/2)
- [ ] **Clear next step.** Named, scoped, timed. (0/1/2)
- [ ] **Length discipline.** Within target. (0/1/2)

Target: ≥ 1.8 average. Emails are high-visibility; the bar is higher than research.
