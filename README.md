# Entry//Check — Trading Entry Confluence Checklist

A single-file, offline-first checklist and trade journal for disciplined entries. Built around SMC/ICT-style price-action confluence, with a full history log, live analytics, and export/import backup — all running from one self-contained HTML file with zero dependencies.

Open the file in Chrome and it just works. No install, no server, no build step.

---

## Why this exists

Most losing "textbook" setups aren't a checklist problem — they're a discipline problem. This tool exists to remove impulsive, no-confluence entries by forcing a consistent pre-trade check, and to keep an honest, reviewable log of what was actually confirmed at the moment of entry — not reconstructed afterward once the outcome is known.

**A green checklist does not guarantee a winning trade.** It filters for setup quality; it does not predict outcomes. See [Honest Limitations](#honest-limitations).

---

## Features

### Checklist
7 confluence criteria per entry:
- **VWAP checked**
- **Confirmed BOS / CHoCH**
- **Fair value gap present**
- **SL/Entry possible at retracement / level**
- **Liquidity sweep**
- **Good volume / volatility**
- **HTF context** — relabels itself based on trade type:
  - *Continuation* -> "Does this align with the 4H/D trend?"
  - *Reversal* -> "Is this at a real HTF structural point (equal high/low, liquidity pool, major level)?"

Plus:
- **Continuation / Reversal** trade-type toggle
- Live readiness meter (x/8 confirmed) with a **READY / ALMOST / NOT READY** status pill
- Optional notes field
- A full-screen "NOW OR NEVER — TAKE ACTION — EXECUTE NOW" banner that fires for 15 seconds whenever a full 8/8 entry is saved, as a nudge against hesitating on your highest-quality setups

### History log
- Every saved entry logs its timestamp, score, trade type, and notes
- **Outcome tagging**: P(rofit) / L(oss) / M(issed — never entered) — kept separate so your win rate isn't inflated by setups you saw but didn't take
- **Fully editable after the fact** — checkboxes, trade type, and notes can all be corrected on any past entry
- **Flag important entries** with a pin marker for quick visual reference
- **Undo on delete** — a 5-second undo toast in the bottom-right lets you recover an accidentally deleted entry
- Capped scroll window (~10 entries visible) with a themed scrollbar

### Filters
Above the history list: filter by **trade type**, **outcome**, **date range** (From/To), and **important only** — with a live "showing X of Y" count and a one-click clear.

### Stats (collapsible)
- **Win Rate** — Profit / (Profit + Loss), missed entries excluded entirely. Red below 50%, green at/above.
- **Missed Rate** — Missed / Total entries. Amber below 50%, red at/above.
- **Current Win Streak** and **Best Winning Streak / Worst Losing Streak** — computed from P/L outcomes only, missed entries skipped.

### Analytics (collapsible)
- **Full Confluence (8/8)** meter — % of *all* saved entries that hit full confluence, regardless of outcome (setup-quality signal).
- **Setup Type breakdown** — split bar showing Continuation vs Reversal share of total entries, each with its own win rate.
- **Consistency (Taken Trades)** — % of entries you actually *executed* (P or L only) that were full 8/8. Isolates discipline at the point of pulling the trigger, separate from setup-recognition accuracy. Red below 50%.

### Special Notes
- A general-purpose sticky note box, independent of the checklist — for session context, reminders, anything
- Fully editable, deletable, sorted newest-first
- **Flag as important** (accent-colored highlight)
- **Pin to top** — pinned notes appear in a dedicated bar directly above the header, spanning the same width as the "ENTRY//CHECK" title through today's date

### Theming
Dark (default) and light theme, toggle top-left, preference remembered across sessions.

### Backup
**Export** downloads your full history, Special Notes, theme preference, and current draft as a .json file. **Import** restores from a previous export, with a confirmation prompt showing exactly what will be replaced.

---

## Getting started

1. Download entry-checklist.html (or index.html if hosted)
2. Open it directly in Chrome — double-click, or drag into a tab
3. That's it

### Hosting via GitHub Pages (optional)
1. Rename the file to index.html
2. Push to a repo
3. Settings -> Pages -> Deploy from branch (main / root)
4. Live URL in a minute or two

**Note:** hosting doesn't sync history across devices — data lives in the browser's localStorage, per-browser, per-device. Two devices opening the same URL get two independent, empty-until-used logs.

---

## Data & privacy

- All data (history, notes, theme, draft) lives in localStorage, scoped to the browser you're using — nothing leaves your machine.
- Clearing "Cookies and other site data" wipes it. Clearing cache/history alone does not.
- Incognito windows, a different browser, or a different device all start with an empty log.
- **Export regularly.** There's no automatic cloud backup — the Export button is your safety net. Do it before clearing browser data, switching machines, or moving the file between drives.

---

## Honest limitations

- **This is a filter, not a predictor.** A confirmed checklist improves the quality of candidate trades; it does not guarantee a win.
- **The concepts used (VWAP, BOS/CHoCH, FVG, liquidity sweeps) are discretionary SMC/ICT-style frameworks**, not a peer-reviewed, statistically verified edge. Results depend on execution, risk management, and market context.
- **Editable history is a double-edged feature.** Going back to correct a genuine data-entry mistake is useful; retroactively "improving" a checklist after already knowing the outcome defeats the purpose of logging it. The tool is only as honest as the discipline behind using it.
- **No cross-device sync, no automatic backup, single-user.** See Data & Privacy above.

---

## Tech stack

HTML, CSS, vanilla JavaScript. No frameworks, no build tools, no dependencies. localStorage for persistence.

---

## License

Add your preferred license here (MIT is a common choice for a personal tool like this).

---

## Disclaimer

This tool does not provide financial advice and does not guarantee trading performance. Trading involves substantial risk of loss. Use at your own discretion and always manage risk independently of any checklist output.
