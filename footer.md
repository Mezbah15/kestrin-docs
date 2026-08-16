# Footer

The footer appears on every page and has two parts: a set of **columns** you build from blocks,
and a **bottom bar** of store-wide links and icons.

**Where to find it:** Theme Editor → **Footer**, at the bottom of the left sidebar. It appears on
every template and is configured once.

---

## Footer columns

Columns are blocks. Add them with **Add block**, reorder by dragging, remove with
**Remove block**.

| Setting | Notes |
| --- | --- |
| **Columns** | 2–5. The most blocks per row on desktop. Extra blocks wrap onto a new row, and every block stacks into an accordion on mobile. |

### Menu block

A column of links from one of your Shopify menus.

| Setting | Notes |
| --- | --- |
| **Heading** | Leave blank to reuse the menu's own name as the column title. |
| **Menu** | Any menu from **Shopify admin → Content → Menus**. Defaults to `footer`. |

You can add several Menu blocks pointing at different menus — one for "Shop", one for "Help", one
for "Company".

Only the **first two levels** of a menu make sense in a footer column; nesting deeper than that
in a footer is rarely useful.

### Text block

A short paragraph — usually a one-line description of the business.

| Setting | Notes |
| --- | --- |
| **Heading** | Optional. |
| **Text** | Rich text. |

### Newsletter block *(once)*

An email sign-up form in a footer column.

| Setting | Notes |
| --- | --- |
| **Heading** | Optional. |
| **Text** | Rich text above the field. |

Sign-ups are saved as customers in Shopify admin, tagged `newsletter`. Sending the emails is your
email platform's job — Shopify Email or an app from the App Store.

### Social block *(once)*

Places the social icons in a specific footer column.

| Setting | Notes |
| --- | --- |
| **Heading** | Optional. |

The icons themselves come from **Theme settings → Social media**. This block only decides which
column they sit in. If you also have **Show social icons** enabled in the bottom bar, you will
have them twice — pick one.

### Contact block *(once)*

Contact details as a column.

| Setting | Notes |
| --- | --- |
| **Heading**, **Text** | Optional. |
| **Phone** | Rendered as a clickable phone link. |
| **Email** | Rendered as a clickable email link. |

### Image block

An image in a footer column — a payment badge Shopify does not provide, a certification, an
award.

| Setting | Notes |
| --- | --- |
| **Image** | Any image. |
| **Width** | 60–240px. |
| **Link** | Optional. |

### App blocks

Any app that provides a footer block can be placed here.

---

## The bottom bar

The strip below your footer columns. Each part is a toggle.

| Setting | What it shows | Where the content comes from |
| --- | --- | --- |
| **Show social icons** | Icons for your social profiles | **Theme settings → Social media**. Stays hidden while no links are filled in. |
| **Show Follow on Shop button** | A button letting shoppers follow your store in the Shop app | Shopify. The button's wording and colors are set by Shopify and cannot be restyled. |
| **Show payment icons** | The payment methods you accept | **Settings → Payments** in Shopify admin. Icons cannot be uploaded here — use a footer Image block for a badge Shopify does not provide. |
| **Show country/region and language pickers** | Market and language selectors | **Settings → Markets** and **Settings → Languages**. Nothing appears until you sell in more than one country or publish more than one language. |
| **Show store policy links** | Refund, privacy, terms of service and shipping | **Settings → Policies**. Nothing appears until at least one is saved. |
| **Extra copyright text** | Added after the year and your store name | Typed here — for example a company number, VAT ID, or "All rights reserved". |

The copyright line is generated automatically as the current year and your store name. The
**Extra copyright text** field adds to it; it does not replace it.

### Appearance

| Setting | Default |
| --- | --- |
| **Color scheme** | `scheme-2` — a tinted scheme, so the footer reads as separate from the page. |
| **Top padding** | 56px |
| **Bottom padding** | 32px |

---

## Store policies

Policy links are worth setting up properly. In **Shopify admin → Settings → Policies** you can
save a refund policy, privacy policy, terms of service, shipping policy and contact information.
Shopify provides templates you can adapt.

Once saved, they appear in the footer automatically with **Show store policy links** on. They
are also linked from checkout. In many jurisdictions publishing them is a legal requirement, and
several payment providers require them before approving an account.

---

## Responsive behavior

| Screen | Footer |
| --- | --- |
| **Phone** | Every column becomes a collapsible accordion row, so the footer is a short list of headings rather than a long scroll. The bottom bar stacks and centers. |
| **Tablet** | Two columns. |
| **Desktop** | Your configured number of columns; extra blocks wrap to a new row. |

The accordion behavior on mobile is automatic. It is the main reason a five-column footer does
not become a problem on a phone.

---

## Recommended footer structure

A four-column footer that covers what shoppers actually look for:

| Column | Block | Content |
| --- | --- | --- |
| 1 | Text | One or two sentences about the business. |
| 2 | Menu | **Shop** — main collections. |
| 3 | Menu | **Help** — shipping, returns, FAQ, contact, size guide. |
| 4 | Newsletter | Sign-up form. |

With the bottom bar showing social icons, payment icons, policy links and — if you sell
internationally — the country and language pickers.

The **Help** column matters more than it looks. Shipping and returns information is one of the
most-sought things on any store, and the footer is where shoppers instinctively look for it.

---

## Troubleshooting

**Policy links do not appear.** Save at least one policy under **Settings → Policies**.

**Payment icons do not appear.** They are read from **Settings → Payments**. If no provider is
configured, there is nothing to show. They also cannot be customized or uploaded — use an Image
block instead.

**Social icons do not appear.** Fill in at least one URL under **Theme settings → Social media**.

**Country and language pickers do not appear.** They only show when you actually sell in more
than one country (**Settings → Markets**) or publish more than one language
(**Settings → Languages**).

**A menu column is empty.** Confirm the selected menu exists and has items in
**Shopify admin → Content → Menus**.

More in [Troubleshooting](troubleshooting.md).
