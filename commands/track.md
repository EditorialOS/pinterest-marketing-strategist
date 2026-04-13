---
description: Log pin performance, extract learnings, and feed them back into future batches. Every tracked batch makes the next /create smarter — better image-copy pairings, better boards, better timing. Track at 7 days for early signal and 30 days for full picture.
argument-hint: "Batch: editorial operations gap" or paste Pinterest analytics data
---

# /track

Log results. Learn from them. Next batch gets smarter.

Pinterest pins live for months. A pin that looks weak at 7 days may be strong at 60. The learning loop accounts for this with multiple tracking windows.

## Trigger

Use after pins have been live for 7+ days. Run again at 30 days for the full picture. Works with a batch name, individual pin data, or a Pinterest analytics export.

## Inputs

- **Batch name or pin topic** — which pins to track (required)
- **Results** — impressions, saves, clicks, close-ups per pin. Accepts any format: Pinterest analytics CSV, manual entry, summary numbers, even partial data ("Pin 1 got 200 saves, the rest got about 30 each")
- **Notes** — optional. "Pin 3 got repinned by a content strategist," "The diagram pin got high saves but low clicks."
- **Time period** — optional. Default: since posted. Can specify: "7-day check" or "30-day review."

Don't block on perfect data. Partial data is still useful.

---

## Step 1 — Gather Results

Accept Pinterest analytics in any format:
- Pinterest analytics export (CSV or pasted)
- Manual entry per pin (impressions, saves, clicks, close-ups, outbound clicks)
- Summary numbers for the batch
- Partial: "Pin 1 did great, the rest were average"

**Key Pinterest metrics:**
- **Impressions** — times the pin appeared in feeds and search
- **Saves** — users saving to their boards (strongest signal — compounds over time)
- **Pin clicks / close-ups** — users tapping to see the pin larger
- **Outbound clicks** — users clicking through to the destination URL (the traffic metric)
- **Engagement rate** — (saves + clicks) / impressions

---

## Step 2 — Compare to Prediction

Pull the prediction from the batch record saved during /create.

- **Within 15%**: accurate prediction. Note what held.
- **Over 15% above**: outperformed. Identify what was different.
- **Over 15% below**: underperformed. Identify what was different.

If no prediction existed (first batch): this establishes the baseline.

**Pinterest timing caveat:** If tracking at 7 days, note: "Pinterest's algorithm distributes pins slowly. A 7-day read may understate long-term performance. Run /track again at 30 days for the full picture."

---

## Step 3 — Analyze What Worked

Break down by every variable the system controls:

### Image-Copy Pairing (the new intelligence layer)

This is what makes the learning loop compound. Analyze which image-copy combinations drove results:

- Did vertical images outperform horizontal? By how much?
- Did lifestyle images paired with problem-solution titles drive more saves than product shots with the same title pattern?
- Did diagram/infographic images drive more close-ups (users zooming in)?
- Did any image get reused from a prior batch? If so, did performance degrade? (Pinterest deprioritizes duplicate images)
- Which specific image drove the highest save rate? What was the copy paired with it?

**Be specific:** Not "lifestyle images did well" but "Vertical lifestyle image (content-workflow-team.jpg) paired with a problem-solution title on the Content Operations board: 4.2% save rate. Same board's average with product shots: 1.1%. Lifestyle + problem-solution = 3.8x product shots on this board."

### Title Effectiveness

- Did certain title patterns (numbers, questions, how-to, specific vs. generic) drive more impressions or clicks?
- Did front-loaded keywords deliver higher search impressions than clever-first titles?
- Which title got the most outbound clicks? What was distinctive about it?

### Board Performance

- Which boards drove the most impressions?
- Any boards where pins consistently underperform?
- Board-to-board comparison: same pin type on different boards — any clear winners?

### Search Term Alignment

- Did pins appear for the target search terms? (If analytics shows search data)
- Any unexpected search terms surfacing? These are opportunities for new pin concepts.

### Timing

- Did posting time/day correlate with first-24hr performance?
- Note: timing matters less on Pinterest than other platforms — the algorithm distributes over days. Don't over-optimize here.

### Destination URL

- Did certain landing pages convert better than others?
- Did pins without URLs get lower engagement (no action to take)?

---

## Step 4 — Extract Learnings

Generate 3-5 specific, reusable learnings per batch. The bar is: each learning must be specific enough to change a decision in the next /create run.

**Good learnings:**
- "Vertical lifestyle images + problem-solution titles on Content Operations board = 4.2% save rate (3.8x product shots). Sample: 8 pins across 2 batches."
- "Titles with numbers ('3 Workflow Fixes...') = 2.1x more outbound clicks than titles without. Sample: 12 pins."
- "Diagram/checklist images get 65% more close-ups than lifestyle images, but 40% fewer saves. Use diagrams for traffic-goal pins, lifestyle for save-goal pins."
- "Sunday 9am posting = highest first-24hr impressions for SaaS content (3 batches consistent)."

**Bad learnings:**
- "Lifestyle images work better" (no metric, no comparison, no sample size)
- "Post on weekends" (no specificity)
- "Some boards perform better" (useless without naming which and why)

---

## Step 5 — Assess Image Library Health

After analyzing results, evaluate the image library:

- **Images that drove results** — flag as "proven performers." These images (or similar ones) should inform future image sourcing.
- **Image types missing** — did any pin concept struggle because no good image existed? Log what's needed: "Need more vertical team/workplace images for content operations pins."
- **Image freshness** — if the library hasn't been updated in 60+ days, flag: "Image library is getting stale. Pinterest rewards visual freshness. Add new images."
- **Orientation gap** — if most pins used horizontal images (because that's all that was available), flag: "Most pins used horizontal images. Add vertical (2:3 ratio) photos — they get 60% more engagement."

---

## Step 6 — Save Learnings to Drive

Write to three files in ~~docs. All plain markdown, human-readable, human-editable.

**pin-log.md** — append this batch's record:
```
## Batch: [topic] — [Date posted] — [Tracking period]
Pins: [N]
Boards: [list]
Goal: [traffic/awareness/saves/sales]
Images used: [filenames + sources (Cloudinary/Drive)]
Top performer: Pin [N] — "[title]" — [image filename] — [save rate, CTR]
Bottom performer: Pin [N] — "[title]" — [image filename] — [save rate, CTR]
Image-copy insight: [1-line summary of best pairing]
Key learning: [1-line summary]
Tracking period: [7-day / 30-day / lifetime]
```

**pin-learnings.md** — append new learnings organized by category:
- Image-copy pairing effectiveness
- Image type effectiveness (vertical vs. horizontal, lifestyle vs. product vs. diagram)
- Title pattern performance
- Board effectiveness
- Timing patterns
- Search term performance
- Destination URL conversion
- Image library gaps

**pin-baselines.md** — update current baselines:
- Overall averages (save rate, CTR, engagement rate)
- Per-board baselines
- Per-image-type baselines
- Per-image-copy-combination baselines (the compound intelligence layer)
- Best/worst performing pin concepts
- Best posting windows
- Image library health score
- Pin count (determines confidence level)

---

## Output Format

```
PINTEREST MARKETING STRATEGIST — PIN PERFORMANCE

Batch: [Topic]
Posted: [Date range]
Tracking period: [7 days / 30 days / lifetime]
Pins tracked: [N]

---

RESULTS

| Pin | Title | Image | Impressions | Saves | Clicks | Save Rate | CTR |
|-----|-------|-------|:-----------:|:-----:|:------:|:---------:|:---:|
[Row per pin — including which image was used]

Batch averages:
  Save rate: [X%] [vs. predicted — ✅ accurate / ⬆ outperformed / ⬇ underperformed]
  CTR: [X%] [vs. predicted]
  Engagement rate: [X%]

---

TOP PERFORMER

Pin [N]: "[title]"
Image: [filename] ([orientation], [category])
Why it worked: [specific analysis — image-copy pairing, title pattern, board, timing]

UNDERPERFORMER

Pin [N]: "[title]"
Image: [filename] ([orientation], [category])
Why it lagged: [specific analysis]

---

IMAGE-COPY PAIRINGS

| Image Type | Title Pattern | Board | Save Rate | CTR | Sample |
|-----------|---------------|-------|:---------:|:---:|:------:|
[Best-performing combinations first]

Best pairing: [image type] + [title pattern] on [board] = [metric]
Worst pairing: [image type] + [title pattern] on [board] = [metric]

---

WHAT WORKED

✅ [Specific finding with metric]
✅ [Specific finding with metric]

WHAT DIDN'T

⬇ [Specific finding with metric]

---

BOARD HEALTH

| Board | Pins (all time) | Avg Save Rate | Avg CTR | Trend |
|-------|:---:|:---:|:---:|:---:|
[Per-board metrics]

---

IMAGE LIBRARY HEALTH

Total images: [N]
Used in tracked pins: [N]
Proven performers: [list top 3 images by save rate]
Needed: [image types or subjects missing for upcoming topics]
Freshness: [last updated / stale warning if 60+ days]

---

LEARNINGS RECORDED

→ "[Learning 1 — specific, metric, comparison, sample size]"
→ "[Learning 2]"
→ "[Learning 3]"

Saved to: [location in ~~docs]

---

PREDICTION ACCURACY

This batch: predicted [X%] → actual [X%] = [variance]
Overall accuracy: [avg variance across N batches]
Confidence for next batch: [Baseline / Low / Medium / High / Very High] ([N] tracked)

---

NEXT BATCH RECOMMENDATIONS

Based on what this batch taught:
→ Image: [use more/fewer of specific image type]
→ Copy: [title pattern to lean into or avoid]
→ Board: [which board to prioritize]
→ Timing: [any posting time signals]
→ Library: [what images to add for better matching]

Run /create and these learnings apply automatically.

---

QUALITY GATES
✓ Results compared to prediction with variance
✓ Learnings are specific (metric + context + comparison + sample size)
✓ Per-pin and per-board breakdown included
✓ Image-copy pairing effectiveness assessed
✓ Image type effectiveness tracked (orientation, category)
✓ Image library health evaluated
✓ Pin performance memory updated in Drive
✓ Pin count incremented ([N] total tracked)
✓ Confidence level updated
✓ Next /create will reference these learnings
✓ Long-lifespan caveat noted if tracking < 30 days
```
