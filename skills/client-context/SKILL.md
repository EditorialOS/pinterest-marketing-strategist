---
name: client-context
description: "Reads the client's Google Drive folder and image library to build structured Pinterest context. Extracts brand voice, audience, boards, image inventory with orientation analysis, and pin performance history. Called automatically at the start of every command."
---

# Client Context — Pinterest Intelligence Layer

## Purpose

Read the client's real documents and images to build the context layer that makes every composed pin client-specific. Pinterest is a visual search engine — context here means images and search terms as much as voice and audience. The image library inventory is the foundation of composed pin output.

## Core Principle

This skill exists so that /create produces pins from real brand assets, not generic templates. Without context, pins are generic. Without images, pins are incomplete. Without learnings, pins don't improve. This skill loads all three.

## When This Activates

Every /create and /track command starts here. Load context silently — show a one-line status header and move to the command's work. Don't narrate the loading process.

## Priority Documents

Read the ~~docs folder. Look for these in priority order:

| Priority | Document Type | What to Extract | If Missing |
|:--------:|--------------|-----------------|------------|
| 1 | Image library | Available images — from ~~images (Cloudinary) or ~~docs images/ folder. Filenames, dimensions, orientation, categories, tags, visual descriptions. This is the most critical asset. | Cannot produce composed pins. Flag: "No images found. Add brand images to create composed pins." |
| 2 | Brand guide / style guide | Visual identity, voice for descriptions, vocabulary rules, banned words | Ask for brand name and 2-3 adjectives |
| 3 | Product / service catalog | Names, descriptions, prices, destination URLs, categories | Ask what they sell and where it links |
| 4 | Audience personas | Demographics, interests, Pinterest search behavior, planning patterns | Ask who the target Pinterest user is |
| 5 | Board structure | Board names, descriptions, themes, goals | Recommend boards based on brand vertical |
| 6 | Pin learning files | pin-log.md, pin-learnings.md, pin-baselines.md from /track | First batch — no learning history |
| 7 | Pinterest config | pinterest-config.md from /setup | Run /setup first or proceed with defaults |
| 8 | Content strategy | Goals, pillars, seasonal calendar, pin queue | Ask for primary goal |

## Image Library Scanning

This is the most critical context step for composed pin production.

### Source Priority

1. **~~images (Cloudinary)** — if connected, this is the primary image source. Advantages: automatic orientation data, metadata tags, transformation URLs for Pinterest sizing, CDN delivery.

2. **~~docs images/ folder** — if Cloudinary is not connected, scan the Drive images folder. Less metadata available but functional.

3. **Both** — if both exist, Cloudinary is primary (better metadata and transforms), Drive is supplemental.

### Image Inventory Protocol

For each image in the library, capture:

| Dimension | What to Capture | Why It Matters |
|-----------|----------------|----------------|
| Filename / Asset ID | Exact reference for pin output | Required for composed pin attribution |
| Dimensions (px) | Width × height | Determines orientation and Pinterest suitability |
| Orientation | Vertical (2:3), square (1:1), horizontal (3:2) | Vertical gets 60% more engagement on Pinterest |
| Aspect ratio | Exact ratio | Determines if smart crop is needed for 2:3 |
| Category | Product, lifestyle, team, diagram, quote card, seasonal, behind-scenes | Matches pin concept type |
| Tags / metadata | Cloudinary tags or Drive folder conventions | Enables topic-based search during /create |
| Visual description | What's in the image — subject, setting, mood | Enables concept-to-image matching |
| Quality signals | Resolution adequate? Well-lit? Clear subject? | Low-quality images hurt pin performance |
| Reuse status | Used in last 10 pins? (from pin-log.md) | Pinterest deprioritizes duplicate images |
| Transform URL | Cloudinary URL with Pinterest sizing applied | Ready-to-use for composed pin output |

### Orientation Classification

| Orientation | Aspect Ratio | Pinterest Performance | Action |
|-------------|:---:|:---:|--------|
| Vertical | 2:3 or taller | Optimal — 60% more engagement | Use as-is or crop to exactly 1000×1500 |
| Square | 1:1 | Acceptable — less feed space | Can use, or crop to vertical with smart crop |
| Horizontal | 3:2 or wider | Worst performer | Smart crop to vertical if possible, flag if not |

### Image Health Assessment

After scanning, assess the library:

| Condition | Status | Recommendation |
|-----------|--------|----------------|
| 20+ vertical images | 🟢 Healthy | Sufficient for sustained batches |
| 10-19 vertical images | 🟡 Thin | Will run low within 2-4 weeks of regular posting |
| 1-9 vertical images | 🟠 Critical | Add more vertical images before regular production |
| 0 images | 🔴 Empty | Cannot produce composed pins. Blocker. |
| All horizontal | ⚠️ Misfit | Pinterest penalizes horizontal. Add vertical shots. |
| No new images in 60+ days | ⚠️ Stale | Pinterest rewards visual freshness. Add new photos. |
| Fewer images than batch size | ⚠️ Insufficient | Reduce batch size or add images |

### Category Distribution

Track the mix of image types:

| Category | Ideal For | Count | Status |
|----------|-----------|:-----:|--------|
| Product shots | Product spotlight pins, sales goal | | |
| Lifestyle | Aspirational pins, save goal | | |
| Team / workspace | Behind-scenes, brand building | | |
| Diagrams / infographics | Educational, how-to pins | | |
| Quote cards / text overlay | Thought leadership | | |
| Seasonal | Timely, event-driven pins | | |

If any category has zero images but the pin queue includes topics that need that category, flag: "Pin queue includes [topic] but no [category] images exist. Add [specific suggestion] before creating pins for that topic."

## Brand Voice (Adapted for Pinterest)

Pinterest copy is shorter and more search-oriented than email or blog. Extract voice differently:

| Dimension | Where to Find It | Pinterest Adaptation |
|-----------|------------------|---------------------|
| Core visual identity | Brand guide | Informs image selection preferences and text overlay decisions |
| Description voice | Brand guide tone | Same voice, fewer words. Pinterest descriptions are 150-300 chars. |
| Vocabulary — use | Word list from guide | Prioritize search-relevant terms from the list |
| Vocabulary — avoid | Banned words from guide | Apply same restrictions in titles and descriptions |
| CTA style | Brand guide or past pins | Pinterest CTAs are soft — "Tap to explore" not "BUY NOW" |

**Critical Pinterest voice rule:** Descriptions serve search first, personality second. Front-load keywords. Save the brand character for the title. A SaaS brand's description: "Content workflow automation for stretched marketing teams. Reduce approval cycles by 60% with editorial infrastructure." Not: "We believe content should be joyful!"

## Audience Segments (Pinterest-Specific)

Pinterest users behave differently from other channels:

| Dimension | What to Extract |
|-----------|----------------|
| Pinterest demographics | 60% female (male growing fastest), median age 25-44, high-income skew |
| Search behavior | What terms does this audience type into Pinterest? |
| Planning stage | Planning ahead (saves) or ready to act (clicks)? |
| Save vs. click profile | Some audiences build boards. Some click through. Which is this? |
| Device | 85% mobile. All pins must look good at mobile dimensions. |

### Intelligence Levels

| Data Available | Intelligence Level |
|:---|:---|
| Personas only | Basic — demographics, interests, likely search terms |
| Personas + pin history | Moderate — knows which topics and image types engaged |
| Personas + history + learnings | Deep — knows save rate by image-copy combo, CTR by board |
| All above + analytics | Full — real data per variable |

## Board Structure

For each configured board:
- **Name** and description (descriptions should include keywords for Pinterest SEO)
- **Theme** — what content belongs here
- **Goal** — traffic, saves, awareness, sales
- **Pin count** — from pin-log.md
- **Board health** — getting fresh pins? Growing?
- **Best image-copy combo** — from learning files (if tracked)

**Board strategy rules:**
- Minimum 4 boards for serious presence
- Each board needs 15-25 pins to look established
- Board descriptions must include search keywords
- Seasonal boards can be archived post-season but pins stay discoverable

## Performance Baselines

| Source | What to Read |
|--------|-------------|
| pin-baselines.md | Overall averages, per-board, per-image-type, per-combo baselines |
| pin-learnings.md | Cumulative learnings by category |
| pin-log.md | Last 20-30 pins with images used, boards, metrics |

### Confidence Scale

| Tracked Pins | Confidence | What the System Knows |
|:---:|:---:|---|
| 0 | Baseline | Pinterest vertical benchmarks only |
| 1-10 | Low | Directional. "Lifestyle images seem to save better." |
| 11-30 | Medium | Board-level patterns. Image type preferences. Title effects. |
| 31-75 | High | Multi-variable patterns. Image-copy combo predictions. |
| 76+ | Very High | Full predictive capability. Specific combinations optimized. |

## Connector Awareness

| Connector | If Available | If Unavailable |
|-----------|-------------|----------------|
| ~~docs | Read all documents. Write learning files back. Full context. | Ask user to describe brand and paste info. No persistent learning. |
| ~~images | Scan Cloudinary for image library. Get metadata, transforms, CDN URLs. Composed pins with ready-to-use images. | Fall back to ~~docs images/ folder. Less metadata, no transforms. |
| ~~pinterest | Post pins via API. Pull analytics for /track. | User posts manually. Pastes analytics for /track. |
| ~~calendar | Seasonal timing recommendations. | Use general seasonal knowledge. |

### Degradation Behavior

| Level | Connected | Capability |
|:---:|---|---|
| Full | ~~docs + ~~images + ~~pinterest | Complete: context + composed images + auto-post + auto-track |
| Composed | ~~docs + ~~images | Strong: context + composed images. User posts manually. |
| Docs only | ~~docs (with images/) | Good: context + image matching from Drive. No transforms. |
| Manual | Nothing | Functional but limited: user describes brand, provides images. No learning persistence. |

## Status Header

Display one line at the start of every command:

- 🟢 `Config: Connected — [brand] — [N] images ([N] vertical) — [N] boards — [confidence level]`
- 🟡 `Config: Partial — [what's found] — missing [what's not] — [image library status]`
- ⚪ `Config: Manual — provide brand context and images`

## Cross-Plugin Compatibility

Same Drive folder serves Editorial OS, Email Marketing Strategist, and Pinterest Marketing Strategist. Shared: brand guide, audience personas, content strategy. Pinterest-specific: image library (shared with Composer), pin-log.md, pin-learnings.md, pin-baselines.md.

## Teammate Protocol Compatibility

This skill works in both modes:

**Plugin mode (Cowork):** Reads from ~~docs and ~~images. User triggers /create and /track manually.

**Teammate mode (Autonomous):** Reads from workspace Drive folder. Cron triggers create and track per standing orders. Same skill, different trigger. Same learning files, same image library.

```
Standing orders example:
- Task: Create composed pin batch
  Day: Monday, Wednesday, Friday
  Skill: pin-strategist + client-context
  Image source: Cloudinary folder "editorial-os/pinterest"
- Task: Track pin performance
  Day: Monday
  Skill: performance-learning
```
