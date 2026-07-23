# RiTrade 1.2.37

_Released 2026-07-23_

### New features

- **A new tile shows you the money, plainly: Symbol Performance (P&L).** One bar per symbol, sized by what that symbol's closed trades made or lost you. One number runs the whole tile: pick Net P&L (after all costs) or Gross P&L (before them) in the tile's settings, and the filter, the order and the bars all read that same figure. Narrow the list to your winners, your losers, or the symbols that broke even; put your biggest gain first or your biggest loss first; and flip between Net and Gross to see which symbols your costs move from one side to the other.

### Improvements

- **The Symbol Performance (Trades) tile now reads one way: what one trade in each symbol earns you.** Every bar is the same number -- dollars per trade, after fees or before them, your choice -- so the ranking and the bars always agree. Your best-paying symbols sit at the top and your worst bleeders at the bottom; flip the sort to lead with the cut list instead. A thin strip beside each name shows how often that symbol wins -- and when a symbol wins most of its trades yet still loses money, the row wears a "WINS OFTEN, LOSES BIG" tag and the footer adds up what those symbols are costing you: the single most expensive pattern in a trading book, now visible at a glance. Narrow the ladder to your winning, losing or near-breakeven symbols, and symbols with fewer than five trades stay out by default, so a lucky short run can't fake an edge.
- **The two symbol tiles now say exactly what they show.** The chart formerly called "P&L by Symbol" is now **"Symbol Performance (Trades)"** and the per-symbol table is now **"Symbol Performance (Stats)"**, so the family is easy to tell apart when adding tiles. Any custom titles you have typed on your own tiles stay exactly as you typed them.

### Bug fixes

- Removing a dashboard tile now asks you to confirm first, and names the tile it will remove, so a single mis-click can no longer wipe a tile you meant to keep -- along with its settings, filters and place on the dashboard.
- Your very first file import into an account no longer stops you with a false "Format has changed" warning - that warning now appears only when you really do have saved column settings that the new file differs from. A genuine format change still shows the same comparison as before.
- When you match up your columns for a file that records whole trades, the Sample column now shows real values from your own file next to each choice - the value the import will actually use, or a dash when it can't be sure - so you can trust what you see before importing.

---

## Verify

SHA256: `f647b59f70590b79c90edf73e94620fded6318a9485fdb7e3d34de8a5c7259c2`

## License

Proprietary - [RiTrade EULA](https://github.com/RiTrade/ritrade-releases/blob/main/EULA.md). The installer requires EULA acceptance.