# Changelog

  All notable changes to Pinterest Marketing Strategist are documented here.
  Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/). Versioning follows [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

  ## [Unreleased]

  ### Planned
  - Cloudinary-native batch JSON export

  ## [1.0.0] — 2026-07-05

  ### Added
  - 3 commands: `/setup`, `/create`, `/track`
  - 3 skills: `client-context`, `pin-strategist`, `performance-learning`
  - Composed pin batches: matched image, SEO-structured title and description, board assignment, staggered posting schedule
  - Image-to-copy matching from Cloudinary or a Drive `images/` library
  - Performance prediction per pin (expected save-rate range) on every `/create`
  - Learning loop: save rates + outbound clicks → learnings → baselines → next batch
  - Learning files written back to Drive: `pin-log.md`, `pin-learnings.md`, `pin-baselines.md`

  [Unreleased]: https://github.com/EditorialOS/pinterest-marketing-strategist/compare/v1.0.0...HEAD
  [1.0.0]: https://github.com/EditorialOS/pinterest-marketing-strategist/releases/tag/v1.0.0
  