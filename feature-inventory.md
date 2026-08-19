# Feature inventory

Every significant capability in Kestrin, with its real status verified against the code rather
than against a section existing. Read this before promising a customer something.

**Status meanings**

| | |
| --- | --- |
| **Implemented** | Present and functional end to end |
| **Partial** | Present, but narrower than the name suggests — see the note |
| **Shopify** | Provided by the Shopify platform; the theme surfaces it but does not implement it |
| **Not implemented** | Absent by design. The note says why |

---

## Foundations

| Feature | Status | Where | Notes |
| --- | --- | --- | --- |
| Online Store 2.0 architecture | Implemented | `templates/*.json`, `sections/`, `blocks/` | 12 JSON templates; `gift_card.liquid` is the one Liquid template |
| Design tokens from theme settings | Implemented | `layout/theme.liquid` | Color, type, spacing, radius, motion, layers |
| Native color schemes | Implemented | `config/settings_schema.json` | `color_scheme_group` with roles mapped; four schemes ship |
| Theme style preset | Implemented | `config/settings_data.json` | Named **Kestrin**; restores the shipped design |
| Theme blocks | Partial | `blocks/group.liquid`, `blocks/text.liquid` | Two blocks, accepted only by `custom-section` and by `group` itself |
| App blocks (`@app`) | Implemented | 21 sections + `blocks/group.liquid` | Product, collection, cart, search, blog, article, page, and every marketing section |
| Dedicated Apps section | Implemented | `sections/apps.liquid` | Addable to any template outside the header and footer groups |
| No build step | Implemented | — | No package manager, bundler or dependencies |

---

## Header, navigation and announcement bar

| Feature | Status | Where | Notes |
| --- | --- | --- | --- |
| Three header layouts | Implemented | `sections/header.liquid` | Logo left/nav inline, logo left/nav below, logo center/nav below |
| Static, sticky, reveal-on-scroll | Implemented | `header.js` → `site-header` | The section wrapper sticks, not the inner `<header>` |
| Transparent header | Partial | `sections/header.liquid` | Home page only (`transparent_mode: index`), with its own color scheme |
| Three-level navigation | Implemented | `header.js` → `header-nav`, `snippets/header-mega-menu.liquid` | Rendered as links, dropdowns or mega menus from the menu's own structure |
| Mega menu | Implemented | `sections/header.liquid` blocks | Up to 8 blocks, each targeting a top-level item by position, 2–5 columns, optional promotion |
| Mobile navigation drawer | Implemented | `snippets/header-mobile-nav.liquid`, `header.js` → `mobile-nav` | Panelled, one panel per level; inactive panels are made inert |
| Header search (icon / field / hidden) | Implemented | `sections/header.liquid`, `snippets/search-form.liquid` | |
| Cart icon with live count | Implemented | `sections/cart-icon-bubble.liquid` | Refreshed by the same request as every cart mutation |
| Announcement bar | Implemented | `sections/announcement-bar.liquid`, `header.js` | Up to 6 blocks, static or rotating, per-block color scheme and icon |
| Announcement dismissal | Implemented | `header.js` → `announcement-bar` | Scope: none / single announcement / whole bar. Persistence: page, session, N days, forever |
| Back to top | Implemented | `snippets/back-to-top.liquid`, `global.js` | Global setting, rendered from the layout |

---

## Product

| Feature | Status | Where | Notes |
| --- | --- | --- | --- |
| Product page from blocks | Implemented | `sections/main-product.liquid` | 16 block types; 14 present in the shipped template |
| Media gallery layouts | Implemented | `snippets/product-media-gallery.liquid` | Stacked, thumbnails left, thumbnails below; carousel or stacked on mobile |
| Image zoom on hover | Implemented | `product.js` → `product-media` | Setting-gated; respects reduced motion |
| Video and external video in gallery | Implemented | `snippets/product-media-gallery.liquid` | Hosted video via `video_tag`, YouTube/Vimeo via `external_video_tag`, both deferred |
| 3D models | Implemented | `snippets/product-media-gallery.liquid` | `model_viewer_tag`, revealed on interaction |
| Variant picker | Implemented | `snippets/product-variant-picker.liquid`, `product.js` | Radios or dropdowns; unreachable combinations are marked before they are clicked |
| Color swatches | Implemented | `snippets/swatch-color.liquid` | Shopify swatch image → swatch color → CSS color name → built-in retail color map. An option becomes swatches only when every value resolves |
| Variant selection without JavaScript | Implemented | `snippets/product-variant-picker.liquid` | `<noscript>` fallback form |
| Inventory / stock state | Implemented | `snippets/product-inventory.liquid` | In stock, low stock, backordered, sold out. Untracked inventory reports availability with no number |
| Low-stock bar and count | Implemented | `snippets/product-inventory.liquid` | Both optional, both derived from real `inventory_quantity` |
| Quantity rules | Shopify | `snippets/quantity-input.liquid`, `variant-quantity-max.liquid` | Min/max/increment come from `variant.quantity_rule`; Shopify populates it for B2B |
| Volume pricing tiers | Shopify | `sections/main-product.liquid` | From `variant.quantity_price_breaks`, gated on `size > 0`. B2B catalogs only |
| Merchant-typed discount tiers | **Not implemented** | — | Deliberate. Liquid cannot read an automatic discount or a Shopify Function at render time, so a typed table would be a promise the theme cannot keep |
| Pickup availability | Implemented | `snippets/pickup-availability.liquid`, `pickup-availability.js` | Uses Shopify's pickup availability endpoint |
| Payment terms | Shopify | `snippets/product-buy-buttons.liquid` | Rendered by Shopify's `form.payment_terms` |
| Gift card recipient form | Shopify | `snippets/product-buy-buttons.liquid` | Shopify's recipient fields, shown for gift card products |
| Share | Implemented | `snippets/share-button.liquid`, `global.js` | Web Share API where available, copy-link fallback |
| Size chart | Implemented | `snippets/product-variant-picker.liquid` | Opens a merchant-chosen page in a dialog |
| Product recommendations | Shopify | `sections/product-recommendations.liquid` | Shopify's recommendations API; `related` or `complementary` intent |
| Product structured data | Shopify | `snippets/structured-data.liquid` | Shopify's `| structured_data` filter, to keep the graph duplicate-free |

---

## Collections, search and filtering

| Feature | Status | Where | Notes |
| --- | --- | --- | --- |
| Collection page | Implemented | `sections/main-collection.liquid` | Banner, description, grid, filters, sorting, pagination |
| Collection list page | Implemented | `sections/main-list-collections.liquid` | |
| Storefront filtering | Shopify | `snippets/facets.liquid`, `facets.js` | Filters come from Shopify's Search & Discovery app. The theme renders whatever is configured; with none configured, no sidebar is reserved |
| Filter layouts | Implemented | `snippets/facets.liquid` | Sidebar, horizontal, drawer — one filter tree, three layouts from CSS |
| Sorting | Shopify | `snippets/facets.liquid` | Shopify's sort options |
| Filtering without JavaScript | Implemented | `snippets/facets.liquid` | The same form submits as a normal GET |
| Filter/sort history | Implemented | `facets.js` | URL is updated and `popstate` restores state |
| Search results page | Implemented | `sections/main-search.liquid` | Products, articles and pages, each toggleable; filterable and sortable |
| Predictive search | Implemented | `sections/predictive-search.liquid`, `predictive-search.js` | Products always; collections, articles and pages by setting |
| Search without JavaScript | Implemented | `snippets/search-form.liquid` | `<noscript>` path |
| Pagination | Implemented | `snippets/pagination.liquid` | `rel="prev"` / `rel="next"`, anchored back to the grid |

---

## Product cards and quick add

| Feature | Status | Where | Notes |
| --- | --- | --- | --- |
| Product card | Implemented | `snippets/card-product.liquid` | One card everywhere: grids, recommendations, search, drawer |
| Secondary image on hover | Implemented | `snippets/card-product.liquid` | Marked decorative for screen readers |
| Sale and sold-out badges | Implemented | `snippets/card-badges.liquid` | Sale badge as percentage optional; position configurable |
| Vendor, rating, price | Implemented | `snippets/card-product.liquid`, `rating.liquid`, `price.liquid` | Rating needs a review app writing Shopify's standard metafields |
| Card swatches | Implemented | `snippets/card-variant-picker.liquid` | Falls back to a compact select when values do not resolve as colors |
| Quick add — standard | Implemented | `quick-add.js` → `quick-add-button` | Single-variant products add directly |
| Quick add — bulk | Implemented | `quick-add.js` | Multi-variant selection from the card |
| Deferred card variant work | Implemented | `global.js`, `quick-add.js` | `quick-add.js` is fetched once per page, only when card pickers are present |

---

## Cart

| Feature | Status | Where | Notes |
| --- | --- | --- | --- |
| Cart drawer | Implemented | `snippets/cart-drawer.liquid`, `cart.js` → `cart-drawer` | Focus trapped, Escape to close, scroll locked, focus returned |
| Cart page | Implemented | `sections/main-cart.liquid` | Both always exist; the setting only decides what the icon opens |
| Quantity change and remove | Implemented | `cart.js` → `cart-items` | Debounced, with a stock cap and a spoken message when capped |
| Cart note | Implemented | `snippets/cart-items.liquid`, `cart.js` | Debounced save, announced when saved |
| Line item properties and SKU | Implemented | `snippets/cart-items.liquid` | Setting-gated |
| Discount display | Implemented | `snippets/cart-items.liquid`, `price.liquid` | Lines render `line_item.final_price`, and every discount allocation is listed, so unit price, line total and discount agree |
| Free shipping progress bar | Partial | `snippets/cart-free-shipping.liquid` | Shown **only** in the shop's primary currency. Shopify exposes no per-market threshold, so the bar is hidden rather than wrong elsewhere |
| Drawer recommendations | Implemented | `snippets/cart-drawer.liquid` | From a merchant-chosen collection |
| Discount code entry in cart | **Not implemented** | — | Shopify accepts discount codes at checkout, not in the cart |

---

## Content templates

| Feature | Status | Where | Notes |
| --- | --- | --- | --- |
| Home page | Implemented | `templates/index.json` | Ships populated with 22 section instances covering every content section |
| Page template | Implemented | `sections/main-page.liquid` | |
| Blog and article | Implemented | `sections/main-blog.liquid`, `main-article.liquid` | Tag filtering, reading time, comment counts, related posts, prev/next |
| Article comments | Shopify | `snippets/article-comments.liquid` | Shopify's comment form and moderation |
| Contact form | Shopify | `sections/contact-form.liquid` | Shopify's `form 'contact'`. Optional phone and order-number fields, details, map and social blocks |
| Contact map | Partial | `sections/contact-form.liquid` | A merchant-supplied embed URL, loaded only when the visitor asks |
| 404 page | Implemented | `sections/main-404.liquid` | Optional search and a product grid |
| Password page | Implemented | `layout/password.liquid`, `sections/main-password.liquid` | Own layout, optional newsletter and social |
| Gift card | Implemented | `templates/gift_card.liquid` | Copy-code and print, via `customer.js` |
| Breadcrumbs | Implemented | `snippets/breadcrumbs.liquid` | Mirrors the BreadcrumbList schema; setting-gated per template |
| Newsletter | Shopify | `sections/newsletter.liquid`, footer block | Shopify's `form 'customer'`; subscribers land in Shopify admin |

---

## Marketing sections

All 21 of these can be added to any template outside the header and footer groups. Each has a
preset, a color scheme and top/bottom padding.

| Section | Status | Notes |
| --- | --- | --- |
| Slideshow | Implemented | Up to 8 slides, autoplay with a pause control, arrows, dots, two transitions |
| Image banner | Implemented | Separate mobile image, two buttons, overlay opacity and overlay scheme |
| Featured collection | Implemented | Grid or mobile carousel, quick add |
| Featured product | Implemented | |
| Collection list | Implemented | |
| Image with text | Implemented | |
| Multicolumn | Implemented | Image or icon per column |
| Collapsible content | Implemented | Optional image; content from richtext or a page |
| Testimonials | Implemented | Optional ratings and avatars |
| Logo list | Implemented | Grid or marquee, pausable, optional grayscale |
| Marquee | Implemented | Text and icons, pause on hover |
| Featured blog | Implemented | |
| Video | Implemented | Hosted or YouTube/Vimeo; facade, inline or background presentation |
| Before and after | Implemented | A native range input drives the comparison, so it is draggable and keyboard-operable for free |
| Countdown | Partial | An absolute merchant-supplied end date only. No evergreen or per-visitor timer, by design |
| Newsletter | Implemented | Optional background image and name field |
| Rich text | Implemented | |
| Custom section | Implemented | Background image plus `@theme` and `@app` blocks |
| Custom Liquid | Implemented | |
| Contact form | Implemented | Also usable on the home page |
| Apps | Implemented | App blocks only |

---

## Customer accounts

| Feature | Status | Where | Notes |
| --- | --- | --- | --- |
| Sign in, account menu, order history | Shopify | `snippets/customer-account.liquid` | Shopify's hosted `<shopify-account>` component. Rendered only when customer accounts are enabled |
| Theme-rendered account templates | **Not implemented** | — | Deliberate. No `templates/customers/`; Shopify owns the entire account experience |

---

## Localization

| Feature | Status | Where | Notes |
| --- | --- | --- | --- |
| Storefront translations | Implemented | `locales/` | 8 languages, exact key parity, 272 storefront keys |
| Theme Editor translations | **Not implemented** | `locales/en.default.schema.json` | English only |
| Language selector | Implemented | `snippets/localization-form.liquid` | Renders only when more than one language is published. Works without JavaScript |
| Country/region selector | Implemented | `snippets/localization-form.liquid` | Renders only when Markets offers more than one country. Works without JavaScript |
| Markets, currency, conversion | Shopify | — | The theme reads and displays; it never converts or formats money itself |
| RTL layout | Implemented | `base.css` and every stylesheet, `global.js`, `header.js`, `slideshow.js`, `product.js` | Logical properties, icon mirroring, reversed arrow keys, tracking removed from uppercase labels |
| Arabic font fallback | Implemented | `layout/theme.liquid` | Naskh-first chain applied only under `[dir='rtl']`, inserted before the generic fallbacks |
| Client-side plural forms | Implemented | `layout/theme.liquid`, `global.js` | Every CLDR form the locale declares travels in `#KestrinConfig`; `Intl.PluralRules` selects per update |

---

## Accessibility

| Feature | Status | Where |
| --- | --- | --- |
| Skip to content link | Implemented | `layout/theme.liquid` |
| Focus trapping, stacked for nested overlays | Implemented | `global.js` |
| Scroll locking with reference counting | Implemented | `global.js` |
| Live-region announcements | Implemented | `global.js`, used by cart, facets, predictive search, pickup |
| Inert off-screen mobile nav panels | Implemented | `header.js` |
| Reduced-motion handling | Implemented | `base.css`, `section-marketing.css`, `header.js`, `slideshow.js`, `product.js` |
| Slideshow pause control | Implemented | `sections/slideshow.liquid` |
| Landmarks, `role="list"`, `aria-current` | Implemented | Throughout |
| Accessible form errors | Implemented | `aria-invalid`, `aria-describedby`, `role="alert"` |
| Decorative images marked as such | Implemented | `snippets/card-product.liquid` and others |

---

## SEO

| Feature | Status | Where | Notes |
| --- | --- | --- | --- |
| Title, meta description, canonical | Implemented | `snippets/meta-tags.liquid`, `layout/theme.liquid` | Title carries tag and page number |
| `noindex,follow` on search pages | Implemented | `snippets/meta-tags.liquid` | |
| Open Graph and Twitter Card | Implemented | `snippets/meta-tags.liquid` | Absolute image URL, correct dimensions, product price and availability, article dates and tags |
| BreadcrumbList, BlogPosting, WebSite, Organization schema | Implemented | `snippets/structured-data.liquid` | Organization is setting-gated |
| Product schema | Shopify | `snippets/structured-data.liquid` | |
| `robots.txt`, sitemap, URL handles, redirects | Shopify | — | The theme does not override them |

---

## Performance

| Feature | Status | Where |
| --- | --- | --- |
| Page-scoped CSS and JS | Implemented | Every section |
| Shared scripts emitted once from the layout | Implemented | `layout/theme.liquid` |
| On-demand `quick-add.js` | Implemented | `global.js` → `loadAsset` |
| Conditional font preload | Implemented | `layout/theme.liquid` |
| Responsive images with `srcset` and `sizes` | Implemented | Throughout |
| Lazy loading below the fold | Implemented | Throughout |
| Deferred video and map | Implemented | `global.js` → `deferred-media`, `sections/video.liquid`, `contact-form.liquid` |
| Background video paused off screen | Implemented | `slideshow.js` → `background-video` |
| Scrollbar measured once while idle | Implemented | `global.js` |
| Scroll reveal through one observer | Implemented | `global.js` |
