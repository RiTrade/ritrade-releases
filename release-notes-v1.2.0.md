# RiTrade 1.2.0

_Released 2026-06-12_

### Added

- **Auto-update is live** (work 0026). RiTrade now checks for new versions
  quietly (a few seconds after launch and every six hours) and shows a slim
  banner when one is ready - never a pop-up. One confirm dialog tells you
  three true things: your data is snapshotted first, the app restarts, and
  Windows will show a SmartScreen warning because RiTrade isn't code-signed
  yet. Every download is hash-verified before it runs, the pre-update
  snapshot is a consistent database copy (never a hot file grab), and an
  update never starts while an import is running. A Settings switch turns
  checking off entirely. If anything fails before install, nothing changed
  and Retry is safe. Updates that can't be applied in one click (a too-old
  install or a newer manifest format) say so honestly and link the download
  page instead of pretending nothing happened.

- **Demo data on first run** (work 0146). A fresh install now offers to load
  demo data: one click seeds two clearly-badged demo accounts ("Demo - Day
  Trading" and "Demo - Swing", 108 sample fills imported through the normal
  pipeline with dates shifted to look recent) so every dashboard is alive in
  minute one. The moment your first real account or import arrives, RiTrade
  offers — once — to remove the demo cleanly, leaving zero trace. Declining
  either prompt is respected permanently; demo accounts stay deletable like
  any other account; existing installs never see any of this.

- **Six redesigned default dashboards for new installs** (work 0008). Performance,
  Timing, Edge Discovery, Costs & Friction, Consistency and Position Sizing are
  now composed around how a real scalper, day trader or swing trader reads their
  results: a headline answer row on every dashboard (named, e.g. "Luck vs Skill",
  "Gross to Net"), time-of-day and overtrading checks built from the trader's own
  distribution (no hardcoded market sessions), holding-period views for swing
  traders, sample counts visible wherever thin data could masquerade as edge, and
  a gross-vs-net equity view that shows the lifetime cost of trading as one gap.
  Existing installs are untouched — the new compositions seed only where a
  dashboard with that name does not already exist. Finance now seeds as the last
  tab on fresh installs.

### Fixed

- **The Accounts filter can now actually multi-select** — picking a second
  account (or mixing an account with a whole category) used to silently reset
  the filter to "All accounts" whenever the picks happened to cover every
  account you have. Hand-picked selections now stay selected; only clearing
  everything or selecting whole categories that span all accounts still
  resolves to "All accounts" (work 0148).
- **Typing in the Slicer tile's symbol box no longer kicks you out after every
  keystroke** — the slicer's own filter broadcast re-rendered the tile and
  destroyed the box mid-word, forcing a re-click per character. The field now
  keeps focus, caret and your typed text across re-renders, including ones
  triggered by other tiles (work 0149).
- **Automatic backups no longer bundle the application itself** — pre-update
  and pre-migration snapshots were ~96 MB of app binaries on installed
  copies; they now contain only your data (database, key, documents,
  receipts), making them ~50x smaller and instant (work 0136).
- **Deleting an account with its trades now also removes its import/sync log
  entries** — previously these provenance rows were orphaned. Deleting an
  account while keeping its trades still keeps the logs (work 0146).
- **Keyboard focus is now clearly visible on all header buttons** — the header
  button family gained the standard 2px accent focus ring (previously the
  browser default), and screen readers are now notified when a modal's
  loading state becomes an error (work 0141, accessibility advisories from
  the 0139 Help cycle).
- **Fresh installs were missing most of the metric catalog** — `migrate_db()`
  returned early on databases without the legacy trades table (every fresh
  install since 0105), so 22 of 42 metrics and all formula tooltips never
  seeded; multi-stat tiles showed "UNKNOWN METRIC" and the metric picker was
  crippled. Metric seeding now runs on every boot; existing installs heal
  automatically on next start (work 0008, UAT finding F1).
- **Default Performance and Consistency headline tiles rendered empty on fresh
  installs** — the seeds passed a config shape the multi-stat tile never read
  ("No metrics selected" on first launch). Seeds now use the tile's real
  slot-based config (work 0008, finding F-DA-1).

---

## Verify

SHA256: `30387cf23cd56cb43a9d536c88244241c648b7775b22803bf13a46b2060e6dd9`

## License

Proprietary - [RiTrade EULA](https://github.com/RiTrade/ritrade-releases/blob/main/EULA.md). The installer requires EULA acceptance.