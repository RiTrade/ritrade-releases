# RiTrade 1.2.14

_Released 2026-06-26_

### Changed

- **A one-time, automatic database upgrade.** Opening this version adds a small
  field so RiTrade can remember which header row you chose for each saved custom
  CSV format. It applies on first launch, needs nothing from you, and leaves your
  existing trades untouched.

### Fixed

- **Custom CSV import now honours which row you pick as the header.** When you
  import a broker file RiTrade does not recognise, the "Check file format" step
  lets you say which line holds your column names - and now that choice actually
  takes effect. Point at the real header line, even when your broker stacks a
  title, an export date, or a blank line above it (any line, however deep), and
  the column-matching screen, the preview, and the trades that land in your
  journal all read from that line. Files with no header row at all work too:
  choose "This file has no header" and RiTrade numbers the columns (Column 1,
  Column 2, ...) so you can still match them. The choice is remembered for next
  time, including on other accounts that import the same format. Previously the
  choice was collected and silently ignored - the column-matching screen always
  read the file's first line, so any file with extra lines above the header was
  impossible to import.
- **A row with the wrong number of values is now caught before it is saved.** If a
  data row does not line up with the header you chose (too few or too many
  values), RiTrade flags it on the pre-commit review and sets it aside by default,
  so a misaligned row can never quietly carry a wrong price or quantity into your
  journal. You can still choose to keep it.

---

## Verify

SHA256: `88ea570224d1ac92c011513816713b3c0545e591d63cf8f01e0ba4bf7940349b`

## License

Proprietary - [RiTrade EULA](https://github.com/RiTrade/ritrade-releases/blob/main/EULA.md). The installer requires EULA acceptance.