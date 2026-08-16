# Mega menu

A mega menu is a full-width dropdown panel that shows several columns of links at once, instead
of a single narrow list. It is the right choice when a top-level menu item covers enough ground
that a plain dropdown would be a long, hard-to-scan column.

---

## The one thing to understand first

**The theme decides between a dropdown and a mega menu from the shape of your Shopify menu, not
from a setting.**

| Your menu | Result |
| --- | --- |
| Parent → children | Compact dropdown list |
| Parent → children → grandchildren | Full-width mega menu |

The **Mega menu** block in the Theme Editor does *not* turn a mega menu on. It adds an optional
**promotional panel** — an image, heading, text and button — to a menu item, and sets how many
columns that panel uses. (Adding a promotion with an image, heading or text does also force a
mega menu layout, even for a two-level item, because a promotion needs the width.)

So: **build the structure in Shopify admin, then optionally decorate it in the theme.**

---

## Step 1 — Build the navigation in Shopify

Go to **Shopify admin → Content → Menus** and open your main menu (usually `main-menu`).

Add a top-level item, then add items nested beneath it, then add items nested beneath those.
Shopify supports three levels.

For a clothing store, a mega menu on "Men" looks like this:

```text
Men                          ← top level (level 1)
├── Clothing                 ← level 2 — becomes a column heading
│   ├── T-shirts             ← level 3 — becomes a link in that column
│   ├── Shirts
│   ├── Knitwear
│   └── Jackets
├── Footwear                 ← level 2 — a second column
│   ├── Trainers
│   ├── Boots
│   └── Loafers
├── Accessories              ← level 2 — a third column
│   ├── Bags
│   ├── Belts
│   └── Hats
└── Shop all Men             ← level 2 with no children — a column with just a heading
```

On the storefront that renders as three columns of links, plus a fourth column that is just the
"Shop all Men" heading, with a **View all Men** button underneath if the "Men" item itself has a
URL.

### How each level maps to the panel

| Menu level | Where it appears |
| --- | --- |
| **Level 1** ("Men") | The item in the header bar. Clicking it opens the panel. Its URL becomes the **View all** button. |
| **Level 2** ("Clothing") | A column heading inside the panel. It is a link, so it can point at a collection. |
| **Level 3** ("T-shirts") | A link listed under its column heading. |

A level-2 item with no children still gets its own column — useful for a single prominent link
like "Sale" or "New in".

---

## Step 2 — Add a promotion (optional)

1. In the Theme Editor, select the **Header** section.
2. Click **Add block → Mega menu**.
3. Set **Menu item position** — the position of the top-level item this promotion attaches to,
   counting from the left. `1` is the first item in your menu.
4. Set **Columns** (2–5) — how many columns the link area is divided into.
5. Fill in the promotion fields you want:

| Field | Notes |
| --- | --- |
| **Image** | Shown at the top of the promotion panel. Landscape works best. |
| **Heading** | A short line above the promotion text. |
| **Text** | One or two sentences. Plain text, no formatting. |
| **Link** | Where the promotion button goes. |
| **Link label** | The button text. Only appears once a Link is set. The button needs both. |

The promotion panel sits to the side of the link columns. If you leave the image, heading and
text all empty, no promotion panel is rendered — but the **Columns** setting still applies.

You can add up to eight mega menu blocks, one per top-level menu position.

> **Watch out:** the block attaches by *position*, not by name. If you later reorder your menu in
> Shopify admin, the promotion follows the position, not the item — so a promotion set for
> position 1 will attach to whatever is first after the reorder. Check your mega menu blocks after
> any menu reorder.

---

## How the panel behaves on desktop

- Clicking the top-level item opens the panel; clicking again closes it.
- Only one panel is open at a time.
- **Escape** closes it and returns focus to the item that opened it.
- Clicking anywhere outside closes it.
- The panel spans the full page width and is centered on your page width setting.
- Columns are set by the block's **Columns** value; without a block, four columns are used.

---

## How it behaves on mobile

**There is no mega menu on mobile.** Mobile uses the panelled drawer described in
[Header and navigation](header-and-navigation.md), which is a better fit for a small screen.

The same menu structure drives both:

- Tap **Men** → a panel of its level-2 items slides in
- Tap **Clothing** → a panel of its level-3 items slides in
- Each panel has a **Back** button and a **View all** link

The promotion image, heading, text and button do **not** appear on mobile. If a promotion carries
information a shopper genuinely needs, put it somewhere else as well — a home page section, or a
menu item of its own.

---

## Recommended complexity

These are practical limits, not enforced ones.

| | Recommended maximum | Why |
| --- | --- | --- |
| Top-level items | 7 | Beyond this the header wraps or crowds on smaller laptops. |
| Mega menus | 2–3 | Not every item needs one. Reserve them for your biggest departments. |
| Columns per mega menu | 4 | Five is supported but gets cramped once you add a promotion. |
| Links per column | 8 | Longer columns are scanned less. Split into two columns instead. |
| Levels | 3 (Shopify's maximum) | Two is often better — every extra level is an extra tap on mobile. |

A mega menu with 60 links is not more useful than one with 20. It is a navigation aid, not a
sitemap.

---

## Worked example: a small mega menu

Goal: one mega menu on "Shop", with a promotion for a new range.

**In Shopify admin → Content → Menus → Main menu:**

```text
Shop                     → /collections/all
├── New in               → /collections/new-in
├── Best sellers         → /collections/best-sellers
├── Clothing             → /collections/clothing
│   ├── Tops             → /collections/tops
│   └── Bottoms          → /collections/bottoms
└── Sale                 → /collections/sale
About                    → /pages/about
Journal                  → /blogs/news
Contact                  → /pages/contact
```

Because "Clothing" has children, the whole "Shop" item renders as a mega menu with four columns:
New in, Best sellers, Clothing (with two links), and Sale.

**In the Theme Editor → Header → Add block → Mega menu:**

- Menu item position: **1** (Shop is first)
- Columns: **4**
- Image: your new-range photo
- Heading: `Autumn arrivals`
- Text: `Twelve new pieces, in store now.`
- Link: `/collections/autumn`
- Link label: `Shop the range`

---

## Troubleshooting

**The panel is a narrow dropdown instead of full width.**
None of the level-2 items have children, and no promotion image, heading or text is set. Add a
third level, or add a promotion.

**The promotion is on the wrong menu item.**
The **Menu item position** is counted from the left. Count your top-level items again — and check
whether the menu was reordered in Shopify admin since you set the block up.

**The promotion button does not appear.**
Both **Link** and **Link label** must be filled in.

**Level-3 links are missing.**
Confirm they are nested under a level-2 item in Shopify admin, not added as separate level-2
items. The indentation in the Shopify menu editor shows the nesting.

**Nothing shows on mobile.**
Promotions are desktop only, by design. The links themselves should still be there in the drawer.

More in [Troubleshooting](troubleshooting.md).
