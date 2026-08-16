# Getting started

A first-time setup checklist, in the order that causes the least rework. Each step assumes the
one before it is done.

Work through this on an **unpublished** theme. Publish at the very end.

---

## 1. Add products

**Shopify admin → Products**

The theme reads everything about a product from Shopify. Before you style anything, get a
handful of real products in, each with:

- A **title** and a **description**
- At least **one image**, ideally two or more (a second image enables the hover effect on
  product cards)
- A **price**, and a **Compare-at price** only where there is a genuine discount
- **Variants** if the product has options, each with its own image where the variants look different
- **Inventory tracking** on or off, chosen deliberately — the theme shows stock information
  differently depending on this

**Optional but useful:** set a **Vendor** if you want to show brand names, and use the
**Media** section to add video (Shopify-hosted or a YouTube/Vimeo URL) where it helps.

> **Custom badges.** The theme can show a custom badge on a product card — for example "New" or
> "Limited". Create a product metafield with the namespace and key `custom.badge`, type
> **Single line text**, and fill it in on the products that need it. Products without it show
> only the automatic Sale and Sold out badges.

See [Images and media](images-and-media.md) for image preparation advice.

---

## 2. Create collections

**Shopify admin → Products → Collections**

Collections are how customers browse. Create the ones your navigation will point at.

For each collection, set:

- A **title** and a short **description** (the theme shows both on the collection page)
- A **collection image** — the theme uses it in the collection banner and on collection cards
- Products, either manually or by an automated condition

Start with a small number of broad collections. You can always add more later, and a menu with
six good collections works better than one with thirty thin ones.

---

## 3. Configure navigation

**Shopify admin → Content → Menus**

The theme uses two menus by default:

| Menu handle | Where it appears |
| --- | --- |
| `main-menu` | The header navigation and the mobile drawer |
| `footer` | A footer column (you can point footer columns at any menu) |

Shopify supports up to **three levels** of menu items, and the theme renders all three. How the
levels are used is explained fully in [Navigation best practices](navigation.md) — read that
before building a large menu, because the structure you choose decides whether an item becomes a
simple dropdown or a full-width mega menu.

A quick summary:

- A top-level item with **no children** is a plain link.
- A top-level item with **children only** becomes a compact dropdown list.
- A top-level item whose children **have their own children** becomes a full-width mega menu.

---

## 4. Configure theme settings

**Theme Editor → Theme settings** (the gear icon at the bottom of the left sidebar)

These are the global settings that apply everywhere. Set them before styling individual sections,
so you are not undoing work later. Work top to bottom:

1. **Logo** — upload your logo, set its width, upload a favicon
2. **Colors** — edit the color schemes, which every section then selects from
3. **Typography** — pick heading and body fonts and their size scales
4. **Layout** — page width, section spacing, grid spacing
5. **Appearance** — corner rounding, animations, back-to-top button
6. **Product cards** — image ratio, hover image, quick add
7. **Badges** — sale and sold-out badge behavior
8. **Cart** — drawer or page, note, free shipping bar
9. **Search** — predictive search and which result types to include
10. **Social media** — your profile URLs
11. **SEO and sharing** — social share image and organization schema

Every setting is explained in [Theme settings](theme-settings.md).

---

## 5. Configure the header

**Theme Editor → Header** (in the left sidebar, at the top of any page)

Set the menu, the layout, the scroll behavior and which actions appear. The full reference is in
[Header and navigation](header-and-navigation.md).

The three decisions that matter most:

- **Layout** — logo left with nav inline, logo left with nav below, or logo centered with nav below
- **Scroll behavior** — static, sticky, or reveal-on-scroll-up
- **Search** — an icon that opens a drawer, an always-visible field, or hidden

If you want a mega menu, add a **Mega menu** block to the header now. See [Mega menu](mega-menu.md).

---

## 6. Configure the announcement bar

**Theme Editor → Announcement bar** (above the Header in the left sidebar)

Add up to six announcements. Decide whether they rotate or all show at once, whether customers
can dismiss them, and how long a dismissal is remembered. See
[Announcement bar](announcement-bar.md).

Keep the messages true. An announcement promising free delivery over $75 should match an actual
shipping rate configured under **Settings → Shipping and delivery**.

---

## 7. Configure the homepage

**Theme Editor → Home page**

The theme ships with a starter home page: slideshow, featured collection, multicolumn, collection
list, image with text, testimonials, featured blog, newsletter.

Go through each one and either fill it with your own content, or remove it. Then add anything
missing. Full instructions and a description of every available section are in
[Homepage](homepage.md).

A home page of six to eight well-filled sections outperforms one of fifteen half-filled ones.

---

## 8. Configure collection pages

**Theme Editor → template dropdown → Collection**

Set the number of products per page, the grid columns, the image ratio, and where filters appear.

To get filters at all, install Shopify's free **Search & Discovery** app from the Shopify App
Store and define your filters there. The theme renders whatever filters that app provides; it
does not define its own. See [Collection pages](collection-page.md).

---

## 9. Configure product pages

**Theme Editor → template dropdown → Product**

The product page is built from blocks you can reorder, remove and add: vendor, title, rating,
price, variant picker, inventory, quantity, buy buttons, pickup, icon-with-text, description,
collapsible rows, SKU and share.

Drag them into the order you want. Set the gallery layout and image ratio at the section level.
See [Product page](product-page.md).

---

## 10. Configure the footer

**Theme Editor → Footer**

Add columns as blocks: menus, text, a newsletter form, social icons, contact details or an image.
Then configure the bottom bar — social icons, payment icons, country and language pickers, policy
links, and extra copyright text. See [Footer](footer.md).

---

## 11. Configure the other templates

Work through the remaining templates in the dropdown:

| Template | What to check |
| --- | --- |
| **Search** | Which result types to include, filter layout, results per page |
| **Cart** | Line item details, order note, recommendations collection |
| **Page** | Content width, heading display, breadcrumbs |
| **Contact** | Form fields, contact details block, optional map |
| **Blog posts** | Posts per page, card details, tag filter |
| **Blog post** | Featured image, meta, related articles, share |
| **404 page** | Message, search box, an optional collection to show |
| **Collections list** | Sort order, columns, card style |
| **Password page** | Logo, message, sign-up form, background image |

See [Pages, blog and contact](pages-blog-and-contact.md).

---

## 12. Preview on desktop and mobile

Click the eye icon in the Theme Editor to open a full preview.

Check at desktop width, tablet width and phone width. The Theme Editor's own device toggles are
useful, but always confirm on a real phone before publishing — see
[Responsive design](responsive-design.md) for what to look for.

---

## 13. Test the cart and checkout

Using the preview link, on a real device:

1. Add a product from a collection page using quick add
2. Add a product from a product page, having changed a variant first
3. Open the cart, change a quantity, remove a line
4. Click **Checkout** and confirm you reach Shopify's checkout with the right items and totals

Checkout itself is Shopify's, not the theme's. If the totals are right on the cart and the
checkout page loads, the theme has done its job. See [Cart](cart.md).

---

## 14. Publish

Go to **Online Store → Themes**, find Kestrin, and click **Publish**.

Then visit your real domain and repeat the quick checks above on the live site. Keep your
previous theme in the library as a rollback.

---

## After launch

- Re-check any apps that inject storefront code — see [Third-party apps](third-party-apps.md)
- Run a performance check — see [Performance](performance.md)
- Set page titles and meta descriptions on your key pages — see [SEO](seo.md)
- If you sell in more than one language, see [Translations and languages](translations.md)
