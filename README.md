# Order Allocation Manager — interactive demo

A static, click-through demo of the redesigned customer-portal order allocation experience.
Everything runs in the browser on made-up data. There is no server and no Salesforce connection.

## Open it

- **Hosted:** <https://crouseamplify.github.io/order-allocation-demo/>
- **Locally:** open `index.html` in a browser, or run `python3 -m http.server` in this folder and visit <http://localhost:8000>.

## How it works

`index.html` is a **shell**: a dark control bar above a device frame. The whole demo — **Manage Orders** and then the
**Allocation Manager** — runs inside that frame, so you can click through it at any screen size.

### Screen sizes (top bar → *Screen*)

| Option | Size (CSS px) | Notes |
|---|---|---|
| 1080p | 1920 × 1080 | |
| 1440p | 2560 × 1440 | |
| 4K | 3840 × 2160 | |
| Tablet | 834 × 1194 | iPad Pro 11" |
| Phone | 390 × 844 | iPhone 14 |
| Small phone | 360 × 800 | |

**Rotate** swaps width and height for the tablet and phones. **Fit to window** scales the frame down so the whole
screen is visible (the pages inside still see the true size); untick it for 100%.

The site's content area is capped at **1440px**, so on 1080p, 1440p and 4K the content stays 1440 wide and centred,
with the sides shaded.

### The layouts switch in CSS

The size buttons are plain radio inputs; `:has()` changes the frame size. Inside the frame each page uses CSS media
queries against that size, so nothing is toggled by script:

| Viewport width | Manage Orders | Allocation Manager |
|---|---|---|
| ≥ 1280 | Four status columns | Product × site grid |
| 640 – 1279 | Two-up columns | Site list + product list (split) |
| < 640 | One column with status tabs | Site dropdown / By product, stacked |

A phone held sideways (width ≥ 640, height ≤ 500) uses a tightened version of the split layout.

JavaScript only fits the frame to your window, remembers your choices for the tab, and passes the test switches to the page.

### Test switches (in the top bar)

- **Manage Orders:** `displayMode` — Card or Table.
- **Allocation Manager:** *Amplify lock (read-only)* with a reason, and *Confirm all allocations* (Submit stays disabled until every site is Confirmed).
- One product (Amplify ELA G7 Student Consumable Set) is deliberately over-allocated so the banner, the filter and the Submit error modal can be seen. Reduce its quantities to clear it.
- Every button and order number on Manage Orders opens the Allocation Manager.

You can also open `orders.html` or `manager.html` directly. They then follow your browser window's width and show their own small switch bar.

## Data

All numbers, sites, addresses and order identifiers are fabricated for the demo. Product names, ISBNs and programs are taken from the public product catalog so the lists look realistic. Quantities and availability are invented.

## Styling

The pages load the same stylesheets the live portal serves (`assets/site-styles/`): the Salesforce Lightning Design System, the Experience Cloud (`dxp-*`) styling hooks and extensions, and `site-theme.css`, which holds the portal's branding values (brand blue `#0169E4`, text colour, destructive red, spacing). The Benton Sans font is not bundled, so browsers fall back to a system font.

## Files

```
index.html     Shell: device frame, screen-size selector, test switches
orders.html    Step 1 · Manage Orders (Card / Table)
manager.html   Step 2 · Allocation Manager (grid / split / stacked)
assets/site-styles/   Portal stylesheets and theme variables
.nojekyll      Tells GitHub Pages to serve the files as-is
```
