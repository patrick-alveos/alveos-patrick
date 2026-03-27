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

## Step 2 — Broad research (target 50–100 signals)

Use web search extensively across the following angles. Run **multiple targeted searches** to build a wide pool of signals before filtering.

### Search angles to cover:
- **Product launches & announcements**: new wearables, health trackers, smart rings, patches, hearables, smart clothing announced or released within the time window
- **Funding & M&A**: funding rounds, acquisitions, partnerships in the wearable/digital health space
- **Regulatory**: FDA clearances, CE markings, SaMD approvals for wearable health devices
- **Research & clinical**: academic papers, clinical trials, university research on wearable sensing, respiratory monitoring, HRV, sleep, autonomic nervous system, breathing biomarkers
- **Consumer trends**: press coverage of wearable adoption, user behaviour, market reports
- **Breathing & respiratory specifically**: any new product, study, or company working on respiratory rate, breathing patterns, nasal/oral airflow, sleep disordered breathing, or respiratory biometrics
- **Larger players**: Apple Watch, Garmin, Fitbit/Google, Samsung Galaxy, Oura, Whoop, Ultrahuman, Polar, Suunto, Withings — any notable updates
- **Smaller/emerging players**: startups, Kickstarter/Indiegogo campaigns, university spinouts in the wearable health space

### Search query ideas (adapt as needed):
- `wearable health tracker launch [year]`
- `wearable startup funding [month] [year]`
- `respiratory rate wearable`
- `breathing wearable device`
- `FDA clearance wearable [timeframe]`
- `smart ring new release`
- `HRV wearable research`
- `autonomic nervous system wearable`
- `sleep wearable clinical study`
- `acoustic sensor wearable`
- `digital biomarker wearable startup`

Aim for breadth. Run at least 10–15 distinct searches. Collect all findings before filtering.

---

## Step 3 — Filter to top 5–10 signals

From your pool of 50–100 items, select the **5–10 most impactful** for Alveos. Prioritise:

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

## All Sources

| # | Title | URL | Date |
|---|-------|-----|------|
| 1 | ... | ... | ... |
[Full list of all sources consulted, including ones not in the top 10]
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
