---
description: Produce composed Pinterest pins — copy, matched image, board, keywords, posting schedule — ready to review and post. Reads your brand context and image library from Google Drive. Every batch is informed by learnings from prior /track runs.
argument-hint: "Topic: editorial operations gap" or "Next from queue" or "Seasonal: summer content planning"
---

# /create

One command. Composed pins out. Review, approve, post.

This is a production workflow, not a brainstorming tool. The output is a batch of pins where every element — title, description, image, board, keywords, posting time — is selected and matched. The human reviews the composed batch and decides what ships. Everything else is handled.

## Trigger

Use when the user wants Pinterest pins created. Works with a specific topic, "next from queue," a product to promote, content to repurpose, or "this week's pins." Minimum input: a topic or "next."

## Inputs

- **Topic or "next"** — what the pins are about. "Next" picks the first unposted topic from the pin queue in ~~docs. (Required)
- **Batch size** — optional. Default: 5 pins. Max recommended: 10.
- **Boards** — optional. Default: uses configured boards from /setup.
- **Goal override** — optional. Default: uses goal from /setup.
- **Seasonal hook** — optional. "Memorial Day," "back to school," "Q4 planning season."

---

## Step 1 — Load Context

Use client-context skill. Show one-line status header.

🟢 Configured: load brand guide, audience, boards, pin history, learnings, image library inventory, and destination URLs from ~~docs.
🟡 Partial: load what exists, flag what's missing.
⚪ No client: ask for brand name, audience, boards, image source. State output will be directional.

**Hard requirements before proceeding:**
- Image library must have at least 1 usable image. If zero images exist anywhere (~~images or ~~docs images/), stop and tell the user: "No images found. Pinterest is a visual platform — add approved brand images to your Drive images/ folder or connect Cloudinary, then re-run."
- If no destination URLs are configured, flag it but proceed: "No destination URLs configured. Pins will drive awareness but not trackable traffic. Add landing pages and re-run /setup to enable traffic goals."

---

## Step 2 — Check Pin History

Read pin-log.md from ~~docs (written by prior /track runs).

- What topics were covered in the last 14 days? Avoid exact repeats.
- What images were used in the last 10 pins? Don't reuse the same image.
- What angles performed best? Lean toward proven patterns.
- What angles underperformed? Note and avoid unless the underperformance had an identifiable cause (e.g., horizontal image, not the angle itself).
- Which boards are overdue for fresh pins? Prioritize underserved boards.

If no history exists (first batch): skip. All boards, angles, and images are available.

---

## Step 3 — Scan Image Library

This step makes composed pins possible. Without it, the output is concepts. With it, the output is product.

**If ~~images (Cloudinary) is connected:**
1. Search the configured folder/tags for images related to the batch topic
2. For each candidate image, capture: filename/asset ID, dimensions, orientation, tags/metadata, visual description
3. Sort by relevance to the batch topic
4. Flag orientation: vertical (2:3) = optimal, square = acceptable, horizontal = will underperform
5. Check reuse against pin-log.md — skip any image used in last 10 pins

**If using ~~docs images/ folder:**
1. List all images in the folder and subfolders
2. For each image, capture: filename, path, orientation (from dimensions if available, else note "orientation unknown")
3. Categorize by subfolder or filename convention (product/, lifestyle/, seasonal/)
4. Check reuse against pin-log.md

**Image inventory output (internal, not shown to user):**
```
Available for this batch: [N] images
Vertical (optimal): [N]
Square (acceptable): [N]
Horizontal (will underperform): [N]
Previously used (skip): [N]
Fresh and relevant: [N]
```

If fewer than [batch size] relevant images are available, reduce batch size or flag: "Only [N] fresh images match this topic. Creating [N] pins instead of [batch size]. Add more images for full batches."

---

## Step 4 — Generate Pin Concepts

For each pin in the batch, determine:

- **Pin angle** — the specific hook. Not "editorial operations" but "The real reason your content feels chaotic (it's an operations gap)." Each pin in the batch needs a distinct angle.
- **Target search terms** — 2-3 Pinterest search queries this pin should appear for. Pinterest is a search engine. 96% of top searches are unbranded.
- **Intended action** — save (planning), click (ready to act), or close-up (curious). Informs CTA choice.

### Concept Quality Test

Every pin concept must pass:
1. **Not a repeat** — different angle from any pin in the last 14 days
2. **Search-aligned** — maps to real Pinterest search queries
3. **Board-appropriate** — fits the assigned board's theme
4. **Image-matchable** — a relevant image exists in the library for this concept

If a concept fails any test, replace it. Don't ship weak pins to hit a batch quota.

---

## Step 5 — Match Images to Concepts

This is the step that turns concepts into composed pins.

For each pin concept, select the best image from the library:

### Matching Logic (in priority order)

1. **Topic relevance** — the image content must relate to the pin's subject. A pin about "content workflows" should not show a product headshot unless the product IS a workflow tool.

2. **Orientation** — Pinterest heavily favors vertical (2:3). Selection priority:
   - Vertical (1000×1500 or similar 2:3) → optimal. Use as-is.
   - Square (1000×1000) → acceptable. Will display smaller in feed.
   - Horizontal (1500×1000) → worst performer. Use only if no vertical/square alternative exists. Flag: "Horizontal image — expect lower engagement."

3. **Freshness** — not used in the last 10 pins (from pin-log.md).

4. **Category fit** — lifestyle images for aspirational pins, product shots for product pins, diagrams for educational pins, quote cards for thought leadership.

5. **Visual quality** — well-lit, clear subject, high contrast. Dark, blurry, or cluttered images should be deprioritized.

### Image Sizing for Pinterest

Pinterest optimal dimensions:
- **Standard pin:** 1000 × 1500 px (2:3 ratio)
- **Long pin:** 1000 × 2100 px (for infographics, step-by-step)
- **Square pin:** 1000 × 1000 px (acceptable but less feed real estate)
- **Minimum width:** 600 px (below this, image appears low quality)

If ~~images (Cloudinary) is connected, request the image transformed to Pinterest optimal dimensions:
- Crop/resize to 1000 × 1500 (2:3) using smart crop (subject-aware)
- If the source image is horizontal, apply smart crop to extract the best vertical portion
- Output the Cloudinary URL with transformation parameters applied

If using Drive images, note the recommended crop in the output so the user can resize before posting.

### When No Image Matches

Write the full pin concept (title, description, board, keywords) and provide specific image direction:
```
IMAGE NEEDED
Subject: [what the image should show]
Orientation: vertical (1000×1500)
Mood: [bright/moody/minimal/editorial]
Category: [lifestyle/product/diagram/quote card]
```

This is a fallback, not the normal mode. If more than 2 pins in a batch require "IMAGE NEEDED," the image library is too thin for this topic. Flag it.

---

## Step 6 — Write Pin Copy

For each pin, write copy matched to the selected image:

### Title
- **Under 100 characters** — Pinterest truncates at 100
- **Front-load the keyword** — first 3-4 words determine search ranking
- **Specific over clever** — "3 Content Workflow Fixes for Small Teams" beats "Content Made Easy"
- **Match the image** — if the image shows a checklist, the title should reference a list or steps. Title and image should tell the same story.

### Description
- **150-300 characters** optimal (Pinterest allows 500 but truncates in feed)
- **First sentence is the hook** — must work in the truncated preview
- **2-3 keyword phrases woven naturally** — not stuffed, but present
- **CTA at the end:**
  - Traffic goal → "Tap to read the full guide"
  - Save goal → "Save this for your next planning cycle"
  - Sales goal → "Get started — link in pin"
- **No hashtags** unless brand guide specifically uses them

### Alt Text
- **Describe the image** for accessibility — what's visually in the image
- **Under 500 characters**
- **Include one keyword naturally**

### Link
- Destination URL from configured URLs (from /setup)
- If no URL exists for this topic: "No destination URL — pin drives awareness only. Add a landing page to capture traffic."

---

## Step 7 — Assign to Boards

Place each pin on the most relevant board:

1. **Topic match** — pin content matches board theme
2. **Board balance** — distribute across boards. If one board received 5+ of the last 10 pins, prioritize others.
3. **Board maturity** — boards with fewer than 15 pins should be prioritized to build them up
4. **Multi-board limit** — 1-2 boards maximum per pin. More than 2 triggers Pinterest spam signals.

---

## Step 8 — Recommend Posting Schedule

**Pinterest cadence rules:**
- Optimal: 3-5 pins per day for growth
- Minimum: 1 pin per day for consistency
- Spacing: 2-4 hours between pins on the same board

Schedule each pin:
```
Pin [N]: [Day], [Time] → [Board]
```

Use ~~calendar data if connected. Otherwise: weekday evenings (8-11pm) and weekend mornings (8-11am) for most verticals.

---

## Step 9 — Performance Prediction

Use performance-learning skill.

**If tracked history exists:**
- Predict save rate and CTR per pin based on similar past pins (same image type × title pattern × board)
- State confidence level
- Note which pins are most likely to outperform

**If no history (first batch):**
- Use Pinterest vertical benchmarks. State they're benchmarks.
- "After you run /track on this batch, the next prediction uses your real data."

---

## Step 10 — Save Record and Present Composed Batch

Save the full batch to ~~docs as a pin record for /track reference.

**Do NOT auto-post.** Present the composed batch for review:

---

## Output Format

```
PINTEREST MARKETING STRATEGIST — COMPOSED PIN BATCH
[Config status header]
Generated: [Date]

---

BATCH: [Topic/theme]
PINS: [N] composed
BOARDS: [boards served]
GOAL: [traffic / awareness / saves / sales]
IMAGES: [N] matched from library, [N] need manual sourcing

---

PIN 1 of [N]

COPY
  Title: [title] ([char count])
  Description: [description] ([char count])
  Alt text: [alt text]
  Link: [destination URL or "No URL — awareness only"]
  Search terms: [2-3 target queries]

IMAGE
  Source: [Cloudinary URL with transforms / Drive path]
  Original: [filename]
  Dimensions: [output dimensions, e.g., 1000×1500]
  Orientation: [vertical ✓ / square ○ / horizontal ⚠]
  Match reason: [why this image fits this concept]

PLACEMENT
  Board: [primary] / [secondary or "single board"]
  Post time: [recommended day + time]

---

PIN 2 of [N]
[same format]

[Repeat for all pins]

---

POSTING SCHEDULE

| Day | Time | Pin | Board | Image |
|-----|------|-----|-------|-------|
[Full schedule with image references]

---

PERFORMANCE PREDICTION

Batch predicted save rate: [X%] ([confidence level])
Batch predicted CTR: [X%] ([confidence level])
Strongest pin: Pin [N] — [reason]
Based on: [N tracked pins or "Pinterest benchmarks — first batch"]

---

PIN RECORD

Saved to: [location in ~~docs]
Images used: [filenames — logged for reuse prevention]

Run /track after 7+ days to log results.
Every tracked batch makes the next one smarter.

---

QUALITY GATES
✓ Brand voice applied from [source]
✓ All titles under 100 characters
✓ All descriptions front-load keywords
✓ Images matched from approved library — [N/N] pins have composed images
✓ All matched images are vertical or square (horizontal flagged if any)
✓ No image reused from last 10 pins
✓ Boards balanced — no single board overloaded
✓ Each pin targets distinct search terms
✓ No concept repeats from last 14 days
✓ Destination URLs assigned (or explicitly flagged as missing)
✓ Posting schedule spaced properly (2-4hr gaps per board)
✓ Performance prediction stated with honest confidence
✓ Batch record saved for /track
```
