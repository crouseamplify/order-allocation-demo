# Order Allocation Manager — interactive demo

A static, click-through demo of the redesigned customer-portal order allocation experience.
Everything runs in the browser on made-up data. There is no server and no Salesforce connection.

## Open it

- **Hosted:** GitHub Pages (see the repo's "About" link once enabled).
- **Locally:** open `index.html` in a browser, or run `python3 -m http.server` in this folder and visit <http://localhost:8000>.

## What's in it, in the order it was built

| Step | Page | What to try |
|---|---|---|
| 1 | `index.html` — **Manage Orders** | Use the **Card / Table** switch in the dark bar (stand-in for the `displayMode` property). Cards are grouped Open → Submitted → Processing → Shipped. Search by PQ, quote or PO and filter by program. Orders on an Amplify-side lock show a banner and a **View Order** button. Every button and order number opens step 2. |
| 2 | `manager.html` — **Allocation Manager** | Switch layouts with **Desktop / Tablet / Mobile**; Tablet and Mobile also have **Portrait / Landscape** and **Fit to window**. Edit quantities, open **Site Details**, **Add Site**, **Hide Confirmed**, and the **Columns** menu (Available / Distributed can be hidden; Remaining cannot). |

### Test switches (top bar of the manager)

- **Amplify lock (read-only)** + reason: shows the read-only state for returns/adjustments.
- **Confirm all allocations**: enables **Submit Order**, which is otherwise disabled until every site is Confirmed.
- One product (Amplify ELA G7 Student Consumable Set) is deliberately over-allocated so the banner, the filter and the Submit error modal can be seen. Reduce its quantities to clear it.

## Data

All numbers, sites, addresses and order identifiers are fabricated for the demo. Product names, ISBNs and programs are taken from the public product catalog so the lists look realistic. Quantities and availability are invented.

## Styling

The pages load the same stylesheets the live portal serves (`assets/site-styles/`): the Salesforce Lightning Design System, the Experience Cloud (`dxp-*`) styling hooks and extensions, and `site-theme.css`, which holds the portal's branding values (brand blue `#0169E4`, text colour, destructive red, spacing). The Benton Sans font is not bundled, so browsers fall back to a system font.

## Files

```
index.html     Step 1 · Manage Orders (Card / Table)
manager.html   Step 2 · Allocation Manager (Desktop / Tablet / Mobile)
assets/site-styles/   Portal stylesheets and theme variables
.nojekyll      Tells GitHub Pages to serve the files as-is
```
