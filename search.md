# Search

The theme provides two search experiences: **predictive search**, the live suggestions that
appear as a shopper types, and the **search results page** at `/search`.

---

## How shoppers reach search

**Theme Editor → Header → Search**

| Option | Result |
| --- | --- |
| **Icon** | A magnifying glass in the header opens a search drawer over the page. Available at all screen sizes. |
| **Field** | An always-visible search box in the header on desktop. On mobile the icon behavior is used. |
| **Hidden** | No search control in the header. `/search` is still reachable directly. |

Search also appears on the **404 page** when **Show a search box** is enabled there — useful,
because a shopper who hits a dead link is usually looking for something specific.

---

## Predictive search

**Theme settings → Search**

As a shopper types, suggestions appear beneath the input.

| Setting | Default | What it includes |
| --- | --- | --- |
| **Enable predictive search** | On | The feature as a whole. Turning it off leaves a plain search box that submits to the results page. |
| **Show collections in results** | On | Matching collections. |
| **Show blog posts in results** | Off | Matching articles. |
| **Show pages in results** | Off | Matching pages. |

Products are always included when predictive search is on.

### Behavior

- Suggestions appear after a short pause in typing, not on every keystroke.
- Results are grouped by type, each group labeled.
- **Arrow keys** move through suggestions, **Enter** opens the highlighted one, **Escape** closes
  the panel.
- Screen readers are told how many results were found and which one is highlighted.
- A **View all results** link at the bottom goes to the full results page.
- If nothing matches, a short message says so — the panel does not simply stay empty.

**Recommended:** leave products and collections on. Add blog posts and pages only if you have
enough of them to be worth searching; otherwise the panel fills with weak matches and pushes
products down.

---

## The search results page

**Theme Editor → template dropdown → Search**

### Results

| Setting | Range | Notes |
| --- | --- | --- |
| **Results per page** | 8–48 | Default 16. |
| **Columns on desktop** | 2–5 | Default 4. |
| **Columns on mobile** | 1 or 2 | Default 2. |
| **Image ratio** | Adapt, Square, Portrait, Landscape | For product results. |

### Sources

| Setting | Default |
| --- | --- |
| **Include products** | On |
| **Include blog posts** | On |
| **Include pages** | On |

### Filtering

| Setting | Notes |
| --- | --- |
| **Show filters** | Filters come from the Search & Discovery app, and **Shopify only offers them when the search is limited to products**. To use filters, turn off **Include blog posts** and **Include pages** above. |
| **Filter layout** | Sidebar, Horizontal or Drawer. Default Horizontal. |
| **Show the sort menu** | On by default. |

This is a Shopify constraint, not a theme limitation: a mixed result set of products, articles
and pages cannot be filtered by product attributes, so the option is only meaningful when
products are the only source.

### Section

| Setting | Notes |
| --- | --- |
| **Show breadcrumbs** | On by default. |
| **Color scheme**, **Top padding**, **Bottom padding** | Standard section settings. |

---

## What results look like

- **Products** use the standard product card — image, title, price, badges. See
  [Product cards](product-cards.md).
- **Blog posts** show their title, date and excerpt.
- **Pages** show their title and a short extract.

The page states the search term and how many results were found, and paginates when there are
more than fit on one page.

---

## No results

When a search matches nothing, the page shows a clear message naming the term that was searched,
and offers a way to search again. If filters were applied, a **Clear all** link is offered — a
common cause of zero results is a filter combination, not the term itself.

---

## Improving what search finds

Shopify runs the search, so the way to improve results is to give Shopify better data:

- **Product titles and descriptions** are the main input. Include the words customers actually
  use, including alternatives ("trainers" and "sneakers").
- **Product type**, **Vendor** and **Tags** are searched too. Tags are a good place for
  synonyms and materials.
- **Search & Discovery** (free, from Shopify) lets you add **synonyms**, **boost** specific
  products for specific terms, and see **what shoppers actually searched for** — including
  searches that returned nothing. That report is the single most useful thing you can look at
  for improving search.

---

## Limitations worth knowing

- **Search is Shopify's.** The theme presents results; it does not rank them, and it has no
  settings that change ranking. Ranking is influenced through Search & Discovery.
- **Filters need product-only search**, as described above.
- **Predictive search does not filter or sort.** Those are for the full results page.
- **Only published, available content is searchable.** Draft products and unpublished pages do
  not appear.

---

## Mobile behavior

- The search drawer takes the full screen width, with the keyboard opening automatically.
- Suggestions are large enough to tap without hitting the wrong one.
- On the results page, filters and sort collapse into a drawer behind a button, whichever layout
  you chose for desktop.

---

## Troubleshooting

**Predictive search shows nothing.** Confirm **Enable predictive search** is on in Theme settings
→ Search. Try a term you know matches a product title exactly. Very short terms may not match.

**A product I expect is missing.** Check it is Active and published to the Online Store sales
channel, and that the search term appears in its title, description, type, vendor or tags.

**No filters on the search page.** Filters require **Show filters** to be on, the Search &
Discovery app to be installed with filters defined, **and** blog posts and pages to be excluded
from the results.

**Results look different from the collection page.** Check the Search template's own columns and
image ratio settings — they are separate from the Collection template's.

More in [Troubleshooting](troubleshooting.md).
