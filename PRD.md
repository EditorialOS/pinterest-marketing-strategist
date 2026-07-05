# PRD — Pinterest Marketing Strategist v1.0

  **Status:** Shipped · v1.0.0 · [Changelog](CHANGELOG.md)
  **Owner:** Roger Gurbani

  ---

  ## Problem

  Pinterest rewards daily volume — 3–5 pins per day — and punishes inconsistency. Most small teams post for two weeks, burn out on per-pin production cost, and go dark; the algorithm forgets them. The bottleneck is not ideas. It's that each pin requires image selection, SEO copy, board assignment, and scheduling — too much labor per unit to sustain at the volume the platform demands.

  ## Users

  - **Small marketing teams and solo operators** for whom sustained daily posting is currently impossible
  - **Brands with an existing approved image library** (Cloudinary or Drive) that's underexploited
  - **Agencies** running Pinterest for clients where per-pin cost determines margin

  ## What v1 does

  - Generates **composed batches**: for each pin — matched image from the approved library, keyword-targeted title within character limits, SEO-structured description, board assignment, staggered posting schedule
  - Reduces the human role to two tasks: keep the image library fed, and review batches before posting
  - Grounds copy and board logic in Drive context: brand guide, personas, board structure, seasonal calendar
  - Predicts an expected save-rate range per pin based on the account's own history
  - Closes the loop via `/track`: logs save rates, impressions, and outbound clicks; extracts which **image type × title pattern × board** combinations performed; writes learnings to Drive for the next batch
  - Scores every batch before delivery: voice consistency, board alignment, image-copy fit

  ## What v1 explicitly does NOT do

  - **Does not generate images.** It composes from an approved library only. Brand-safe by construction — no AI imagery enters the account.
  - **Does not auto-post.** Batches are staged for human review; Pinterest API auto-posting is an optional connector, not core behavior.
  - **Does not pull analytics automatically.** `/track` accepts pasted or reported analytics; API sync is a connector-level extension.
  - **Does not run ads.** Organic pin production only. Promoted-pin strategy is out of scope.
  - **Does not chase trends off-brand.** Concepts come from the brand's topics, boards, and seasonal calendar — not from trending-keyword scraping.

  ## Success criteria

  - A review-ready batch sustains the platform cadence: enough approved pins per session to cover 3–5/day between sessions <!-- ⚠️ RAJ: state your measured numbers — batch size, generation time, and % of pins approved without edits on your test account. Approval rate is the number that matters. -->
  - 100% of pins in a batch use only approved library images
  - `/track` learnings are specific enough to act on: pattern statements at the image-type × title-pattern × board level, not "pins did well"
  - Save-rate predictions narrow against actuals as tracked batches accumulate <!-- ⚠️ RAJ: even 2–3 tracked batches of predicted-vs-actual is worth stating here. -->

  ## v1.1 roadmap

  - Cloudinary-native batch JSON export

  ## Decision log

  - **Approved library only, no generation** — the constraint is the feature; brand safety and production speed both come from composing over creating
  - **Performance tracked as a three-way combination** (image type × title pattern × board) — single-variable learnings on Pinterest are noise
  - **Batch + review over pin-by-pin** — the product attacks per-unit production cost; the human review step is where judgment stays
  