# RiTrade 1.1.0

_Released 2026-06-11_

### Changed

- **The application's core code now ships compiled to native machine code** (Cython)
  instead of Python bytecode — protecting RiTrade's intellectual property. All 36
  backend and importer modules are compiled; behaviour is unchanged.

- The application window title now reads "RiTrade.app (Alpha Test Version)", so it's
  always clear you're on a test build.

### Fixed

- A failed broker sync could crash while composing its error message instead of
  showing the friendly explanation (an unimported module in the HTTP-error path —
  found by the new compilation step's static analysis).

- **Ledger features work on fresh installs.** On a brand-new installation, every
  ledger surface (P&L ledger, ledger entries, expense breakdown) failed because new
  databases were created with an outdated ledger table layout — long-time databases
  were unaffected, which is why this hid until the first Alpha install. New databases
  are now created correctly, and existing ones are repaired automatically on launch
  (work 0135).

### Added

- **The user guide is now built into the app.** A "?" button in the header (and a
  "User guide" link in Settings) opens the full 15-chapter guide in a near-fullscreen
  reader without leaving RiTrade, with an "Open in browser" option for comfort
  reading. The guide ships inside the installer and updates with every release —
  no separate download (work 0139).

- **RiTrade now ships under its own license agreement.** The installer presents the
  RiTrade End User License Agreement (EULA) and asks you to accept it before
  installing - the standard step you'd expect from a desktop app. A copy of the EULA
  is installed alongside the app and published with every release, so the terms that
  govern your copy are always the ones it shipped with. This replaces the placeholder
  open-source license text from earlier builds: RiTrade is proprietary software.

- **Alpha and Beta builds are now clearly marked.** Releases can be published to the
  download channel as pre-releases with their own title (this build: "RiTrade 1.1.0
  (Alpha)"), so a testing build is never mistaken for a stable one.

- **Dialogs are becoming one consistent system — starting with the windows you see most
  (work 0128, first migration).** The "Bring in your data" hub, the Sync log, and the
  duplicate-trades review window now share one modal pattern: a fixed size that **never jumps
  or re-centers** while you use it (the review window's "why is my dialog moving?" bug is
  gone for good), the same close behaviour everywhere (Escape, clicking outside, or the X all
  work — and all ask first if you'd lose unapplied choices, with a clear "Keep reviewing"
  option), and calmer transitions (opening the Sync log now neatly swaps the hub away and
  brings it back exactly as you left it, instead of stacking windows). Keyboard and screen-
  reader behaviour is consistent too: focus lands in the window when it opens and returns to
  where you were when it closes. The remaining dialogs move onto the same system next.

- **Settings and everything it opens now ride the same modal system (work 0128, second
  migration).** Settings is a steady, full-size window with a fixed shape — switching tabs
  no longer makes the panel grow and jump (a long-standing annoyance), and Escape now closes
  it like every other dialog. Everything Settings spawns behaves as one family: the account
  wizard (add and edit), per-account Import settings, the clear-trades confirm, and the
  danger-zone delete flow each neatly swap Settings away and bring it back exactly as you
  left it when they close — Import settings no longer piles up visibly on top. Windows
  holding unsaved work ask first: the account wizard and Import settings only question a
  close when you actually have unsaved edits; plain confirms always close freely. Also fixed
  along the way: a console error when closing the account wizard quickly after opening it,
  and the hub's close button now respects the same "not while a sync is running" rule as
  Escape and clicking outside.

- **The import windows joined the same modal system (work 0128, third migration).** The
  import wizard is now a steady, fixed-size window — no more growing, jumping, or the
  broken-looking collapsed panel when you tried to close it mid-import. Closing works the
  same as everywhere else: Escape, clicking outside, or the X all work, and while an import
  is underway they all ask the same clear question — "Cancel import? Any changes you've made
  will not be saved." with **Keep importing** and **Yes, cancel import** buttons (the old
  confusing "Continue import / Cancel" double-negative is gone). While trades are actually
  being saved, the window simply won't close until that finishes. Opening the wizard from
  Settings, from the account-setup wizard, or from the "Bring in your data" hub now neatly
  swaps that window away and **brings it back exactly as you left it** when the import
  closes. The big import-preview window (folder imports) behaves the same way and asks
  before discarding a not-yet-saved import. Also fixed along the way: the "file couldn't be
  imported — no date found" prompt's buttons did nothing at all — they now work (rename-and-
  retry or import manually), and finishing an import with the X or Escape now refreshes your
  accounts and dashboard just like the Done button.

- **Every dialog in the app now rides the one modal system (work 0128, closing
  migration).** The last two holdouts are in: the New/Edit-dashboard dialog and the
  tile-config gear window now share the same steady shell as everything else — fixed
  size, centered, no jumping when you switch tile-config tabs (the tab strip now stays
  put while the content scrolls). The dashboard dialog finally has a close X, and both
  windows close like every other: Escape, clicking outside, or the X — asking first
  only when you actually have unsaved edits ("Keep editing" / "Discard changes").
  Also fixed for light themes: the import-preview window's currency badges, the
  "currency not found" prompt, and the parser-warning blocks were hardcoded dark
  colours that washed out on Daylight — they now follow your theme. A new automated
  check guards the whole system so a "jumping dialog" can't quietly come back.

- **Importing a file RiTrade doesn't recognise is now one plain-language screen — including files where each row is a whole trade (work 0091).** When you map columns yourself, the screen first asks "what is each row in this file?" — **one order per row** (a single buy or a single sell) or **one whole trade per row** (a buy and a sell, paired) — pre-selecting the likely answer from your file's columns. Whole-trade files map Opened / Closed, Direction (Long or Short), Quantity, and Opening / Closing prices, and each row is saved as its buy and its sell so every broker's trades line up in one place. **Fees & taxes are now additive**: add every fee or tax column your file has (Commission, SEC, GST, ...), each auto-sorted into the right fee bucket with a dropdown to correct it — replacing the single "Fees" picker that couldn't express multi-fee files. Also fixed: a hand-mapped whole-trade import no longer fails with a misleading "Session expired" message (commit errors now show their real cause), and Generic CSV no longer shows a confusing "5%" confidence — its row reads "works for any CSV file".

- **"Sync All" is now a one-stop "Bring in your data" hub, and watch-folder import actually works
  (work 0130).** The button opens a window that lists every account with the *right* action for how
  it's set up — **Sync** for broker-API accounts, **Import folder** for watch-folder accounts,
  **Import a file** for manual accounts, and a calm **Finish setup** for ones not configured yet —
  instead of trying to API-sync everything and showing a red "Error" on the rest. Watch-folder
  import now runs each new file through the **same import pipeline as picking the file yourself**
  (same detection, dedup, conflict review, and integrity checks — no separate code path), imports
  automatically once an account knows its format, and **sorts each file into an `imported/` or
  `failed/` subfolder** so your watch folder stays tidy. Any conflicts a sync/folder import finds go
  to the **same review window** file imports use. (This also fixed a latent crash that had stopped
  folder import from working at all.)


- **Each account now has one source of truth, so the same trades can't be counted twice
  (work 0120, increment 6).** If an account is fed by a broker **sync**, its "Import a file"
  button is now switched off (it shows "Fed by broker sync", and you can click it to learn why)
  — because importing a file for an account you also sync risked silently **double-counting**
  the same trades (inflating volume, P&L, and every tile for that account). You can deliberately
  switch an account's source between **Broker sync** and **Files I import** in **Import
  settings** at any time; the switch never deletes anything. If you import a file that overlaps
  dates already covered by your sync (or vice-versa), RiTrade now asks one clear question —
  **keep what's there and import only the new days**, or **replace those days** with the file —
  so no date is ever owned by two sources. (Accounts fed only one way are unaffected.)

- **You can now filter a dashboard by any combination of accounts (work 0121).** The filter
  bar's separate **Account** dropdown and **Type** buttons are replaced by a single
  **Accounts** picker. Open it to search your accounts and tick any combination, or tick a
  whole category header (Statement / Simulated / Platform / PropFirm) to select every account
  of that type — including ones you import or add later. Every tile re-scopes immediately to
  the accounts you choose (no reload), and picking everything is the same as "All accounts".
  When you're on a single account the picker shows that account's name, just like the old
  dropdown did. Your existing dashboards keep exactly the scope they had. (Account totals are
  always derived per account and then combined — never pooled — so a long in one account and a
  short in another are never matched against each other.)

- **You can now tell each account how to handle re-import conflicts (work 0120, increment 5).**
  Each account card has a new **Import settings** button. When a re-import brings in the same
  trade with a different number (a corrected fee or multiplier), you can choose, per account:
  **Ask me each time** (the default — flag it for review), **Skip duplicates automatically**
  (keep the copy you already have), or **Always use the newest version** (replace your saved
  copy). It's editable any time, and only the last option changes recorded numbers without
  showing you first — so it's clearly flagged and off by default. Nothing changes for existing
  accounts unless you opt in.

- **Imports are now double-checked, and the result tells you so (work 0120, increment 4).**
  After an import commits, RiTrade runs a quick integrity check: every row your file produced
  must be accounted for — imported, recognised as already in your records, flagged for review,
  or skipped by you. If it all adds up, the import summary now says so ("Verified: N fills
  landed, all accounted for"); if a row ever goes missing or gets counted twice — a silent
  data-loss bug — you get a clear heads-up before you trust the numbers, and "Cancel this
  import" is right there to back out. The check is plain row-accounting (no guesswork against
  the broker's own P&L figures, by design).

### Changed

- **The duplicate-review screen is redesigned around the decision you actually have to make
  (work 0120, increment 3).** When an import finds a trade that matches one already in your
  records but with *different numbers*, RiTrade now opens one clear, summary-first screen:
  "your import is in — N trades need a quick look," with a headline of how the file
  reconciled (N new, M already in your records, K need review). For each conflict it shows
  exactly *what* differs — "Commission $1.00 → $1.05", "Contract multiplier 1× → 50×" — and
  offers one plain choice: **keep what I have**, **use the new version**, or **keep both
  (two different trades)**. You can clear all the "keep mine" cases in one click, decide
  later, or **cancel the whole import** to undo everything it brought in. The old "Keep All"
  button — which silently kept two copies of the same trade and quietly double-counted its
  P&L — is gone; keeping two copies is now a deliberate, labelled choice. "Use the new
  version" correctly carries the new trade's fees across, and "keep both" gives each trade
  its own fees so neither is under-counted.

- **The duplicate-review screen now matches the approved design and is honest about exact
  copies (work 0120, inc-3 fidelity).** Opening the review from an account's duplicate badge
  now reads "N trades need your review — <account>" with the live count, instead of a bare
  title with no numbers. When a flagged trade is a **byte-identical copy** of one you already
  have, the card now says exactly that — "an exact copy of a trade you already have" — instead
  of wrongly claiming "different numbers", and its buttons say "current copy" / "identical
  copy". Cards now open **pre-selected with a sensible recommendation**: identical copies
  default to *keep mine* (zero change to your P&L), fee-only corrections default to *use the
  new one* (your journal mirrors what the broker actually charged), and anything that would
  rescale a trade's value — multiplier, currency, instrument type — is **never pre-chosen**;
  you must decide those yourself. The Apply button tells you exactly what it will do ("Apply
  48 choices — keep 46, replace 2") and stays off until every trade has a decision. A second
  one-click bulk action, "Use the new versions", joins "Keep my current versions", and
  "Cancel this import" now counts what it would undo ("...including the 5 new trades").

### Fixed

- **Filter pills now clear the way you expect.** Clicking the x on a top-bar filter pill
  (Yesterday, Short, a symbol) removes the pill immediately — before, the filter was
  actually cleared and your tiles updated, but the pill stubbornly stayed on screen until
  the next full refresh, which read as "the x does nothing". The accounts pill (e.g.
  "Platform") is now a real pill too: when an account selection is active it shows its own
  x that returns you to All accounts in one click — previously it could only be changed by
  reopening the filter bar. Also fixed: the x's hover colour no longer borrows the P&L
  loss colour, so it stays visible under the Tonal P&L style instead of fading into the
  pill on dark themes.

- **The per-tile "Text size" slider actually changes text size now — and goes up to 2x.**
  The slider saved its value but several tiles never read it: the Symbol Heat Map, the P&L
  Calendar, and the Trade Duration tile pinned their text to fixed pixel sizes, and on Stat
  Card / Multi-Stat tiles the overall Text size only took effect if you also moved one of
  the per-stat sliders off its default. All of those now respond — drag the slider and the
  tile's text follows, live, including tiles where you'd set a size long ago and nothing
  happened (your saved value kicks in on next load). The ceiling is raised from 1.5x to 2x
  across all text sliders. A few text-dense tiles (P&L Ledger, Slicer) still have fixed
  type and are queued for the same treatment.

- **The P&L Calendar tile works again, and tile settings windows got their dropdowns back.**
  Three casualties of the frontend modularisation surfaced together: the P&L Calendar tile
  failed to load at all (a stray "dashboards is not defined" error), the Stat Card and
  Multi-Stat settings windows offered an empty Metric dropdown (so neither card could be
  configured or re-pointed at a different number), and every tile's settings window was
  titled "Configure: undefined" instead of the tile's name. All three are fixed — the
  calendar renders and navigates again, the metric pickers list the full catalogue, and the
  settings title names the tile. The Slicer tile and Multi-Stat drag-to-rearrange had the
  same latent fault and were repaired before anyone hit them.

- **Symbol Performance no longer punishes your best symbols.** A symbol with only winning
  trades has no profit factor or average loser (there are no losses to divide by) — those
  cells show a dash by design. But sorting by PF treated that dash as zero, ranking
  all-winner symbols below everything, and the dash itself was coloured loss-red. All-winner
  symbols now sort to the top of the PF column and the dash is neutral. Also guarded a rare
  backend crash when a symbol's only trades are exact break-evens.

- **Importing a PropReports file now works (work 0112).** Bringing a PropReports XLS in
  through "Import a file" used to fail at the last step with an error mis-labelled
  "Session expired" — nothing imported. RiTrade now reads the file's round trips faithfully
  and breaks each one into its buy and sell, the same way the live broker sync does, so the
  import goes through and the "Ready to import" count is shown in actual executions. It also
  now recognises the account number from the file, and gives each closed trade its proper
  date (a stray timestamp bug that also affected synced trades).

- **Broker-synced (PropReports) accounts are now correctly protected from the double-count guard
  (work 0120, increment 6 follow-up).** The new "one source of truth per account" protection
  recognises sync-fed data by a marker on each row. PropReports' API sync was writing the wrong
  marker, so if you switched such an account to file-import and brought in a file that overlapped
  your synced dates, RiTrade failed to notice the overlap and could silently count those trades
  twice. Sync rows are now marked correctly, a one-time automatic data fix corrects any already-
  imported sync data on first launch, and the overlap question now fires as intended. (Accounts
  fed only one way were never affected.)

- **Re-importing a file you already imported no longer floods the duplicate-review queue
  (work 0120, increment 2).** Previously, re-importing an overlapping broker export (moomoo's
  rolling-window History CSV being the classic case) pulled every already-imported trade out
  of your records and into the review queue to be cleared by hand. Now that each trade has a
  trustworthy fingerprint (increment 1), RiTrade recognises an exact re-import as the same
  trade and simply skips it — your existing data is left untouched and the import just reports
  "N already in your records." The review queue is now reserved for genuine conflicts: the
  same trade re-imported with *different* numbers (a corrected fee, a fixed contract
  multiplier, a currency change), which is the only case that actually needs your decision.

- **Re-importing an overlapping broker export no longer silently double-counts trades
  (work 0120, increment 1).** For brokers that don't give each fill a unique order ID —
  TradingView, DasTrader (Local CSV), Webull SG (CSV), and the Warrior simulator —
  RiTrade used to tell two fills apart by their position in the file. Re-exporting the
  same trades in a different order (e.g. moomoo's rolling-window "History" export, or any
  re-download) made already-imported fills look brand new, so they were imported twice
  with no warning. Each fill now gets a stable fingerprint that doesn't depend on file
  order, so a re-import is correctly recognised as the same trades — while two genuine
  same-second fills at the same price still stay distinct and both survive. Identity is
  now computed in one shared place for every broker (the per-fill and the duplicate-check
  recipes, previously written twice, were merged). Brokers that *do* carry a real order ID
  (including moomoo) are unaffected — their data is identical to before. On first launch
  after this update, fills from the four affected brokers are cleared and you'll be told
  exactly which files to re-import (named, per account); everything else is untouched.

### Changed

- **Trade storage unified: executions are now the single source of truth (work 0105).**
  RiTrade previously stored trading data in two different shapes depending on the broker —
  per-fill for some, per-round-trip for others — which meant fees lived in two places and
  cross-broker numbers didn't always line up. Now **every** broker's data lands as
  executions (fills), and trades, positions and P&L are derived from them on demand. Files
  that come as completed round trips (PropReports, Webull order CSV, and generic CSVs you
  mark as round-trip) are **split into a buy and a sell on import**, sharing one combined
  fee — so nothing is double-counted and no leg is faked. Your existing data is migrated
  automatically on first launch, with a pre-migration backup and a P&L-conservation check
  that aborts the migration rather than ship numbers that don't add up. Equity P&L is
  unchanged to the cent. Groundwork for futures/options/forex/crypto (a per-instrument
  contract multiplier) is now in the schema. For round-trip imports, the confirm step shows
  the resulting buy + sell and explains the split in plain language; generic files are asked
  once whether each row is a single fill or a complete round trip (never guessed), and a
  round-trip mapping requires you to map the Long/Short direction before importing.

- **Recognised-broker imports are now transparent and consistent (work 0091).** Every
  recognised broker file — DasTrader (AutoReport and Local), TradingView, Webull SG
  (Order History CSV), Warrior Trading, and moomoo — now shows a clear "here's how we'll
  read your file" confirmation (your column → what it becomes → an example from your file)
  before anything is imported, with fees landing in the right place. Under the hood each
  reader was split into a transcribe step and one shared interpret step, so every broker
  is read the same way and the same fix benefits all of them. Imports are byte-for-byte
  identical to before, so re-importing the same file still safely skips duplicates.
  Fixes shipped alongside:
  - The "Check file format / which row is the header?" step no longer pops up for a
    broker RiTrade already recognises — it only appears for genuinely unknown files.
  - Webull SG CSV imports no longer fail on the new storage model.
  - DasTrader Local files (which contain only a time, no date) now reliably ask you for
    the trade date on every import and apply it correctly.

- **Imported trades now show the real file name they came from (work 0116).** Previously
  an imported fill recorded an internal temp name like `ritrade_import_baas8ev8.csv` —
  so the "Source File" column (e.g. in the duplicate-fills review) was meaningless. Now
  it records your actual file name (e.g. `AGRI fills.csv`). The "name your file with a
  date" convention for time-only files (DasTrader Local) also works again, since it reads
  the real name. The file picker also now accepts `.xls` and `.pdf` (PropReports / Webull),
  which it was previously hiding.

- **Fixed moomoo imports losing shares on multi-fill orders (work 0118).** A moomoo order
  filled in several small lots at the same price within the same second (very common) had
  its identical partial fills mistaken for duplicates of each other — so one was dropped
  and the order came in short (e.g. a 50-share order imported as 49), and the legitimate
  fills cluttered the duplicate-review. Each partial fill is now tracked distinctly, so
  the full order imports correctly. (Re-import any moomoo file that was imported before
  this fix — delete the old copy first — to correct already-imported data.)

- **Filter-bar dropdowns now match the active theme.** The Account and Period
  dropdowns rendered their open option list with the operating system's default
  colors — a white panel with a washed-out, near-invisible group heading (e.g.
  "Simulated") — instead of the app's theme. The options and group headings are now
  themed from the same tokens as the rest of the UI, so the list matches whichever
  theme you're on (all ten, light and dark), with the native popup chrome switching
  to light/dark to suit.

### Added

- **Import wizard: manual column-mapping screen reworked (work 0091).** The screen
  you see when mapping an unrecognised / generic CSV is clearer and safer: RiTrade's
  fields now read in plain language ("Date", "Time", "Commission", "ECN fee" — not raw
  `filled_at`/`comm`/`ecn_fee`); the timestamp is mapped as **two rows, Date and Time**,
  so a file with separate date and time columns maps cleanly (RiTrade recombines them),
  and a single combined column still works; and a **live preview** now shows the first
  rows exactly as they'll be stored — combined date+time, "Buy", "$187.50", total fees —
  updating as you map, instead of a box that never filled in. A manually-mapped file is
  now always imported as executions (fills) and fed to the FIFO engine, fixing a case
  where such imports could silently commit zero rows.

- **Import wizard: unified mapping-confirmation surface (work 0091/0067).** When
  RiTrade recognises a broker file, the wizard now shows one screen —
  `surf-mapping-confirm` — that both claims the provider and proves it with a
  field-centric mapping table ("In your file" -> "Becomes" -> "Example from your
  file"), so you can see exactly how each column will be read before importing.
  Three states: clean (State A), a non-blocking amber heads-up when an optional
  column (e.g. an ECN-fee) is absent (State B), and a blocking red gap with
  "Match the columns myself" when a required column is missing (State C). If the
  guess is wrong, "This isn't [Provider]" offers the ranked runner-ups (with
  confidence %); a hand-mapped, named format is remembered as a global custom
  signature and auto-recognised next time on any account. Backend wires the
  readers' `field_map()` into the import-preview response (deriving a per-field
  ok/missing_optional/missing_required status). Also fixed: moomoo CSV exports
  carry a UTF-8 BOM that previously made the first column ("Side") read as
  missing — every moomoo import would have been falsely blocked; the reader now
  opens with `utf-8-sig`. The wizard dialog is also now top-anchored: its header
  and step dots stay at a fixed position and the panel grows downward (with
  internal scroll for tall steps) instead of re-centering and jumping each time a
  step's content height changes.

- **Imports now preserve every fee a broker reports.** Per-fill records
  previously stored only commission, TAF and tax, so other fee components were
  silently dropped at import — e.g. moomoo's Settlement Fees and CAT Fees, and
  ECN/SEC/NSCC fees on other brokers. `trade_fills` now carries `sec`, `nscc`,
  `ecn_fee`, `clr` and `cat` as well, the FIFO engine prorates them into each
  round-trip alongside commission, and net P&L now reflects the complete fee
  total. Existing imports are unaffected (the lost fees can't be recovered
  retroactively — re-import to capture them); new imports are complete. Also:
  `tax` is now a mappable/auto-mapped field for generic files, and a column-
  mapping screen is no longer shown for already-recognised providers. Redesigned the add/edit ledger entry
  modal into a first-class form with a four-type model (Deposit / Withdraw /
  Payment / Receive) that makes accounting intent explicit. The form features a
  labelled type selector row with contextual per-type notes, a context-sensitive
  FROM/TO movement block (locked context account on one side; picker or free-text
  on the other depending on type), multi-document attachment (replacing the old
  single receipt_path), and a delete confirmation overlay nested inside the panel.
  Schema migration adds `ledger_documents` table (ON DELETE CASCADE), drops
  `category` and `receipt_path` columns via SQLite table rebuild, adds `purpose`
  (same vocabulary as old `category` keys) and `mirror_entry_id` (ON DELETE SET
  NULL), and data-migrates `entry_type` values (paid->Payment, received->Receive,
  invest->Deposit, withdraw->Withdraw). Backend: `LEDGER_CATEGORIES` renamed to
  `LEDGER_PURPOSES`; `GET /api/ledger/purposes` replaces `/api/ledger/categories`
  (alias retained); `POST /api/ledger` and `PUT /api/ledger/<id>` create/update
  mirror entries atomically; `DELETE /api/ledger/<id>` deletes mirror atomically;
  document upload/delete endpoints added (`POST/DELETE /api/ledger/<id>/documents`).
  Frontend: `table-ledger.js` fully rewritten; `table-pnl-ledger.js`,
  `table-transactions.js`, and `chart-expense-donut.js` updated for new field
  names and entry_type values; `tiles.css` updated with `.le-*` class system
  replacing old `.ledger-modal-*` styles. LE workflow registered.

- **Universal Smart Import Interpreter + Warrior Trading Simulator (work 0035-E).**
  New 8-layer import pipeline (`src/importers/universal/pipeline.py`) that is
  format-agnostic: extraction readers normalise raw bytes to canonical row dicts;
  the pipeline handles header detection, account discovery, column identification,
  coverage checks, validation, conflict detection, and confirmation. First reader:
  Warrior Trading Simulator CSV (UTF-16 LE, 7-column headerless, positional mapping).
  Existing Webull and PropReports importers wrapped as extraction readers (Option A,
  no refactor). Fill-hash formula extended with `|row:<row_index>` tiebreaker when
  `order_id` is absent. Import wizard: 9-modal sequential-replace state machine at
  z-260 (Modals A, 1, 2A/B/C, 3, 4, 5, 6, 7), opacity crossfade transitions (no
  translateX), back navigation, cancel confirmation, loading/error/cache-miss panels,
  step indicator with fixed dot count. Full accessibility pass: ARIA dialog/progressbar
  attributes, focus trap, focus restore, fieldset grouping for radio/checkbox groups.
  Preview cache gains 30-minute TTL eviction. Bulk conflict detection replaces N+1
  queries. `sync_log` index added. Format mismatch on folder sync writes
  `needs_review` entry instead of aborting.

- **FIFO integration (work 0035-D-B).** Webull SG import now routes through the fill
  engine end-to-end: preview computes a file-hash guard (409 on re-import), commit
  stores fills in `trade_fills` via `_insert_fills`. All five tile query endpoints
  (P&L by month, symbol, hour, weekday, duration) branch on `delivers_fills` and
  compute P&L in-memory from FIFO-paired fills when the account filter resolves to a
  fill-level account. Tile responses include a `pending_duplicates` flag; affected tile
  headers show an amber warn icon (clickable, opens the review modal). Duplicate review
  modal (`GET /api/fills/duplicates/<id>`, `POST /api/fills/resolve`): groups duplicate
  fills by hash, per-row Delete / Keep / Keep All, auto-promotes the lone sibling to
  active on resolve, updates the account-card badge count on each action. Account cards
  show an inline amber pill ("N duplicate fills") beside the sync/edit buttons when
  pending duplicates exist.

- **FIFO foundation (work 0035-D-A).** Webull SG data now stored as raw execution fills
  in a new `trade_fills` table instead of pre-matched round-trips in `trades`. A shared
  FIFO engine (`src/importers/fifo_engine.py`) replaces the private `webull/fifo.py`.
  Migration 2 wipes existing Webull SG rows (all re-importable from source PDFs) and
  creates `trade_fills` with duplicate-detection and tombstone support. Provider registry
  gains a `delivers_fills` flag on all entries; `moomoo` stub added.

### Fixed

- **Generic / manually-mapped CSV imports were silently zeroing every fee (work
  0091).** When you mapped columns yourself (a generic CSV, or any column
  override), the commit path rebuilt each fill with only symbol/side/qty/price/
  time and dropped all fee fields — so commission, SEC, TAF, NSCC, ECN, clearing,
  CAT and tax all imported as 0. The override now runs through a single shared
  interpreter (`apply_mapping`, the new "Layer 2" of the transcribe/interpret
  reader split) that carries every fee through to the stored fill, so a
  hand-mapped import records the same complete fees as a recognised-provider one.
  Core values (symbol/side/qty/price/time) are produced identically to before, so
  existing imports still de-duplicate correctly on re-import.

---

## Verify

SHA256: `ad6546e4090448f17a37c7d06c083ba4336e11e71bd7ef8d769be387ec802137`

## License

Proprietary - [RiTrade EULA](https://github.com/RiTrade/ritrade-releases/blob/main/EULA.md). The installer requires EULA acceptance.