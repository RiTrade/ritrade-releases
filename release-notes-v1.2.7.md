# RiTrade 1.2.7

_Released 2026-06-22_

### Fixed

- **A folder sync now tells you when a file couldn't be brought in, instead of
  saying "Up to date."** When you sync a watched folder and a file can't be imported
  automatically (its columns moved, or it's an unfamiliar layout), RiTrade sets that
  file aside in the folder's "failed" subfolder for you to fix and drop back in. It
  used to still report the account as "Up to date" -- hiding that a file needs your
  attention. The account now shows "N file(s) need attention" with the reason, so
  nothing is quietly skipped. (Work 0174.)

- **A watched folder for a known broker now imports on its own after the first time.**
  When you set up a "watch a folder" account for a broker RiTrade recognises (like
  moomoo), hitting Sync used to send you straight back to the "pick a file" setup
  screen every single time — it never settled into quietly pulling in new files. Now,
  once you've brought in that first file, every later Sync just scans the folder and
  imports whatever's new, no prompts. Recognised-broker files come in through that
  broker's own format on the folder scan — they're no longer set aside as "needs
  review." Folder accounts you'd already set up before this fix repair themselves on
  the next launch — no need to delete and recreate them.
  (A one-time self-heal runs automatically on first launch; it's additive and leaves
  your existing data untouched. Work 0173, schema migration m_009.)

---

## Verify

SHA256: `5c472deb980e6b0224fd429976310a0e7e855042e2ea140bce28aa8a6c6a4dd8`

## License

Proprietary - [RiTrade EULA](https://github.com/RiTrade/ritrade-releases/blob/main/EULA.md). The installer requires EULA acceptance.