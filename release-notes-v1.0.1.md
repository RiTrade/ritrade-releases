# RiTrade 1.0.1

_Released 2026-05-06_

### Added

- `GET /api/version` — public, unauthenticated endpoint returning `{version, build_ts, channel}`. Enabler for auto-update (work 0026), bug-report context, and a future About panel. (work 0033)

### Fixed

- **Triage queue noise.** `werkzeug.exceptions.HTTPException` (404, intentional `abort(...)`, etc.) no longer writes a `critical` triage ticket and now returns its proper status code instead of being rewritten as 500. (work 0030)
- **Layout save crash.** `POST /api/dashboards/<id>/layout` no longer raises `KeyError` when GridStack emits a partial tile object; malformed entries are skipped and reported via `skipped` count in the response. Frontend adds defense-in-depth filtering. (work 0031)
- **SQLite locking on layout save.** `get_db()` now opens connections with `timeout=30.0`, `PRAGMA journal_mode=WAL`, and `PRAGMA busy_timeout=30000`. WebView2's near-simultaneous requests no longer race. (work 0032)

---

## Verify

SHA256: `f0dd28bfab3ccd0cf479dfa67391bcb2201d8faa20681486d2d7e9b44c03afd2`

## License

[GPL-3.0](https://github.com/RiTrade/ritrade-releases/blob/main/LICENSE)