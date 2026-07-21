# RiTrade 1.2.34

_Released 2026-07-21_

### Bug fixes

- Delete, reset and remove buttons stay clearly legible -- and still read unmistakably as "danger" -- whatever theme and P&L style you pick. On the light themes the delete-account button's hover text had faded to nearly invisible, and under the two-shade Tonal style the "Reset filters", "Reset Design", "Clear all filters" and broker-connection "remove" buttons flipped to a hard-to-read navy on hover. Now they hold a consistent danger red, their hover background settles onto a neutral plate that follows your theme (with the danger cue kept in the outline) rather than a fixed wash that could turn navy, and their focus outline matches the rest of the app. Danger buttons are theme-aware too -- a softer pale-pink on the light themes and the deeper maroon on dark -- instead of one fixed shade.
- A backwards date range no longer leaves your dashboard looking mysteriously blank. If you set a custom From/To range with the end date before the start date, RiTrade now shows a clear note right under the filter bar explaining that's why nothing is showing and how to put it right -- instead of an empty dashboard that looks like your trades have vanished. And switching from a custom range back to a preset period (like "All time") now clears the old From/To dates, so the date controls always match what the dashboard is actually showing.
- A handful of smaller colour clean-ups so every control reads the way it should on every theme: the toggle-switch knob is visible again on the Graphite theme (the white knob had all but disappeared against its light track), the filter-slicer's selected side now clearly reads as selected on the light themes, a dashboard tile's hover glow picks up your theme's accent colour instead of a fixed blue, and other stray colours now follow your chosen theme.

---

## Verify

SHA256: `c646706c0084245de606b21818f78092bc505876faed283aad17729f39b075ad`

## License

Proprietary - [RiTrade EULA](https://github.com/RiTrade/ritrade-releases/blob/main/EULA.md). The installer requires EULA acceptance.