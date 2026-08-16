# Translations and languages

The theme's text is fully translatable, and five languages ship with it. This guide explains how
language works in Shopify, what the theme supplies, and how to change the wording.

---

## Two kinds of text

This distinction explains almost everything about translating a Shopify store.

| | Comes from | Translated in |
| --- | --- | --- |
| **Your content** — product titles, descriptions, collection names, page content, menu labels, blog posts | Shopify admin | Shopify's Translate & Adapt app, or a translation app |
| **Theme text** — "Add to cart", "Sold out", "Search", "Your cart is empty", form labels, error messages | The theme's language files | Shopify admin → Themes → Edit default theme content |

The theme supplies the second kind. It cannot translate the first — that is your content, and
Shopify handles it.

---

## Languages included

The theme ships storefront text in **five languages**:

| Language | Code |
| --- | --- |
| English (default) | `en` |
| French | `fr` |
| German | `de` |
| Spanish | `es` |
| Italian | `it` |

Every piece of theme text is present in all five. When you publish one of these languages,
shoppers browsing in it see the theme in their language with no work from you.

> **The Theme Editor itself is English only.** Setting names and help text in the editor are
> supplied in English. This affects you as the merchant configuring the theme; it does not affect
> what shoppers see.

---

## Publishing a language

**Shopify admin → Settings → Languages**

1. Click **Add language** and choose one.
2. Translate your content — see below.
3. Click **Publish** when you are ready for shoppers to see it.

An unpublished language is visible to you for preparation but not to shoppers.

Once more than one language is published, the theme's **language picker** becomes available. Turn
it on in **Theme Editor → Header → Show country/region and language pickers** and
**Theme Editor → Footer → Show country/region and language pickers**. It stays hidden until you
actually have more than one language, so enabling it early does no harm.

---

## Translating your content

Install **Translate & Adapt** (free, made by Shopify) from the Shopify App Store.

It walks you through every translatable item — products, collections, pages, blog posts, menus,
policies, checkout text and theme text — language by language. It also offers machine translation
as a starting point, which you should review rather than publish as-is.

Third-party translation apps work too. Any app that uses Shopify's translation system will
translate the theme's text alongside your content.

---

## Changing theme wording

You can reword any of the theme's text — to change "Add to cart" to "Add to bag", for example —
without editing code.

**Shopify admin → Online Store → Themes → ⋯ (next to Kestrin) → Edit default theme content**

You get a searchable list of every piece of theme text, grouped by area (Products, Cart, Search,
Accessibility, and so on). Change any entry and save.

Notes:

- Changes apply to **that theme only**, and are kept when you edit the theme further.
- **They are not carried across when you upload a new version of the theme.** Note any wording
  changes you make so you can reapply them after an update — see [Updating](updating.md).
- Do the same in each published language, from the language switcher at the top of that screen.
- Some entries contain placeholders in braces, like `{{ count }}` or `{{ title }}`. Keep them
  exactly as they are — they are replaced with real values. Removing one breaks the message.

---

## Multi-market stores

If you sell internationally, **Settings → Markets** lets you set which countries you sell to,
which currency each uses, and which language each defaults to.

The theme's **country/region picker** lets shoppers switch market, which changes prices into that
market's currency. It appears in the header and footer when enabled, and in the mobile menu
drawer.

Both pickers work without JavaScript, so they remain usable in any browser.

### Things to check on a multi-market store

- **Prices are formatted by Shopify** in the active currency throughout the theme. The theme
  never formats currency itself, so amounts are always correct for the market.
- **The free shipping threshold is a single number.** It cannot be right in three currencies at
  once. If you use the free shipping bar across several markets, check what it says in each one,
  and confirm it matches your actual shipping rates per market. See [Cart](cart.md).
- **Announcement bar and section text you typed** is your content — translate it with Translate &
  Adapt like any other content.
- **Text direction** is handled automatically. If you publish a right-to-left language, the
  layout mirrors.

---

## What is not translated automatically

- **Text you type into theme settings** — headings, announcement text, button labels, testimonial
  quotes. This is your content; translate it with Translate & Adapt.
- **Product and collection data.** Same.
- **Images containing text.** Upload a per-language image if you need one.
- **Apps.** Each app is responsible for its own translations.

---

## Troubleshooting

**Text appears in English on a translated store.**

1. Confirm the language is **published** under Settings → Languages, not just added.
2. Check whether the text is theme text or your content. Your content needs translating with
   Translate & Adapt.
3. Look for the specific phrase under **Edit default theme content** in that language.

**A translation shows the wrong thing, or a message looks broken.** A placeholder like
`{{ count }}` was probably removed or altered during editing. Restore it exactly.

**My wording changes disappeared after an update.** Theme content edits belong to the theme they
were made on and do not transfer to a newly uploaded version. Reapply them, and keep a note next
time. See [Updating](updating.md).

**The language picker does not appear.** It only shows when more than one language is published,
and when the setting is enabled on the header or footer.

More in [Troubleshooting](troubleshooting.md).
