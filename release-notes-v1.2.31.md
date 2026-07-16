# RiTrade 1.2.31

_Released 2026-07-16_

### Improvements

- The good / caution / bad colours on your quality tiles -- Win Rate, Profit Factor, and any metric that carries a health rating -- now follow the colour style you have chosen instead of always showing as a bright green / amber / red stoplight. On the muted styles (the two-shade Tonal look most of all) they settle into your own palette, so they no longer look like they wandered in from another app; and on the colourblind-friendly style they switch to a blue / amber / vermillion set, so a red-green colourblind trader can still tell a strong number from a weak one at a glance. Your profit-and-loss figures are untouched, and every quality colour stays comfortably readable on its tile.

### Bug fixes

- Your profit-and-loss numbers stay clearly readable whatever colour theme and P&L style you pick. On some styles -- the two-shade Tonal look most of all, but also the colourblind-friendly and red-up styles -- a loss, a Short position tag, or the little chart previews in the "Add a tile" picker could fade until they were nearly invisible against a dark row. Now your figures, tags and previews stay legible on every combination, a loss still reads as a loss and a gain as a gain, and the style you picked still looks like the style you picked.
- The app's own colours hold up on every theme too, so nothing it needs to tell you gets lost against the background. Its error and warning messages -- and the failure pop-up that appears exactly when something has broken -- were sometimes too close in shade to the panel behind them to read; the green "saved" and "all accounted for" confirmations had washed out on the light themes; the labels on the main action buttons strained to be read; the favourite-account star all but vanished on a white account card; and a delete control could briefly stop looking like danger. All of these now stay clearly legible whatever theme and P&L style you are using -- including Graphite, whose lighter panels had been the hardest case of all -- so a warning still reads unmistakably as red, a confirmation as green, and a delete button as danger.
- When something behind the scenes goes wrong, RiTrade now handles it gracefully instead of leaving you stranded. A hiccup loading one part of your data as the app starts no longer keeps the whole app from opening -- it starts with what it has. A failed action -- deleting a dashboard, saving your layout, adding or removing a tile, clearing an account's trades, deleting a ledger entry, reordering stats, saving a tile's settings -- now tells you plainly that it did not go through, instead of silently doing nothing or leaving a blank tile. And when a problem does slip past, the automatic problem report now captures what actually went wrong, so it can be fixed faster.
- RiTrade now reopens on its own after it installs an update. Previously an auto-update swapped in the new version successfully but left the app closed, so it looked like RiTrade had vanished and you had to find and relaunch it yourself. Now the app comes back automatically to the updated version once the update finishes -- the update feels like a brief close and a reopen rather than a quit. (Takes effect on the next update after this one.)
- Re-importing a saved custom format that records whole trades (one buy-and-sell per row, with a Long / Short column) now works. Previously, bringing in a second file of a format you had already imported once dead-ended at "we need a direction column" -- even though RiTrade already knew your columns from the first import -- so you could never add more trades in that format. Now RiTrade recognises the saved layout and the import completes, splitting each round trip into its buy and its sell just like the first time. (A file whose columns have genuinely changed still asks you to match them up again, so nothing is imported with the wrong layout.)
- The "Add a tile" panel now always opens in view. Previously, if you had scrolled down a busy dashboard and clicked the "+" to add a tile, the panel opened off the top of the screen, so it looked like nothing had happened and you had to scroll back up to find it. Now the panel is pinned just under the header wherever you have scrolled, over a dimmed dashboard, and a long list of tiles scrolls inside the panel instead of running off-screen. Close it by clicking the dimmed area, pressing Esc, clicking the "x", or clicking "+" again -- and once you pick a tile, the dashboard scrolls to show you the tile you just added.
- Small visual clean-ups in the import wizard: the "which row has your column names?" selectors are round again (they had been rendering as slightly squashed ovals), and toggle switches now show a single clean knob (a faint doubled-up knob had been showing on the "on" state).

---

## Verify

SHA256: `60d2614b0cdee2fb1140d4672ce16fc63bfaf725209f83db3b70f4be510abe69`

## License

Proprietary - [RiTrade EULA](https://github.com/RiTrade/ritrade-releases/blob/main/EULA.md). The installer requires EULA acceptance.