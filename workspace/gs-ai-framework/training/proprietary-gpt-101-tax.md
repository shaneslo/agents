# Proprietary GPT 101 — Tax / institutional clients

Audience: Senior Associates and analysts on a tax team newly onboarded to the firm's proprietary GPT. Duration: 30 minutes + 15 minutes Q&A.

**Positioning:** this session complements the Copilot 101 session. Copilot is the M365-surface assistant. The proprietary GPT is a firm-grounded reasoning and research surface. They solve different problems; use each for what it's good at.

---

## Opening — 3 min

- What the proprietary GPT is: a firm-hosted, firm-grounded LLM interface. RAG over internal corpora (policies, research, prior memos, etc., subject to what the platform team has indexed). Different data-handling posture from public chatbots.
- What it is not: not the M365 Copilot; not a substitute for a specialty tax-research platform; not authorized for all data classifications (confirm your own rules).
- The three rules:
  1. **Citations are the deliverable.** Responses without cites are drafts at best.
  2. **Corpus silence is not the same as absence of authority.** If the prop-GPT doesn't surface something, check the specialty platform too.
  3. **Never have the prop-GPT state a tax position.** It frames, scaffolds, surfaces. You conclude.

---

## Surface 1 — Research synthesis (8 min)

The highest-leverage use for a tax SA.

**Demo:**
- Paste a research question using the `research-synthesis` prompt template.
- Show the output: issue framing, authorities with cites, tensions, unknowns.
- Open one cite; confirm it says what the summary claims.
- Push back on a summary that looks too confident on a split issue; ask for the contrary view.

**What to point out:**
- The structured ask ("produce 1–6, do not conclude") controls the output far more than a vague question.
- Always open at least two citations. Always.
- Use the model as a second pass, not a first pass, for areas you know well — that's how you calibrate its reliability for the areas you don't.

**Traps to flag:**
- Fabricated cites are the #1 failure mode.
- "The prevailing view is…" on a genuinely contested area.
- Corpus gaps masquerading as doctrinal silence.

**Hands-on (2 min):** Pick a research question you answered last week. Run the prompt. Compare.

---

## Surface 2 — "What am I missing?" review (6 min)

The quietest-highest-leverage use. Use it every day on your own work.

**Demo:** Paste your own memo or analysis (generic / internal only). Ask:

```
I am about to send this to my reviewer. Identify:
1. Any issue I may have under-analyzed.
2. Any counter-argument a reviewer might raise.
3. Any cross-cutting consideration (withholding / treaty / state / reporting / timing) I may have missed.
4. Any internal firm precedent that would strengthen or challenge my analysis.

Do not rewrite. Just critique.
```

**What to point out:**
- The constraint "do not rewrite" keeps the output useful.
- Cross-cutting considerations (the usual four) are where the model earns its keep.
- This is where you learn the fastest — the model sometimes raises something you didn't consider, and that's the whole game.

**Traps:**
- The model sometimes invents counter-arguments that don't apply. Score them yourself; don't just paste them into your memo.

---

## Surface 3 — Memo scaffolding (5 min)

Use the `tax-memo-scaffold` prompt template.

**Demo:** Ask for an outline, issue list, framework-of-analysis, facts-to-confirm, cross-cutting list, risk-flag list. Note: it does not write the analysis.

**What to point out:**
- Scaffold-only discipline: strip any sentence with a conclusion.
- "Facts to confirm" is the most useful section for a Senior Associate; it reveals what the deal team needs to tell you.
- Risk flags should include at least one thing you'd want to pre-warn your VP about.

---

## Surface 4 — Onboarding to unfamiliar domains (4 min)

The quiet superpower.

**Use:** you're staffed on a matter in an area you haven't done in a while (or ever). Ask for a progression, not a conclusion:

```
I'm about to work on a matter involving [generic description]. Produce:
1. A 5-level progression of what a tax professional at this firm should understand about this area, from beginner to sign-off.
2. The 10 most-cited authorities for each level.
3. The 5 most common traps at each level.
4. A reading order if I have 4 hours to prepare.
```

**Why it works:** structured progression prompts produce usable outputs where "explain X" produces shapeless ones.

---

## The grounding discipline — 4 min (the most important 4 minutes)

Every time the proprietary GPT surfaces a piece of authority:

1. **Click through.** If there is no link, ask for a more specific cite or treat the claim as unsourced.
2. **Read the cited passage.** Does it actually say what the summary claims?
3. **Check the date.** Tax law changes. Authority from five years ago might be superseded.
4. **Check the jurisdiction.** Models sometimes mix jurisdictions. Confirm.

If any of these checks fail, treat the whole response as compromised and redo.

**The norm:** "AI-assisted research" means AI surfaced it, you verified it. No verification = no use.

---

## What we did not cover today

- API / programmatic use. Separate session.
- Fine-tuning / customization. Only for the platform team.
- Use with client-identifiable data. Policy-bound; confirm classification first.

## Resources

- Prompt library (team channel link) — five tax-flavored templates to start with.
- Office hours — weekly, drop in with your real questions.
- Escalation path for hallucinations / grounding failures / access issues.

## One-page takeaway card

```
┌────────────────────────────────────────────────────┐
│  Proprietary GPT — Three Rules                     │
│  1. Citations are the deliverable.                 │
│  2. Corpus silence ≠ no authority.                 │
│  3. Never let it state a tax position.             │
│                                                    │
│  Three signature use-cases                         │
│  • Research synthesis (with cites)                 │
│  • "What am I missing?" self-review                │
│  • Memo scaffolding (structure, not substance)     │
│                                                    │
│  The grounding discipline                          │
│  • Click through every cite                        │
│  • Read the cited passage                          │
│  • Check date and jurisdiction                     │
│  • Any failure → redo                              │
└────────────────────────────────────────────────────┘
```

## Facilitator notes

- Show a real (synthetic) fabricated-citation example. Nothing teaches grounding discipline like seeing a plausible-but-fake cite.
- Resist the temptation to demo the "wow" features. The quiet ones are the ones they'll actually use.
- Budget time for questions. This tool raises more questions than Copilot does — good sign.
