# Changelog

All notable changes to Kestrin are recorded here.

The version currently installed in your store is shown in the Theme Editor under
**Theme settings**, at the bottom of the sidebar.

---

## [1.2.0]

Right-to-left storefronts, three more languages, and a round of correctness and performance
fixes.

### Added

- **Right-to-left storefronts are fully supported.** Publishing an RTL language mirrors the whole
  layout, flips directional arrows and chevrons, reverses what the left and right arrow keys do in
  menus and slideshows, and drops letter-spacing from uppercase labels where it damages Arabic
  word shaping.
- **Arabic, Polish and Romanian storefront translations**, bringing the theme to eight languages.
- **An Arabic font fallback.** On a right-to-left storefront the theme inserts a Naskh-first chain
  after your chosen font and before the generic fallbacks, so Arabic renders in a proper face
  while Latin text keeps the font you picked. Left-to-right storefronts are unaffected.
- **A fallback favicon**, so a store with no favicon uploaded still gets a real tab icon.

### Changed

- **Counted messages now pick the right grammatical form in the browser.** Search and filter
  counts that update without a page reload carry every form the language declares — six for
  Arabic, four for Polish, three for Romanian — instead of freezing the grammar at whatever the
  count happened to be on first paint.
- **The free shipping bar now appears only in your store's primary currency.** The threshold is a
  single number in a single currency, and Shopify offers no per-market equivalent, so comparing it
  against a cart priced elsewhere could promise free shipping the checkout would not honour. Other
  markets fall back to the shipping rates Shopify actually applies. Nothing to configure.
- **The home page now ships populated** with an instance of every content section, so a new store
  has something to edit rather than an empty canvas.
- **The accent color was darkened** so it clears 4.5:1 contrast on both light color schemes.

### Fixed

- The cart page no longer executes `cart.js` twice.
- The search stylesheet no longer blocks the first paint.
- Per-card variant work is deferred until the card is near the viewport.
- Merchant-entered text is escaped on the way into image `alt` attributes.
- Closed overlays are taken out of the tab order, and the collection page heading order was
  corrected.
- Banner styles were split out of the marketing stylesheet, so pages that only need one no longer
  download both.

---

## [1.1.0]

### Added

- A named theme style, **Kestrin**. The theme now ships a preset, so the original design can be
  restored from the Theme Editor after settings have been changed. No design values changed —
  the preset holds exactly the settings 1.0.0 shipped with.
- An [FAQ](faq.md) covering the questions that come up most often after installing, including the
  logo fallback, three-level menus and the mega menu, storefront filters, color swatches, the size
  chart button and what happens to settings on update.
- A **Custom code and tutorials** policy in [Support](support.md), setting out what happens when
  the theme is edited, and why to duplicate before changing any file.

### Changed

- **Mobile layout options now read the same way in every section.** Sections that offered
  "Grid / Scroll" now offer "Grid / Carousel", matching the wording already used elsewhere. If you
  had chosen Scroll on a featured collection or category list, re-select **Carousel** to keep the
  swipe behavior.

### Fixed

- Featured collections and category lists set to swipe on mobile were rendering as a grid instead.
- The "View all" button under a category list no longer appears when no collections are selected.
- Collection pages no longer reserve an empty filter sidebar before storefront filters have been
  set up. Until you add filters, the page shows sorting on its own and gives the full width to the
  product grid. Filtering scripts are now loaded only on pages that actually offer filtering or
  sorting.

---

## [1.0.0] — Initial release

The first public release. Everything below is present in the theme as supplied; nothing here
describes work planned or in progress.

### Added

**Foundations**

- Online Store 2.0 architecture — JSON templates, sections on every page, reorderable blocks
- Native Shopify color schemes, so any section can be recolored from the Theme Editor
- Global design tokens driven by theme settings: color, typography, spacing, corner radius and
  motion
- Theme settings for logo, colors, typography, layout, appearance, product cards, badges, cart,
  search, social media, and SEO and sharing
- No framework and no build step — nothing to compile before uploading

**Header and navigation**

- Three header layouts: logo left with nav inline, logo left with nav below, logo center with nav
  below
- Static, sticky and reveal-on-scroll header behaviors
- Optional transparent header over the first home page section, with its own color scheme
- Three-level navigation, rendered as plain links, dropdowns or full-width mega menus according to
  menu structure
- Mega menu blocks (up to eight) adding a promotional image, heading, text and button, with a
  configurable column count
- Panelled mobile navigation drawer — one panel per level, with back and "view all" links
- Header search as an icon-and-drawer, an inline field, or hidden
- Customer account entry point using Shopify's hosted account component
- Live cart count with drawer or cart page behavior
- Optional country/region and language pickers in the header, footer and mobile drawer

**Announcement bar**

- Up to six announcement blocks, each with text, link, icon and its own color scheme
- Static or rotating display, with configurable rotation speed
- Dismissal scoped to a single announcement or the whole bar, remembered for a page, a session,
  a set number of days, or permanently
- Separate desktop and mobile visibility

**Sections** (23 addable from the Theme Editor, plus dedicated template, header, footer and cart
sections)

- Marketing: Slideshow, Image banner, Image with text, Rich text, Multicolumn, Collections,
  Featured collection, Featured product, Featured blog, Testimonials, Logo list, Marquee, Video,
  Before and after, Countdown, Collapsible content, Newsletter, Contact form
- Utility: Custom section (with Text and Group blocks), Custom liquid, Apps
- Template sections for product, collection, collections list, cart, search, blog, article, page,
  404 and password

**Product page**

- Three desktop gallery layouts (stacked, thumbnail left, thumbnail below) and two mobile layouts
  (carousel, stacked), with optional full-screen zoom and video looping
- Sixteen block types, all reorderable: vendor, title, price, rating, variant picker, quantity
  selector, buy buttons, inventory, SKU, description, collapsible row, icon with text, share,
  pickup, text and custom liquid
- Variant picker in dropdown, pill or swatch styles, with automatic color swatch detection and an
  optional size chart pop-up
- Inventory display driven by Shopify's own tracking, including backorder state, with a
  configurable low-stock threshold
- Volume pricing from Shopify's B2B quantity price breaks, and quantity rules honoured throughout
- Local pickup availability, gift card recipient fields, and payment terms where configured
- Related and complementary product recommendations

**Collection, search and product cards**

- Configurable grid density, image ratio and card content per template
- Storefront filtering in sidebar, horizontal or drawer layouts, collapsing to a drawer on mobile
- Sorting, pagination, and clear empty states with a one-click filter reset
- Product cards with hover image, sale and sold-out badges, custom badge metafield support,
  color swatches, ratings and quick add in standard or bulk modes

**Cart**

- Cart drawer and cart page, both fully featured
- Quantity changes, line removal and live totals without a page reload
- Optional order note, free shipping progress bar, drawer recommendations and cart page
  recommendations
- Line item properties, vendor and SKU display options
- Automatic discounts and Shopify Functions reflected accurately in line and order totals

**Search**

- Predictive search across products, collections, blog posts and pages, keyboard navigable and
  announced to screen readers
- Full search results page with configurable sources, filtering and sorting

**Footer**

- Configurable column count with menu, text, newsletter, social, contact and image blocks
- Bottom bar with social icons, Follow on Shop button, payment icons, localization pickers,
  policy links and copyright
- Columns collapse to accordions on mobile

**Content templates**

- Blog listing with tag filter and configurable cards
- Article page with featured image, meta, reading time, tags, share, related articles and
  previous/next links
- Page template with content width options, and a dedicated contact template with details, map
  and social blocks
- 404 page with search and an optional product grid
- Password page with logo, message, sign-up form and background image

**SEO and metadata**

- Page titles with tag and pagination awareness, meta descriptions, canonical URLs and
  pagination hints
- Structured data: product, breadcrumbs, blog posting, website search action and organization
- Open Graph and Twitter Card metadata, including product price and currency

**Accessibility**

- Skip-to-content link, visible focus states, focus trapping in drawers and modals, inert
  off-screen panels
- Live announcements for cart, filter and search result changes
- Reduced-motion support across animations, marquees, slideshow autoplay and background video

**Internationalization**

- Storefront text in English, French, German, Spanish and Italian
- Localization forms that work without JavaScript
- Automatic text direction handling

**Apps**

- App blocks supported on the product, collection, cart, search, blog, article, page and 404
  templates, on every marketing section, and through a dedicated Apps section

### Notes on this release

- **Theme naming.** The theme is published as **Kestrin**. **MezTech** is the theme author. Both
  appear in Shopify admin.
- **Pre-release versions.** Versions 0.9.0 through 0.9.2 were internal development builds and
  were not publicly distributed. 1.0.0 is the first release.
- **Quality gates at release.** Shopify Theme Check (`theme-check:recommended`) reports zero
  offenses across 95 files, and all 1,708 translation references resolve — 369 storefront
  references against `en.default.json` and 1,339 editor references against
  `en.default.schema.json`. The five storefront locales hold identical key sets.

---

## Version numbering

Kestrin follows semantic versioning:

| Change | Example | Means |
| --- | --- | --- |
| **Major** | 1.0.0 → 2.0.0 | Significant changes; reconfiguration likely needed |
| **Minor** | 1.0.0 → 1.1.0 | New features and settings, backwards compatible |
| **Patch** | 1.0.0 → 1.0.1 | Fixes and small improvements |

Read the entry for each release before updating, and see [Updating](updating.md) for how to do it
safely.
