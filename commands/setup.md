---
description: Configure your brand, boards, image library, and Pinterest goals. Run once to set up, re-run anytime to update. Everything saves to your Google Drive folder.
argument-hint: "Brand: Editorial OS" or "Update boards" or "Add image library"
---

# /setup

Configure once. Every /create and /track reads this.

## Trigger

Run when starting fresh, adding a new brand, changing boards, updating the image library location, or shifting Pinterest goals. Safe to re-run — updates existing config without losing history.

## What Setup Captures

### 1 — Brand Identity

- **Brand name** — as it should appear in pin descriptions
- **What you sell or promote** — products, services, content, SaaS, destinations
- **Brand voice** — adjectives, vocabulary rules, tone. If a brand guide exists in ~~docs, extract from there.
- **Visual style** — clean/bold/editorial/minimal/colorful. Informs image selection and text overlay choices.
- **Off-limits** — words, tones, or visual styles to avoid ("never say 'hustle'", "no stock photo aesthetic")

### 2 — Target Audience

- **Who finds you on Pinterest** — demographics, interests, planning behavior
- **What they search for** — actual Pinterest search terms your audience uses
- **Planning stage** — are they dreaming (saves), deciding (clicks), or buying (conversions)?
- **Device** — 85% of Pinterest is mobile. All pin sizing assumes mobile-first.

### 3 — Board Structure

For each board:
- **Board name** — descriptive, keyword-rich (Pinterest indexes board names)
- **Board theme** — what content belongs here
- **Board goal** — traffic, saves, awareness, or sales
- **Board description** — 2-3 sentences with keywords (for Pinterest SEO)

Minimum recommended: 4 boards. Maximum recommended: 10 for active management.

### 4 — Image Library

This is the critical setup step that makes composed pins possible.

**Option A — Cloudinary (recommended)**
If ~~images is connected, provide:
- Cloudinary folder path containing approved brand images
- Any tag conventions used ("product", "lifestyle", "headshot", "seasonal")
- Whether text overlay is permitted on images

**Option B — Google Drive**
If images live in ~~docs:
- Folder path within Drive (e.g., `images/` or `brand-assets/pinterest/`)
- Any subfolder conventions (e.g., `images/products/`, `images/lifestyle/`)

**Option C — Both**
Cloudinary as primary library, Drive as supplemental. System checks both.

**Image library health check on setup:**
- Count total available images
- Flag orientation breakdown (how many vertical vs. horizontal vs. square)
- Flag if fewer than 20 images exist ("You'll run out of fresh images within 4 batches — plan to add more")
- Flag if zero vertical images exist ("Pinterest heavily favors vertical images — add 2:3 ratio photos")

### 5 — Pinterest Goals

- **Primary goal** — traffic, brand awareness, saves, or sales
- **Posting cadence** — how often (recommended: 3-5x/week for growth)
- **Content pillars** — 3-5 topic categories that organize your pin strategy
- **Seasonal priorities** — upcoming launches, events, or seasonal pushes
- **Destination URLs** — where pins link to (blog, landing pages, product pages, newsletter signup). Flag if none exist: "Pins without destination URLs drive awareness only — no trackable traffic."

### 6 — Pin Queue

Initial list of 8-12 topics to create pins about, in priority order. Each topic should be a theme, not just a subject:
- ❌ "Travel tips" (too generic)
- ✅ "The editorial operations gap — why marketing teams struggle without editorial infrastructure" (specific angle)

The queue is consumed by /create (picks the next unposted topic) and can be replenished anytime by re-running /setup or editing the queue in Drive.

---

## Output

Save configuration to ~~docs as `pinterest-config.md`. Display summary:

```
PINTEREST MARKETING STRATEGIST — SETUP COMPLETE

Brand: [name]
Voice: [2-3 key attributes]
Visual style: [style]
Audience: [summary]
Boards: [N] configured
Image library: [source] — [N] images available ([N] vertical, [N] horizontal, [N] square)
Goal: [primary goal]
Cadence: [frequency]
Destination URLs: [configured / not configured — flag if missing]
Pin queue: [N] topics loaded

Ready to create pins. Run /create to generate your first composed batch.
```

---

## Quality Gates
✓ Brand voice captured (not just adjectives — vocabulary rules, banned words)
✓ Boards have keyword-rich descriptions (not just names)
✓ Image library located and inventoried
✓ Image orientation breakdown flagged
✓ Pin queue has 8+ topics with specific angles (not generic subjects)
✓ Destination URLs configured or explicitly flagged as missing
✓ Config saved to Drive for /create and /track to read
