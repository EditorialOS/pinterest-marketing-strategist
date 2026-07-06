# Pinterest Marketing Strategist

**Docs:** [PRD](PRD.md) · [Changelog](CHANGELOG.md)

Produce composed Pinterest pins from your real documents and approved image library. Not a scheduling tool — a production system that generates pins ready to review and post, then learns from performance data to make every batch smarter.

## What It Does

Pinterest rewards consistency (3-5 pins/day) but most small marketing teams can't sustain that volume because the production cost per pin is too high. They post for two weeks, burn out, and quit.

This plugin reduces the human effort to two things: keep your image library fed, and review batches before posting. Everything else — concept generation, image-to-copy matching, board placement, keyword targeting, performance tracking, and compounding intelligence — is automated.

### The workflow

1. System reads your Google Drive folder (brand guide, audience, boards, learnings)
2. System scans your image library (Cloudinary or Drive images/ folder)
3. System generates pin concepts matched to approved images
4. You review the composed batch — approve, swap an image, tweak a title
5. Post to Pinterest

Content in, composed pins out, human quality gate, publish.

### The learning loop

Every /create generates a pin batch with performance predictions. Every /track logs results and extracts specific learnings — which image types paired with which title patterns on which boards drive the highest save rates. Every subsequent /create reads those learnings and gets smarter.

By batch 10, the system knows things about your Pinterest performance that your team may not have noticed, because it cross-references every variable (image type × title pattern × board × timing) without forgetting.

No scheduling tool does this.

## Commands

### /setup
Configure your brand, boards, image library, and Pinterest goals. Run once to set up, re-run to update.

```
/setup Brand: Editorial OS
```

### /create
Produce composed pins — copy, matched image, board, keywords, posting schedule — ready to review and post.

```
/create Topic: editorial operations gap
/create Next from queue
/create Seasonal: summer content planning
```

### /track
Log performance, extract learnings, make the next batch smarter. Run after pins have been live for 7+ days.

```
/track Batch: editorial operations gap
/track [paste Pinterest analytics]
```

## Install

```
/plugin marketplace add EditorialOS/pinterest-marketing-strategist
/plugin install pinterest-marketing-strategist@pinterest-marketing-strategist
```

## Example Usage

**Example 1:** Run `/create Topic: content workflow automation` to generate a batch of 5 composed pins with titles, descriptions, matched images from your library, board assignments, and a posting schedule.

**Example 2:** Run `/track Batch: content workflow automation` after 7 days with your Pinterest analytics data. The system compares results to predictions, extracts learnings about what image-copy combinations worked, and saves them to Drive.

**Example 3:** Run `/create Next from queue` to generate the next batch. This time, the system reads learnings from the last tracked batch and applies them — avoiding underperforming combinations and leaning into proven ones.

**Example 4:** Run `/setup Update boards` to add a new board or change your image library source.

## Connectors

- **Google Drive** (required) — reads brand context and learning files
- **Cloudinary** (recommended) — scans image library, delivers Pinterest-sized images
- **Pinterest API** (optional) — auto-post pins, auto-pull analytics
- **Google Calendar** (optional) — seasonal event alignment

See [CONNECTORS.md](CONNECTORS.md) for degradation behavior at each level.

## How It Works with the Editorial OS Network

Same Drive folder serves [Editorial OS](https://github.com/EditorialOS/editorial-os) (content strategy), Email Marketing Strategist (newsletters), and this plugin (Pinterest). Shared documents: brand guide, audience personas, content strategy. Pinterest-specific: pin-log.md, pin-learnings.md, pin-baselines.md.

## License

Apache 2.0 — see [LICENSE](LICENSE).
