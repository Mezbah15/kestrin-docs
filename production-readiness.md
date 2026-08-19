# Production readiness

What is finished, what is genuinely limited, what the merchant has to supply, and what must be
tested before publishing. Written against the current code, not against intent.

For the per-feature breakdown, see the [Feature inventory](feature-inventory.md).

---

## State of the theme

| | |
| --- | --- |
| Version | 1.2.0 (`config/settings_schema.json` → `theme_info`) |
| Templates | 12 JSON templates plus `gift_card.liquid`; every storefront page type is covered |
| Sections | 38, of which 21 are addable to any content template |
| Storefront locales | 8, exact key parity |
| Build step | None. The repository is the theme |
| Release gates | `shopify theme check` (zero offenses), `node bin/check-liquid-tags.js` |

Every storefront page type Shopify can route to has a template, every section has editor strings
in `en.default.schema.json`, and every content section carries a preset so merchants can add it.

---

## Known limitations

These are real, verified in the code, and mostly deliberate. Say them out loud rather than
discovering them in a support ticket.

### By design

- **No merchant-typed discount tiers.** Liquid cannot read an automatic discount rule or a Shopify
  Function at render time, so a "buy 3, save 10%" table would be a promise the theme cannot keep.
  Use Shopify's own discounts; the cart picks up the result and renders it accurately.
- **Volume pricing and quantity rules are B2B-only.** They come from
  `variant.quantity_price_breaks` and `variant.quantity_rule`, which Shopify populates only for
  customers whose company location has a catalog. On a retail store they render nothing.
- **The countdown takes an absolute end date only.** No evergreen timer, no per-visitor timer. A
  cached page must not be able to show a stale clock.
- **The free shipping bar appears only in the shop's primary currency.** The threshold is one
  number in one currency and Shopify offers no per-market equivalent, so it is hidden elsewhere
  rather than shown wrong.
- **No `templates/customers/`.** The whole account experience is Shopify's hosted
  `<shopify-account>` component. The theme cannot restyle the account pages beyond the custom
  properties it maps in `section-header.css`.
- **The Theme Editor is English only.** `en.default.schema.json` has no translations. Merchant-facing
  setting labels appear in English regardless of the admin language.

### Practical

- **The transparent header only applies to the home page.** There is no per-template option.
- **Mega menu blocks target a top-level item by position (1–8), not by name.** Reordering the main
  menu moves which item a mega menu attaches to.
- **The mega menu supports up to 8 blocks and 2–5 columns.** Five columns get cramped once a
  promotion is added.
- **Theme blocks are limited to `group` and `text`,** and only `custom-section` (and `group`
  itself) accepts them. Everywhere else, content comes from section-defined blocks.
- **The contact map is a merchant-supplied embed URL.** There is no geocoding, no API key handling
  and no address lookup.
- **The theme ships no Arabic webfont.** RTL typography relies on faces already on the device.
- **Product ratings need a review app** that writes Shopify's standard rating metafields. Without
  one, the rating settings render nothing.
- **Storefront filters need Shopify's Search & Discovery app.** With no filters configured, the
  collection page shows sorting alone and gives the full width to the grid — correct, but it does
  mean "the filters do not show" is usually an admin configuration answer.

---

## Shopify platform dependencies

The theme surfaces these; it does not implement them. If one is misconfigured, the theme cannot
compensate.

| Area | Depends on |
| --- | --- |
| Customer accounts | Customer accounts enabled in admin; the hosted `<shopify-account>` component |
| Filtering | Search & Discovery app, filters configured |
| Search relevance and predictive results | Shopify's search and predictive search endpoints |
| Product recommendations | Shopify's recommendations API and its `related` / `complementary` intents |
| Currency, markets, pricing | Settings → Markets. All money is formatted by Shopify |
| Languages | Settings → Languages. The selector renders what is published |
| Content translation | Translate & Adapt or an equivalent app |
| Product structured data | Shopify's `structured_data` filter |
| `robots.txt`, sitemap, URL handles, redirects | Shopify |
| Checkout, discount codes, payment terms, gift card recipients | Shopify |
| Pickup availability | Shopify's pickup availability endpoint and configured locations |
| Newsletter subscribers, contact form, article comments | Shopify's `customer`, `contact` and comment forms |
| Volume pricing, quantity rules | B2B catalogs |
| Payment icons, Follow on Shop | Shopify |

---

## Configuration the merchant must supply

Nothing below has a sensible default the theme can invent.

**Before the store looks right**

- Logo and favicon (**Theme settings → Logo**). Without a logo the header falls back to the store
  name as a wordmark — workable, but not a finished store.
- Menus: `main-menu` and `footer` at minimum. The header defaults to `main-menu`; the mega menu
  blocks assume top-level items exist.
- Real products with real images. Every image ratio setting assumes consistent source images.
- Color schemes checked for contrast. The shipped four pass, but any edit is the merchant's to
  verify.

**Before the store is honest**

- A free shipping rate under **Settings → Shipping and delivery** that matches the threshold, if
  the free shipping bar is enabled.
- Inventory tracking configured the way stock messages should read.
- A countdown end date that is a real deadline.
- Announcement text that is currently true.

**Before the store ranks or shares well**

- A social sharing image (**Theme settings → SEO and sharing**), 1200 × 628.
- Organization name and social links, if organization schema is left on.
- Page titles, meta descriptions and alt text on the things that matter.

**If selling internationally**

- Markets configured, with currencies and default languages per market.
- Each language **published**, not merely added.
- The localization selectors enabled on the header and/or footer.

---

## Test before publishing

Grouped by what tends to actually break.

**Templates** — open every one on a real store with real data: home, collection, product,
collections list, cart, search, blog, article, page, contact page, 404, password page, gift card.

**Cart**

- [ ] Add to cart from a product page, a card quick add, and a bulk quick add
- [ ] Change quantity and remove a line in both the drawer and the cart page
- [ ] Push a quantity past available stock and confirm the cap message
- [ ] Save a cart note
- [ ] Free shipping bar below, at, and above the threshold — and in a second currency, where it
      should not appear at all
- [ ] Cart type set to Page: the icon links to the cart page and no drawer opens

**Product**

- [ ] Select every variant on a multi-option product; confirm unreachable combinations are marked
- [ ] A sold-out variant, a backordered variant, and an untracked-inventory variant
- [ ] A product with video, and with a 3D model
- [ ] A single-variant product and a product with no image

**Collection and search**

- [ ] Filter, sort, paginate, then use the browser back button
- [ ] A collection with no filters configured
- [ ] Predictive search with results, with no results, and with a slow connection
- [ ] Search with products, articles and pages all enabled

**Header and navigation**

- [ ] All three header layouts, and all three behaviors (static, sticky, reveal)
- [ ] Transparent header over the first home section, then scrolled
- [ ] A three-level menu, as dropdowns and as a mega menu
- [ ] Mobile drawer: forwards, back, and "view all" on every level
- [ ] Announcement bar rotating, and each dismissal persistence option

**Localization**

- [ ] A second published language, switched with the language selector
- [ ] A second country, switched with the country selector — prices change, nothing is
      double-converted
- [ ] Arabic (or another RTL language) published: layout mirrors, arrows point correctly, arrow
      keys step in reading order, Arabic text renders in a proper face
- [ ] A counted message (search results, filter count) at 0, 1, 2, 5 and 100 in each language

**Accessibility**

- [ ] Keyboard-only pass over the header, mobile drawer, cart drawer, filters, predictive search,
      size chart dialog, and the slideshow
- [ ] Escape closes every overlay and returns focus to its opener
- [ ] Screen reader pass over add-to-cart, filter results and search suggestions
- [ ] `prefers-reduced-motion: reduce` — no autoplay, no marquee motion, no background video
- [ ] Contrast checked on every color scheme in use

**Robustness**

- [ ] JavaScript disabled: search, filtering, sorting, variant selection and both localization
      selectors still work
- [ ] All three breakpoints (750, 990, 1400) plus a real phone
- [ ] Theme Editor: add, remove and reorder every section and block without a page reload breaking
      a component

**Release gates**

- [ ] `shopify theme check` — zero offenses
- [ ] `node bin/check-liquid-tags.js` — no wrapped statements
- [ ] Locale key parity across all eight storefront files
- [ ] `theme_version` bumped and the [changelog](changelog.md) updated

---

## What the theme cannot control

Worth setting expectations on, because these arrive as theme bug reports.

- **Checkout.** Appearance and behavior belong to Shopify (and, on Plus, to checkout branding).
- **Customer account pages.** Shopify's hosted component owns them entirely.
- **Currency conversion and market pricing.** Shopify's, always.
- **Search relevance and which products a filter returns.** Shopify's search index.
- **App output.** An app block renders whatever the app renders, including its own CSS and network
  requests. Apps are the single largest variable in a store's performance.
- **Email templates.** Shopify admin → Settings → Notifications.
- **Shipping rates, taxes and discounts.** The theme displays the results; it never computes them.
- **A PageSpeed score.** Scores are measured on a finished store, with its images, apps and
  scripts. The theme contributes a small, page-scoped amount of CSS and JavaScript; the rest is
  what is put on top of it.

---

## Known issues and follow-ups

Observed during the documentation audit. None have been changed — they are recorded here for a
decision.

- **`config/settings_data.json` ships `current: "Kestrin"`**, meaning the preset is also the live
  configuration. This is intentional for a fresh install, but a full `theme push` to a store with
  merchandising in the editor will overwrite it. Ignore `config/settings_data.json` and
  `templates/*.json` when pushing to a populated store.
- **`AGENTS.md` and `copilot-instructions.md` are byte-identical duplicates** (46 KB each) at the
  repository root. Both are excluded from uploads by `.shopifyignore`, so this costs nothing at
  runtime, but one of them should become a pointer to the other.
- **`.vscode/launch.json` targets `http://localhost:8080`**, which is not the port
  `shopify theme dev` serves on (9292 by default). The file is untracked (`.vscode/` is gitignored),
  so it only affects whoever has it locally — but it will not attach to a theme dev session as
  written.
