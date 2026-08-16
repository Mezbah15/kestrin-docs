# Navigation best practices

Good navigation is the single highest-impact thing you can get right on a storefront. This guide
covers how Shopify menus work, how the theme interprets them, and how to structure yours.

---

## How Shopify navigation works

Menus live in **Shopify admin → Content → Menus**, not in the theme. Each menu has a **handle**
(a short identifier like `main-menu`) that the theme uses to select it.

A menu item has:

- A **name** — the text shoppers see
- A **link** — a collection, product, page, blog, policy, external URL, or the home page
- Optionally, **nested items** beneath it

Shopify allows **three levels**. A fourth is not possible.

Editing a menu takes effect immediately on every theme that uses it, including your live theme.
There is no per-theme copy of a menu. Bear this in mind: restructuring your menu while testing an
unpublished theme will also change your live store.

---

## The two menus the theme uses by default

| Handle | Where it appears | Set in |
| --- | --- | --- |
| `main-menu` | Header navigation and mobile drawer | Theme Editor → Header → Menu |
| `footer` | A footer column | Theme Editor → Footer → each Menu block |

You can point either at any menu you like, and the footer can use several different menus across
its columns.

Shopify also maintains `customer-account-main-menu`, used inside the signed-in account panel.

---

## How the theme interprets nesting

The theme renders each top-level item differently depending on what is nested beneath it.

| Structure | Desktop | Mobile |
| --- | --- | --- |
| No children | Plain link | Plain link |
| Children only | Compact dropdown list | Slide-in panel |
| Children with grandchildren | Full-width mega menu | Slide-in panel, then another for the third level |

You do not switch between these in the theme. You choose them by how you nest items in Shopify
admin. See [Mega menu](mega-menu.md) for the details.

**A parent item's own link is never lost.** When an item has children, clicking the parent opens
the panel rather than following its link — so the theme adds a **View all [name]** link inside
the panel pointing at the parent's URL. Give your parent items real links wherever you can.

---

## Naming conventions

- **Use the words your customers use.** "Trousers" or "Pants" — whichever your market says. Not
  your internal category codes.
- **Keep names short.** One or two words. Long names wrap awkwardly in the header and push other
  items off the row.
- **Be consistent.** Either all plural ("Shirts", "Jackets") or all singular. Mixing reads as
  careless.
- **Avoid clever labels.** "The Edit" tells a shopper nothing. "New in" tells them everything.
- **Sentence case beats ALL CAPS** in the menu editor — if you want capitals, use
  **Theme settings → Typography → Heading case**, which handles letter-spacing properly.

---

## Depth: prefer two levels

Three levels are supported, but each level costs a tap on mobile. A shopper reaching a level-3
collection has tapped the menu button, a parent, a child, and then the link — four taps.

Use three levels when a department genuinely has sub-departments (Men → Clothing → Shirts).
Use two when it does not (Accessories → Bags, Belts, Hats).

Signs your menu is too deep:

- A level-2 item has only one or two children — merge it upward
- You have level-3 items that duplicate level-2 items elsewhere
- You cannot explain the difference between two levels without pausing

---

## Breadth: keep the top level short

Seven top-level items is a good ceiling. Beyond that, the desktop header starts wrapping on
smaller laptop screens, and the mobile drawer becomes a scroll.

Items that almost always earn a top-level slot: your main product departments, **Sale** if you
run one, and **Contact**. Items that usually do not: **About**, **FAQ**, **Shipping** — those
belong in the footer, where shoppers look for them anyway.

---

## Mobile considerations

- **Test the drawer, not just the header.** They are different layouts driven by the same menu.
- **Long lists are fine** in the drawer; deep nesting is what hurts.
- **Put your highest-traffic link near the top.** Shoppers do not scroll a menu they expected to
  be short.
- **Mega menu promotions do not appear on mobile.** Anything essential must exist as a menu item
  too.

---

## Worked examples

These are starting points. Adapt the names to your catalogue.

### Fashion

```text
New in                → /collections/new-in
Women
├── Clothing
│   ├── Dresses
│   ├── Tops
│   ├── Knitwear
│   └── Trousers
├── Shoes
│   ├── Boots
│   ├── Flats
│   └── Heels
├── Accessories
│   ├── Bags
│   └── Jewellery
└── Shop all Women
Men
├── Clothing
│   ├── Shirts
│   ├── T-shirts
│   ├── Knitwear
│   └── Trousers
├── Shoes
└── Accessories
Sale                  → /collections/sale
Journal               → /blogs/journal
```

Women and Men both become mega menus. New in, Sale and Journal are plain links.

### Electronics

```text
Computers
├── Laptops
│   ├── Ultrabooks
│   ├── Gaming laptops
│   └── Workstations
├── Desktops
├── Monitors
└── Components
Audio
├── Headphones
├── Speakers
└── Turntables
Phones & tablets
├── Phones
├── Tablets
└── Cases & covers
Accessories           → /collections/accessories
Deals                 → /collections/deals
Support               → /pages/support
```

Computers becomes a mega menu; Audio and Phones & tablets become dropdowns. Note that
"Components" and "Desktops" have no children and still get their own column in the Computers
panel.

### Home and living

```text
Furniture
├── Living room
│   ├── Sofas
│   ├── Armchairs
│   └── Coffee tables
├── Bedroom
│   ├── Beds
│   └── Wardrobes
└── Dining
Textiles
├── Bedding
├── Towels
└── Rugs
Kitchen               → /collections/kitchen
Lighting              → /collections/lighting
Sale                  → /collections/sale
```

Furniture becomes a mega menu. Textiles becomes a dropdown. Kitchen, Lighting and Sale are plain
links.

---

## A checklist before you publish

- [ ] Every menu item points somewhere that exists — no dead links
- [ ] Every parent item has its own URL, so **View all** works
- [ ] Seven or fewer top-level items
- [ ] Names match what customers call things
- [ ] Tested in the mobile drawer, not only the desktop header
- [ ] Mega menu block positions still match after any reordering
- [ ] Footer menu covers About, policies, contact and help
