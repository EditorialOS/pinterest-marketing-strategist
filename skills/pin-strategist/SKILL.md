---
name: pin-strategist
description: "Pinterest content creation methodology. Generates composed pins — copy matched to images from the brand's approved library — optimized for Pinterest's visual search engine. Handles concept generation, image-to-concept matching, copy writing, board placement, and search targeting."
---

# Pin Strategist — Composed Pin Methodology

## Purpose

Turn brand documents and approved images into composed Pinterest pins ready to review and post. Pinterest is a visual search engine — this skill optimizes for search intent first, image-copy pairing second, and brand voice third. That order matters. The output is a finished product, not a concept deck.

## Core Principle

Pinterest is not social media. It's a visual search engine where people plan purchases, trips, projects, and decisions. Users arrive with intent. Every pin must answer a search query with a compelling image-copy combination. A beautiful image with no search relevance gets zero impressions. A well-targeted pin with a matched image gets discovered for months.

The FAZ model applies: content in, finished product out, human quality gate, publish. The human reviews composed pins. Everything upstream — concept generation, image matching, copy writing, board assignment — is automated.

## How Pinterest Discovery Works

**Search weight:** Pinterest ranks pins by keyword relevance in title, description, and alt text. Title keywords carry the most weight. Front-loading is not optional.

**Visual ranking:** Pinterest's algorithm evaluates image quality, orientation, and freshness. Vertical images get more feed space. High-contrast, well-lit images rank higher. Duplicate images get deprioritized.

**Save signals:** Saves compound. One save leads to impressions for similar audiences. Save rate is the most important engagement metric.

**Freshness factor:** New images with new URLs get priority distribution. Reuploading the same image to the same URL gets deprioritized. Each pin in a batch must use a different image.

**Domain authority:** Pins from consistently active, trusted domains get higher initial distribution.

**Content lifespan:** Average pin lifespan is 3-4 months. Top pins drive traffic for years. This makes Pinterest the highest-ROI channel per unit of effort — every pin is a long-term asset.

## Image-Copy Matching Engine

This is the methodology that transforms pin concepts into composed pins.

### The Matching Principle

An image and its copy must tell the same story. A lifestyle image of a team collaborating pairs with a title about content workflows — not product pricing. A checklist diagram pairs with a "5 steps to..." title — not an aspirational quote. When image and copy align, the user's brain processes the pin as one coherent message. When they don't, the user scrolls past.

### Matching Decision Matrix

| Pin Concept Type | Ideal Image Category | Fallback Image Category |
|------------------|---------------------|------------------------|
| Problem-solution | Lifestyle (person experiencing problem or solution) | Quote card with headline |
| How-to / tutorial | Diagram, checklist, step-by-step | Workspace/desk flat lay |
| Listicle | Collage, multi-image, or text overlay with number | Bold single image with number in title |
| Product spotlight | Product shot (clean, well-lit) | Product in context (lifestyle with product visible) |
| Aspirational | Lifestyle (aspirational scene) | Scenic/destination |
| Behind-the-scenes | Team, workspace, process photos | Candid, unpolished shots |
| Comparison | Side-by-side diagram, 2-column graphic | Bold text overlay with vs. framing |
| Seasonal / timely | Seasonal imagery (colors, setting) | Any image with seasonal text overlay |

### Matching Algorithm

For each pin concept, score candidate images across five dimensions:

1. **Topic relevance (40% weight)** — Does the image content relate to the pin's subject matter? A pin about "content workflow burnout" needs an image that suggests work, team, or process — not a product logo.

2. **Orientation fitness (25% weight)** — Vertical (2:3) = full score. Square = 70% score. Horizontal = 40% score. Pinterest's feed layout gives vertical images 60% more real estate.

3. **Freshness (15% weight)** — Not used in last 10 pins = full score. Used 11-20 pins ago = 50% score. Used in last 10 = 0% (disqualified).

4. **Category fit (10% weight)** — Does the image category match the concept type? Lifestyle image for aspirational pin = full score. Product shot for aspirational pin = reduced score.

5. **Quality (10% weight)** — Well-lit, clear subject, sufficient resolution (600px+ width). Dark, blurry, or cluttered = reduced score.

**Score threshold:** If the best candidate scores below 50%, flag the pin as "IMAGE NEEDED" with creative direction rather than forcing a poor match. A bad image-copy pairing hurts more than a concept waiting for the right image.

### Image Sizing for Pinterest

Pinterest displays pins at fixed widths, variable heights. Optimal dimensions:

| Pin Type | Dimensions | Aspect Ratio | When to Use |
|----------|:---:|:---:|-------------|
| Standard pin | 1000 × 1500 | 2:3 | Default for all pins |
| Long pin | 1000 × 2100 | 1:2.1 | Infographics, step-by-step, checklists |
| Square pin | 1000 × 1000 | 1:1 | Product shots, headshots (less ideal) |
| Story pin | 1080 × 1920 | 9:16 | Multi-page idea pins |

**Minimum width:** 600px. Below this, the image appears low quality on mobile.

**If ~~images (Cloudinary) is connected:**
Apply transformation to deliver Pinterest-optimized dimensions:
- `c_fill,w_1000,h_1500,g_auto` — smart crop to 2:3 vertical, subject-aware gravity
- `c_fill,w_1000,h_2100,g_auto` — for long pins
- `q_auto,f_auto` — automatic quality and format optimization

The transformation URL is included in the composed pin output so the image is ready to download or post.

**If using Drive images:**
Note the recommended crop dimensions in the output. The user resizes before posting.

## Pin Concept Generation

### Angle Types

| Angle | Best For | Title Pattern | Save vs. Click Profile |
|-------|---------|---------------|:---:|
| Problem-solution | High CTR, engaged audience | "[Problem] — [solution exists]" | Click-heavy |
| How-to | Engagement, shares | "How to [achieve outcome]" | Balanced |
| Listicle | Discovery, saves | "[N] [things] for [audience]" | Save-heavy |
| Comparison | Consideration stage | "[A] vs. [B]: [what matters]" | Click-heavy |
| Seasonal | Timely discovery | "[Season] [topic] [year]" | Save-heavy |
| Aspirational | High saves | "[Aspirational scene/outcome]" | Save-heavy |
| Product spotlight | Sales, traffic | "[Product] — [key benefit]" | Click-heavy |
| Behind-the-scenes | Brand building | "[Inside look at process]" | Balanced |

### Batch Diversity Rules

Within a single batch of 5-10 pins:
- No two pins use the same angle type consecutively
- No two pins target the same primary search term
- No two pins use the same image
- At least 2 different boards are served
- Mix of save-oriented and click-oriented angles
- Mix of image categories (don't use 5 lifestyle images in one batch)

### Concept Quality Test

Every concept must pass four gates:

1. **Not a repeat** — different angle from any pin in the last 14 days
2. **Search-aligned** — maps to real Pinterest search queries. 96% of top searches are unbranded.
3. **Board-appropriate** — fits the assigned board's theme
4. **Image-matchable** — a relevant image scores 50%+ in the matching algorithm

If a concept fails any gate, replace it. Never ship weak pins to hit batch quota.

## Title Writing for Pinterest

### Non-Negotiable Rules

- **Under 100 characters** — Pinterest truncates at 100
- **Front-load the keyword** — first 3-4 words determine search ranking. "Content Workflow Automation" not "How You Can Improve Your Content Workflows"
- **Be specific** — numbers, outcomes, audiences. "3 Content Fixes for Teams Under 10" beats "Content Tips"
- **Match the image** — title and image must tell one story. If the image shows a checklist, reference steps or items in the title.
- **Match search intent** — use words people type. "content operations for marketing teams" not "editorial paradigm optimization"

### Title Patterns by Effectiveness

| Pattern | CTR Profile | Save Profile | Example |
|---------|:---:|:---:|---------|
| Number + specific | High | Medium | "5 Content Workflow Fixes for Small Teams" |
| How to + outcome | High | High | "How to Run Editorial Operations Without an Editor" |
| Year + topic | Medium | High | "2026 Content Operations Checklist" |
| Question | Medium | Medium | "Is Your Content Calendar Actually a System?" |
| Direct value | High | Low | "Editorial OS — Content Operations Automated" |
| Aspirational | Low | High | "The Content Team That Never Burns Out" |

### Title Failures

- Vague: "Content Tips" (no search specificity)
- Clever-not-searchable: "Operations Unleashed" (nobody searches this)
- Too long: truncated to "Here Are Some Of The Most Amazing Content Workflow Strategies Tha..."
- Brand-first: "Editorial OS Presents: Content Tips" (nobody searches your brand name)

## Description Writing for Pinterest

### Structure

```
[Keyword-rich first sentence — shows in truncated preview]
[Supporting detail — expands on the promise]
[CTA — what to do next]
```

### Rules

- **150-300 characters** optimal
- **First sentence is everything** — it's the preview. Front-load value.
- **2-3 keyword phrases woven naturally** — not stuffed. "Content workflow automation for stretched marketing teams" hits three terms naturally.
- **No hashtags** unless brand guide uses them. Pinterest guidance de-emphasizes hashtags.
- **CTA matches goal:**

| Goal | CTA | Example |
|------|-----|---------|
| Saves | Soft invite | "Save this for your next planning cycle." |
| Traffic | Direct invite | "Tap to read the complete guide." |
| Sales | Action invite | "Get started today — link in pin." |
| Audience | Cross-channel | "Follow for weekly content ops insights." |

## Board Placement Strategy

### Selection Logic

1. **Topic relevance** — content matches board theme
2. **Board balance** — distribute. If one board got 5+ of last 10 pins, prioritize others.
3. **Board maturity** — boards under 15 pins should be prioritized
4. **Goal alignment** — traffic-goal pins → traffic-goal boards
5. **Multi-board limit** — 1-2 boards maximum per pin. More than 2 is spam.

### Board Health Indicators

| Indicator | Healthy | Needs Attention |
|-----------|---------|-----------------|
| Pin count | 15+ | Under 15 — board looks empty |
| Recency | New pin within 7 days | No pin in 30+ days |
| Save rate | Above brand average | Consistently below average |
| Theme coherence | All pins match theme | Mixed content — confuses algorithm |

## Search Term Strategy

### How to Choose Target Terms

1. **Think like a Pinterest user** — planning intent. "content operations workflow 2026" not "content marketing"
2. **Long-tail beats broad** — "editorial workflow for marketing teams" beats "content strategy"
3. **96% unbranded** — target category terms, not brand names
4. **Vertical norms** — SaaS users search "[problem] [solution]", travel searches "[destination] [activity]", food searches "[cuisine] [meal type] recipe"

### Terms Per Pin
- 2-3 target terms per pin
- Primary: appears in title (front-loaded)
- Secondary: appears in description and alt text
- Natural integration — never keyword-stuff

## Seasonal Strategy

Pinterest users plan ahead. Publish 2-3 months BEFORE the season:

| Content Season | Publish By |
|---------------|-----------|
| Summer campaigns | March-April |
| Back to school | June |
| Fall planning | July-August |
| Holiday / Q4 | September-October |
| New Year / Q1 | November |
| Spring launches | January-February |

## Performance Benchmarks (Defaults)

Use when no client-specific data exists. Replace with real data after first /track.

| Vertical | Avg Save Rate | Avg CTR | Avg Engagement |
|----------|:---:|:---:|:---:|
| SaaS / B2B | 1-2.5% | 0.8-1.5% | 2-4% |
| Travel & hospitality | 1.5-3% | 0.8-1.5% | 3-5% |
| Food & recipe | 2-4% | 1-2% | 4-6% |
| Home & lifestyle | 1.5-3% | 0.8-1.2% | 3-5% |
| Ecommerce / product | 0.8-2% | 1-2% | 2-4% |

## Teammate Protocol Compatibility

Same skill, different trigger:

**Plugin mode (Cowork):** User runs /create. Skill generates composed pins for review.

**Teammate mode (Autonomous):** Standing orders trigger batch creation on schedule. Skill reads Drive + image library, generates composed batch, emails morning summary with composed pins for approval.

The image matching methodology is identical in both modes. The only difference is who triggers it and where the output goes.
