# RiTrade 1.2.46

_Released 2026-08-05_

### Improvements

- **Cancelled orders are no longer mentioned when you import.** The confirm screen used to count them and tell you they had been left out, wherever you imported from. A cancelled order never filled, it is not a trade, and it is not news, so that count is gone from every import screen. A file that imports nothing still tells you so in one line, rather than showing you a button you cannot press and no reason for it.

### Bug fixes

- **A broker file that holds cancelled orders no longer has half its rows called faulty.** Import an orders export that lists orders you cancelled, and RiTrade could name 49 of the file's 101 rows as bad, four complaints each, about columns you had matched correctly. Every one of those rows was a cancelled order that was never going to be imported anyway. RiTrade now checks only the rows it is about to import, so a file like that goes straight through and the 52 fills in it are imported.
- **A file with no fill time matched now says so on the screen where you fix it.** RiTrade needs to know when each order filled. Where no column was matched to that, you got a banner saying RiTrade could not finish checking the file, offering a retry that could never work. That refusal now appears in plain words on the screen where you match your columns, and it names what is missing. The columns you already matched stay matched.
- **The screen where you match your columns now tells you the truth about every row.** Match a column, then clear it, and the row kept a green tag saying it was matched beside an empty dropdown. Step back to that screen after moving on, and a row you had matched by hand redrew as matched to nothing. The tag was reading RiTrade's own guess while the dropdown beside it read your answer, so the two could disagree, and on a file with no fill time matched the screen carried a red banner saying a field was missing directly above a green tag saying it was fine. Both screens now read one thing: your current answer. Every row says which of five things it is, in the same five words on both screens, and it changes the moment you change the dropdown.
- **A column that cannot be read as the field you matched it to now stops the import and names the value that failed.** Point Price at a column of company names and RiTrade used to accept it, carry on, and tell you later. Press Confirm now and RiTrade checks what your chosen columns actually hold. If a column will not read at all, you stay on the screen, the row turns red, and a line under it names the field, what that field needs, and the first value from your own file that did not work. Fix that row and it clears itself. A column with a few odd rows in it is not this: those still go to the step that asks you about them one at a time. Nothing about importing from a watched folder changes.

---

## Verify

SHA256: `be96f7a00c645622ef4893a9def05a9b9e38e527a076dcf48e157fdb5d444257`

## License

Proprietary - [RiTrade EULA](https://github.com/RiTrade/ritrade-releases/blob/main/EULA.md). The installer requires EULA acceptance.