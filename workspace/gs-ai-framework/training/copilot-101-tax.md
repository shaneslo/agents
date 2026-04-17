# M365 Copilot 101 — Tax / institutional clients

Audience: Senior Associates, VPs, and analysts on a tax team newly onboarded to M365 Copilot. Duration: 30 minutes + 15 minutes Q&A. Format: live demo with one hands-on exercise per surface.

**Bias:** fewer features demoed well beats all features demoed poorly. Pick the three signature use-cases and go deep.

---

## Opening — 3 min

- What Copilot is and what it is not. It is an assistant grounded in your M365 tenant. It is not a general-purpose chatbot. The distinction matters for data handling and for expectations.
- What we will and will not cover today. We will cover Outlook, Word, Teams, and a bit of BizChat. We will not cover Excel-on-real-data or anything touching client-identifiable content — those need their own session.
- The three rules before any demo:
  1. **Human review is non-negotiable.** AI assists a draft. A person ships the draft.
  2. **Cite-and-verify.** If Copilot surfaces a source, open it. If the source doesn't say what the summary claims, the summary is wrong.
  3. **Classification is in your head, not the tool's.** Copilot does not know which email thread has sensitive content. You do. Act accordingly.

---

## Surface 1 — Teams meeting summaries (5 min)

The universal "easy win." Zero controversy, immediate value.

**Demo:** A recorded internal meeting. Generate a summary. Walk through the "Recap" view.

**What to point out:**
- Action items with owners and due dates.
- The chapters view for long meetings.
- The search-across-meeting-content feature.

**Trap to flag:** Action items are often almost-right. "X will draft the memo" might have been "X will decide whether to draft the memo." Always sanity-check owner+verb before re-circulating.

**Hands-on prompt (1 min):** Pull up a recent meeting. Generate summary. Spot one thing the summary got wrong or under-stated.

---

## Surface 2 — Outlook triage and draft (8 min)

The showcase. This is the one that will win the room.

**Demo sequence:**
1. "Catch me up on this thread" — a long internal thread.
2. "Draft a reply" — show how to constrain tone and length with a one-line instruction.
3. "Summarize all emails from X this week" — the inbox-triage play.

**What to point out:**
- Tone constraints in the prompt itself ("measured, 100 words, no commitments beyond scheduling").
- The "highlight key points" feature inside the thread.
- How to iterate: generate → edit → regenerate → keep.

**Traps to flag:**
- Copilot defaults to a slightly too-warm corporate voice. Always correct for institutional-client tone.
- Hallucinated context is real. If the thread is thin, Copilot fills in. Verify.
- Never — *never* — send a Copilot draft without reading every sentence. One hallucinated commitment is a client problem.

**Reference:** the `client-email-draft` prompt in our prompt library for the full template.

**Hands-on prompt (2 min):** Pick an internal thread you've been avoiding. Draft a reply with Copilot. Critique the tone match.

---

## Surface 3 — Word for memo drafting (6 min)

**Demo sequence:**
1. Start with an outline-only Word doc.
2. "Draft section II based on this outline and the attached notes."
3. "Rewrite this paragraph to be more measured."
4. "Compare this version with the previous version."

**What to point out:**
- Copilot is strong at structural work (outlines, transitions, formatting).
- Copilot is weak at substantive tax content — never let it draft a tax position.
- The "rewrite to tone" feature for reviewer-voice adjustments.

**Traps to flag:**
- Substantive tax content must come from you. Copilot writing "is treated as X" is a red flag.
- Formatting drift: Copilot sometimes breaks citation formatting. Spot-check.

**Reference:** the `tax-memo-scaffold` prompt for how to get structural scaffolds from the prop-GPT first, then prose-work in Word.

---

## Surface 4 — BizChat for cross-app synthesis (4 min)

The one people miss. Strongest for "find it across my stuff" use-cases.

**Demo sequence:**
1. "What did I commit to in the [project] meeting last week?"
2. "Find the prior-year memo on [generic topic] in our shared library."
3. "Summarize the last three emails from this client and any related docs."

**What to point out:**
- Grounds across mail, calendar, SharePoint, Teams, OneDrive.
- Returns cited sources — always open them.

**Traps to flag:**
- Cross-app search returns what *you* have access to. It will not find documents outside your permissions. This is correct and good.
- Wrong-file grounding happens. If the cited source doesn't match the summary, the summary is wrong.

---

## What we did not cover today

Flag these for future sessions:
- Excel on real data. Policy and classification conversation first.
- Client-facing email automation. Deliberately out of scope.
- Copilot agents / custom workflows. Later.

## Resources

- Prompt library (team channel link).
- Office hours — 30 minutes weekly, drop in with real work.
- Incident-reporting path if something goes wrong. Know this before you need it.

## One-page takeaway card

Close with a printed one-pager:

```
┌────────────────────────────────────────────────────┐
│  Copilot — Three Rules                             │
│  1. Human review is non-negotiable.                │
│  2. Cite and verify every source it surfaces.      │
│  3. Classification is in your head, not the tool.  │
│                                                    │
│  Three signature use-cases                         │
│  • Teams meeting summaries                         │
│  • Outlook catch-up and draft                      │
│  • BizChat cross-app search                        │
│                                                    │
│  Three red lines                                   │
│  • Never ship a Copilot draft unread               │
│  • Never let it draft a tax position               │
│  • Never paste client-identifiable data without    │
│    explicit policy authorization                   │
└────────────────────────────────────────────────────┘
```

## Workshop facilitator notes

- Arrive 15 minutes early; test every demo live on the actual environment.
- Have a backup demo recorded in case the tenant hiccups.
- If a question is beyond your knowledge, say so and log it. Never guess at policy questions in front of a room.
- End on time.
