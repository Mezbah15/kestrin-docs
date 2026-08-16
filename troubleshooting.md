# Troubleshooting

Common problems, their usual causes, and how to fix them.

---

## Before anything else

Four checks that resolve a surprising proportion of reported problems:

1. **Hard-refresh the page** — **Ctrl + Shift + R** (Windows) or **Cmd + Shift + R** (Mac). You
   may be looking at a cached page.
2. **Try a private/incognito window.** This rules out browser extensions, which frequently
   interfere with carts and scripts.
3. **Check you are looking at the right theme.** Preview links and the live store are different
   things. Changes made to an unpublished theme do not appear on your live store.
4. **Check whether an app is involved.** If the problem started after installing one, preview the
   theme with that app disabled.

---

## Theme changes are not visible

**On the live store, but not in the preview**
You are editing an unpublished theme. Publish it (**Online Store → Themes → Publish**), or
confirm you are editing the published one.

**In the Theme Editor, but not on the storefront**
The change was not saved. The Theme Editor autosaves, but a lost connection can interrupt it.
Reopen the editor and confirm the change is still there.

**Nowhere, even after saving**
Hard-refresh. If it still does not appear, try another browser or a private window — you are
almost certainly seeing a cached page. Shopify's CDN can hold a page briefly after a change.

**On your phone but not your computer, or vice versa**
Each device caches separately. Hard-refresh both.

**Only for some visitors**
Give it a few minutes. CDN caches clear at slightly different times in different regions.

---

## The menu does not appear correctly

**No navigation at all**
Check **Theme Editor → Header → Menu** points at a menu that exists and has items. The theme
hides the navigation entirely — including the mobile menu button — when the selected menu is
empty.

**Items in the wrong order**
Menu order is set in **Shopify admin → Content → Menus**, by dragging. It is not set in the
theme.

**A link goes to the wrong place**
Check the item's link in Shopify admin. A link typed by hand rather than picked from the
dropdown is a common source of typos.

**The menu wraps onto two lines or overflows**
Too many top-level items, or names that are too long. Shorten the names, move some items to the
footer, or switch **Layout** to "Logo left nav below", which gives the menu its own row.

**A dropdown covers content or is cut off**
Usually custom CSS or an app adding an `overflow` rule to a parent element. Test with recent
custom code removed.

**Changes to the menu affected my live store too**
Expected. Menus live in Shopify admin and are shared by every theme. There is no per-theme copy.

---

## The mega menu does not show what I expect

**It is a narrow dropdown instead of a full-width panel**
The theme decides this from your menu structure. A full-width mega menu requires either
grandchildren (three levels) or a Mega menu block with an image, heading or text. Add a third
level in Shopify admin, or add a promotion.

**Some links are missing**
They are probably nested one level too high. In the Shopify menu editor, indentation shows the
nesting — level-3 items must sit under a level-2 item, not alongside them.

**The promotion is on the wrong menu item**
The **Menu item position** setting counts from the left. Count your top-level items again. Also
check whether the menu has been reordered in Shopify admin since you set the block up — the
promotion follows the position, not the item.

**The promotion button is missing**
Both **Link** and **Link label** must be filled in.

**Nothing shows on mobile**
Mega menu promotions are desktop only, by design. The links themselves appear in the mobile
drawer.

See [Mega menu](mega-menu.md).

---

## Product variant information does not update

**Price, SKU or stock does not change when switching variant**

- Confirm the **Variant picker** block is present on the product template. Without it, only the
  default variant can be selected.
- Confirm each variant has its own price, SKU and inventory set in Shopify admin. A blank field
  shows blank.
- Try a private window with extensions disabled.

**The image does not change when switching variant**
Variant images must be **assigned to the variant**, not merely uploaded to the product. Open the
variant in Shopify admin and set its image there.

**There is no variant picker**
The product has only one variant. This is correct — there is nothing to choose.

**Color options show as pills instead of swatches**
Either the option is not named as a color, **Picker style** is set to Dropdown, or at least one
value could not be resolved to a color. The theme only uses swatches when *every* value in the
option resolves — a value like "Black/White" or a SKU code keeps the whole option as pills. Set
explicit swatch values in Shopify admin for every value.

**A sold-out variant can still be added to cart**
Check **Continue selling when out of stock** on that variant. When it is on, Shopify permits the
sale and the theme shows the item as backordered — which is correct.

**Volume pricing does not appear**
It only appears for B2B customers whose company location has a catalogue with quantity breaks.
On a retail store it is expected to be absent. See [Product page](product-page.md).

---

## A product image is not displayed

- Confirm the image is attached to the product under **Media** in Shopify admin.
- If it should appear for a specific variant, confirm it is assigned to that variant.
- Large uploads take a moment to process. Wait a minute and reload.
- If the product genuinely has no image, the theme shows a placeholder illustration — add an
  image.
- If images show on some pages but not others, check that section's own image settings.
- On product cards, the **hover image** is the product's second image. Products with one image
  show no hover, which is correct.

---

## The announcement bar does not behave as expected

**It does not rotate**
Rotation needs more than one announcement block, and **Display** must be set to Rotate.

**The close button does not appear**
Two settings are involved. The section's **Customers can close** must not be "Nothing", and — if
it is set to "The announcement they are reading" — the individual block's **Let customers close
this announcement** must also be on.

**It keeps coming back after being closed**
Either **Remember the choice** is "Not at all", or the browser blocks local storage — common in
private browsing and with some privacy extensions. The theme cannot work around a browser that
refuses to remember.

**It disappeared entirely**
You closed it and the dismissal is being remembered. Clear the site's data in your browser, or
open a private window.

**A closed announcement came back**
Its text was edited. That is intended — a reworded announcement is treated as a new one.

**It is too tall on mobile**
Shorten the message, reduce the padding, or turn **Show on mobile** off.

See [Announcement bar](announcement-bar.md).

---

## The cart is not updating

1. Hard-refresh.
2. Try a private window with extensions disabled — ad and script blockers sometimes block cart
   requests.
3. Check for an app conflict: preview the theme with recently installed apps disabled.
4. Try a different browser to rule out corrupt local storage.

**Items disappear from the cart**
Shopify removes lines whose product became unavailable, was unpublished, or ran out of stock.
Check the product's status and inventory in admin.

**The drawer does not open**
Confirm **Theme settings → Cart → Cart type** is set to Drawer. If it is, a JavaScript error —
often from an app — may be preventing it. The cart icon still links to the cart page, so shoppers
are not stranded.

**The free shipping bar shows the wrong amount**
The threshold must be a plain number in your store currency, with no symbol, comma or decimal
point. Check the field, and confirm the number matches an actual free shipping rate under
**Settings → Shipping and delivery**.

**Discount codes cannot be entered in the cart**
Correct. Shopify accepts discount codes at checkout, not in the cart. Automatic discounts and
Shopify Functions do apply in the cart.

See [Cart](cart.md).

---

## The layout looks wrong on mobile

Work through these in order:

1. **Reproduce it on a real phone**, not just a narrow browser window. Send yourself the preview
   link.
2. **Note which section** is affected. If it is one section, the cause is in that section's
   settings. If it is every section, the cause is global.
3. **Check that section's mobile settings** — columns on mobile, mobile layout, mobile image.
4. **Check for custom code.** Sideways scrolling on a phone is almost always custom CSS or an
   app. Remove recent custom code and retest.
5. **Check apps.** Disable recently installed apps one at a time.
6. **Check for very long unbroken text** — a long product title with no spaces, or a pasted URL —
   which can force a page wider than the screen.

| Symptom | Usual fix |
| --- | --- |
| Page scrolls sideways | Custom code or an app |
| Hero text unreadable | Raise **Overlay opacity** |
| Hero subject cropped out | Add a **Mobile image**, or set the image focal point |
| A section is endlessly tall | Switch **Mobile layout** to Carousel/Scroll, or show fewer items |
| Grid cramped | One column on mobile, or shorter product titles |
| Header takes too much space | Use **Reveal** scroll behavior, reduce header padding |

See [Responsive design](responsive-design.md).

---

## Translation text is missing or wrong

**Text appears in English on a translated store**

1. Confirm the language is **published**, not just added, under **Settings → Languages**.
2. Work out whether it is theme text or your content. Product titles, collection names, page
   content and text you typed into theme settings are *your content* — translate them with
   Shopify's **Translate & Adapt** app.
3. For theme text, look for the phrase under **Online Store → Themes → ⋯ → Edit default theme
   content**, with the right language selected.

**A message looks broken, or shows literal braces**
A placeholder like `{{ count }}` was altered or removed while editing theme content. Restore it
exactly as it was.

**My wording changes vanished after uploading a new theme version**
Theme content edits belong to the theme they were made on. They do not transfer to a newly
uploaded copy. Reapply them — and note them down before your next update.

**The language picker does not appear**
It only shows when more than one language is published, and when enabled on the header or footer.

See [Translations and languages](translations.md).

---

## Filters are missing on a collection or search page

Filters come from Shopify's free **Search & Discovery** app, not from the theme.

1. Install **Search & Discovery** from the Shopify App Store.
2. Open it, go to **Filters**, and add the filters you want.
3. On the **search page only**, filters also require the search to be limited to products — turn
   off **Include blog posts** and **Include pages** on the Search template.

A filter value only appears when at least one product in the current results has it.

---

## No products appear in a section

- **Featured collection / Collections** — confirm a collection is selected and it contains
  published products available on the Online Store sales channel.
- **Product recommendations** — "Related" recommendations are generated by Shopify from sales
  data and may be sparse on a new store. Use "Complementary" and pair products yourself in
  Search & Discovery for immediate results.
- **Cart or drawer recommendations** — items already in the cart are skipped, so a small
  collection can end up with nothing left to show.

---

## Something broke right after installing an app

This is the most common cause of sudden storefront problems.

1. Disable or uninstall the app and check whether the problem goes away.
2. If it does, contact the app's support — they are best placed to fix an interaction with a
   theme.
3. Then contact theme support with the app's name and what you observed.

**Always test new apps on an unpublished copy of your theme first.** See
[Third-party apps](third-party-apps.md).

---

## Still stuck?

Before contacting support, gather:

- What you expected, and what happened instead
- The exact page URL
- Browser and device
- A screenshot or short screen recording
- What you changed most recently — a setting, an app, custom code
- Whether it happens in a private window with extensions disabled

See [Support](support.md).
