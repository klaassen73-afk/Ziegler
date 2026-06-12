# Zeigler Honda — "At Home Delivery" Landing Page

A static, responsive landing page for Zeigler Honda of Racine's at-home delivery program.
Built with plain HTML + CSS (no build step) and a small amount of vanilla JS.

## Files

| File | Purpose |
|---|---|
| `index.html` | Markup + inline scripts (map, popup links) |
| `styles.css` | All styling (responsive: desktop / ≤1024 tablet / ≤760 / ≤460 mobile) |
| `*.webp` | Optimized photos & vehicle shots |
| `*.svg` | Logo, badge icons, step icons, trust icons (vector) |
| `greet2.jpg` | Driveway section background |
| `6523368.png` | Footer/CTA phone icon |
| `Zeigler At Home Delivery landing page.png` | Original design mockup (reference only — not used by the page) |

## Run locally
Any static server, e.g.:
```
python3 -m http.server 8000
```
Then open http://localhost:8000

## External runtime dependencies (loaded via CDN)
- **Google Fonts** — Bebas Neue, Montserrat, Playfair Display, Dancing Script
- **Leaflet 1.9.4** (unpkg) — delivery-radius map
- **CARTO basemap tiles** (Positron, no-labels) — map background

## ⚠️ TODO before production launch
1. **Wire up the form.** `#schedule .cta__form form` is currently inert (`action="#"`).
   Point it at the dealership's lead handler / CRM (ADF email or API), and add
   submit success/error UI + server-side validation. Field `name`s are already set:
   `firstName, lastName, email, phone, zip, vehicle, deliveryLocation, comments`.
2. **Map tile attribution / licensing.** The map uses free CARTO/OSM tiles with a
   minimal attribution. For production, confirm CARTO usage limits or switch to a
   keyed provider (Mapbox/Google Static Maps) or a static image.
3. **Self-host fonts & libraries** (optional but recommended) instead of CDNs for
   performance/privacy/reliability.
4. **Analytics & call tracking** — add GA4 / dealer call-tracking number as needed.
5. **Verify content with client:** phone `262-260-9760`, hours (Mon–Sat 8:30am–7:00pm),
   Sturtevant, WI location, the WI/IL city lists, and the 50-mile radius.

## Notes / decisions
- **Links open in a popup window** (see script at bottom of `index.html`); all external
  links also have `target="_blank" rel="noopener"` as a fallback. Remove the popup
  script if standard new-tab behavior is preferred.
- **Inventory links** are wired to `zeiglerhondaracine.com` (model-filtered for each
  vehicle; main inventory for SHOP/VIEW ALL; financing app for GET PRE-APPROVED).
- **Images** were resized + converted to WebP (page image weight reduced from ~11 MB
  to <1 MB). Re-run the same optimization if new source images are added.
- **Accessibility:** form fields have visually-hidden `<label>`s (`.sr-only`); decorative
  icons use empty `alt`; photo blocks use `role="img"` + `aria-label`.
