# Theme settings

Theme settings apply to your whole store. Individual sections have their own settings on top of
these, but the settings here decide the overall look and the behavior of things that appear on
every page.

**Where to find them:** open the Theme Editor and click the **gear icon** at the bottom of the
left sidebar, or choose **Theme settings** from the sidebar menu.

Settings are grouped into eleven panels, described below in the order they appear.

---

## Logo

| Setting | What it controls |
| --- | --- |
| **Logo** | Your store logo, shown in the header and — optionally — on the password page. |
| **Logo width** | 60–320px, in 10px steps. This is the desktop width; on mobile the logo is automatically capped at 120px so it never crowds the menu and cart icons. |
| **Favicon** | The small icon in the browser tab. Scaled down to 32 × 32px. |

**Recommended:** a PNG or SVG with a transparent background, supplied at roughly twice your chosen
display width so it stays sharp on high-resolution screens. If no logo is uploaded, the header
shows your store name as styled text — which is a perfectly good option for a wordmark-only brand.

---

## Colors

The theme uses Shopify's native **color schemes**. Instead of setting one palette for the whole
store, you define several schemes, and then each section picks which scheme it uses. This is what
lets you alternate light and dark bands down a page without any code.

### Editing a scheme

Click a scheme to edit these ten values:

| Color | Used for |
| --- | --- |
| **Background** | The section's background color. |
| **Background gradient** | An optional gradient that replaces the flat background. |
| **Text** | Body text, headings, icons, and the color borders are derived from. |
| **Button background** | The fill of primary buttons. |
| **Button label** | The text on primary buttons. |
| **Accelerated button background** | The fill of Shopify's accelerated checkout buttons (Shop Pay, PayPal and similar). |
| **Accelerated button label** | The text on accelerated checkout buttons. |
| **Secondary button label** | The text and border of secondary (outlined) buttons. |
| **Accent** | Links, and highlights throughout the section. |
| **Shadow** | The color shadows are tinted with. |

**The theme ships four schemes**, and the shipped sections reference them:

| Scheme | Role |
| --- | --- |
| `scheme-1` | Light — white background, used for most content |
| `scheme-2` | Tinted — warm off-white, for alternating bands and the footer |
| `scheme-3` | Dark — near-black, for banners, overlays and the transparent header |
| `scheme-4` | Accent — the accent color as a background, for a single high-contrast band |

You can edit all four, and add more. Keeping the light/tinted/dark/accent pattern means fewer
surprises, because the shipped section defaults are written against it.

**Important:** make sure text has real contrast against its background in every scheme. This is
the single most common accessibility failure on a Shopify store. See
[Accessibility](accessibility.md).

### Status colors

These three sit outside the schemes and are shared by every scheme, because they mean the same
thing everywhere.

| Setting | Used for |
| --- | --- |
| **Sale price** | Sale prices and sale badges. |
| **Success** | Confirmation messages, in-stock indicators. |
| **Error** | Form validation errors and failed cart actions. |

---

## Typography

| Setting | What it controls |
| --- | --- |
| **Headings → Font** | The font for all headings. |
| **Headings → Font size scale** | 90–130%. Scales every heading size at once. |
| **Heading case** | **Default** keeps your capitalization as typed. **Uppercase** renders all headings in capitals and adds letter-spacing to keep them readable. |
| **Body → Font** | The font for body text, buttons, labels and navigation. |
| **Body → Font size scale** | 90–120%. Scales all body text at once. |

Fonts come from Shopify's font library. Shopify serves them from its own CDN, so there is no
performance penalty for using them — and no third-party font service to configure.

**Recommended:** one font for headings and one for body is enough. If you pick the same family
for both, vary the weight instead. Keep the body scale at or above 100% unless you have a
specific reason — smaller body text is harder to read on phones.

---

## Layout

| Setting | Range | What it controls |
| --- | --- | --- |
| **Page width** | 1200–1800px | The maximum width content occupies on large screens. Content is centered within it. |
| **Section spacing** | 80–130% | Scales the top and bottom padding of every section at once. Use this to tighten or loosen the whole page rhythm without editing each section. |
| **Grid spacing** | 8–40px | The gap between items in product grids, collection grids and multi-column layouts. |

**Recommended:** 1440px page width suits most catalogs. Go wider only if your product
photography is strong enough to hold a very wide grid.

---

## Appearance

### Corners

| Setting | Range |
| --- | --- |
| **Button corner radius** | 0–30px |
| **Card corner radius** | 0–24px |
| **Input corner radius** | 0–24px |

Keep these consistent with each other. Sharp buttons with heavily rounded cards reads as
accidental rather than deliberate.

### Motion

| Setting | What it controls |
| --- | --- |
| **Enable animations** | Adds subtle transitions and reveal effects across the theme. On by default. |

Visitors whose device is set to reduce motion always see the static version, regardless of this
setting. You do not need to turn animations off for accessibility — the theme already respects
that preference.

### Navigation

| Setting | What it controls |
| --- | --- |
| **Show back to top button** | A floating button that appears once the visitor has scrolled past the first screen. On by default. |

Most useful on long pages — a large collection, a long article, a heavily built home page.

---

## Product cards

These control the product tiles used on collection pages, featured collection sections, search
results, recommendations and cart cross-sells. Some sections can override them individually.

| Setting | Options | Notes |
| --- | --- | --- |
| **Image ratio** | Adapt, Square, Portrait, Landscape | **Adapt** uses each image's own proportions, which looks uneven unless your photography is already consistent. **Square** is the safest default. |
| **Alignment** | Left, Center | Alignment of the title, price and other card text. |
| **Show second image on hover** | On / off | Shows the product's second image when a shopper hovers over the card. Desktop only. Products with only one image are unaffected. |
| **Show vendor** | On / off | Shows the product's Vendor field above the title. Off by default. |
| **Show product rating** | On / off | Requires a product review app that writes to Shopify's standard review metafields. Nothing appears without one. |
| **Show color swatches** | On / off | Shows a preview of each product's color options, up to five then a "+N" marker, linking to the product page. Applies when **Quick add** is None — with quick add on, cards show working option controls instead of a preview. |
| **Quick add** | None, Standard, Bulk | See below. |

### Quick add

| Option | Behavior |
| --- | --- |
| **None** | No add-to-cart control on cards. Shoppers open the product page. |
| **Standard** | An **Add to cart** button that adds one unit. Products with options show those options on the card, so the shopper chooses a variant without leaving the page — the theme never guesses one. Only products with more than 50 variants fall back to **Choose options**. |
| **Bulk** | As Standard, plus a quantity stepper on the card. Suited to wholesale and repeat-purchase catalogs. |

Quick add never appears on sold-out products.

See [Product cards](product-cards.md) for the full behavior.

---

## Badges

| Setting | What it controls |
| --- | --- |
| **Badge position** | Top left, Top right or Bottom left corner of the product image. |
| **Show sale badge** | Shows a badge when a variant has a Compare-at price higher than its price. |
| **Show discount as a percentage** | Turns the sale badge into a calculated percentage saving rather than the word "Sale". |
| **Show sold out badge** | Shows a badge on unavailable products. Takes priority over the sale badge. |

Sale badges are driven entirely by your **Compare-at price** in Shopify admin. Setting a
compare-at price that was never the real selling price is misleading and, in many jurisdictions,
unlawful — so only use it for genuine reductions.

---

## Cart

| Setting | What it controls |
| --- | --- |
| **Cart type** | **Drawer** slides the cart in from the side without leaving the page. **Page** sends shoppers to `/cart`. The cart page exists and works either way. |
| **Cart drawer title** | The heading at the top of the drawer. Leave empty for "Cart". Drawer only. |
| **Cart drawer recommendations** | A collection to suggest products from inside the drawer. Items already in the cart are skipped. Drawer only. |
| **Cart drawer color scheme** | Which color scheme the drawer uses. Drawer only. |
| **Enable cart note** | Lets shoppers add a note to their order, which you see alongside the order in admin. |
| **Show vendor** | Shows the vendor on cart line items. |
| **Show free shipping progress bar** | Shows how much more a shopper needs to spend to reach free shipping. |
| **Free shipping threshold** | The amount, in your store currency, with no symbols or separators — for example `100`. |

> **The free shipping bar does not create free shipping.** It only displays progress towards a
> number you type here. You must also configure a matching free shipping rate under
> **Settings → Shipping and delivery**, or shoppers will be charged for delivery after being told
> they had earned it.

See [Cart](cart.md).

---

## Search

| Setting | What it controls |
| --- | --- |
| **Enable predictive search** | Shows live suggestions as the shopper types. On by default. |
| **Show collections in results** | Includes matching collections in the suggestions. |
| **Show blog posts in results** | Includes matching articles. Off by default. |
| **Show pages in results** | Includes matching pages. Off by default. |

These control the **live suggestions dropdown** only. What appears on the full search results
page is set separately on the Search template. See [Search](search.md).

---

## Social media

Seven fields: **Instagram**, **Facebook**, **TikTok**, **X**, **YouTube**, **Pinterest**,
**LinkedIn**.

Paste the full URL of each profile you have. Leave the rest empty — icons only appear for filled
fields.

These links feed the footer social icons, the social block on the contact page, the password page
and, when organization schema is enabled, your structured data. You set them once here rather
than in each place.

---

## SEO and sharing

| Setting | What it controls |
| --- | --- |
| **Social sharing image** | Used when a page has no image of its own, for example when someone shares your home page. 1200 × 628px recommended. |
| **Enable organization schema** | Adds structured data identifying your business to search engines. On by default. |
| **Organization name** | Your legal or trading name if it differs from your store name. Leave blank to use the store name. |

See [SEO](seo.md) for what the theme handles automatically and what remains your responsibility.
