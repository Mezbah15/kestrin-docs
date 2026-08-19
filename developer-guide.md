# Developer guide

Technical reference for developers working on Kestrin. Merchants do not need this document —
everything a merchant needs is in the guides listed in the [README](README.md).

---

## Overview

| | |
| --- | --- |
| Theme name | Kestrin |
| Version | 1.2.0 |
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

**Nothing uses {% raw %}`{% stylesheet %}`{% endraw %} or {% raw %}`{% javascript %}`{% endraw %}.** Those tags bundle every section's code
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
| `section-customer.css` | Contact form, gift card, account component styling |
| `component-banner.css` | Banner primitives shared by slideshow, image banner, newsletter, video |

`section-header.css` is the exception: it is emitted from `layout/theme.liquid`, not from the
header section, because the announcement bar and the localization form need it too and three
identical tags cost three parses.

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
| `t(key, replacements)` | Substitutes {% raw %}`{{ token }}`{% endraw %} placeholders in a string |
| `debounce(fn, wait)` | |
| `fetchConfig(type)` | Standard fetch options for cart requests |
| `getFocusable(container)` | |
| `trapFocus(container, elementToFocus)` / `removeTrapFocus(container)` | |
| `lockScroll()` / `unlockScroll(force)` | |
| `announce(message)` | Live-region announcement |
| `sectionUrl(url, sections)` | Builds a Section Rendering API URL |
| `isDesignMode()` | True inside the Theme Editor |
| `assets` | Asset URLs fetched on demand — currently `quickAdd` |
| `loadAsset(name, selector, root)` | Appends a script tag once per page, and only if `selector` matches inside `root` |
| `loadQuickAdd(root)` | `loadAsset` for `quick-add.js`; called by anything that renders cards after load |
| `isRTL()` | Reads `documentElement.dir` per call, so the Theme Editor can swap language without a reload |
| `pluralForm(n)` | CLDR plural category for `n` in the active locale, via `Intl.PluralRules` |
| `measureScrollbar()` | Caches the scrollbar width into `--scrollbar-width` outside of a lock |
| `variantPicker` | Option reading shared by the product page and card pickers — `read`, `containers`, `nodes`, `selected`, `match`, `valueAvailable`, `markAvailability` |

### Custom elements

Thirty elements, defined across the script files below. Definitions are guarded with
`customElements.get` first, because several sections may request the same script file.

| Defined in | Elements |
| --- | --- |
| `global.js` | `accordion-group`, `overlay-element`, `quantity-input`, `deferred-media`, `back-to-top`, `share-button` |
| `header.js` | `site-header`, `header-nav`, `mobile-nav`, `announcement-bar`, `localization-selector`, `collapsible-on-mobile` |
| `cart.js` | `cart-items`, `cart-drawer` |
| `product.js` | `product-media`, `variant-selects`, `product-form`, `product-recommendations` |
| `quick-add.js` | `card-variant-picker`, `quick-add-button` |
| `slideshow.js` | `slideshow-carousel`, `background-video` |
| `customer.js` | `form-status`, `copy-text`, `print-button` |
| `facets.js` | `facet-filters` |
| `predictive-search.js` | `predictive-search` |
| `countdown.js` | `countdown-timer` |
| `before-after.js` | `before-after` |
| `pickup-availability.js` | `pickup-availability` |

`<shopify-account>` is Shopify's, not the theme's.

### Script files

| File | Scope |
| --- | --- |
| `global.js` | Core runtime, loaded on every page |
| `header.js` | Header, announcement bar, mobile nav, localization, footer accordions |
| `cart.js` | Cart mutations and section swapping |
| `product.js` | Variant selection, media gallery, product form |
| `quick-add.js` | Variant selection and add-to-cart from product cards |
| `facets.js` | Filtering and sorting |
| `predictive-search.js` | Live search suggestions |
| `slideshow.js` | Slideshow carousel |
| `before-after.js`, `countdown.js`, `pickup-availability.js`, `customer.js` | Single-purpose |

`global.js` and `header.js` are emitted once from `layout/theme.liquid` and load on every page.
Everything else is requested by the section or snippet that needs it, so its definitions are
guarded against a duplicated script tag.

`quick-add.js` is the one script with no tag of its own. Cards arrive after load in several
places — recommendations, a re-rendered drawer, a filtered grid — and markup injected that way
fires no `shopify:section:load`, so Liquid cannot dedupe a per-section tag. Its URL travels in
`#KestrinConfig` instead, and whoever renders cards calls `Kestrin.loadQuickAdd(root)`. The call
is cheap to repeat: it short-circuits once the file is loading, and does nothing at all if the
subtree contains no card picker or quick-add button.

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

- **Snippets carry a {% raw %}`{% comment %}`{% endraw %} header** documenting their accepted parameters.
- **Blocks rendered statically** via {% raw %}`{% content_for 'block' %}`{% endraw %} carry a {% raw %}`{% doc %}`{% endraw %} tag.
- **Translation keys are spelled out literally**, not built with `append`, so Theme Check's
  `TranslationKeyExists` can verify them.
- **Escape user and merchant content** with `| escape` on text output.
- **Prefer {% raw %}`{%- liquid -%}`{% endraw %} blocks** for multi-statement logic over chains of tags.
- **One statement per line inside {% raw %}`{% liquid %}`{% endraw %}** — a newline ends the statement there, so a
  `render` wrapped across lines is a broken tag followed by unparseable ones. Shopify rejects the
  whole file on upload and the storefront blames whichever file *referenced* it, reporting
  "Could not find asset". Standalone {% raw %}`{% render %}`{% endraw %} tags may span lines. Theme Check accepts the
  wrapped form; `bin/check-liquid-tags.js` is what catches it.
- **Gate optional UI on real data**, not on a setting alone — for example, volume pricing renders
  only when `variant.quantity_price_breaks.size > 0`.

### Product schema and structured data

`snippets/structured-data.liquid` emits breadcrumb, article, website and organization schema.
Product schema comes from Shopify's native `| structured_data` filter, to keep the graph free of
duplicates.

**The breadcrumb trail mirrors `snippets/breadcrumbs.liquid` — change both together.**

---

## Localization and direction

The theme renders selectors for what Shopify publishes. It does not own Markets, currency,
conversion or the language list, and nothing in it should start doing so.

**Direction.** `layout/theme.liquid` sets `dir` from `request.locale.text_direction`. Layout
mirroring is the browser's job, which is why CSS is written with logical properties throughout.
`[dir='rtl']` rules exist only where mirroring is not enough:

- `base.css` flips directional icon glyphs (`.icon--arrow-*`, `.icon--chevron-*`) and the native
  select caret.
- Several stylesheets zero out `letter-spacing` on uppercase eyebrows, badges and vendor lines.
  Tracking is a Latin device and it breaks Arabic word shaping.

In JavaScript, `Kestrin.isRTL()` covers the two things CSS cannot mirror: which way a horizontal
arrow key should step (`header.js`, `slideshow.js`) and the sign of a scroll offset
(`product.js`). It reads the attribute per call rather than caching, because the Theme Editor can
swap the previewed language without a reload.

**Arabic typography.** `--font-arabic-fallback` is defined on `:root` but applied only inside the
`[dir='rtl']` block, which re-declares `--font-body-family` and `--font-heading-family` with the
Arabic chain inserted **after** the merchant's face and **before** the generic fallbacks. Order
matters: font matching walks the list per character and stops at the first face carrying the
glyph, so anything placed after the generic is unreachable. An LTR document keeps the merchant's
chain untouched.

**Currency.** Never format money in JavaScript and never compare an amount across a currency
boundary. `snippets/cart-free-shipping.liquid` is the worked example: the threshold is one number
in `shop.currency`, so the bar renders only while `cart.currency.iso_code == shop.currency`.

---

## Honest merchandising

Three areas deliberately constrain what the theme can display. Preserve these constraints.

**Quantity pricing.** Volume tiers come from `variant.quantity_price_breaks`; quantity
minimum/maximum/increment rules come from `variant.quantity_rule`. Shopify populates both only
for B2B customers whose company location has a catalog with quantity breaks, and charges those
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

`snippets/swatch-color.liquid` resolves a single option value to a swatch appearance. It is shared
by the product page picker and the product card, so the two cannot disagree about which options
can be drawn as swatches. It resolves in order:

1. Shopify's swatch image
2. Shopify's swatch color
3. The value name read as a CSS color
4. A built-in map of retail color words, with `multi` and `pattern` markers

It outputs one token — `image:<url>`, `color:<css>`, `multi`, `pattern`, or nothing. Callers
capture the output and split on the first colon. A blank token means "not a color", which is what
separates a real color option from one merely named like it.

Both pickers detect color options by name against the translatable `products.swatch.option_names`
key. **An option only becomes swatches when every value resolves**, so SKU codes and values like
"Black/White" keep the pill layout. Extend the fallback map in `swatch-color.liquid` rather than
loosening this rule.

The card applies one extra rule: an option whose values all carry merchant-set swatch data renders
as swatches whatever it is named. Anything else falls back to a compact select.

---

## Configuration

`config/settings_schema.json` holds `theme_info` plus eleven setting groups: logo, colors,
typography, layout, appearance, product cards, badges, cart, search, social media, and SEO and
sharing.

Color uses `color_scheme_group` with roles mapped so Shopify's own controls behave correctly.
Conditional settings use `visible_if`.

`config/settings_data.json` ships a named preset, **Kestrin**, which is also the current value, so
merchants can restore the original design from the Theme Editor. It defines four color schemes the
sections reference: `scheme-1` light, `scheme-2` tinted, `scheme-3` dark, `scheme-4` accent.

---

## Locales

| File | Contents |
| --- | --- |
| `en.default.json` | Storefront strings (272 keys) |
| `en.default.schema.json` | Theme Editor labels and help text |
| `ar.json`, `de.json`, `es.json`, `fr.json`, `it.json`, `pl.json`, `ro.json` | Storefront strings |

**Editor strings are English only.** Storefront strings exist in all eight languages.

**Release invariant: exact key parity across all eight storefront locale files, and zero broken
translation references.** Adding a storefront string means adding it to all eight files.

Plural keys are the one permitted exception to strict parity: a locale carries exactly the CLDR
categories it declares, so `ar.json` holds six forms where `en.default.json` holds two. Extra
plural leaves are expected; a missing non-plural key is not.

Client-side strings are passed through `#KestrinConfig` in `layout/theme.liquid`. Placeholders
that must survive into JSON — like {% raw %}`{{ count }}`{% endraw %} — are built with `assign` before the output tag,
because a brace-wrapped token cannot be written inline in a Liquid output tag.

Pluralised strings travel as an object keyed by CLDR category rather than as one resolved string,
because Liquid would otherwise freeze the grammar at whatever the count was at first paint. Each
form is probed by addressing the leaf directly; a form the locale does not declare comes back as a
missing-translation marker and is dropped. `Kestrin.t` then selects a form per update using
`Kestrin.pluralForm`.

---

## Section groups

`sections/header-group.json` holds the announcement bar and header;
`sections/footer-group.json` holds the footer. Both are rendered by `layout/theme.liquid` with
{% raw %}`{% sections %}`{% endraw %}.

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

```bash
node bin/check-liquid-tags.js
```

`shopify theme dev` serves the theme locally with hot reload against real store data.
`shopify theme check` must report **zero offenses** before any release.

`bin/check-liquid-tags.js` needs no dependencies and covers the one mistake Theme Check passes
silently: a statement wrapped across lines inside a {% raw %}`{% liquid %}`{% endraw %} tag. Shopify rejects such a file
at upload, so it never reaches the theme and the storefront reports a missing asset against a
different file. Run it before pushing.

`.shopifyignore` excludes Markdown files (except `templates/*.md`), `.git`, `.github`,
`node_modules` and the config files themselves from uploads — so this `docs/` directory is not
deployed to the store.

---

## Release checklist

- [ ] `shopify theme check` — zero offenses
- [ ] `node bin/check-liquid-tags.js` — no wrapped statements
- [ ] Exact key parity across all eight storefront locale files (plural leaves excepted)
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

**Add translations to all eight storefront locales** for any new storefront string, with every
plural form each locale declares.

**Write direction-neutral CSS.** Use logical properties (`padding-inline`, `inset-inline-start`,
`text-align: start`) so RTL needs no second rule. Reserve `[dir='rtl']` for the handful of things
mirroring cannot fix on its own — icon flips and letter-spacing on uppercase labels. In JavaScript,
use `Kestrin.isRTL()` for anything with a horizontal sign: arrow-key direction and scroll offsets.

**Run Theme Check before committing.**
