# Cart

The theme offers two cart styles — a slide-out drawer or a full cart page — and both are always
available. Which one the cart icon opens is up to you.

**Global settings:** Theme Editor → **Theme settings → Cart**
**Cart page settings:** Theme Editor → template dropdown → **Cart**

---

## Choosing drawer or page

**Theme settings → Cart → Cart type**

| Option | Behavior |
| --- | --- |
| **Drawer** | The cart slides in from the side. Shoppers stay on the page they were browsing. Clicking the header cart icon opens it. |
| **Page** | Clicking the header cart icon goes to `/cart`. Adding a product also takes the shopper there. |

**Recommended: Drawer.** It keeps shoppers in the browsing flow, which usually means more items
per order. Choose **Page** if your cart carries a lot of information — complex line item
properties, long notes, or a shipping calculator from an app — that needs the room.

The cart page at `/cart` works either way. It is where shoppers land if they navigate there
directly, and it is the fallback when JavaScript is unavailable.

---

## Adding products

Products reach the cart from three places:

| From | How |
| --- | --- |
| **A product page** | Choose a variant and quantity, then **Add to cart**. |
| **A product card** | Quick add, when enabled. Single-variant products add directly; multi-variant products link to the product page. |
| **The cart drawer** | Drawer recommendations, when a recommendations collection is set. |

In every case the header cart count updates immediately, and — with the drawer cart — the drawer
opens so the shopper can see what happened.

If an add fails (stock ran out, a quantity rule was not met), an error message appears next to the
control that was used. The cart is never left in a state that disagrees with Shopify.

---

## Changing quantities

Each line has a quantity stepper.

- Changing a quantity updates the line total, the cart subtotal and the header count.
- Any **minimum, maximum or increment** rule set on the variant is respected.
- Reducing a quantity to zero removes the line.
- Rapid changes are batched, so holding the increase button does not fire a request per click.

---

## Removing products

Each line has a remove control. Removing a line updates the totals and the header count
immediately. Removing the last line switches the cart to its empty state.

---

## The cart count

The number on the header cart icon is the total number of items — not lines. Two of one product
and one of another shows `3`.

It updates from every part of the theme that changes the cart, on every page, without a reload.

---

## Cart drawer

**Theme settings → Cart**, with **Cart type** set to Drawer.

| Setting | Notes |
| --- | --- |
| **Cart drawer title** | The heading at the top. Leave empty for "Cart". |
| **Cart drawer recommendations** | A collection to suggest products from. Items already in the cart are skipped, and the row hides when nothing is left to show. |
| **Cart drawer color scheme** | Which color scheme the drawer uses. |

The drawer contains: heading and close button, the free shipping bar (if enabled), the line items,
recommendations (if set), the order note (if enabled), the totals, and the checkout button.

**Behavior:** the drawer traps keyboard focus while open, closes on **Escape**, on a click
outside, or on the close button — and returns focus to whatever opened it. Background scrolling
is locked while it is open.

---

## Cart page

**Theme Editor → template dropdown → Cart**

| Setting | Notes |
| --- | --- |
| **Show vendor** | Shows the vendor on each line. Overrides the same setting under Theme settings → Cart. |
| **Show SKU** | Shows each line's SKU. |
| **Show line item properties** | Shows custom fields added by an app or a product form — engraving text, an uploaded file, a delivery date. Fields whose name starts with an underscore stay hidden, which is the convention apps use for internal data. |
| **Show order note** | Overrides the same setting under Theme settings → Cart. |
| **Recommendations collection** | Up to four products from this collection are shown below the cart. Items already in the cart are skipped, and the row hides when nothing is left. |
| **Color scheme**, **Top padding**, **Bottom padding** | Standard section settings. |

The cart page also accepts **app blocks**, so a shipping calculator or upsell app can be placed
in it.

---

## Order notes

**Theme settings → Cart → Enable cart note** (or the cart page's own **Show order note**).

Adds a text field where shoppers can leave a message with their order — gift wrapping, delivery
instructions, a purchase order reference. The note appears alongside the order in Shopify admin.

Notes are saved as the shopper types, so nothing is lost if they navigate away and come back.

---

## Free shipping progress bar

**Theme settings → Cart → Show free shipping progress bar**

Shows how much more a shopper needs to add to reach free shipping, and confirms when they have.

Set **Free shipping threshold** to the amount in your store currency, with no symbols or
separators — `100`, not `$100.00`.

> **This setting does not create free shipping.** It only displays progress towards the number you
> type. You must also configure a matching free shipping rate under
> **Settings → Shipping and delivery**. If the two disagree, shoppers will be told they qualified
> and then charged for delivery — which is the fastest way to lose an order at checkout.
>
> Also check the threshold in every market you sell to. A single number cannot be right in three
> currencies at once.

The bar updates automatically as the cart changes, and only appears when the cart has items.

---

## Discounts

Discount codes are entered at **checkout**, not in the cart — this is how Shopify works, and it
is not something the theme changes.

**Automatic discounts** and **Shopify Functions** are different: those apply before checkout, and
the cart shows them. Each line displays its discounted unit price and lists the discounts applied
to it, and order-level discounts appear in the totals. The unit price, the line total and the
discount always agree, because all three come from Shopify.

This is the supported way to run "buy 3, save 10%" style offers — see the note under
[Product page → Quantity selector](product-page.md#quantity-selector-once).

---

## Totals, tax and shipping

The cart shows the subtotal, any order-level discounts, and a note clarifying whether tax is
included in your prices and that shipping is calculated at checkout.

The theme does not calculate tax or shipping. Both are Shopify's, based on
**Settings → Taxes and duties** and **Settings → Shipping and delivery**, and are finalized at
checkout once the customer's address is known.

---

## Empty cart

An empty cart shows a short message and a link to continue shopping, rather than a blank panel.
This applies to both the drawer and the cart page.

---

## Checkout

The checkout button takes shoppers to **Shopify's checkout**.

**Everything from that point on is Shopify's, not the theme's:**

- The checkout pages, their layout and their branding — configured under
  **Settings → Checkout** and the checkout branding editor
- Payment methods — configured under **Settings → Payments**
- Tax and shipping calculation
- Order confirmation and notification emails

**The theme does not process payments and does not handle any payment data.** It hands the cart to
Shopify and Shopify takes over.

**Accelerated checkout buttons** — Shop Pay, PayPal, Google Pay, Apple Pay and similar — are
Shopify's too. They appear on the cart page automatically once you enable them under
**Settings → Payments**. There is no theme setting for them.

---

## Mobile behavior

| | |
| --- | --- |
| **Drawer** | Takes nearly the full screen width, scrolls internally, with the checkout button always reachable. |
| **Cart page** | Line items stack vertically. Quantity steppers and remove controls are sized for touch. |
| **Free shipping bar** | Full width, above the line items. |
| **Recommendations** | Become a swipeable row. |

Test a real add-to-cart and a real checkout on a phone before publishing. See
[Responsive design](responsive-design.md).

---

## Troubleshooting

**The cart is not updating.**

1. Hard-refresh the page (**Ctrl/Cmd + Shift + R**) — you may be seeing a cached page.
2. Try a private browsing window with extensions disabled. Ad and script blockers sometimes
   block cart requests.
3. Check whether a recently installed app is involved: preview the theme with the app disabled.
4. Check the cart in a different browser to rule out one browser's storage being corrupt.

**Items disappear from the cart.** Shopify clears cart lines whose product became unavailable,
was unpublished, or ran out of stock. Check the product's status and inventory in admin.

**The free shipping bar shows the wrong amount.** The threshold is entered as a plain number in
your store currency. Check for a currency symbol, a comma or a decimal point in the field, and
confirm the number matches your actual shipping rate.

**The drawer does not open.** Confirm **Cart type** is set to Drawer. If it is, a script error —
often from an app — may be preventing it. The header cart icon still links to the cart page, so
shoppers are not stranded.

**Discount codes cannot be entered in the cart.** Correct — Shopify accepts them at checkout.

More in [Troubleshooting](troubleshooting.md).
