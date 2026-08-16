# Collection pages

A collection page shows the products in one collection, with filtering and sorting.

**Where to find it:** Theme Editor → template dropdown → **Collection** → the **Collection**
section.

---

## Collections and the theme

A **collection** is a group of products, created in **Shopify admin → Products → Collections**.
There are two kinds:

- **Manual** — you choose each product
- **Automated** — Shopify includes products matching conditions you set (tag, price, vendor, and
  so on)

The theme's Collection template renders **every** collection in your store. You do not create a
page per collection; one template serves them all, and each one pulls its own title, description,
image and products from Shopify.

If you need one collection to look different, create a **template variant**: in the Theme Editor
template dropdown choose **Create template**, base it on `collection`, give it a name, customize
it, then assign it to that collection under **Online Store → Themes → Customize**, or from the
collection's **Theme template** field in Shopify admin.

### What to set on each collection in Shopify admin

| Field | Where it appears |
| --- | --- |
| **Title** | The page heading and the browser title. |
| **Description** | Below the title in the banner. |
| **Image** | Used in the collection banner and on collection cards elsewhere in the theme. |
| **Search engine listing** | The meta title and description — see [SEO](seo.md). |

---

## Section settings

### Banner

| Setting | Options | Notes |
| --- | --- | --- |
| **Show the collection banner** | On / off | Turning it off hides the title from view but keeps it for screen readers and search engines. |
| **Show the collection description** | On / off | |
| **Banner image layout** | None, Split, Banner | **Split** places the image beside the text. **Banner** places the text over a full-width image. **None** is text only. Uses the collection image from Shopify admin; collections without one fall back to text only. |

### Grid

| Setting | Range | Notes |
| --- | --- | --- |
| **Products per page** | 8–48 | Default 16. Higher numbers mean fewer page loads but a heavier page. |
| **Columns on desktop** | 2–5 | Default 4. |
| **Columns on mobile** | 1 or 2 | Default 2. |
| **Image ratio** | Adapt, Square, Portrait, Landscape | Overrides the global product card ratio for this template. |
| **Show vendor** | On / off | |
| **Show product rating** | On / off | Needs a review app. |
| **Quick add** | None, Standard, Bulk | Overrides the global setting. |

### Filtering

| Setting | Options | Notes |
| --- | --- | --- |
| **Filter layout** | Sidebar, Horizontal, Drawer | Where filters appear on desktop. |
| **Show the sort menu** | On / off | On by default. |

### Section

| Setting | Notes |
| --- | --- |
| **Show breadcrumbs** | A trail back to the store home. On by default. |
| **Color scheme**, **Top padding**, **Bottom padding** | Standard section settings. |

---

## Filtering

**Filters come from Shopify's free Search & Discovery app, not from the theme.**

Until you install that app and define filters, the filter area is empty — that is expected, not a
fault.

### Setting filters up

1. Install **Search & Discovery** from the Shopify App Store (free, made by Shopify).
2. Open the app and go to **Filters**.
3. Add the filters you want: Availability, Price, Product type, Vendor, or any product option
   (Size, Color) or tag.
4. Save. They appear on your collection and search pages immediately.

### Filter layouts

| Layout | Desktop behavior |
| --- | --- |
| **Sidebar** | A permanent column of filters beside the grid. Best for large catalogues where filtering is the main way to browse. |
| **Horizontal** | A row of filter dropdowns above the grid. Keeps the grid wide. |
| **Drawer** | A **Filter** button that opens a panel. The most compact. |

On **mobile all three become a drawer**, because a sidebar is not workable on a phone.

### How filtering behaves

- Applying a filter updates the grid without a full page reload.
- The number of matching products is announced, so screen reader users know the result changed.
- Active filters are listed with individual remove buttons, plus a **Clear all**.
- Filter state is kept in the page URL, so a filtered view can be bookmarked or shared.
- Filtering and sorting work together — sorting does not clear your filters.
- If JavaScript is unavailable, filters still work as a standard form submission.

---

## Sorting

The sort menu offers Shopify's standard options: Featured, Best selling, Alphabetically A–Z and
Z–A, Price low to high and high to low, Date old to new and new to old.

**Featured** uses the manual product order you set on the collection in Shopify admin — drag
products into your preferred order there, and set the collection's sort order to **Manually**.

Turn the sort menu off with **Show the sort menu** if you want to enforce a curated order.

---

## Pagination

When a collection has more products than your **Products per page** setting, numbered pagination
appears below the grid, with previous and next links.

**Recommended:** 16–24 products per page. Very high numbers make the first load slow, especially
on mobile; very low numbers make shoppers click too much.

Search engines are given `prev`/`next` hints for paginated collections automatically.

---

## Empty collections

A collection with no products — or a filter combination that matches nothing — shows a clear
message rather than a blank grid. When filters are active, a **Clear all** link is offered so
shoppers can recover in one click.

If a collection is empty because it is an automated collection whose conditions match nothing,
check the conditions in Shopify admin.

---

## The collections list page

There is a separate template for `/collections`, listing all your collections as cards.

**Theme Editor → template dropdown → Collections list**

| Setting | Notes |
| --- | --- |
| **Heading** | Leave blank to use the page title. **Description** below it. |
| **Sort collections by** | Alphabetical; Product count, high to low; Date, newest first; Date, oldest first. |
| **Collections per page** | 6–48. Default 24. |
| **Columns on desktop** (2–5) / **Columns on mobile** (1 or 2) | Grid density. |
| **Image ratio** | Square, Portrait, Landscape, Wide. |
| **Card style** | **Stacked** (title below image) or **Overlay** (title over image). |
| **Show product count** | On by default. |
| **Show breadcrumbs** | On by default. |

Each card uses the collection image from Shopify admin — set them, or the page will be a grid of
placeholders.

---

## Responsive behavior

| Screen | Collection page |
| --- | --- |
| **Phone** | One or two columns as configured. Filters and sort in a drawer behind a button. Banner stacks. |
| **Tablet** | Two to three columns. Filters usually still in a drawer. |
| **Desktop** | Your configured columns, with the filter layout you chose. |

See [Responsive design](responsive-design.md).

---

## Troubleshooting

**No filters appear.** Install Shopify's **Search & Discovery** app and define filters in it. The
theme has no filters of its own.

**A filter is missing an option.** Search & Discovery only offers values that exist on products
in that collection. If no product in the collection is tagged "Waterproof", that value will not
appear.

**Products are in the wrong order.** Check the collection's sort order in Shopify admin. For a
manual order, set it to **Manually** and drag the products.

**The banner has no image.** Set a **collection image** on the collection in Shopify admin, and
choose Split or Banner for **Banner image layout**.

**A collection is empty.** For an automated collection, check its conditions match at least one
active, published product available on your sales channel.

More in [Troubleshooting](troubleshooting.md).
