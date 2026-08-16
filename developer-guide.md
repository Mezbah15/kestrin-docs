# Developer guide

Technical reference for developers working on Kestrin. Merchants do not need this document —
everything a merchant needs is in the guides listed in the [README](README.md).

---

## Overview

| | |
| --- | --- |
| Theme name | Kestrin |
| Version | 1.0.0 |
| Author | MezTech |
| Architecture | Shopify Online Store 2.0 |
| Build step | None |
| JavaScript framework | None |
| CSS framework | None |
| Package manager | Not used |
| Theme Check | `theme-check:recommended`, zero offenses |

There is nothing to compile. The repository is the theme; `shopify theme push` deploys it as-is.

---

## Directory structure

```
assets/     Design system (base.css), core runtime (global.js), page-scoped CSS and JS
blocks/     Theme blocks — group, text
config/     settings_schema.json and settings_data.json
layout/     theme.liquid, password.liquid
locales/    Storefront strings and editor strings
sections/   All sections, plus header/footer section-group JSON
snippets/   Shared components — cards, price, cart items, facets, media, icons
templates/  JSON templates, plus gift_card.liquid
```

**No `templates/customers/`.** Sign-in and the account menu are delegated to Shopify's hosted
`<shopify-account>` component in `snippets/customer-account.liquid`, so the theme ships no
customer templates.

---

## Design tokens

All color, spacing, typography, radius and motion values are CSS custom properties emitted by
`layout/theme.liquid` from theme settings.

**Sections never hard-code a color or a spacing value.** Color schemes use Shopify's native
`color_scheme_group`, so every section is recolorable from the Theme Editor.

Tokens emitted include:

| Group | Examples |
| --- | --- |
| Color, per scheme | `--color-background`, `--color-foreground`, `--color-button`, `--color-accent`, `--border-color` |
| Status color | `--color-sale`, `--color-success`, `--color-error` |
| Typography | `--font-body-family`, `--font-heading-family`, `--text-xs` … `--text-h0` |
| Layout | `--page-width`, `--page-margin`, `--grid-gap` |
| Spacing | `--space-1` … `--space-12`, scaled by `--spacing-scale` |
| Radius | `--radius-button`, `--radius-card`, `--radius-input` |
| Motion | `--duration-short`, `--duration-default`, `--duration-long` |
| Layers | `--layer-backdrop` (30), `--layer-overlay-panel` (31), `--layer-overlay` (40) |

Layer values not in that list are local to their component: dropdown panels 5, header 20,
localization 25, skip link 100.

Heading and body scales are ratios (`--heading-scale`, `--body-scale`) applied through `calc()`,
so a single setting rescales the whole type ramp.

---

## CSS architecture

**Page-scoped assets.** Each section loads only the CSS it needs via `asset_url | stylesheet_tag`.
Shopify deduplicates repeated stylesheet tags, so a shared stylesheet requested by three sections
is downloaded once.

**Nothing uses `{% stylesheet %}` or `{% javascript %}`.** Those tags bundle every section's code
into a single file served on every page, which defeats page-scoping.

| File | Loaded by |
| --- | --- |
| `base.css` | `layout/theme.liquid` — every page |
| `component-card.css` | Any section rendering product cards |
| `component-cart.css` | Cart drawer, cart page |
| `section-header.css` | Header, localization form |
| `section-footer.css` | Footer |
| `section-main-product.css` | Product page |
| `section-collection.css` | Collection, collections list |
| `section-search.css` | Search, predictive search |
| `section-blog.css` | Blog, article |
| `section-marketing.css` | Marketing sections |
| `section-slideshow.css` | Slideshow |
| `section-customer.css` | Account component styling |

**Breakpoints.** Three, min-width only:

```css
@media (min-width: 750px)  { }  /* large phone / tablet */
@media (min-width: 990px)  { }  /* desktop */
@media (min-width: 1400px) { }  /* large desktop */
```

Write mobile-first. Do not add breakpoints.

---

## JavaScript architecture

**No framework, no build step, no bundler.**

Components are **custom elements**, which means they re-initialize automatically when the Theme
Editor replaces section markup — no `shopify:section:load` listeners needed.

### The global

`window.Kestrin`, populated by `assets/global.js` from the `#KestrinConfig` JSON block in
`layout/theme.liquid`.

| Member | Purpose |
| --- | --- |
| `routes` | `root`, `cart`, `cartAdd`, `cartChange`, `cartUpdate`, `predictiveSearch`, `search` |
| `settings` | `cartType`, `predictiveSearch` |
| `strings` | Translated strings for client-side messages |
| `t(key, replacements)` | Substitutes `{{ token }}` placeholders in a string |
| `debounce(fn, wait)` | |
| `fetchConfig(type)` | Standard fetch options for cart requests |
| `getFocusable(container)` | |
| `trapFocus(container, elementToFocus)` / `removeTrapFocus(container)` | |
| `lockScroll()` / `unlockScroll(force)` | |
| `announce(message)` | Live-region announcement |
| `sectionUrl(url, sections)` | Builds a Section Rendering API URL |
| `isDesignMode()` | True inside the Theme Editor |

### Custom elements

```
accordion-group      background-video     cart-items          facet-filters
announcement-bar     before-after         collapsible-on-mobile  header-nav
back-to-top          cart-drawer          countdown-timer     localization-selector
mobile-nav           overlay-element      pickup-availability predictive-search
quantity-input       quick-add-button     share-button        site-header
slideshow-carousel   deferred-media
```

### Script files

| File | Scope |
| --- | --- |
| `global.js` | Core runtime, loaded on every page |
| `header.js` | Header, announcement bar, mobile nav, localization, footer accordions |
| `cart.js` | Cart mutations and section swapping |
| `product.js` | Variant selection, media gallery, product form |
| `quick-add.js` | Add-to-cart from product cards |
| `facets.js` | Filtering and sorting |
| `predictive-search.js` | Live search suggestions |
| `slideshow.js` | Slideshow carousel |
| `before-after.js`, `countdown.js`, `pickup-availability.js`, `customer.js` | Single-purpose |

`header.js` is requested by several sections, so its definitions are guarded against a duplicated
script tag.

---

## Data flow

**Cart mutations, filtering, sorting, variant changes and predictive search all use the Section
Rendering API.** Markup and money are rendered in Liquid and swapped in.

**The theme never builds HTML in JavaScript and never formats currency client-side.** This keeps
localization, market pricing and discount display correct in every context, because Shopify
renders them.

### Cart section swapping

Every mutation POSTs to `Kestrin.routes.cartChange` or `cartUpdate` with a `sections` parameter,
and the returned markup replaces the children of each `[data-cart-section]` element.

`data-cart-section` is shared by `cart.js`, `quick-add.js` and `product.js`, so one request
refreshes the cart page, the drawer and the header bubble together.

`data-cart-section` on the drawer must match the file name of `sections/cart-drawer.liquid`.

---

## Liquid conventions

- **Snippets carry a `{% comment %}` header** documenting their accepted parameters.
- **Blocks rendered statically** via `{% content_for 'block' %}` carry a `{% doc %}` tag.
- **Translation keys are spelled out literally**, not built with `append`, so Theme Check's
  `TranslationKeyExists` can verify them.
- **Escape user and merchant content** with `| escape` on text output.
- **Prefer `{%- liquid -%}` blocks** for multi-statement logic over chains of tags.
- **Gate optional UI on real data**, not on a setting alone — for example, volume pricing renders
  only when `variant.quantity_price_breaks.size > 0`.

### Product schema and structured data

`snippets/structured-data.liquid` emits breadcrumb, article, website and organization schema.
Product schema comes from Shopify's native `| structured_data` filter, to keep the graph free of
duplicates.

**The breadcrumb trail mirrors `snippets/breadcrumbs.liquid` — change both together.**

---

## Honest merchandising

Three areas deliberately constrain what the theme can display. Preserve these constraints.

**Quantity pricing.** Volume tiers come from `variant.quantity_price_breaks`; quantity
minimum/maximum/increment rules come from `variant.quantity_rule`. Shopify populates both only
for B2B customers whose company location has a catalogue with quantity breaks, and charges those
prices at checkout. The tier list is gated on `breaks.size > 0`.

There is deliberately **no setting for merchant-typed discount tiers**. Liquid cannot read an
automatic discount rule or a Shopify Function at render time, so a typed table would be a promise
the theme cannot keep. Cart lines render `line_item.final_price` as the unit price and list each
discount allocation, so the unit price, line total and discount always agree.

**Stock.** `snippets/product-inventory.liquid` reads `variant.inventory_quantity`,
`inventory_management` and `available`. Untracked inventory reports availability without a
number; a variant available at zero tracked stock is shown as backordered. The block is
variant-aware through the Section Rendering API, and if that request fails the stock text is
cleared rather than left describing the previous variant. **No number is ever invented.**

**Countdown.** The countdown section renders an absolute merchant-supplied timestamp, so a cached
page cannot show a stale clock. It never loops or resets. There is no per-visitor or evergreen
mode.

---

## Color swatch resolution

`snippets/product-variant-picker.liquid` detects color options by name against the translatable
`products.swatch.option_names` key, then resolves each value in order:

1. Shopify's swatch image
2. Shopify's swatch color
3. The value name read as a CSS color
4. A built-in map of retail color words, with `multi` and `pattern` markers

**An option only becomes swatches when every value resolves**, so SKU codes and values like
"Black/White" keep the pill layout. Extend the fallback map rather than loosening this rule.

---

## Configuration

`config/settings_schema.json` defines eleven groups: theme info, logo, colors, typography,
layout, appearance, product cards, badges, cart, search, social media, and SEO and sharing.

Color uses `color_scheme_group` with roles mapped so Shopify's own controls behave correctly.
Conditional settings use `visible_if`.

`config/settings_data.json` holds the shipped defaults, including the three color schemes the
sections reference (`scheme-1` light, `scheme-2` tinted, `scheme-3` dark).

---

## Locales

| File | Contents |
| --- | --- |
| `en.default.json` | Storefront strings |
| `en.default.schema.json` | Theme Editor labels and help text |
| `fr.json`, `de.json`, `es.json`, `it.json` | Storefront strings |

**Editor strings are English only.** Storefront strings exist in all five languages.

**Release invariant: exact key parity across all five storefront locale files, and zero broken
translation references.** Adding a storefront string means adding it to all five files.

Client-side strings are passed through `#KestrinConfig` in `layout/theme.liquid`. Placeholders
that must survive into JSON — like `{{ count }}` — are built with `assign` before the output tag,
because a brace-wrapped token cannot be written inline in a Liquid output tag.

---

## Section groups

`sections/header-group.json` holds the announcement bar and header;
`sections/footer-group.json` holds the footer. Both are rendered by `layout/theme.liquid` with
`{% sections %}`.

The cart drawer and back-to-top button are rendered directly from the layout rather than
occupying a section group, because they are theme behavior rather than merchant-placed content.

Section `enabled_on` / `disabled_on` values control where each section can be added. Marketing
sections declare `{"groups": ["header", "footer"]}` as a *disabled* set so they remain available
on every template.

---

## Development workflow

Requires [Shopify CLI](https://shopify.dev/docs/api/shopify-cli) 3.x.

```bash
shopify theme dev --store your-store.myshopify.com
```

```bash
shopify theme check
```

```bash
shopify theme push --unpublished
```

`shopify theme dev` serves the theme locally with hot reload against real store data.
`shopify theme check` must report **zero offenses** before any release.

`.shopifyignore` excludes Markdown files (except `templates/*.md`), `.git`, `.github`,
`node_modules` and the config files themselves from uploads — so this `docs/` directory is not
deployed to the store.

---

## Release checklist

- [ ] `shopify theme check` — zero offenses
- [ ] Exact key parity across all five storefront locale files
- [ ] Zero broken translation references
- [ ] `theme_version` bumped in `config/settings_schema.json`
- [ ] [Changelog](changelog.md) updated
- [ ] Every new merchant-facing setting has editor locale strings with a useful `info`
- [ ] New sections carry a preset where merchants should be able to add them
- [ ] Tested at all three breakpoints
- [ ] Keyboard and screen reader pass on anything new and interactive
- [ ] Reduced-motion path verified for anything animated

---

## Safe customization principles

For anyone extending the theme:

**Add rather than edit.** A new snippet or section survives an update; an edited file has to be
re-merged.

**Use tokens, never literals.** No hard-coded colors, spacings or radii. If a token is missing,
add one in `layout/theme.liquid` rather than hard-coding a value in a section.

**Keep assets page-scoped.** Load new CSS and JS from the section that needs it. Do not add to
`base.css` unless it genuinely applies to every page.

**Build components as custom elements** so they survive Theme Editor re-renders.

**Render markup and money in Liquid**, swapping it in via the Section Rendering API. Do not build
HTML strings in JavaScript and do not format currency client-side.

**Do not display anything Shopify will not honour.** No invented stock numbers, no typed discount
tables, no evergreen countdowns. If Liquid cannot verify it at render time, do not render it.

**Respect reduced motion** in anything animated.

**Add translations to all five storefront locales** for any new storefront string.

**Run Theme Check before committing.**
