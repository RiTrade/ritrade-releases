# RiTrade 1.2.22

_Released 2026-07-10_

### New features

- **Arrange your dashboard tabs the way you actually work — drag one left or right and
  it stays put.** Your tabs used to sit in the order they were made, with no way to move
  the one you open every morning to the front. Now you can grab any tab and slide it
  along the strip to wherever it belongs, and the new order sticks the next time you open
  RiTrade. Prefer the keyboard, or find dragging fiddly? Right-click any tab and you'll
  find **Move left** and **Move right** right there beside Edit and Delete — the same
  reorder, one click at a time, and fully reachable by keyboard and screen reader (the
  choice greys out at the ends, so a leftmost tab can only go right). Any dashboard you
  add still lands at the end of the strip, ready to be dragged into place.

- **See how every share is working for you — six new "per share" stats, headlined by
  Net / Share.** Totals and per-trade averages can't tell you whether each unit of
  exposure is actually paying off, and they don't let you compare a run of 100-share
  trades against a run of 2,000-share trades. The new **Net / Share** answers it in one
  number: for every share (or contract) you put through the market, are you net ahead
  after fees? Alongside it, **Gains / Share** and **Loss / Share** show how much you make
  per share when you're right versus give back when you're wrong — each in two lenses: a
  size-weighted version (big positions carry more weight) and an equal-weight-per-trade
  version (every trade counts the same, so you can see your typical trade's efficiency).
  Add any of them as a Stat Card, or line several up in a Multi-Stat. They read down to
  the tenth of a cent (like `+$0.043`), colour green when you're ahead and red when
  you're behind, work across shares, options, and futures (per contract), and follow your
  dashboard filters like every other stat. Two of them come ready-placed on the
  Performance tab out of the box — a size-weighted card and a per-trade-average card,
  side by side — so you see your per-share edge on day one.

- **A new Rolling Per-Share chart shows whether that per-share edge is climbing or
  fading — not just where it stands.** Where the per-share cards give you a single
  number, this chart trends any of the six per-share metrics as a rolling line over
  time, the same way the Rolling P&L tile does for your daily dollars. Pick the metric
  and a smoothing window (5 to 60 days); the line runs green when each share is working
  for you and red when it's costing you, so you can catch an edge quietly eroding as you
  size up — even while your total P&L still looks fine. It comes pre-placed on the
  Performance tab, right beside the per-share cards, and its numbers always agree with
  the card next to it.

### Improvements

- **Every tile and every stat now explains itself the same way, everywhere you ask.**
  The help you got used to vary tile by tile — some explained the number, some gave a thin
  blurb, and choosing a metric told you nothing at all. Now a single, consistent explainer
  answers the same three questions in the same order — **what it is**, **how it's worked
  out** (with your own live figures where the tile has them), and **the edge** it gives
  your trading — and it reads identically wherever you meet it: hovering a tile in the
  picker before you add it, opening a tile's help, choosing which metric a card shows, and
  the little "?" beside any number in a Multi-Stat. Choosing a metric now shows its full
  explainer right beside the picker as you flip through options, so you can tell Profit
  Factor from Expectancy before you commit. Every one of the 48 stats and all 30 tiles were
  written from scratch to this shape, in plain language — including the honest note that a
  breakeven trade counts as a loss in today's win rate. Keyboard and screen-reader friendly
  throughout, and it follows your theme like everything else.

- **The Win Rate donut now shows your win rate right in the middle.** The ring told you
  the balance of winners to losers, but you had to read it off the arc — the number that
  gives the tile its name was never actually on it. Now the centre of the donut carries
  your win rate as a headline figure, with the raw split (e.g. `340W / 171L`) underneath,
  so you get the percentage at a glance and the trade counts behind it in the same look.
  It matches the Win Rate stat card exactly and follows your dashboard filters like the
  rest of the tile.

- **The post-import fees question now asks only when it should — and you can switch it
  off for an account for good.** The prompt that follows an import into a Platform account
  used to appear even when your broker file already carried the fees, which was just
  noise. Now it stays quiet whenever your import brought fees in (including a broker that
  reports an explicit $0 commission, or a round trip whose only fee is an exchange or
  clearing charge) and asks only when the trades genuinely landed with no fee information —
  the one case where your P&L could silently read as if trading were free. And if you'd
  rather never be asked for a particular account, the prompt now offers a quiet "Don't ask
  about fees for this account" choice that sticks; turn the question back on any time from
  that account's settings under Accounts. As before, your answer only changes how this
  account's P&L is labelled (fees-included or gross) — it never adds, removes, or
  recalculates any fee amounts.

### Bug fixes

- **The post-import fees question now actually appears — it was built but had never once
  shown up.** When trades land in a Platform account that has never answered the fees
  question, a short prompt now follows the import and asks whether the fees are already in
  your data or should be labelled as gross — so your P&L reads honestly instead of quietly
  assuming your trading was free. Your answer is remembered per account and the prompt
  never returns for that account once answered; skip it (close button, click outside, or
  Escape) and it simply asks again after your next import. Answering only labels this
  account's P&L — it never changes your imported fee amounts. It waits politely behind any
  duplicate-review or demo prompt rather than stacking on top of them.

- **Dashboards you delete now stay deleted — the default set no longer rebuilds itself on
  reload.** Deleting a default-named tab (Overview, one of the trading tabs, or Finance)
  used to be undone silently on your next reload, because the starter dashboards were
  re-created every time the app started. They are now seeded only once, so your deletions
  persist and you can keep the workspace you want.

---

## Verify

SHA256: `f40962bd5fc8570edc60ea541a5f24fe583f2afbb5b72cef257ba901e0540732`

## License

Proprietary - [RiTrade EULA](https://github.com/RiTrade/ritrade-releases/blob/main/EULA.md). The installer requires EULA acceptance.