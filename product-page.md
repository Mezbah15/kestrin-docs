# Product page

The product page is where most purchase decisions happen. It is built from **blocks** you can
reorder, remove and add — so you decide what a shopper sees first.

**Where to find it:** Theme Editor → template dropdown → **Product** → the
**Product information** section.

---

## Preparing your products first

The product page displays what Shopify holds. Before styling it, make sure your products carry:

| In Shopify admin | Why it matters |
| --- | --- |
| **Title** and **Description** | The description block shows your formatted description as written. |
| **Media** — at least two images | A second image enables hover on product cards; more images fill the gallery. |
| **Variant images** | Assign an image to each variant so the gallery jumps to the right one when a shopper switches. |
| **Price** | Required. |
| **Compare-at price** | Only where there is a genuine reduction — it drives the sale badge and sale price color. |
| **SKU** / **Barcode** | Shown by the SKU block if you add it. |
| **Inventory tracking** | Decides how stock information is shown. See [Inventory](#inventory). |
| **Vendor** | Shown by the Vendor block if you add it. |
| **Options** with clear names | Options named "Color" or "Color" render as swatches automatically. |
| **Swatch values** | Set under **Settings → Metafields → Products** or in the variant editor, so color options show real colors. |

---

## Section settings

These apply to the whole product page.

### Media

| Setting | Options | Notes |
| --- | --- | --- |
| **Desktop gallery layout** | Stacked, Thumbnail left, Thumbnail below | **Stacked** shows every image down the page. The thumbnail layouts show one large image with a strip of thumbnails. |
| **Image ratio** | Adapt, Square, Portrait, Landscape | **Adapt** uses each image's own proportions. Choose a fixed ratio if your photography is inconsistent. |
| **Mobile gallery layout** | Carousel, Stacked | Carousel is swipeable and takes far less vertical space. |
| **Let shoppers zoom images** | On / off | Opens the image full screen when tapped or clicked. On by default. |
| **Loop videos** | On / off | Off by default. |

### Section

| Setting | Notes |
| --- | --- |
| **Show breadcrumbs** | A trail back to the collection the shopper came from. On by default. |
| **Color scheme**, **Top padding**, **Bottom padding** | Standard section settings. |

---

## Blocks

Add, remove and reorder these in the left sidebar. Blocks marked *once* can only be added a
single time.

### Vendor *(once)*

Shows the product's Vendor field.

- **Link to the vendor's products** — makes it a link to that vendor's products. Off by default.

### Title *(once)*

The product title.

- **Title size** — h3, h2 or h1 visual size. (The heading level for screen readers and search
  engines is handled by the theme regardless of this setting.)

### Price *(once)*

Price, compare-at price, and related notes.

| Setting | Notes |
| --- | --- |
| **Show sale badge** | A badge next to the price when a compare-at price is set. |
| **Show unit price** | For products sold by weight or volume, where Shopify calculates a unit price. |
| **Show tax and shipping note** | A short line clarifying whether tax is included and that shipping is calculated at checkout. |

The price updates automatically when the shopper changes variant.

### Rating *(once)*

A star rating read from Shopify's standard review metafields.

- **Show review count** — the number of reviews alongside the stars.

This block needs a **product review app** that writes to those metafields. It stays hidden until
a product has reviews. The theme does not collect reviews itself.

### Variant picker *(once)*

The option selectors. Only appears on products that have variants.

| Setting | Options | Notes |
| --- | --- | --- |
| **Picker style** | Dropdown, Pills, Swatches | Color options render as swatches automatically when Pills or Swatches is selected. |
| **Swatch shape** | Circle, Square | Not shown for the Dropdown style. |
| **Size chart page** | Any page | Adds a link under the options that opens the page's content in a pop-up, using the page title as the link text. |

**How color swatches are chosen.** The theme treats an option as a color option when its name
means "color" — and then resolves each value to an actual color, in this order: Shopify's
swatch image, Shopify's swatch color, the value name read as a color name, and finally a
built-in list of retail color words (`terracotta`, `oatmeal`, `charcoal`, and so on, plus
pattern and multicolor markers for values like `Leopard` or `Rainbow`).

An option only becomes swatches when **every** value resolves. If one value is a SKU code or a
name like "Black/White", the whole option stays as pills — which is the right outcome, because a
half-swatch, half-text row is confusing.

**For reliable swatches:** set the swatch value in Shopify admin rather than relying on the name.
That way "Midnight" shows your actual midnight, not the theme's approximation.

### Quantity selector *(once)*

A stepper for choosing how many to buy.

| Setting | Notes |
| --- | --- |
| **Show how many are already in the cart** | A line confirming the current cart quantity for this variant. |
| **Show volume pricing** | Shows quantity price tiers. |

**About volume pricing.** These tiers come from Shopify and are shown only for **B2B customers
whose company location has a catalogue with quantity breaks** — and Shopify charges those prices
at checkout. There is deliberately no setting for typing your own "buy 3, save 10%" table,
because the theme cannot verify that a typed discount will actually be applied. To run quantity
discounts on a normal retail store, use **Discounts → automatic discount**, a Shopify Function,
or a discount app; the theme picks the result up on its own and the cart totals will agree.

The stepper also respects any **minimum, maximum and increment** rules Shopify has set on the
variant.

### Buy buttons *(once)*

Add to cart, plus Shopify's dynamic checkout buttons.

| Setting | Notes |
| --- | --- |
| **Show payment terms** | Instalment wording next to the checkout button. Nothing appears until an instalments provider is set up under **Settings → Payments**. |
| **Let shoppers send gift cards to someone else** | Adds recipient name, email and message fields. Only appears on gift card products. |
| **One-time purchase wording** | The first choice in the subscription menu, for shoppers who want to buy once. Only appears on products that offer a subscription without requiring one. |

**Dynamic checkout buttons** (Shop Pay, PayPal, Google Pay and so on) are Shopify's, driven by
**Settings → Payments**. They are shown automatically when configured. The theme does not
process payments.

### Inventory *(once)*

Stock availability.

| Setting | Notes |
| --- | --- |
| **Low stock threshold** | 0–50. Stock at or below this count is shown as low. Set to `0` to show only "in stock" or "sold out". |
| **Show the number of units left** | The actual count. Only shown when the threshold is above 0. |
| **Show a stock level bar** | A visual bar. Off by default. Only shown when the threshold is above 0. |

**What the block shows, and why:**

| Your product setup | What shoppers see |
| --- | --- |
| Inventory not tracked | Availability, with no number. |
| Tracked, plenty in stock | In stock. |
| Tracked, at or below your threshold | Low stock, optionally with the count. |
| Tracked, zero but still available (continue selling) | Backordered. |
| Tracked, zero and unavailable | Sold out. |

**No number is ever invented.** If Shopify does not know the count, the theme does not show one.
The block is variant-aware — switching variant updates it — and if that update fails, the stock
text is cleared rather than left describing the previous variant.

### SKU *(once)*

The variant's SKU.

- **Show barcode** — also shows the barcode. Off by default.

Updates when the shopper changes variant.

### Description *(once)*

Your product description, formatted as written in Shopify admin.

| Setting | Notes |
| --- | --- |
| **Show as a collapsible row** | Puts the description in an accordion. Off by default. |
| **Open by default** | Only shown when collapsible is on. |

### Collapsible row *(repeatable)*

An accordion row for shipping, returns, care instructions or materials.

| Setting | Notes |
| --- | --- |
| **Heading** | The row label. |
| **Icon** | Truck, Pin, Mail, Phone, Info, Success, Star, or None. |
| **Content** | Rich text. |
| **Page** | The page's content is appended below the text — reuse a policy page you already maintain. |
| **Open by default** | Off by default. |

A row with neither text nor page stays hidden.

**Recommended:** two or three rows. Shipping and returns, materials and care, and anything
product-specific.

### Icon with text *(repeatable)*

Up to three short trust lines with icons — free delivery, returns window, guarantee.

| Setting | Notes |
| --- | --- |
| **Layout** | Horizontal or Vertical. |
| **First / Second / Third icon** and **text** | Each pair. Set an icon to None to skip it. |

### Share *(once)*

A share button. Uses the device's native share sheet where available, and falls back to copying
the link.

- **Share button label** — leave blank for "Share".

### Pickup *(once)*

Local pickup availability.

- **Let shoppers check other stores** — shows availability at your other locations.

Availability comes from the locations that have local pickup turned on under
**Settings → Shipping and delivery**. The block stays hidden on products with no pickup
locations.

### Text *(repeatable)*

A free rich-text block.

- **Text style** — Body, Subtitle or Uppercase.

### Custom liquid *(repeatable)*

A block for a code snippet — app snippets, metafields and Liquid tags. Useful for anything the
other blocks do not cover. See [Custom code](custom-code.md).

### App blocks

Any app that provides a product-page block can be added here and positioned like any other block.

---

## A recommended block order

The default order works for most stores:

1. Vendor
2. Title
3. Rating
4. Price
5. Variant picker
6. Inventory
7. Quantity selector
8. Buy buttons
9. Pickup
10. Icon with text
11. Description
12. Collapsible row (shipping and returns)
13. SKU
14. Share

The principle: identity, then price, then choice, then the buy button — and everything a shopper
needs to *decide* above the button, not below it.

---

## Related products

The **Product recommendations** section sits below the product information section by default.

| Setting | Notes |
| --- | --- |
| **Heading** | Leave blank for "You may also like", or "Pairs well with" when complementary products are selected. |
| **Heading alignment** | Left or center. |
| **Recommendation type** | **Related** products are chosen by Shopify from your store's sales and product data. **Complementary** products are the ones you pair up yourself in the Search & Discovery app. |
| **Products to show** | 2–12. **Columns on desktop**: 2–6. **Columns on mobile**: 1 or 2. |

Related recommendations improve as your store accumulates sales data — a brand new store may show
few or none. Complementary products work immediately, because you choose them.

---

## Responsive behavior

| Screen | Product page |
| --- | --- |
| **Phone** | Gallery at the top (swipeable carousel or stacked, your choice), then all blocks in one column. Buy buttons full width. |
| **Tablet** | Similar to phone, with wider media. |
| **Desktop** | Gallery on one side, blocks on the other, using your chosen gallery layout. |

See [Responsive design](responsive-design.md).

---

## Troubleshooting

### Variant information does not update

**Check in Shopify admin:**

- Each variant has its own price, SKU and inventory set. A blank field shows blank.
- Variant images are **assigned to variants**, not just uploaded to the product. In the variant
  editor, each variant has its own image slot.
- The variant is not in a draft or archived state.

**Check in the theme:** the **Variant picker** block is present. Without it, only the default
variant can be selected.

If the price and stock update but the image does not, the variant has no image assigned.

### The variant picker does not appear

The product has only one variant — Shopify calls this the "default" variant. The picker is
correctly hidden; there is nothing to choose.

### Color options show as pills instead of swatches

Either the option is not named as a color, the picker style is set to Dropdown, or at least one
value could not be resolved to a color. Set explicit swatch values in Shopify admin for every
value in that option.

### A product image is missing

- Confirm the image is attached to the **product** in Shopify admin, under Media.
- If it is a variant image, confirm it is assigned to that variant.
- Very large files can be slow to process after upload — wait a minute and reload.
- If nothing is attached at all, the theme shows a placeholder illustration.

### Sold-out products can still be added to cart

Check **Inventory → Continue selling when out of stock** on the variant. When that is on, Shopify
allows the sale and the theme shows the item as backordered rather than sold out — which is
correct behavior.

### The sale badge is not showing

The variant needs a **Compare-at price** higher than its price, and **Show sale badge** must be
on in **Theme settings → Badges**.

### Volume pricing does not appear

It only appears for B2B customers whose company location has a catalogue with quantity breaks.
For a retail store it is expected to be absent — see the note under
[Quantity selector](#quantity-selector-once).

More in [Troubleshooting](troubleshooting.md).
