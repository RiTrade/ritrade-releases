# RiTrade 1.2.78

_Released 2026-10-31_

### New features

- Add your own dated fee lines in account settings, charged on each fill, order or trade.
- RiTrade counts the fees you enter in every net figure on that account.
- See your fees beside the broker's on Costs & Friction, Daily Summary, P&L Calendar, and the trades and per-symbol tables.
- RiTrade sets the broker's figure aside when your fee line covers the same fee, so each fee counts once.
- Change, stop or delete a fee line in the account's Fees part, and see what each line charged.
- Pick Before or After fees in the account's Fees part, and RiTrade saves your choice at once.
- When you import broker fees your lines already cover, RiTrade names the fee type and how many buys and sells.
- See every file you imported and every sync on the account card, newest first.
- Delete a single import from its row on the account card.
- See every row RiTrade could not read, with its line and reason, from the account card, Sync all and History.
- Set money to whole amounts, 1 to 4 places or your broker's places in Appearance > Money display.
- Give any money tile its own places on its Design tab.

### Improvements

- RiTrade rounds money the same way on every screen, and decides wins and losses to the cent.
- RiTrade shows averages to at least 2 places at every money setting.
- RiTrade now shrinks wide figures on the P&L Calendar, Symbol Heat Map, Multi-Stat and Stat Card to fit.
- Hover a figure shown only by its sign to read it in full.
- RiTrade now shows a day of fee rebates the same way on every screen.
- RiTrade checks each fee value you enter before it saves the line.
- RiTrade applies your fee lines as soon as you import trades that show the account's currency.
- Until an account's currency is known, the Fees part says your lines count once you import files in one currency.
- If you change an account's currency, RiTrade pauses its fee lines until the currencies match, and keeps their amounts.
- Symbol links now asks whether two symbols are one stock when an account holds trades under both.
- The menu shows how many Symbol links questions you have left to answer.
- For a file with one row per trade, column matching now suggests the entry, exit and Long/Short columns.
- The account card, Sync all and History now say what each import figure counts.
- The account card says when an account holds no imported buys or sells.
- Sync all shows the whole account name and keeps its status on one line.
- The sync log now names the accounts a stopped Sync all did not reach.
- The account card and sync log now say "Could not finish" when a sync cannot run.
- Account setup shows how many steps your account needs, and the last step's button says Done.
- You can now choose Try again if a live connection's sign-in details fail to load.
- The P&L Calendar and Monthly P&L now leave the win rate empty for a month of only breakeven trades.
- The P&L Calendar now marks weekends without trades with faint diagonal lines.
- Symbol Performance now says when you have no finished trades yet.
- The faintest text is easier to read on the Slate, Ocean and Graphite themes.

### Bug fixes

- Fixed Total Net and each trade's net differing from your broker's own figures.
- Fixed a fee of exactly half a cent back to you showing as neutral instead of a rebate.
- Fixed $0.00 amounts showing green or red on charts and tables.
- Fixed the ledger entry counts (deposits, draws, expenses, payments in) showing as 0.00 instead of whole numbers.
- Fixed the P&L Calendar's day popup running past the bottom of the window.
- PropReports: fixed short sales being refused, so trades that include them now close.
- Fixed importing a file again raising a new conflict for a row you have not yet decided on.
- Fixed Keep both on a review card keeping different amounts from the ones the card showed.
- Fixed the column matching and fees steps previewing rows other than the first ones RiTrade will import.
- Fixed the fees question being skipped after watched-folder scans and long Accounts panel visits.
- Fixed the import wizard not opening fresh after you closed it while RiTrade was still reading a file.
- Fixed the sync log showing "Finished" for a Sync all that stopped part way.
- Fixed the account card and sync log quoting your computer's errors for watched-folder files RiTrade could not import.
- Fixed the sync log hover text quoting your computer's error when RiTrade cannot open a watched folder.
- Fixed hard-to-read text on coloured P&L Calendar days, on every theme.
- Fixed the sync log's Stopped and Needs attention labels being hard to read on light themes.
- Fixed the account card's Re-link account link being hard to read.

---

## Verify

SHA256: `ed58e3f1d2fb4a964d4b374385754427589abc392c4997f389ccfe12fab090cd`

## License

Proprietary - [RiTrade EULA](https://github.com/RiTrade/ritrade-releases/blob/main/EULA.md). The installer requires EULA acceptance.