# RiTrade 1.2.57

_Released 2026-09-01_

### New features

- Import now checks the account number in your file against the account you chose.
- Added an account picker for a file that covers more than one account.
- Added a date step that asks which day a file covers when its rows carry times but no dates.
- Set the day for every waiting file in a watched folder on one screen.
- Added a bar on the import result screen showing where every row of your file went.
- PropReports: the connection now imports each buy and sell instead of your broker's matched trades. A position built from five buys is stored as five buys, not as one at an average price.

### Improvements

- The account settings page now shows the confirmed account number, the file layouts the account accepts, and whether a mismatch stops an import or warns.
- Show what changed and ask before importing a file that no longer matches its usual layout.
- List the rows RiTrade could not read, with a reason for each, on the import result screen.
- Count the rows left out when you keep your own dates, on the import result screen.
- Say why an import stopped or imported nothing.
- Import screens now count the rows in your file and what RiTrade stored from them, never trades.
- Say on the import result screen when RiTrade split a whole trade into a buy and a sell.
- Call two versions of the same record conflicts on every screen that shows them.
- Label overlapping counts as previously imported, and say where the numbers came from.
- The delete screen now states the accounts and dates it covers, and that everything else stays.
- An account now takes its trades from your broker sign-in or from files, not both.
- Adding a second account on the same broker now names the account already using it.
- Refuse a file that records trades differently from the rest of the account, before anything is saved.
- Warn when you pick a watched folder another account is already using.
- Accounts that shared a watched folder have it cleared on this update. Pick a folder again for each.
- Read the day you typed back to you before the import, and flag a date far from today.
- Name which of two columns is wrong when both are pointed at the same thing.
- Name the symbol and the reason for each whole trade RiTrade could not read.
- Webull: report fees on your statement that do not add up, naming the trades and the amount.
- PropReports: show your own column names, and stop offering to read a recognised export as another broker's file.
- The account import settings page now shows what the account is waiting on when you open it.
- Remove the Keep importing option from the cancel confirmation on a file RiTrade has refused.

### Bug fixes

- Fixed Back in the import wizard clearing the day, column and account number answers.
- Fixed a stock returning under a new symbol being stored twice and counted twice.
- PropReports: fixed a trade held past midnight closing on the wrong day and being refused.
- Fixed "All clear" showing over an import that lost some of your rows.
- Fixed a watched folder file waiting on a date or symbol answer being filed as a failure.
- Fixed the buttons at the top of RiTrade doing nothing in the first moment after it opens.
- Fixed connecting your broker taking over an account set up for files and stranding its trades.
- Removed Sterling Trader and a duplicate Webull SG, which gave accounts that refused every file.
- Fixed the account type badges (PROPFIRM, STATEMENT) being unreadable on six of the eleven themes.
- Fixed a watched folder reporting a clean import over one that failed RiTrade's own check.
- Fixed a file from a known broker being read by columns you once matched by hand.
- PropReports: fixed an export saved as CSV failing to import like the Excel one.
- moomoo and Webull SG: fixed the row count on the import result screen.
- Fixed the conflicts review button missing on some files, and showing a number the review does not list.
- Fixed a sync reporting no new data when it could not read the rows your broker sent.
- Fixed a file with renamed columns and times but no dates failing to import.
- Fixed a file of completed trades with a time at each end failing to import.
- Fixed the column matching screen hiding why your file was refused, or finishing with nothing.

## Verify

SHA256: `a6615737c0924254e3fe8ef7979c16a4539fc260b013ca80234857a9c5823113`

## License

Proprietary - [RiTrade EULA](https://github.com/RiTrade/ritrade-releases/blob/main/EULA.md). The installer requires EULA acceptance.