# RiTrade 1.2.1

_Released 2026-06-13_

### Fixed

- **Imports that ask for a trade date no longer lose per-row fees** (work
  0123). When a file has no date of its own (DasTrader local CSV) and you
  supply one in the date picker, the rebuilt trades now keep every per-row
  fee from the file (e.g. ECN fees). Previously those fees were silently
  zeroed on exactly this path, understating your costs for that import.

---

## Verify

SHA256: `d35c56b3d02d7ac3012995d6576d05df2034af04f30eee94710a6a132ba6e9db`

## License

Proprietary - [RiTrade EULA](https://github.com/RiTrade/ritrade-releases/blob/main/EULA.md). The installer requires EULA acceptance.