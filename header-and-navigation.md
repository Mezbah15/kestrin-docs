# Header and navigation

The header sits at the top of every page and holds your logo, your main menu, and the search,
account and cart controls.

**Where to find it:** Theme Editor → **Header**, in the left sidebar. It appears on every
template, and its settings are shared across all of them — you configure it once.

---

## Header settings

### Menu

| Setting | What it controls |
| --- | --- |
| **Menu** | Which Shopify menu the header navigation uses. Defaults to `main-menu`. |

Menus are created in **Shopify admin → Content → Menus**, not in the theme. See
[Navigation best practices](navigation.md) for how to structure one.

If the selected menu is empty, the header hides the navigation, the mobile menu button, and the
mobile drawer entirely — leaving just the logo and the action icons.

### Layout

| Option | Result |
| --- | --- |
| **Logo left nav inline** | Logo on the left, menu beside it, actions on the right. The most compact option and the default. |
| **Logo left nav below** | Logo and actions on the top row, menu on its own row beneath. Suits long menus. |
| **Logo center nav below** | Logo centered on the top row, menu on its own row beneath. A more formal, symmetrical look. |

All three collapse to the same mobile layout: menu button, logo, actions.

### Behavior

| Setting | Options | What it does |
| --- | --- | --- |
| **Scroll behavior** | Static, Sticky, Reveal | **Static** scrolls away with the page. **Sticky** stays visible at all times. **Reveal** hides the header as shoppers scroll down and brings it back the moment they scroll up. |
| **Transparent header** | Disabled, Home page | Lets the header sit *over* the section below it instead of above it, on the home page only. |
| **Transparent header color scheme** | Any scheme | The colors used while the header is transparent. It switches to the normal scheme once the shopper scrolls. Only shown when transparent mode is on. |

**Recommended:** **Sticky** for most stores — it keeps search and cart one click away.
**Reveal** is a good compromise on content-heavy pages where a permanent header eats too much
screen. **Static** is the lightest, and fine for short pages.

**Transparent header** only works well when the first section on your home page opens with a
full-width image or video. Pair it with a dark color scheme over light imagery, or a light
scheme over dark imagery, and check the logo is still legible.

### Actions

| Setting | Options | What it does |
| --- | --- | --- |
| **Search** | Icon, Field, Hidden | **Icon** shows a magnifying glass that opens a search drawer. **Field** puts a search box directly in the header. **Hidden** removes header search entirely. |
| **Customer account menu** | Any menu | The menu shown inside the account panel once a shopper signs in. Defaults to Shopify's `customer-account-main-menu`. Nothing appears until customer accounts are enabled under **Settings → Customer accounts**. |
| **Show country/region and language pickers** | On / off | Off by default. Choices come from **Settings → Markets** and **Settings → Languages**. Nothing appears until you sell in more than one country or publish more than one language. |

### Appearance

| Setting | What it controls |
| --- | --- |
| **Color scheme** | The header's normal colors. |
| **Show a bottom border** | A hairline rule separating the header from the page. On by default. |
| **Top padding** / **Bottom padding** | 0–48px each. Controls the header's height. |

---

## What appears in the header

| Element | When it appears |
| --- | --- |
| **Menu button** (mobile) | Whenever the selected menu has items. Opens the mobile drawer. |
| **Logo** | Always. Falls back to your store name as text if no logo is uploaded. Links to the home page. |
| **Navigation** (desktop) | Whenever the selected menu has items. |
| **Search field** | Only when Search is set to **Field**. |
| **Country / language pickers** | Only when enabled *and* you have more than one country or language. |
| **Search icon** | Only when Search is set to **Icon**. |
| **Account icon** | Only when customer accounts are enabled in Shopify admin. |
| **Cart icon** | Always, with a live item count. Opens the drawer or goes to the cart page depending on your **Cart type** setting. |

---

## How the theme reads your menu

The theme does not have a separate "menu builder". It reads the menu you built in Shopify admin
and decides what to render from the shape of that menu.

| Your menu structure | What shoppers see on desktop |
| --- | --- |
| Top-level item with **no children** | A plain text link. |
| Top-level item with **children**, none of which have children | A compact dropdown list, anchored below the item. Includes a "View all" link if the parent item has a URL. |
| Top-level item whose **children have their own children** | A full-width **mega menu** panel, with each child as a column heading and its children as the links below. |
| Any top-level item with a **Mega menu block** attached that has an image, heading or text | A full-width mega menu, even if the children have no children of their own. |

This means you control the difference between a dropdown and a mega menu entirely through how you
nest items in Shopify admin. There is no switch in the theme.

Shopify menus go three levels deep and the theme renders all three. A fourth level is not
possible in Shopify.

See [Mega menu](mega-menu.md) for the promotional panel, and
[Navigation best practices](navigation.md) for worked examples.

---

## Desktop menu behavior

- Parent items are buttons, not links. Clicking one opens its panel; clicking again closes it.
- Only one panel is open at a time.
- Pressing **Escape** closes the open panel and returns focus to the item that opened it.
- Clicking outside the panel closes it.
- The parent item is marked as current when the shopper is on one of its child pages.
- Panels are fully keyboard accessible — see [Accessibility](accessibility.md).

If a parent item has a URL of its own (for example, a "Men" item pointing at the Men collection),
that URL is offered as a **View all** link inside the panel, so the parent page stays reachable
even though clicking the parent opens the menu instead.

---

## Mobile navigation

On phones and small tablets the menu becomes a full-height **drawer**, opened with the menu
button on the left of the header.

The drawer uses **one panel per level** rather than nested accordions:

1. The first panel lists your top-level items. Items with children show a chevron.
2. Tapping one **slides in a new panel** showing that item's children, with a **Back** button.
3. Tapping a child that itself has children slides in a third panel, again with a Back button.

Each panel that has a parent URL offers **View all [item name]** at the top of its list, so
shoppers can reach the parent page as well as its children.

This design keeps long menus usable: a shopper never scrolls past dozens of expanded items looking
for the one they want. It also means a deep menu is no harder to use on mobile than a shallow one
— but it does mean every extra level is an extra tap, which is a reason to keep menus to two
levels where you can.

Closing the drawer, tapping the backdrop, or pressing Escape all return focus to the menu button.

If **Show country/region and language pickers** is on, the pickers appear at the bottom of the
drawer.

---

## Search in the header

| Setting | Behavior |
| --- | --- |
| **Icon** | A magnifying glass opens a search drawer over the page. Available at all screen sizes. |
| **Field** | An always-visible search box. On desktop it sits inline in the header row; on mobile it moves to its own full-width row beneath the logo, so the header stays uncluttered. There is no search icon in this mode — the field is always there. |
| **Hidden** | No search in the header. Shoppers can still reach `/search` directly. |

**Recommended:** **Icon** for most stores — it keeps the header clean and the drawer gives the
search field plenty of room. Choose **Field** if search is how most of your customers browse, and
be aware it adds a row to the mobile header.

Either visible option supports predictive search — live suggestions as the shopper types —
controlled by **Theme settings → Search**. See [Search](search.md).

---

## The account icon

The account control is Shopify's own hosted `<shopify-account>` component. The theme styles it to
match your color scheme and supplies the signed-out icon, but sign-in, sign-up and the account
menu are handled by Shopify.

Consequences worth knowing:

- The icon appears only when customer accounts are enabled under **Settings → Customer accounts**.
- There is no theme setting for the sign-in form, because the theme does not render one.
- The **Customer account menu** setting decides what appears in the panel once a shopper is signed in.

---

## The cart icon

Always present, always showing a live count of items in the cart.

- With **Cart type: Drawer**, clicking it opens the cart drawer.
- With **Cart type: Page**, clicking it goes to the cart page.

The count updates automatically whenever anything is added to the cart, from anywhere on the
page. See [Cart](cart.md).

---

## The announcement bar

The announcement bar is a separate section that sits above the header, in the same header group.
See [Announcement bar](announcement-bar.md).

---

## Responsive behavior summary

| Screen | Header |
| --- | --- |
| **Phone** | Menu button, logo, action icons. Menu opens as a panelled drawer. Logo capped at 120px wide. |
| **Tablet** | As phone, with more breathing room. |
| **Desktop** | Full navigation visible, dropdowns and mega menus active, chosen layout applied. |

See [Responsive design](responsive-design.md).
