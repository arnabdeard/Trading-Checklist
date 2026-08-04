# Entry//Check — Trading Entry Confluence Checklist

A single-file, offline-first checklist tool for disciplined trade entries. Built around SMC/ICT-style price-action confluence (VWAP, BOS/CHoCH, FVG, liquidity sweeps, retracement entries, HTF context, and volume/volatility), with a full trade log, editable history, and a companion TradingView indicator that automates the purely structural criteria.

No backend, no build step, no dependencies — open the HTML file in Chrome (or any modern browser) and it just works.

---

## Why this exists

Most losing "textbook" setups aren't a checklist problem - they're a discipline problem. This tool exists to remove impulsive, no-confluence entries by forcing a consistent pre-trade check, and to keep an honest, reviewable log of what was actually confirmed at the moment of entry (not reconstructed afterward once you know the outcome).

**Important:** a green checklist does not guarantee a winning trade. It filters out low-quality setups; it does not predict outcomes. Treat it as a discipline tool, not an oracle — see [Honest Limitations](#honest-limitations) below.

---

## Features

### Checklist
- 7 confluence criteria per entry:
  - **VWAP checked**
  - **Confirmed BOS / CHoCH**
  - **Fair value gap present**
  - **Entry possible at retracement / level**
  - **Liquidity sweep**
  - **Good volume / volatility**
  - **HTF context** — dynamically relabels itself depending on trade type:
    - *Continuation* → "Does this align with the 4H/D trend?"
    - *Reversal* → "Is this at a real HTF structural point (equal high/low, liquidity pool, major level)?"
- **Continuation / Reversal** trade-type toggle
- Live readiness meter (`x/8 confirmed`) with a **READY / ALMOST / NOT READY** status pill
- Optional notes field per entry

### History log
- Every saved entry is logged with a timestamp, score, trade type, and notes
- **Outcome tagging** per entry: **P**rofit / **L**oss / **M**issed (never entered) — kept separate so your real win rate isn't inflated by setups you saw but didn't take
- **Fully editable after the fact** — checkboxes, trade type, and notes can all be revisited and corrected on any past entry
- Delete any entry
- Capped viewport (~10 entries visible) with a themed scrollbar for older history — the page doesn't grow unbounded

### Special Notes
- A separate, general-purpose sticky note box (top-right), unrelated to the checklist itself — for anything you want to jot down (session context, news, reminders)
- Independently editable, deletable, sorted newest-first

### Theming
- Dark theme (default) and light theme, toggle top-left, preference remembered across sessions

### Storage
- Everything persists in the browser's `localStorage` — **no account, no server, no data leaves your machine**
- See [Data & Privacy](#data--privacy) for the tradeoffs this implies

---

## Getting started

1. Download `entry-checklist.html` from this repo
2. Open it directly in Chrome (double-click, or drag into a browser tab)
3. That's it — no install, no server, no build step

### Hosting it (optional)
To access it from any device via a URL instead of a local file:
1. Rename the file to `index.html`
2. Push to a GitHub repo
3. Enable **Settings → Pages → Deploy from branch (main / root)**
4. You'll get a live URL in a minute or two

**Note:** hosting it doesn't sync your history across devices — `localStorage` is per-browser, per-device. Opening the same URL on your phone and laptop gives you two independent, unconnected logs.

---

## Data & privacy

- All data (checklist history, special notes, theme preference) lives in `localStorage`, scoped to the browser you're using.
- Clearing **"Cookies and other site data"** in your browser will wipe it. Clearing cache/history alone will not.
- Opening the file in Incognito, a different browser, or a different device gives you a separate, empty log.
- **There is currently no built-in backup/export.** If preserving your trade history matters to you, back it up manually (e.g. periodically copy the relevant `localStorage` keys) until an export/import feature is added.

---

## Companion: TradingView indicator

`a1-entry-checklist-indicator.pine` is a Pine Script v5 indicator that automates the four purely price-structure criteria from the checklist:

| Checklist item | Automated? |
|---|---|
| Liquidity sweep | ✅ |
| Confirmed BOS / CHoCH | ✅ |
| Fair value gap present | ✅ |
| Entry possible at retracement / level | ✅ (fires on FVG retest) |
| VWAP checked | ❌ manual |
| HTF context | ❌ manual |
| Good volume / volatility | ❌ manual |

It marks `LONG`/`SHORT` labels on the chart when a liquidity sweep is followed by a confirming BOS/CHoCH and price retraces back into the resulting FVG zone. VWAP, HTF context, and volume/volatility are left as manual checks by design — they require judgment the script isn't trying to replace.

**Usage:** paste into TradingView's Pine Editor → "Add to chart." Backtest against your own instrument/timeframe before trusting live alerts — see [Honest Limitations](#honest-limitations).

---

## Honest limitations

- **This is a filter, not a predictor.** A fully confirmed checklist improves the quality of candidate trades; it does not guarantee a win.
- **The concepts used (VWAP, BOS/CHoCH, FVG, liquidity sweeps) are discretionary SMC/ICT-style frameworks**, not a peer-reviewed, statistically verified edge. Results depend heavily on execution, risk management, and market context.
- **Editable history is a double-edged feature.** Being able to go back and correct checkboxes on old entries is useful for fixing genuine data-entry mistakes, but it also makes it possible to retroactively "improve" a log once you know the outcome. The tool is only as honest as the discipline behind using it — don't edit an entry's criteria after you already know how the trade played out.
- **The Pine Script indicator has inherent lag.** Pivot-based structure detection can only confirm a swing high/low a few bars after it forms — same delay a human charting manually would have.
- **No cross-device sync, no backup, single-user.** See [Data & Privacy](#data--privacy).

---

## Tech stack

- HTML, CSS, vanilla JavaScript — no frameworks, no build tools, no dependencies
- `localStorage` for persistence
- Pine Script v5 for the companion TradingView indicator

---

## Roadmap ideas

- [ ] Export/import history to/from a `.json` file for backup and cross-device transfer
- [ ] Raise the visible history cap beyond the current ~10-entry scroll window
- [ ] Optional backend for true cross-device sync
- [ ] Webhook-formatted alerts from the Pine Script indicator for bot integration

---

## License

Add your preferred license here (MIT is a common choice for a personal tool like this).

---

## Disclaimer

This tool does not provide financial advice and does not guarantee trading performance. Trading involves substantial risk of loss. Use at your own discretion and always manage risk independently of any checklist or indicator output.
