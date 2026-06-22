# RiTrade 1.2.6

_Released 2026-06-22_

### Changed

- **A one-time database upgrade applies automatically on first launch.** This release
  adds an internal `source_format` field (records which broker layout each trade came
  from — it powers the cross-source duplicate check below) plus a matching index that
  speeds up overlap detection. It is additive, runs once on launch, needs no action, and
  leaves your existing data untouched. (Schema migration m_008.)

- **RiTrade now warns before you double-count the same trades from two different
  sources.** If you import a file covering days you already have — but from a
  different broker export (say a PDF one time, a CSV the next) — those trades don't
  line up exactly, so the usual duplicate check can't catch them and they'd quietly
  land twice. RiTrade now spots the overlap, shows which trades might be repeats, and
  asks: keep both (the safe default — nothing is deleted), or replace those days with
  this file (it names exactly which trades it would remove, broken down per currency).
  On an unsaved or unfamiliar layout it offers only "keep both", never the deleting
  option. (Work 0130 Phase 5 — cross-source advisory.)

- **Conflicts now feel like one thing, not two.** When an import overlaps days you
  already have — or turns up individual trades that match ones in your journal —
  RiTrade frames both as one "Reconcile" moment with the same wording, instead of two
  unrelated-looking pop-ups. If a single import hits both (overlapping days, then a
  duplicate trade), the second screen picks up where the first left off — "step two of
  sorting this out" — rather than feeling like a fresh surprise. (Work 0130 Phase 5.)

- **A broker sync now handles overlapping days the same way a file import does.**
  If a sync brings in days you'd already imported from a file, RiTrade now asks what
  to do — keep what you have and add only the gap, or replace those days — instead of
  deciding silently. And when a sync turns up trades that look like ones you already
  have, they go to the same review screen every other import uses, rather than
  vanishing. One way to bring data in, one way to reconcile it. (Work 0130 Phase 3.)

- **The "format has changed" screen reads more clearly.** When a saved import's
  columns move, the screen now explains what changed in plain language and asks one
  precise question — keep the current broker signature, or create a new one for this
  layout — with the name field appearing only if you choose to create a new one.
  (Work 0130 Phase 2.)

- **Recognised imports now confirm on a single screen.** When RiTrade recognises a
  file's format — a known broker, a saved custom format, or a returning file whose
  layout matches what you imported before — it shows ONE confirmation: the format it
  recognised, how many trades are ready to import (and how many look like possible
  duplicates), and a single "Looks right — import" button. The column mapping that
  proves the recognition is one click away under "View Data Mapping", but it no longer
  takes two separate screens to get from "we recognised this" to "imported". The
  number on the button is the NET figure that will actually be saved — after dropping
  cancelled / never-filled orders and setting aside rows you already have — so it
  matches what lands. (Work 0130 Phase 1.)

- **A file that's too big or the wrong type is now turned away at the door.** Importing
  a file over 50 MB, or one whose contents don't match what its name claims (a `.pdf`
  that isn't really a PDF), now fails fast with a clear message instead of slipping
  partway into the import. (Work 0130 Phase 4.)

### Fixed

- **A broker sync can no longer quietly pull the wrong account's trades.** When a
  sync couldn't confidently tell which of your broker's accounts matched the one you
  set up, it used to carry on and import whatever it found — which could file another
  account's trades into your P&L with nothing to warn you. Now that account's sync
  stops cleanly and tells you what happened in plain language: it names the account it
  couldn't match and lists the accounts it actually found under that login, so you can
  re-link to the right one. Nothing is imported when there's any doubt, and your other
  accounts keep syncing as normal. The account card now shows this clearly too — the
  usual "Fed by broker sync" tag turns into a "Last sync failed" flag with the broker's
  own reason spelled out underneath and a one-tap "Re-link account" link to put it
  right; it clears itself the moment the next sync succeeds. (Work 0143.)

- **An import that hits a snag no longer blocks every import after it.** Previously,
  if an import failed partway through saving, it could leave the journal stuck — every
  later import would fail until you restarted the app, with no hint that a restart was
  the fix. Now a failed import cleans up fully and steps aside, so the very next import
  just works. (Work 0169.)

- **Your trade dates and times are never treated as optional.** When you match a file's
  columns yourself, RiTrade now always needs the date and time for each trade — it
  fills them in automatically when it spots an obvious "Open Time"/"Close Time" column,
  and asks you which day the trades were made if the file only has times and no date.
  A trade with no time can't sit on the calendar or in a session, so it's never saved
  without one — and the import can no longer fail at the finish line because a date
  column was left unmatched. (Work 0168.)

- **Correcting a wrong format guess no longer dead-ends.** After telling RiTrade
  "this isn't <X>" and picking another format, the wizard used to stall on "File
  could not be read" — the whole correct-a-wrong-guess path was broken. Re-picking a
  format now rebuilds the preview and carries on. (Work 0130 closure.)

- **Re-importing the exact same file now says so plainly.** Importing a file you've
  already imported is caught up front, but it used to be labelled "File could not be
  read" — as if the file were broken. It now shows "You've already imported this file"
  with the date it first went in. (Work 0130 closure.)

- **A non-spreadsheet file renamed `.csv` is stopped at the door.** A binary file
  (a PDF or image) renamed to `.csv` used to slip past the upload check and strand you
  on a mapping screen full of garbled columns. The upload door now sniffs the contents
  and turns a binary file away cleanly with "File could not be read", the same as the
  watch-folder door already did. (Work 0130 closure.)

- **A hand-mapped import now shows possible duplicates before you commit.** When you
  map an unknown file's columns yourself, the confirm screen used to always say "0
  duplicates" and only reveal the repeats as "Skipped" after the fact. It now
  pre-counts them — "N to import, M duplicates" — the same way a recognised import
  already did. (Work 0130 closure.)

- **A "format changed" re-map no longer makes you re-map columns that didn't move.**
  When a saved format's columns shifted and you kept the format, RiTrade re-filled
  Symbol/Side/Qty/Price from your saved mapping but left Date and Time blank even
  though they hadn't moved. It now carries Date and Time over too, so only the column
  that genuinely changed needs your attention. (Work 0130 closure.)

- **An import that finds nothing new now reads cleanly.** When every trade in a file
  was already in your journal, the result screen contradicted itself — "Nothing
  imported... or couldn't be read" right next to "Verified: N fills landed." It now
  says simply "Already in your journal — nothing new to add", with no phantom "landed"
  count and no "couldn't be read" when the file read fine. (Work 0130 closure.)

- **Replacing overlapping days no longer leaves half of an overnight trade behind.**
  Choosing "Replace these dates" now removes the whole overlapping trade, even when it
  opened on one day and closed the next — closing a gap where the leftover half could
  quietly double-count. (Work 0130.)

- **A broker sync no longer counts conflicting trades as "imported".** When a sync
  brought in trades that clashed with ones you already had, it counted them as imported
  AND queued them for review — so the same trades were both tallied and flagged. The
  sync result now reports cleanly imported trades and trades that need your review as
  two separate numbers. (Work 0130 Phase 3.)

- **A re-mapped "format changed" import no longer shows "Import 0 fills".** When a
  saved format's columns moved and you re-mapped the one that changed, the confirm
  screen counted zero (the drift path skips the row-counting pass), so the button read
  "Import 0 fills" even though committing would still have brought the rows in. It now
  shows the real count. (Work 0130 Phase 2.)

- **A hand-mapped import's "Import N" button now matches what actually lands.** When you
  map an unknown file's columns yourself and it contains cancelled / never-filled orders,
  the confirm button counted the raw rows (e.g. "Import 4 fills") while the import
  correctly dropped the cancelled one and saved 3 — with "Skipped: 0" hiding the
  difference. The button now shows the true net number up front, so the count you see is
  the count you get. (Work 0130 Phase 6.)

- **Re-importing a file into an account with a saved custom/generic format no longer
  fails.** A returning import of a previously-mapped generic CSV did not reuse its
  saved column mapping through the file-import wizard (it worked only via folder
  watch), so the second import of the same format hit a validation error. RiTrade now
  reuses the saved mapping the same way no matter how the file arrives, landing on the
  one-click recognised confirmation. (Work 0130 Phase 1.)
- **A watch-folder account now shows an "Import folder" button on its card,
  instead of a "Import a file" button that re-prompted for a single file.** The
  account card never rendered the folder action (only the broker-sync and manual
  file-import buttons were wired), so a local-folder account fell through to the
  manual file-import button and could not scan its watched folder from the card.
  The card now offers "Import new files from the watch folder" (scanning the
  configured folder via the same path as "Sync All"), and the file-import button
  is shown only for manual accounts. (Completes the 0130 ingest-hub card wiring.)
- **Importing a custom CSV from Webull (US) no longer fails with "price: found
  0.0".** Webull writes each fill price with a leading `@` (e.g. `@2.40`, meaning
  "at 2.40"). The custom-CSV importer stripped `$` and `,` from numbers but not
  the `@`, so every price parsed as zero and the import was blocked at the
  validation step. The `@` is now stripped alongside `$` and `,`, so Webull US
  order-history files import cleanly. A price cell that is genuinely unreadable is
  now reported as the offending value instead of being silently treated as 0.00.

---

## Verify

SHA256: `de1fbb5db9b75c1d0cdf2e78934a76ffc90fe876b3a83d42119e2efe8cc4e34d`

## License

Proprietary - [RiTrade EULA](https://github.com/RiTrade/ritrade-releases/blob/main/EULA.md). The installer requires EULA acceptance.