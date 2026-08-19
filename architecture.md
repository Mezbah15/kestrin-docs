# Theme architecture

How Kestrin is put together, and why. This is the map; the [Developer guide](developer-guide.md)
is the reference for conventions and workflow.

---

## Shape of the thing

Kestrin is a Shopify **Online Store 2.0** theme with no build step, no package manager, no
framework and no dependencies. The repository *is* the theme. `shopify theme push` uploads it
as-is, and every file Shopify reads is a file you can read.

That constraint drives most of the decisions below. Anything that would normally be solved by a
bundler — deduplicating a shared script, scoping CSS to a page, passing translated strings to the
client — is solved instead by Liquid, by a JSON config block, or by the browser.

---

## Directory structure

```
assets/       Design system, core runtime, page-scoped CSS and JS. 26 files.
blocks/       Theme blocks: group, text
config/       settings_schema.json (structure), settings_data.json (shipped defaults)
layout/       theme.liquid, password.liquid
locales/      8 storefront locales + en.default.schema.json for the Theme Editor
sections/     38 sections + header-group.json + footer-group.json
snippets/     35 shared components
templates/    12 JSON templates + gift_card.liquid
bin/          check-liquid-tags.js — a release gate, not shipped to the store
docs/         This documentation. Excluded from uploads by .shopifyignore.
```

**There is no `templates/customers/`.** Sign-in and the account menu are delegated to Shopify's
hosted `<shopify-account>` component, rendered by `snippets/customer-account.liquid`.

---

## Rendering flow

A storefront request resolves like this:

{% raw %}
```
templates/<page>.json
  └── names sections + their settings and block order
layout/theme.liquid
  ├── <head>  meta-tags → structured-data, design tokens, base.css, global.js, header.js
  ├── #KestrinConfig   routes, settings and translated strings as JSON
  ├── {% sections 'header-group' %}    announcement-bar, header
  ├── <main>  {{ content_for_layout }}   ← the template's sections render here
  ├── {% sections 'footer-group' %}    footer
  └── cart-drawer, back-to-top          theme behavior, not merchant content
```
{% endraw %}

`gift_card.liquid` and `layout/password.liquid` are the two places that step outside this flow —
`gift_card` is a standalone Liquid template with its own document, and the password page uses its
own layout.

**The cart drawer and back-to-top button are rendered from the layout, not from a section group.**
They are theme behavior rather than merchant-placed content, so a merchant cannot accidentally
remove or reorder them.

---

## Liquid architecture

**Sections own layout and settings. Snippets own components.** A snippet never reads
`section.settings` — everything it needs is passed as a named parameter, documented in a
{% raw %}`{% comment %}`{% endraw %} header at the top of the file. That is what lets `card-product.liquid` render
identically inside a collection grid, a featured collection, search results, product
recommendations and the cart drawer.

The shared components worth knowing about:

| Snippet | Used by |
| --- | --- |
| `card-product`, `card-badges`, `card-sizes`, `card-variant-picker` | Every product grid on the storefront |
| `price` | Cards, product page, cart lines. Accepts overrides so cart lines can show the discounted unit price |
| `swatch-color` | Product page picker and card picker, so the two cannot disagree about what is a color |
| `facets` | Collection and search — one filter tree, three layouts from CSS |
| `cart-items`, `cart-summary`, `cart-free-shipping` | Cart page and cart drawer |
| `meta-tags` → `structured-data` | Every page, from the layout |
| `icon` | Every icon in the theme; one file, one switch |
| `localization-form` | Header, footer and mobile drawer |

**Section groups.** `header-group.json` holds the announcement bar and header; `footer-group.json`
holds the footer. Merchants reorder and configure them in the Theme Editor without touching the
layout.

**Where a section may be placed** is declared in its schema. `main-*` sections are pinned to their
template with `enabled_on`. Marketing sections declare `disabled_on: {"groups": ["header",
"footer"]}` — a disabled set rather than an enabled one, so they remain available on every current
and future template.

---

## Configuration architecture

Three layers, in order of precedence at render time:

1. **`config/settings_schema.json`** — defines what global settings exist. Eleven groups plus
   `theme_info`. Colors use Shopify's native `color_scheme_group` with roles mapped, so Shopify's
   own controls behave correctly. Conditional settings use `visible_if`.
2. **`config/settings_data.json`** — the shipped defaults, published as a named preset (**Kestrin**)
   so merchants can restore the original design after changing things. Defines four color schemes:
   `scheme-1` light, `scheme-2` tinted, `scheme-3` dark, `scheme-4` accent.
3. **Section and block settings** — per-instance, stored in the JSON templates and section groups.

Global settings reach CSS as custom properties emitted by `layout/theme.liquid`, and reach
JavaScript through `#KestrinConfig`. Nothing reads `settings.*` from JavaScript directly.

---

## CSS architecture

**Tokens, then components.** Every color, space, radius, type size and duration is a custom
property emitted from theme settings. Sections never hard-code a color or a spacing value. If a
value is missing, the fix is a new token in the layout, not a literal in a section.

**Page-scoped stylesheets.** Each section requests only the CSS it needs with
`asset_url | stylesheet_tag`; Shopify deduplicates repeated tags, so a stylesheet three sections
want is downloaded once. Nothing uses {% raw %}`{% stylesheet %}`{% endraw %}, which would bundle every section's CSS
onto every page.

**Three breakpoints, min-width only:** 750px, 990px, 1400px. Written mobile-first.

**Direction-neutral by default.** Logical properties throughout (`padding-inline`,
`inset-inline-start`, `text-align: start`), so a right-to-left storefront mirrors without a second
set of rules. `[dir='rtl']` blocks exist only for the things mirroring cannot fix: directional icon
glyphs, the select caret, and letter-spacing on uppercase labels.

---

## JavaScript architecture

**Custom elements, no framework, no bundler.** Every component is a custom element, which means it
re-initializes automatically when the Theme Editor replaces section markup — there are no
`shopify:section:load` listeners to forget. Thirty elements across twelve files; see the
[Developer guide](developer-guide.md#custom-elements) for the full map.

**One global, `window.Kestrin`**, hydrated by `global.js` from the `#KestrinConfig` JSON block.
It carries routes, settings, translated strings and shared helpers — focus trapping, scroll
locking, live-region announcements, plural selection, RTL detection, and the variant-picker logic
shared by the product page and the product card.

**Progressive enhancement is the baseline.** Filtering, sorting, search, the country and language
selectors and the variant pickers are all real forms that submit as ordinary requests when
JavaScript is unavailable. JavaScript intercepts them to avoid a full page load; it does not
create the functionality.

---

## Data flow

**Everything dynamic goes through the Section Rendering API.** Cart mutations, filtering, sorting,
variant changes and predictive search all request rendered markup from Shopify and swap it in.

```
User acts
  → fetch to a Shopify route with ?sections=<ids>
    → Shopify renders the sections in Liquid, in the shopper's locale and market
      → the theme replaces the children of the matching [data-cart-section] / results container
        → Kestrin.loadQuickAdd(newSubtree) for any cards that arrived
          → Kestrin.announce(...) for screen readers
```

**The theme never builds HTML in JavaScript and never formats currency client-side.** That single
rule is what keeps translations, market pricing, discount allocations and tax notes correct in
every context, because Shopify renders them rather than the browser guessing.

One request refreshes several regions: every cart mutation asks for the cart page, the drawer and
the header bubble together, so they cannot drift apart.

---

## Performance architecture

Not a feature list — these are structural properties of the layout above.

- **Page-scoped CSS and JS.** A page without a slideshow never downloads slideshow code.
- **`global.js` and `header.js` are emitted once from the layout**, because three sections wanting
  the same file used to mean three script tags, and a browser parses and executes each one.
- **On-demand assets.** `quick-add.js` has no tag at all; its URL travels in `#KestrinConfig` and
  is requested once, only if matching markup is present.
- **Font preload is conditional** — skipped when the merchant picks a system font, because
  `font_url` has nothing to preload there.
- **Media is deferred.** Third-party video embeds are facades that load a player only on play;
  the contact map loads only when asked; background video pauses off screen.
- **Scrollbar width is measured once while idle**, not when a drawer opens, so opening a drawer
  does not force a synchronous layout.
- **Reveal animations run through one `IntersectionObserver`**, gated on both the merchant's
  animation setting and `prefers-reduced-motion`.

---

## Where to change what

| You want to change… | Go to |
| --- | --- |
| A color, space, radius or type size | `config/settings_schema.json`, then the token in `layout/theme.liquid` |
| What a merchant can configure on a section | That section's {% raw %}`{% schema %}`{% endraw %}, plus `locales/en.default.schema.json` |
| Storefront wording | `locales/en.default.json` and all seven translations |
| A component's markup used in several places | The snippet, not each caller |
| Behavior after a fetch | The relevant custom element in `assets/` |
| What appears on a new store's home page | `templates/index.json` |
| What appears above or below every page | `sections/header-group.json`, `sections/footer-group.json` |
