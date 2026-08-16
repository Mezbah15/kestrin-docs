# Custom code

Most stores never need to edit theme code. This page explains when it is worth it, when it is
not, and how to do it without making your store harder to maintain.

---

## Try these first

Before opening the code editor, check whether one of these covers what you need.

**1. The Theme Editor.** The theme has a large number of settings, and merchants regularly edit
code to achieve something a setting already does. Look through
[Theme settings](theme-settings.md) and the section you are trying to change.

**2. A different section.** Twenty-three sections can be added to any page. Before building
something custom, check whether **Multicolumn**, **Rich text**, **Image with text**, **Collapsible
content** or **Custom section** already does it.

**3. The Custom section.** An empty section you fill with Text and Group blocks. Group blocks
arrange as rows or columns and can nest, so you can build simple custom layouts with no code.

**4. Native Shopify features.** Discounts, Markets, Customer events, Search & Discovery,
Translate & Adapt and metafields cover a great deal. See
[Third-party apps](third-party-apps.md) for a list.

**5. An app.** Sometimes the right answer, if it is a well-built one.

**6. Custom code.** Last, not first.

---

## When custom code is reasonable

- Adding a tracking script that Shopify's **Customer events** cannot handle
- A small visual adjustment no setting covers
- Integrating a service that provides a code snippet
- A genuinely bespoke feature your business depends on

## When it is not

- **Changing colors, fonts, spacing or corner radius** — these are all settings
- **Rearranging a page** — sections and blocks reorder by dragging
- **Hiding an element** — usually there is a setting; hiding with CSS leaves it in the page for
  screen readers and search engines
- **Because a tutorial said to** — tutorials are written against other themes and often other
  eras of Shopify
- **Removing focus outlines** — this breaks keyboard accessibility. Never do this.

---

## Rules for changing code safely

### 1. Never edit your live theme

Duplicate it first: **Online Store → Themes → ⋯ → Duplicate**. Edit the duplicate, preview it,
publish when it works. If it goes wrong, delete the duplicate — your live store was never
touched.

### 2. Back up before you start

**Online Store → Themes → ⋯ → Download theme file**. Shopify emails you a `.zip`. Keep it.

### 3. Change one thing at a time

Make one change, preview it, confirm it works, then make the next. Ten changes at once means ten
suspects when something breaks.

### 4. Document every change

Keep a plain text file recording, for each change: the file, roughly where, what it does, why,
and the date. Comment the code itself too:

{% raw %}
```liquid
{% comment %} Custom: badge for pre-order products — added 2026-03-14 {% endcomment %}
```
{% endraw %}

**You will need this at your next theme update.** Custom code does not carry across, and
undocumented changes are the main reason updates go badly. See [Updating](updating.md).

### 5. Prefer additive changes

Adding a new snippet or a new section is safer than editing an existing one, because a new file
survives an update untouched while an edited file has to be re-edited.

### 6. Test everything

Desktop and mobile. Every page type, not only the one you changed. The full purchase flow. Try a
keyboard.

### 7. Know how to undo it

Shopify keeps a change history per file in the code editor (**⋯ → Older versions** on a file), but
do not rely on it as your only safety net. Your backup and your notes are the real ones.

---

## Where to put custom code without editing files

Several needs can be met without touching theme files at all — which means they survive updates
far better.

| Need | Where |
| --- | --- |
| A tracking pixel or analytics script | **Settings → Customer events → Add custom pixel** |
| A block of Liquid or an app snippet on one page | The **Custom liquid** section |
| Custom Liquid within a product page | The product page's **Custom liquid** block |
| An app's widget | The app's own block, or the **Apps** section |
| Extra product data | **Metafields** (Settings → Custom data) |

**Use Customer events for tracking pixels.** Shopify loads them in a managed sandbox, which is
safer and faster than a script pasted into the layout, and it survives theme changes entirely.

---

## The Custom liquid section and block

The most useful escape hatch the theme provides.

- **Section:** Theme Editor → Add section → **Custom liquid**. Available on any template.
- **Block:** on the product page, **Add block → Custom liquid**.

Both accept Liquid, HTML, app snippets and metafield output. The section has an **Apply theme
text styles** option — leave it on so your content matches the rest of the theme, or turn it off
if your code brings its own styles.

Both stay hidden while empty, so an unused one costs nothing.

**Only paste code you understand, or that came from a source you trust.** Code pasted into a
theme runs on every visit, with full access to the page.

---

## If you are hiring a developer

- Give them this documentation and the [Developer guide](developer-guide.md).
- Ask them to work on a **duplicate** theme, never the live one.
- Ask for **written documentation** of every change, in a file kept with the theme.
- Ask them to prefer **new files** over edits to existing ones.
- Ask them to test on mobile and with a keyboard.
- Get the theme back as a `.zip` as well as installed, so you have a copy.

---

## Support and custom code

Theme support covers the theme as supplied. It does not cover custom code, debugging
modifications, or restoring a theme that customization has broken.

If you report a problem on a customized theme, support may ask you to reproduce it on an
unmodified copy first — that is how a theme bug is distinguished from a customization bug. See
[Support](support.md).

None of this means you should not customize. It means: duplicate, document, and keep a backup.
