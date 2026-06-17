# RiTrade 1.2.4

_Released 2026-06-17_

### Fixed

- **The "Browse..." folder picker now actually works in the installed app.** The
  v1.2.3 fix bundled tkinter but missed its `filedialog` submodule in the
  Cython-protected build (the one that ships), so on installed copies Browse still
  failed with "The folder picker couldn't open." The full tkinter (and urllib)
  submodule set is now collected, so Browse opens the native folder chooser.
- **Importing a custom CSV now shows the real header row in the "Check file format"
  step.** It was listing the first data rows and asking which one was the header —
  the actual column-name row never appeared — so confirming "row 0 as header" could
  treat your first trade as the column names. The detected header (e.g.
  `Name, Symbol, Side, ...`) is now shown as row 0, pre-selected, above the data.

---

## Verify

SHA256: `753cbc9dd8bc8239fe6d57454479ecea39b29d8b3512b4380f4459c4f7077eaf`

## License

Proprietary - [RiTrade EULA](https://github.com/RiTrade/ritrade-releases/blob/main/EULA.md). The installer requires EULA acceptance.