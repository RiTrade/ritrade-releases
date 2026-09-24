# RiTrade 1.2.60

_Released 2026-09-24_

### New features

- RiTrade now asks which timezone your broker's times are in, once per account.
- Added an Open Positions tile: every position you hold, with size, entry price and date.

### Improvements

- The import screens are rewritten in a clearer, more consistent voice.
- Import error messages now name your file and what to do next, not an internal code.
- The import screen now shows your file's own text beside what RiTrade read from it.
- Broker sync now checks every trade before writing any of it, the same as the import wizard.
- A watched folder now waits for one timezone answer, then imports every queued file.
- RiTrade now asks which column holds the fill time when more than one is possible.
- Buttons on the import screens now say the outcome: "Use this signature", "Choose another file", "Cancel import".
- The provider list now calls the fallback format "Custom CSV".
- Account screens (cards, add-account wizard, Import settings, delete dialogs) are rewritten in one consistent voice.
- Timezone names are now consistent across the account form, the picker and broker sign-in.
- Account and delete screens are now fully keyboard accessible, with visible focus and labelled fields.
- The delete dialog is taller and now states "cannot be undone" once.
- Removing an account with saved broker signatures now explains they still work on other accounts.
- Dashboard tiles now update the moment an import, purge, undo, delete, restore or ledger change lands.
- A held position now shows its own row on the by-symbol tiles, with money made and no win/loss verdict.
- ROI, day stats and heat map hours now show an empty value, not a false zero.
- Sortable tables now sort your whole selection and warn when a selection mixes currencies.
- Money now reads one way everywhere: sign, placement and thousands separators match across the dashboard.
- Heat map numbers are now larger and read clearly on every cell colour.
- Tile titles and table headers now print as written instead of in capitals.
- Dashboard forms (Configure, New dashboard, Edit dashboard) are now fully keyboard accessible.
- Add a tile now shows real descriptions and real columns instead of invented figures.
- Narrow Trades and Transactions tables now keep the most useful columns and flag a hidden sort column.
- Long account names and symbols are now shortened in the middle so similar accounts stay distinct.
- Changing a transfer's other side now asks first and names both accounts and the amount.
- Filling in a transfer from either side now keeps everything you already typed.
- Ledger entries now show each account's currency beside the amount.
- The P&L Ledger now shows a Trading plus cash flow line that stays visible while you scroll.
- The Expense Breakdown now shows five purposes by default, up to twenty.
- A capital purpose such as Owner's Draw is now offered only on a deposit or withdrawal.
- Capital Utilisation's empty state now names only what you can actually do next.
- Settings screens (Danger zone, Appearance, Backup and restore, Symbol links, fees, updates) are rewritten in one consistent voice.
- Settings screens are now fully keyboard accessible, with named fields and screen-reader announcements.
- The sign-in page now uses your theme colours and shows a clear focus ring.
- The Add ledger entry button is now visible on the Ledger Entries tile without hovering.
- Text and links are easier to read on the Carbon, Ember, Midnight and Slate themes.
- The User Guide now matches today's labels and covers password reset, Trades and Transactions.

### Bug fixes

- Fixed backup restore failing for traders who never saved a broker sign-in.
- Fixed restore refusing silently, without saying why, including when another restore was already running.
- Fixed a double click on a delete preview's Delete button deleting twice.
- Fixed broker signature and symbol link timestamps showing UTC rather than your local time.
- Fixed Tab leaving the Accounts panel when its Danger zone was closed.
- Fixed the sign-in page promising a key export could recover a lost key.
- Fixed a broker signature match losing a file's own name after import.
- Fixed a narrow window discarding your dashboard tile layout.
- Fixed Warrior Trading exports being refused as unreadable.
- Fixed new Funding accounts asking where their trades come from.
- Fixed Funding accounts accepting the change while still holding trades.
- Fixed a lost import showing an internal code as its heading.
- Fixed the leave-guard on an unsaved form skipping the close button in the tab order.
- Fixed Cancel on Import settings discarding a changed setting without asking.
- Fixed a watched folder reading only CSV files, missing PDF and XLS.
- Fixed a saved broker signature that could not be forgotten.
- Fixed the calendar printing a losing month, or a negative Gross, without its minus sign.
- Fixed Expectancy landing a cent off Avg Trade Net on a mix of accounts.
- Fixed the calendar month total, equity curve and rolling P&L landing a cent or two off Total Net.
- Fixed a zero, or a rounded-to-zero figure, showing a stray minus sign or loss colour.
- Fixed Multi-Stat figures (Edge at a Glance, Luck vs Skill) truncating with an ellipsis.
- Webull SG: fixed statement PDFs being read differently from every other broker, with fees miscategorised under commission.
- Webull SG: fixed a trade whose time wrapped a line being dropped without warning.
- Fixed a PDF past RiTrade's size or page limit reading as an empty file.
- Fixed an account refusing an unreadable file rather than asking how to read it.
- Fixed a watched-folder file RiTrade could not prepare for import stopping the whole run.
- Fixed a trade that finished at exactly zero counting as a loss.
- Fixed the daily summary's two loss counts disagreeing with each other.
- Fixed a selection with nothing won or lost showing 0% rather than no win rate.
- Fixed a failed sync naming an internal account number rather than your account.
- Fixed an unexplained broker sync failure wrongly saying RiTrade could not identify your account.
- Fixed the account card and duplicate warning showing raw error codes.
- Fixed three tiles counting a held position's money into the wrong figure.
- Fixed a ledger entry saving the literal text "[source]" as its description.
- Fixed the P&L Ledger's sections not adding up to their own totals.
- Fixed Net trader P&L reading $0.00 while every other P&L Ledger row read empty.
- Fixed the Expense Breakdown counting money you moved to yourself as an expense.
- Fixed a ledger entry between your own accounts not saving as a transfer on both sides.
- Fixed Capital Utilisation counting an in-view transfer as income or an expense.
- Fixed a transfer between accounts in different currencies being allowed to save.
- Fixed starting balance being counted twice on an account that already had Initial Capital.
- Fixed a ledger document over 10 MB, or the wrong file type, being accepted.
- Fixed the calendar losing a symbol filter's chosen month.
- Fixed a calendar cell being cut off when Text size was turned up.
- Fixed the last import screen claiming nothing would change when part of a file was still new.

---

## Verify

SHA256: `53b3907919adbcd35e0e537b654fc33d750d2e96be7a485a4360ad8ebeae8e37`

## License

Proprietary - [RiTrade EULA](https://github.com/RiTrade/ritrade-releases/blob/main/EULA.md). The installer requires EULA acceptance.