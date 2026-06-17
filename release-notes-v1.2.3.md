# RiTrade 1.2.3

_Released 2026-06-17_

### Changed

- **The default Overview dashboard now fills the full screen width.** Its bottom
  row (Daily Summary + Win Rate) previously stopped at ~3/4 width, leaving the
  right edge empty; it now spans the full grid like the rest of the dashboard.
  Applies to freshly seeded dashboards (new installs).
- **The in-app User Guide now carries the new RiTrade logo.** Its header shows
  the brand mark + orange wordmark, and its accent colour is RiTrade orange
  instead of the old blue. (The guide's embedded tutorial screenshots still show
  the previous branding and are slated for a separate re-capture.)
- **RiTrade now describes itself as "Trade Analytics," not a "trading journal."**
  The Windows app/installer name (shown in Task Manager and the exe's properties),
  the sign-in screen, and the in-app User Guide now call RiTrade a trade-analytics
  app. (The downloadable PDF version of the guide still uses the old wording and
  will update in a later guide refresh.)

### Fixed

- **The "Browse..." button for picking an import-watch folder now works in the
  installed app.** In the packaged build it previously did nothing — it only
  worked when running from source — because the native folder-picker runtime was
  stripped out of the build. It's now bundled, so Browse opens a real folder
  chooser. And if the picker ever can't open, the wizard now says so and points
  you to type the path instead, rather than failing silently.

---

## Verify

SHA256: `846b1dd9d8f6c4f1c02f65bc7f86b55dc1996c8a25ddd1bb0a36a662bc72cdd8`

## License

Proprietary - [RiTrade EULA](https://github.com/RiTrade/ritrade-releases/blob/main/EULA.md). The installer requires EULA acceptance.