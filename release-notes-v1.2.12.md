# RiTrade 1.2.12

_Released 2026-06-25_

### Added

- **A step-by-step User Guide chapter for importing a custom or unrecognised CSV.**
  The guide now walks the whole "Match your columns" flow end to end - picking the
  Generic CSV option, telling RiTrade whether each row is one order or one whole
  trade, mapping each field to a column in your file (and what the "Choose a column"
  prompt means), checking the live preview, and naming the format so it's recognised
  next time. (Work 0190.)

### Changed

- **The in-app User Guide now matches the app you're actually using.** It has been
  refreshed for the new menu and focused settings panels, the choice between a
  per-dashboard filter and one shared Global filter, and the new About & updates
  screen - and it now stamps its own version straight from the app, so it stays
  in step with every release on its own.

- **New RiTrade installs now start with the Mono P&L and Mono calendar palettes**
  (on the Ember theme) - one consistent colour language across the app: the accent for
  up, neutral grey for down, on both the stat cards and the calendar. If you have already
  chosen your own P&L or calendar colours, nothing changes; this only sets the starting
  point for a fresh install.

### Fixed

- **Setting up a custom CSV no longer looks like it's offering to skip a field you have to fill in.**
  On the "Match your columns" screen, a required field that hasn't been matched to one of
  your file's columns yet now reads **"Choose a column"** instead of "-- skip --", so it's
  clear it still needs a column rather than appearing safe to leave out. Genuinely optional
  fields (fees, order id, and the like) still read "-- skip --". The same fix applies whether
  your file is one order per row or one whole trade per row. (Work 0189.)

---

## Verify

SHA256: `65406f14c708514f429446b04d8ac6be690a6e9be610e8dc19ca393c9ec26e93`

## License

Proprietary - [RiTrade EULA](https://github.com/RiTrade/ritrade-releases/blob/main/EULA.md). The installer requires EULA acceptance.