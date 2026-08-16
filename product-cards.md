# Product cards

A product card is the tile representing one product in a grid. The same card is used on
collection pages, featured collection sections, search results, product recommendations, cart
recommendations and the 404 page — so configuring it once configures it nearly everywhere.

**Global settings:** Theme Editor → **Theme settings → Product cards** and **Badges**.

Several sections can override those globals for themselves — Featured collection, Collection,
Search results and the 404 page all have their own **Show vendor**, **Show product rating**,
**Quick add** and **Image ratio** settings.

---

## What appears on a card

Reading top to bottom:

| Element | When it appears |
| --- | --- |
| **Product image** | Always. Falls back to a placeholder illustration if the product has no image. |
| **Hover image** | On desktop, when **Show second image on hover** is on and the product has a second image. |
| **Badges** | Sale or Sold out, plus an optional custom badge. See below. |
| **Vendor** | When **Show vendor** is on and the product has a Vendor set. |
| **Title** | Always. Links to the product page. |
| **Rating** | When **Show product rating** is on and a review app has recorded reviews. |
| **Price** | Always, including compare-at price and unit price where they exist. |
| **Options** | When the product has options. Selectable when **Quick add** is on, a preview otherwise. See below. |
| **Quick add** | When **Quick add** is not None and the product is available. |

The whole card is not a single link — the title is the link, and the option and quick add controls
are separate. This is deliberate: it keeps the card usable by keyboard and by screen readers, and
it is what lets a shopper choose a color without being taken off the page.

---

## Product image

| Setting | Options |
| --- | --- |
| **Image ratio** | Adapt, Square, Portrait, Landscape |

**Adapt** uses each image's own proportions, so a grid of mixed-shape photographs will have
uneven rows. It looks excellent when your photography is already consistent and poor when it is
not.

**Square** is the safest default. **Portrait** suits fashion. **Landscape** suits wide products.

Images are served responsively — the browser downloads a size appropriate to the screen, from
160px up to 1100px wide. You do not need to prepare multiple sizes; upload one good image and
Shopify handles the rest. See [Images and media](images-and-media.md).

---

## Hover image

**Show second image on hover** (Theme settings → Product cards) swaps to the product's **second
image** when a shopper hovers over the card.

- Desktop only. There is no hover on a touch screen, so nothing changes on mobile.
- Products with only one image are unaffected — no flicker, no blank.
- It uses image position 2 in Shopify admin, so control it by reordering the product's media.

**Recommended:** on, with a deliberate second image on every product — a back view, a detail, or
the product in use.

---

## Title

The product title exactly as entered in Shopify admin, linking to the product page.

Long titles wrap. If your titles run to two lines in a four-column grid, that is a signal to
shorten them in Shopify rather than to change the theme.

---

## Price and compare-at price

| Situation | What shows |
| --- | --- |
| Normal price | The price. |
| Compare-at price set higher than the price | The sale price in your **Sale price** color, with the compare-at price struck through beside it. |
| Price varies across variants | A "from" price based on the lowest variant. |
| Unit pricing applies | The unit price below, for products sold by weight or volume. |

Prices are formatted by Shopify in the shopper's active currency, so they are correct in every
market you sell to. The theme never formats currency itself.

---

## Badges

Controlled by **Theme settings → Badges**.

| Badge | When it appears |
| --- | --- |
| **Sold out** | The product has no available variants. Takes priority over the sale badge. |
| **Sale** | A variant has a Compare-at price higher than its price. Shows either the word "Sale" or a calculated percentage saving, depending on **Show discount as a percentage**. |
| **Custom** | The product has a `custom.badge` metafield with text in it. |

**Badge position** — Top left, Top right or Bottom left — applies to all of them.

### Custom badges

To show your own badge text on selected products:

1. In Shopify admin, go to **Settings → Custom data → Products**.
2. Add a definition with namespace and key `custom.badge` and type **Single line text**.
3. Open a product, scroll to its metafields, and enter the badge text — for example `New`,
   `Limited`, `Bundle`.

Products without a value show no custom badge. Keep the text to one or two words; a long badge
overlaps the image awkwardly.

---

## Options and color swatches

What a product's options look like on the card depends on whether **Quick add** is on, because
with quick add the options are how the shopper picks what gets added.

### With quick add on

The card shows working controls for **every** option the product has:

- Options that read as colors become **swatches**.
- Everything else — size, material, length — becomes a compact **dropdown**.

Choosing an option selects that variant **on the card**, without opening the product page. The
selected swatch is ringed, and the card updates to match: price and compare-at price, the image if
that variant has its own, the Sale or Sold out badge, and the quantity limit on the Bulk stepper.
**Add to cart** then adds exactly what is shown. Combinations you cannot buy are struck through
rather than hidden, so the shopper can see a color exists before finding it is out of stock.

The title and the image still open the product page as normal.

### With quick add off

There is nothing on the card to add to, so swatches are a preview instead of a control. When
**Show color swatches** is on:

- Up to **five** swatches are shown; beyond that a `+N` marker indicates how many more exist.
- Clicking one opens the product page with that variant already selected.
- The theme uses the first option that reads as a color.

### Which options become swatches

An option becomes swatches when **every one of its values** resolves to a color. The theme tries,
in order: your swatch image, your swatch color, the value name read as a color name, then a
built-in list of retail color words — burgundy, taupe, oatmeal, rose gold and similar — including
markers for `multi` and patterned values.

Because every value has to resolve, an option holding SKU codes or values like `Black/White` keeps
its readable labels instead of becoming a row of blank circles. If one color in an option comes out
blank, that option falls back to a dropdown — set a swatch value on that one variant to fix it.

Setting swatch values in Shopify admin (**Settings → Custom data → Products → Color swatch**, or
in the variant editor) is still worth doing: it is the only way to get *your* exact colors and to
use artwork for prints and patterns. You no longer have to, though — a product with ordinary color
names now shows swatches without any setup.

### Products with many variants

Past **50 variants** a card stops trying to carry the options and shows **Choose options** instead,
linking to the product page. This is the only case where that button now appears.

---

## Availability and sold-out state

Sold-out products stay in the grid — Shopify's collection settings decide whether they are
listed at all. On a sold-out card:

- A **Sold out** badge appears (if enabled)
- The card is visually de-emphasized
- **Quick add is removed** — the theme never offers to add an unavailable product

A product that is only *partly* sold out keeps its card working. Selecting a sold-out color shows
the Sold out badge and disables **Add to cart** for that variant alone; choosing an available one
brings the button straight back.

To hide sold-out products entirely, use an automated collection condition, or a filter from the
Search & Discovery app.

---

## Quick add

| Option | Behavior |
| --- | --- |
| **None** | No control. The shopper opens the product page. |
| **Standard** | **Add to cart**. Products with options show those options on the card first — see [Options and color swatches](#options-and-color-swatches). |
| **Bulk** | As Standard, plus a quantity stepper on the card. |

Notes:

- **The theme never guesses a variant.** It adds whatever is selected on the card, and a product
  with options shows those options rather than assuming one.
- Adding from a card updates the cart count and, if you use the drawer, opens it — without
  leaving the page.
- **Quantity rules and stock are both respected.** The Bulk stepper will not climb past a
  variant's maximum or past what you actually have, and it says why when it stops — `Only 3
  available.` A shopper who types a larger number gets the same treatment.
- If an add fails anyway — stock ran out between page load and click — Shopify's own message
  appears on the card rather than the theme silently doing nothing.

**Recommended:** **Standard** for most stores. **Bulk** for wholesale, consumables and anything
bought in multiples. **None** if your products genuinely need to be read about before buying.

---

## Ratings

**Show product rating** displays a star rating and, optionally, a review count.

This requires a **product review app** that writes to Shopify's standard review metafields
(`reviews.rating` and `reviews.rating_count`). Most well-known review apps do. The card shows
nothing for products without reviews.

The theme does not collect or store reviews.

---

## Responsive behavior

| Screen | Cards |
| --- | --- |
| **Phone** | One or two columns, set per section. Hover images do not apply. Quick add buttons are full width and comfortably tappable. |
| **Tablet** | Two to three columns. |
| **Desktop** | Your configured columns, with hover images active. |

Some sections offer a **Scroll** or **Carousel** mobile layout, which puts cards in a swipeable
row instead of a stacked grid — useful when a section is a highlight rather than the main
content.

---

## Recommendations

- **Consistent photography matters more than any setting here.** Same background, same framing,
  same crop. A fixed image ratio hides some inconsistency but cannot fix it.
- **Give every product a second image** so the hover effect works everywhere.
- **Set swatch values** for your exact colors. Plain color names now work without them, but only
  swatch values can match your actual dye lot or show a print.
- **Four columns on desktop, two on mobile** suits most catalogs.
- **Do not enable ratings until you have reviews**, or most cards will simply look incomplete.
