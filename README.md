# Material Book — Quotation System

Construction-material **price library / quotation system** for MGD (main contractor of factory construction).
New, standalone system — **independent from the BMS**.

## Concept
1. **Main page = menu**
   Main content cards to the right (Civil Work · Steel Structure · Plumbing Work · Electrical);
   under each card, its detail cards (material names only).
2. **Click a material name → full page** (main page hidden) with **all prices** of that material:
   `Brand · Grade/Spec · Size/THK · Plant/Supplier · Unit price · Unit · Updated · Note` — every cell editable.
3. `‹ Back to main page` to pick another material.

## Design
Chosen style **#29 — Arc Blue + Chamfer**: near-black / electric blue (`#60a5fa`), chamfered (cut-corner) cards,
monospace figures for price columns, HUD-like panels.

## Features
- 4 main contents · material items · unlimited price entries per material
- Inline editing, `＋ Add price`, `⧉ Duplicate`, `✕ delete row`
- `＋ New item` per main content, `＋ Main content` (add your own categories)
- Search across main / item / brand / grade / plant
- `⤓ Export Excel` (CSV, opens in Excel) — single item or everything
- `⤓ Backup JSON` / `⤒ Import JSON` (full backup & restore)
- `🖨 Print / PDF`
- Storage: **localStorage** by default; **Firestore-ready** (fill the `FB` config object in `index.html`)

## Enable Firestore cloud storage
In `index.html`, find:

```js
var FB={on:false,projectId:'',apiKey:'',doc:'pricebook/master'};
```

Fill in your Firebase project id + web API key and set `on:true`.
The app then pushes/pulls the whole price book to/from Firestore (REST, no SDK needed).

## Files
- `index.html` — the whole application (single file, no build step, no dependencies)

## Run locally
Open `index.html` in a browser, or serve the folder:
```
python3 -m http.server 8080
```

## Roadmap (next)
- Quotation builder (pull prices from the library into a quotation sheet)
- Supplier price-comparison view & price history
- Multi-currency (VND / USD) with exchange rate
- User accounts / permissions
