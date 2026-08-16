# Third-party apps

Apps extend your store. They can also break it. This page explains how apps and the theme
interact, and how to install them safely.

---

## Does the theme require any apps?

**No.** The theme has no required app dependencies. Every feature documented in these guides
works with the theme alone, or with a native Shopify feature.

Two theme features are **enhanced** by a free Shopify app, and one depends on the class of app
you choose:

| Feature | Needs | Notes |
| --- | --- | --- |
| **Storefront filters** on collection and search pages | Shopify's free **Search & Discovery** app | The theme renders the filters that app defines. Without it, the filter area is empty. |
| **Complementary product recommendations** | Shopify's free **Search & Discovery** app | Where you pair products together. "Related" recommendations work without it. |
| **Product ratings** on cards and product pages | Any **product review app** that writes to Shopify's standard review metafields | The theme does not collect reviews. |

Search & Discovery is made by Shopify, free, and well worth installing.

---

## How apps interact with a theme

Understanding this makes app problems much easier to diagnose.

**App blocks.** The modern approach. The app provides a block you place yourself in the Theme
Editor, and it loads only on the pages where you have placed it. This theme accepts app blocks on
the product page, collection page, cart, search, article, blog, page, 404 and every marketing
section — plus a dedicated **Apps** section you can add to any template.

**App embeds.** A toggle in the Theme Editor's App embeds panel. The app injects code into every
page of your store. Common for chat widgets, popups and tracking.

**Injected code.** Some apps add snippets directly to your theme files during installation. This
is the oldest approach and the messiest — it modifies the theme itself, and the code frequently
stays behind after uninstalling.

**Prefer apps that use app blocks.** They are cleaner, faster, and they do not modify the theme.

---

## Compatibility

**No theme can claim compatibility with every Shopify app.** There are thousands, they change
constantly, and many inject arbitrary code. Any theme claiming universal compatibility is
overstating it.

What is true of this theme:

- It follows Shopify's Online Store 2.0 conventions, which is what well-built apps expect.
- It supports app blocks broadly, which is the least intrusive integration method.
- It uses standard Shopify cart and section behavior, so apps that hook into those generally
  work.
- It does not require any app, so removing one never breaks the theme itself.

Apps most likely to conflict are those that replace core behavior: cart drawer replacements,
alternative variant pickers, custom quick-view overlays, and anything that rewrites the product
form.

---

## Installing an app safely

**The rule: test on an unpublished copy of your theme first.**

1. **Duplicate your live theme.** Online Store → Themes → **⋯ → Duplicate**.
2. **Install the app.** Most apps ask which theme to add their code to — choose the duplicate.
   If it does not ask, it has added code to your live theme; check that first.
3. **Configure and preview** the duplicate.
4. **Test properly:**
   - Home, collection, product, cart and search pages
   - Add to cart from a product page and from a product card
   - The full checkout flow
   - A phone as well as a desktop
   - Keyboard navigation, if the app adds anything interactive
   - Page speed before and after
5. **If it works**, publish the duplicate. **If it does not**, delete the duplicate — your live
   store was never touched.

This takes ten extra minutes and it is the difference between a bad app being an inconvenience
and being an outage.

---

## When something goes wrong

**Symptoms that usually mean an app conflict:**

- The problem started immediately after installing something
- Something that worked yesterday does not today, with no theme changes
- Errors appear in the browser console
- The layout breaks on one page type only
- The cart stops updating
- The page scrolls sideways on mobile

**How to confirm:**

1. Disable the app (or its app embed) and reload. If the problem goes, you have your culprit.
2. With several apps, disable them all, confirm the problem is gone, then re-enable one at a time.

**Then:**

- **Contact the app's support first.** They know their code and can usually adjust it. Tell them
  the theme name (Kestrin) and what you observed.
- **Then contact theme support** if needed, with the app name, what you tested, and what happened.
  See [Support](support.md).

---

## Leftover code after uninstalling

Apps that inject code often leave it behind when uninstalled. Symptoms: errors in the console,
requests to a service you no longer use, or a visual remnant of a removed feature.

To check: **Online Store → Themes → ⋯ → Edit code** and look for snippet files or `<script>` tags
named after the app. Ask the app's support for removal instructions rather than deleting things
blind — and take a duplicate of the theme before you change anything.

This is the strongest argument for testing apps on a duplicate: an app that leaves debris behind
never touched your real theme.

---

## Native features worth using instead of an app

Every app you avoid is code you do not ship. Shopify covers more than many merchants realize:

| Instead of | Use |
| --- | --- |
| A search or filter app | **Search & Discovery** (free, Shopify) |
| A "buy 3, save 10%" discount app | **Discounts → automatic discount**, or a Shopify Function |
| An email marketing app | **Shopify Email** |
| A currency converter app | **Settings → Markets** |
| A translation app | **Translate & Adapt** (free, Shopify) |
| An analytics or pixel app | **Settings → Customer events** |
| A wholesale pricing app | **B2B** on Shopify Plus, or company-location catalogs |
| A "recently viewed" or recommendations app | The theme's **Product recommendations** section |
| A trust badge app | The theme's **Multicolumn** section, or a footer Image block |
| An FAQ app | The theme's **Collapsible content** section |
| A countdown app | The theme's **Countdown** section |
| A testimonial app | The theme's **Testimonials** section |

See [Performance](performance.md).

---

## Guidance for choosing apps

- **Install what you will actually use.** Every app is permanent overhead until removed.
- **Check the reviews for the theme era, not just the star rating.** Recent reviews mentioning
  Online Store 2.0 themes are the useful ones.
- **Prefer apps offering app blocks.** They say so in their listing.
- **Prefer apps with responsive support.** You will need it eventually.
- **Audit quarterly.** Uninstall what you stopped using.
- **Measure speed before and after** each install.
