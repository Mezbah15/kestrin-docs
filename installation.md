# Installation

This guide takes you from a downloaded theme file to a published store. It takes about ten
minutes and requires no code.

---

## Requirements

### Required

| | |
| --- | --- |
| Shopify plan | Any paid Shopify plan. The theme uses no plan-restricted features. |
| Store access | The **Themes** permission, or a staff account with full admin access. |
| Browser | A current version of Chrome, Edge, Safari or Firefox. |
| Theme file | The `.zip` archive supplied with your purchase or download. |

### Recommended before you start

- At least a few **products**, each with one clear image. The theme shows placeholder
  illustrations while your catalog is empty, which makes it hard to judge the design.
- At least two **collections**, so the collection and navigation sections have something to point at.
- Your **logo** as a PNG or SVG with a transparent background.
- Your store **policies** (refund, privacy, terms, shipping) saved under
  **Settings → Policies**. The footer links them automatically once they exist.
- **Payment providers** configured under **Settings → Payments**, so the footer payment icons
  and the checkout button behave as customers will actually experience them.

None of these are required to install the theme — but doing them first means your very first
preview looks like a real store rather than a demo.

---

## Understanding published, unpublished and preview

These three words appear throughout Shopify and mean different things. Getting them straight
now will save confusion later.

| Term | What it means |
| --- | --- |
| **Published** (live) | The one theme your customers see when they visit your domain. There is exactly one published theme at any time. |
| **Unpublished** | A theme sitting in your theme library. Customers cannot see it. You can edit it freely with zero risk to your live store. |
| **Preview** | A private view of an unpublished theme, on your real store data, through a temporary link. Only people with the link see it. |

The safe way to work is always: **upload as unpublished → customize → preview → publish**.

---

## 1. Download the theme

Download the theme archive to your computer. It will be a single `.zip` file.

**Do not unzip it.** Shopify expects the `.zip` exactly as supplied. If your browser or operating
system unzips it automatically, you will need to re-download it with automatic extraction turned
off, or compress the folder again with the theme's own folders (`assets`, `config`, `layout`,
`locales`, `sections`, `snippets`, `templates`) at the top level of the archive.

---

## 2. Upload the theme to Shopify

1. In Shopify admin, go to **Online Store → Themes**.
2. Scroll to **Theme library**.
3. Click **Add theme → Upload zip file**.
4. Choose the `.zip` file and click **Upload file**.

Shopify validates and installs the theme. This usually takes under a minute. When it finishes,
**Kestrin** appears in your theme library as an unpublished theme.

If the upload is rejected, the most common causes are: the archive was unzipped and re-zipped
with an extra wrapping folder, or the file is not a `.zip`.

---

## 3. Open the Theme Editor

Find Kestrin in your theme library and click **Customize**.

This opens the **Theme Editor** — the visual tool where you will do all of your setup. It has
three parts:

- **Left sidebar** — the sections that make up the page you are looking at
- **Center** — a live preview of your store
- **Right sidebar** — the settings for whatever you have selected

The dropdown at the top center switches between templates (Home page, Product, Collection, Cart,
and so on) so you can customize each page type.

Nothing you do in the Theme Editor on an unpublished theme affects your live store. Changes save
to this theme only.

---

## 4. Preview before publishing

You can preview at any time, and you should preview before you publish.

**From the Theme Editor:** click the eye icon (**Preview**) in the top bar. This opens your
store in a new tab, running the unpublished theme against your real products and collections.

**From the theme library:** click the **⋯** menu next to Kestrin and choose **Preview**. The
same menu has **Share preview**, which generates a link you can send to a colleague or client.
Anyone with that link sees the unpublished theme; nobody else does.

While previewing, check at minimum:

- The home page on a desktop-width window and a phone-width window
- One product page, including changing a variant and adding to cart
- One collection page, including a filter and a sort
- The cart, the search, and the footer links

See [Getting started](getting-started.md) for the full pre-launch checklist.

---

## 5. Publish the theme

When you are satisfied:

1. Go to **Online Store → Themes**.
2. Find Kestrin in your theme library.
3. Click **Publish**, then confirm.

Kestrin becomes your live theme immediately. Your previous theme moves into the theme library,
unpublished, with all of its settings intact — so you can switch back at any moment by
publishing it again.

---

## After publishing

- **Keep the old theme.** Do not delete your previous theme for at least a few weeks. It is your
  fastest possible rollback.
- **Re-test your apps.** Apps that inject code into a theme are configured per theme. Some will
  need to be re-enabled on Kestrin. See [Third-party apps](third-party-apps.md).
- **Check your live URLs.** Visit your real domain, not the preview link, and click through the
  header menu, a product, the cart and checkout.

---

## A note on editing code

You do not need to edit theme code to set up, customize or run this theme. Everything documented
in these merchant guides is done through Shopify admin or the Theme Editor.

If you do eventually need a code change, read [Custom code](custom-code.md) first — it explains
how to make changes that survive a theme update.
