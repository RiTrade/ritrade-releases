# RiTrade 1.2.11

_Released 2026-06-24_

### Added

- **A menu, so the app is easy to find your way around.** A hamburger menu (the
  three-line button) now sits in the header in place of the old settings gear, and
  the header is tidier for it - Sign out, the User guide, and every settings area now
  live together in the menu instead of being scattered across the top bar. Each
  settings area opens as its own focused panel: Accounts, Appearance, Custom broker formats,
  Backup & restore, and Security. And "Accounts" is now an obvious front door for
  adding a trading account, instead of being buried behind the gear. (Work 0184.)

- **An "About & updates" screen - one place for your version and updates.** The menu
  now has a single home for everything to do with keeping RiTrade current: which
  version you're on, a button to check for a newer one, and the auto-update toggle.
  When it can't reach the update server it now tells you so ("Couldn't check") instead
  of looking like nothing happened. (Work 0184.)

- **A gentle "set up your first account" nudge for new users.** The first time you
  open RiTrade, just after the demo-data step, a one-time prompt offers to walk you
  straight into adding your first account - so a brand-new journal isn't a blank screen
  with no obvious next step. You can skip it. (Work 0184.)

- **Apply one filter across your dashboards - or keep each on its own.** Every dashboard
  now has an "Apply to" choice in the filter bar: **This dashboard** (its own filters) or
  **Global** (follow one shared filter - accounts, period, symbol, side - set once and
  reflected on every dashboard that chooses it, instead of re-setting each tab by hand).
  A **Copy filter from** button snapshots another dashboard's filters onto this one in
  a click. The header shows a read-only summary of what's applied; clicking any chip opens
  the filter bar focused on that control. Any dashboard set to follow the Global filter
  shows a small globe on its tab, so you can see at a glance which dashboards are on the
  shared filter. Existing dashboards keep their own filters - nothing changes until you
  switch one to Global. (Work 0150.)

### Fixed

- **Custom broker formats now actually shows your saved formats.** Opening Menu -> Custom
  broker formats used to claim "No saved formats" even when you had import formats saved - it
  was looking in the wrong place. It now lists every format you've saved, and each one
  shows the account it's tied to as a small pill you can remove: click the x to unlink
  the format from that account (with a quick confirm), so the same format is free to be
  used elsewhere. You can also rename or delete any saved format from here. The
  "nothing saved yet" message now appears only when you genuinely have none. (Work 0184.)

- **The Activity-by-hour and P&L-by-weekday chart bars now follow your theme instead of
  rendering black.** When either chart was set to show **Trade Count** or **Win Rate %**,
  the bars came out solid black on every theme; only the Net P&L view coloured correctly.
  The bars now use your theme's accent colour, and on the by-hour chart the "dim bars below
  N trades" setting works again (low-sample hours are shown faded rather than full-strength).
  (Work 0183.)

- **The dashboard and settings on/off switches are now keyboard- and
  screen-reader-friendly.** Every toggle (per-tile sync options, dashboard options)
  now announces its label to a screen reader and shows a visible focus ring when you
  tab to it. (Work 0150 accessibility pass.)

- **Dashboard tabs behave like buttons again.** Hovering a dashboard tab no longer
  flips your pointer to a text-editing I-beam, and a tooltip now spells out what the
  tab does - click to open it, right-click to rename or delete.

- **The "Total Fees" figure now includes every cost.** On accounts whose broker charges a
  consumption tax or GST (such as moomoo), the Total Fees stat and the fee breakdown were
  leaving the tax out, so the number read lower than the costs actually deducted from your
  net P&L. Your net P&L was always correct - only the fee total understated it. Now every
  fee component is counted, on the stat cards, the calendar and the per-symbol tables.
  (Work 0182.)

### Changed

- **Clearer dashboard chrome.** The P&L calendar's month-navigation arrows are larger and
  easier to see, and the toolbar help icon is bigger and simplified to a plain question mark.

---

## Verify

SHA256: `4537d379dc38ec41b32c3cbfc534a46e01947a98f88db664763928e97c1bf122`

## License

Proprietary - [RiTrade EULA](https://github.com/RiTrade/ritrade-releases/blob/main/EULA.md). The installer requires EULA acceptance.