# RiTrade 1.2.8

_Released 2026-06-23_

### Fixed

- **A clear way to reach the trades that are waiting on your decision.** When an
  account has trades to review — copies that differ from ones you already have, like
  a corrected commission — its row in the sync window now shows a **Review** button
  you click straight through to the review. Before, it showed an "needs review" label
  you couldn't click, and the only way in was to press Sync (which re-ran the whole
  import just to reach a screen already waiting for you). The button shows how many
  decisions are waiting, works for broker-sync, watch-folder, and manual accounts
  alike, and turns back into the normal Sync / Import action on its own once you've
  cleared them. (Work 0178.)

- **Re-syncing a broker-fed account no longer floods your trades with duplicates.**
  If you press Sync on an account fed by broker sync that reports completed
  round-trip trades (like PropReports), every Sync used to re-flag all of your
  trades as "needs review" and hide them — leaving an account that showed nothing
  and a review screen with nothing in it to fix. Now a re-sync correctly recognises
  the trades you already have and brings in nothing new; only a genuinely changed
  trade (say a corrected commission) is flagged for your review. If your account was
  already caught by this, its trades are restored. (Work 0177.)

---

## Verify

SHA256: `f973cd6c757313e53765db9e6cdd707350187cc9e07fe663151649ae7e15785e`

## License

Proprietary - [RiTrade EULA](https://github.com/RiTrade/ritrade-releases/blob/main/EULA.md). The installer requires EULA acceptance.