# RiTrade 1.2.19

_Released 2026-07-08_

### New features

- **Import a TradingView file that holds more than one account, and pick which accounts
  to bring in.** When a TradingView export contains trades from several broker accounts,
  the import now asks which ones you want, and only the trades for the accounts you tick
  land here. Before you commit, the confirm screen shows the real count ("import 4
  trades") and a calm note underneath — "Set aside 5 that belong to accounts you didn't
  select" — so nothing rides in unnoticed and nothing vanishes without a trace. The
  set-aside trades aren't lost: import the file again and tick that account to bring them
  in. A single-account file, or the account-less simulator export, imports exactly as
  before with no extra step.

- **Record your real broker account number against an account — and see it on your
  dashboard.** When you import a file, the "Confirm account" step now asks for your
  broker account number and remembers it; you can also set or fix it any time from the
  account's settings. It shows under the account's name on the account card, and — when
  you switch on "Show account number in dashboard" — next to the account name on your
  dashboard. It's purely a label for your own records: it never changes which account
  your trades belong to, and typing a number that happens to match another account can
  never merge the two.

### Improvements

- **When an import can't read some of your rows, it now tells you which ones and why —
  instead of silently dropping them.** If a file has rows but a few can't be brought in
  because a required value (a date, a quantity) isn't in a shape we can read, the import
  screen now shows exactly which column is the problem, an example of the value that
  tripped it, and how many rows it affects — grouped so a whole bad column reads as one
  line, not five hundred. The rows that read cleanly still import; nothing in your file
  or your journal is touched, and you can open the file, fix those cells, and import
  again. A genuinely empty file (a quiet month with no trades) stays quiet, with no
  false alarm. This replaces the old silent "0 rows to import" that left you guessing.

- **Groundwork under the hood so RiTrade is steadier, and future features and fixes ship
  faster and more safely.** We reorganised a large amount of the app's internals this
  release — every dashboard tile and the whole import and reporting engine were moved
  onto a cleaner, more modular footing — with your numbers proven identical before and
  after, so nothing you see or rely on changed. One tangible win came out of it: a slow
  memory leak where old charts piled up as you refreshed your dashboard is now closed, so
  the app stays lighter the longer you leave it open.

### Bug fixes

- **Finishing an import no longer crashes.** In some cases — most often when you'd
  started an import, stepped back to change a setting, and come back to it — pressing the
  button to bring your trades in could fail and import nothing. Now that final step
  completes and lands your trades; and in the rare case where the import can no longer be
  read, it tells you plainly to start the import again instead of failing, with nothing
  half-written to your journal and no trade ever filed to the wrong account.

- **A PropReports export you opened and re-saved in a spreadsheet app now imports every
  trade.** If you opened your PropReports `.xls` in Excel, LibreOffice or OpenOffice and
  saved it, the app quietly rewrote the dates into a format the importer couldn't read —
  so the file imported as **zero trades, with no warning**, even though all your trades
  were still in it. Those dates are now read correctly, so a re-saved file imports its
  full trade history exactly like the untouched export.

- **When a few rows in a mapped CSV can't be read, the good rows now still import.**
  Importing a file where a couple of rows had an unreadable required value used to fail
  the whole import — you got nothing. Now the readable rows import, the unreadable ones
  are listed for you to fix, and the count you see matches what actually comes in. (The
  "review the rows we couldn't read" toggle also now has clearer contrast.)

- **The "Confirm account" step during import no longer throws your entry away.** It
  looked editable, but the broker account number you typed there was silently
  discarded — and the step showed a code that meant nothing to you. Now the number
  you type is saved and shown back to you, and that internal code is never put on
  screen.

- **The "Show account number in dashboard" switch now does something.** It saved your
  choice but never actually displayed anything. Switching it on now shows the
  account's number next to its name on the dashboard; when an account has no real
  number yet, it shows just the name rather than an internal code.

- **Deleting a ledger entry no longer fires the delete more than once.** When you
  confirmed a delete, the same delete could be sent several times over; the entry
  was still removed, but the extra attempts failed quietly in the background. A
  confirmed delete now happens exactly once.

- **Clearing your filters now also clears the Slicer's symbol box.** After you chose
  "Clear all filters", the Slicer could still show the symbol you last typed even
  though it was no longer filtering by it. The box now empties so it matches what
  is actually filtered.

- **Tile settings checkboxes now remember whether they were on.** A handful of tiles
  have a checkbox in their settings (for example "Show trade count labels"). If you
  switched one off and reopened the settings, it wrongly appeared switched back on —
  your choice was always applied to the tile, but the checkbox itself forgot it. It
  now shows the setting you actually saved.

- **The sign-in page no longer shows a dead-end message instead of the password box,
  and its wording is clearer and honest.** In the rare case where your data was left
  unencrypted, the sign-in screen could replace the whole page with an information
  notice and then fail — leaving you no way to sign in at all. That notice now appears
  as a banner above a fully working sign-in form, so you can always get in. The messages
  you see when there is something unusual about your data now speak plainly and no
  longer point you to a place you cannot reach while signed out — in particular, the
  "we can't open this data on this computer" message no longer suggests a recovery step
  that wouldn't actually restore access, and small decorative symbols were replaced with
  plain text.

---

## Verify

SHA256: `a2ebc7edb4c1810101c91913718ec61db0aeb927da7ead095620e650bba9de89`

## License

Proprietary - [RiTrade EULA](https://github.com/RiTrade/ritrade-releases/blob/main/EULA.md). The installer requires EULA acceptance.