# Connectors — Pinterest Marketing Strategist

This plugin reads from your Google Drive folder and optionally connects to additional services for composed pin output, direct posting, and seasonal timing.

## Required

### ~~docs — Google Drive
Reads brand guide, audience personas, product info, board configuration, pin learning files, and image library (if images are stored in Drive). Writes pin records and learnings back to Drive after every /create and /track.

**Without ~~docs:** The plugin works in manual mode — you describe your brand, paste analytics, and provide images directly. No persistent learning between sessions.

## Recommended

### ~~images — Image Library (Cloudinary)
Scans your approved image library for brand photos, product shots, lifestyle images, and visual assets. Returns metadata (dimensions, orientation, tags) and delivers Pinterest-optimized transformation URLs (smart crop to 2:3 vertical at 1000×1500).

**With ~~images:** /create outputs composed pins with ready-to-use image URLs. Full image matching with orientation analysis, category scoring, and freshness tracking.

**Without ~~images:** /create matches images from the ~~docs images/ folder instead. Less metadata available, no automatic transforms. User handles resizing before posting.

## Optional

### ~~pinterest — Pinterest API
Posts pins directly to boards via API. Pulls analytics data for /track automatically instead of requiring manual paste.

**With ~~pinterest:** Full automation — /create can post approved pins directly. /track pulls analytics without manual input.

**Without ~~pinterest:** User posts pins manually (copy-paste from /create output). User pastes analytics into /track. The learning loop works the same — it just requires the human to move data in and out of Pinterest.

### ~~calendar — Calendar
Reads seasonal events, launches, and editorial calendar entries for posting schedule optimization and seasonal hook recommendations.

**With ~~calendar:** /create checks for upcoming events and aligns pin timing and seasonal hooks automatically.

**Without ~~calendar:** Uses general seasonal knowledge (summer travel = publish March-April, holiday content = publish September-October).

## Degradation Behavior

The plugin works at every level. More connectors = less manual work, not different functionality.

| Level | Connected | What Changes |
|:---:|---|---|
| Full | ~~docs + ~~images + ~~pinterest + ~~calendar | Complete automation: composed pins, auto-post, auto-track, seasonal alignment |
| Composed | ~~docs + ~~images | Composed pins with matched images. User posts manually, pastes analytics. |
| Standard | ~~docs (with images/ folder) | Image matching from Drive. No transforms. User posts and tracks manually. |
| Minimal | ~~docs only (no images) | Pin concepts with IMAGE NEEDED flags. User sources images, posts, tracks manually. |
| Manual | Nothing connected | User provides all context. No persistent learning. Functional but limited. |

Each level produces usable output. The difference is how much human effort sits between "run /create" and "pin is live."
