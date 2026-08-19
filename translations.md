# Translations, languages and localization

The theme's text is fully translatable, and eight languages ship with it. This guide explains how
language, country and currency work in Shopify, what the theme actually supplies, and where the
boundary between the two sits.

---

## Four things people call "localization"

These are separate systems. Confusing them is the source of most localization support tickets.

| | What it is | Who owns it |
| --- | --- | --- |
| **Theme translations** | The fixed wording the theme renders — "Add to cart", "Sold out", form labels, error messages | The theme's `locales/` files, editable under **Edit default theme content** |
| **Content translations** | Your product titles, descriptions, collection names, page copy, menu labels, and anything you typed into a theme setting | Shopify — Translate & Adapt or a translation app |
| **Language** | Which language the storefront renders in | Shopify — Settings → Languages |
| **Market, country and currency** | Which countries you sell to, and what currency and pricing each gets | Shopify — Settings → Markets |

**The theme does not control Markets, currency conversion, pricing, or which languages exist.**
It reads what Shopify has published and renders selectors for it. Everything below is written with
that division in mind.

---

## Languages included

The theme ships storefront text in **eight languages**:

| Language | File | Direction |
| --- | --- | --- |
| English (default) | `en.default.json` | Left to right |
| Arabic | `ar.json` | **Right to left** |
| French | `fr.json` | Left to right |
| German | `de.json` | Left to right |
| Italian | `it.json` | Left to right |
| Polish | `pl.json` | Left to right |
| Romanian | `ro.json` | Left to right |
| Spanish | `es.json` | Left to right |

Every piece of theme text is present in all eight. When you publish one of these languages,
shoppers browsing in it see the theme in their language with no work from you.

> **The Theme Editor itself is English only.** Setting names and help text in the editor
> (`en.default.schema.json`) are supplied in English. This affects you as the merchant configuring
> the theme; it does not affect what shoppers see.

### Plural forms

Counted messages — "3 results", "2 items in your cart" — carry every grammatical form the language
declares, not just a singular and a plural. Arabic ships six forms, Polish four, Romanian three,
the rest two. Counts that the theme recalculates without a page reload (filter results, search
suggestion counts) pick the right form in the browser, so the grammar stays correct as the number
changes.

---

## Publishing a language

**Shopify admin → Settings → Languages**

1. Click **Add language** and choose one.
2. Translate your content — see below.
3. Click **Publish** when you are ready for shoppers to see it.

An unpublished language is visible to you for preparation but not to shoppers.

Once more than one language is published, the theme's **language selector** becomes available.
Turn it on in **Theme Editor → Header → Show country/region and language selectors** and
**Theme Editor → Footer → Show country/region and language selectors**. It stays hidden until you
actually have more than one language, so enabling it early does no harm.

---

## The country and language selectors

The theme renders two selectors, both backed by Shopify's own `localization` form:

- **Country/region** — shows the current country and its currency code and symbol, and lists every
  country your Markets configuration makes available. Choosing one submits `country_code`.
- **Language** — shows each language under its own name (Deutsch, Français, العربية) and submits
  `language_code`.

Points worth knowing:

- **Each option is a real submit button**, so both selectors work with JavaScript disabled or
  broken. JavaScript only handles opening and closing the panel and closing it on Escape or an
  outside click.
- **A selector renders nothing at all** unless Shopify reports more than one country (for the
  country selector) or more than one published language (for the language selector). One of the two
  can appear without the other.
- They appear in the **footer** and, when enabled, in the **header** and the **mobile menu drawer**.
- **Switching country changes currency and pricing** because Shopify recalculates the market — the
  theme does not convert anything.

---

## Right-to-left languages and Arabic

Publishing a right-to-left language switches the whole storefront to RTL. This is implemented, not
approximated.

**What happens automatically**

- The page declares `dir="rtl"`, so the entire layout mirrors — text alignment, grid and flex
  order, drawers sliding in from the correct edge, and paddings and offsets that are written as
  logical properties rather than left/right.
- **Directional icons flip.** Arrows and chevrons that mean "forward" or "back" are mirrored, so
  a "next" arrow still points the way the reader is going.
- **Keyboard arrow keys reverse.** Left and right arrow keys move through menus and slideshow
  slides in reading order, not in fixed screen order.
- **Uppercase eyebrow text, badges, vendor lines and similar tracked-out labels** drop their
  letter-spacing, which is a Latin typographic device and damages Arabic word shaping.

**Arabic typography.** Shopify's font picker offers very little with Arabic coverage, so an Arabic
storefront would otherwise fall back to whatever the system happens to resolve — usually a face
that carries Arabic badly. On an RTL document the theme inserts a Naskh-first fallback chain
(`Noto Naskh Arabic`, `Geeza Pro`, `Segoe UI`, `Tahoma`, `Traditional Arabic`) **after** your chosen
font but **before** the generic fallback. The practical effect:

- Latin text on an Arabic storefront still uses the font you picked.
- Arabic glyphs your chosen font does not carry reach a proper Arabic face instead of a default.
- An LTR storefront is untouched — your font stack is exactly what you chose.

**Limitations to be aware of**

- The theme does not ship an Arabic webfont; it relies on faces already present on the device. On
  an unusual device the final fallback still applies.
- Right-to-left rendering of *your* content depends on your content. Text you typed in a
  left-to-right language stays left-to-right, as it should.
- Images with baked-in text are not mirrored. Upload a per-language image if the composition
  depends on direction.

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
- Some entries contain placeholders in braces, like {% raw %}`{{ count }}`{% endraw %} or {% raw %}`{{ title }}`{% endraw %}. Keep them
  exactly as they are — they are replaced with real values. Removing one breaks the message.
- Counted entries have one line per grammatical form. Fill in every form the language shows you;
  leaving one blank means that count renders nothing.

---

## Multi-market stores

**Settings → Markets** is where you set which countries you sell to, which currency each uses, and
which language each defaults to. All of that is Shopify's, not the theme's.

What the theme does with it:

- **Prices are formatted by Shopify** in the active currency everywhere in the theme. The theme
  never formats or converts currency itself, so amounts are always correct for the market — on
  cards, product pages, the cart, and in social sharing metadata.
- **The country selector** lets shoppers change market, which changes prices into that market's
  currency.
- **Text direction** follows the published language automatically.

### The free shipping bar and markets

**The free shipping threshold is a single number you type in your store's own currency**, and
Shopify exposes no per-market equivalent. Comparing that number against a cart priced in another
currency would promise free shipping the checkout will not honour.

So the theme takes the honest option: **the free shipping bar appears only while the shopper is
buying in your store's primary currency.** In every other market it is hidden, and shoppers see
the shipping rates Shopify actually applies at checkout. There is nothing to configure, and
nothing to check per market. See [Cart](cart.md).

### Things to check on a multi-market store

- **Announcement bar and section text you typed** is your content — translate it with Translate &
  Adapt like any other content.
- **Your shipping rates per market** actually match what you promise anywhere you promise it.
- **Each published language reads correctly**, including any wording you changed under Edit default
  theme content — those edits are per language.

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
{% raw %}`{{ count }}`{% endraw %} was probably removed or altered during editing. Restore it exactly.

**A counted message is blank at some numbers.** The grammatical form for that count was left empty
under Edit default theme content. Fill in every form the language lists.

**My wording changes disappeared after an update.** Theme content edits belong to the theme they
were made on and do not transfer to a newly uploaded version. Reapply them, and keep a note next
time. See [Updating](updating.md).

**The language or country selector does not appear.** The language selector only shows when more
than one language is **published**; the country selector only shows when Markets makes more than
one country available. Both also need the setting enabled on the header or footer.

**The free shipping bar disappeared in another currency.** That is deliberate — see above.

More in [Troubleshooting](troubleshooting.md).
