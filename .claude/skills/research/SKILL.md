---
name: research
description: Researches the wearable market for recent news, product launches, and competitor activity. Use when the user invokes /research, optionally with a time window like "/research 14 days". Outputs a dated markdown report saved to the Competitor_agent/ folder and displays a summary in the conversation.
---

# /research — Wearable Market Intelligence

## How to invoke
- `/research` → defaults to a 7-day lookback window
- `/research 14 days` → uses a 14-day window
- `/research 30 days` → uses a 30-day window

Parse the time window from the user's arguments. If no window is specified, default to **7 days**.

---

## Step 1 — Read Alveos context

Before researching, read the file at `alveos/CLAUDE.md` (or `CLAUDE.md` if already inside the alveos project root). Use it to understand:
- What Alveos builds and who they are
- Which biomarkers and product categories are relevant
- What kind of signals would matter to a breathing/respiratory wearable startup

This context will inform which of the research findings are most relevant to surface.

---

## Step 2 — Research (6–8 targeted searches)

Run **6–8 web searches** directly (do NOT spawn sub-agents — keep everything in a single context to conserve tokens). Each search should cover a distinct angle.

### Required searches (run these 6):
1. `wearable health news [month] [year]` — product launches, major player updates
2. `wearable startup funding [month] [year]` — funding rounds, M&A, partnerships
3. `respiratory rate breathing wearable [year]` — breathing/respiratory devices and research
4. `FDA clearance wearable health device [year]` — regulatory developments
5. `Oura Whoop Ultrahuman news [month] [year]` — direct competitor updates
6. `acoustic sensor health wearable [year]` — acoustic sensing tech (most relevant to Alveos)

### Optional searches (add 1–2 if the above missed key angles):
7. `smart ring new release [year]`
8. `sleep wearable clinical study [year]`

Collect findings from all searches before filtering. Target 20–30 raw signals.

---

## Step 3 — Filter to top 5–10 signals

From your pool of 20–30 items, select the **5–8 most impactful** for Alveos. Prioritise:

1. **Directly competitive**: any device doing respiratory, breathing, or acoustic sensing
2. **Category-defining**: moves by major players that set market expectations (features, pricing, UX)
3. **Strategic signals**: funding that validates or challenges Alveos's category; regulatory precedents
4. **Scientific validation**: research that supports or complicates Alveos's biomarker claims (RRV, NSI, oral/nasal ratio)
5. **Distribution or partnership moves**: anything that changes how wearables reach consumers

Discard: generic fitness tracker updates, unrelated medical devices, duplicate coverage of the same story.

---

## Step 4 — Derive 1–3 key takeaways for Alveos

Based on the filtered signals, write **1–3 actionable takeaways** framed from Alveos's perspective. These should be concrete — something the team could discuss or act on. Examples of the right level:
- "Oura's new respiratory rate feature validates the category but positions us to differentiate on continuous oral/nasal detection"
- "Two funded startups are entering sleep-breathing; Alveos should accelerate clinical validation to establish credibility first"
- "FDA cleared X for respiratory monitoring — worth reviewing their approach for CE strategy"

---

## Step 5 — Format the output

Structure the output exactly as follows:

```
# Wearable Market Research — [DATE]
**Period covered:** Last [N] days

---

## Key Industry Updates

- **[Company / Topic]** — [1–2 sentence summary of what happened and why it matters]
  _Source: [title](url)_

- **[Company / Topic]** — ...
  _Source: [title](url)_

[5–10 bullet points total]

---

## Key Takeaways for Alveos

1. [Takeaway / action to consider]
2. [Takeaway / action to consider]
3. [Takeaway / action to consider — optional]

---

## Sources

[List only the sources cited in Key Industry Updates above — no need to list every search result]
```

---

## Step 6 — Save and display

1. **Save** the formatted output as a markdown file to:
   `Competitor_agent/YYYY-MM-DD_research.md`
   (use today's actual date in the filename)

2. **Display** the full output in the conversation.

---

## Important constraints

- Never fabricate sources. Only cite URLs that were actually returned by search.
- If a search returns no results for a specific angle, note it briefly and move on.
- Do not make medical or diagnostic claims about any company's products, including Alveos's.
- Keep the final summary tight. The user is a busy CEO — every bullet should earn its place.
