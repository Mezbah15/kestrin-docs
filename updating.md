# Updating the theme

Updating brings fixes, improvements and support for new Shopify features. Doing it carelessly can
cost you your customizations. This guide covers doing it safely.

---

## Why update

- **Bug fixes** for problems found since your version
- **Compatibility** with changes Shopify makes to its platform
- **New features** and settings
- **Performance and accessibility** improvements
- **Support** — the current version is the one that can be supported effectively

You are not obliged to update. If your store works and you have made significant customizations,
staying put is a legitimate choice. But do read the [changelog](changelog.md) for each release, in
case a fix affects you.

---

## What is carried over, and what is not

**Uploading a new theme version does not update your existing theme.** It adds a second,
separate theme to your library. Nothing about your live store changes until you publish it.

That new theme starts fresh:

| | Carried over? |
| --- | --- |
| Your products, collections, pages, blog posts | ✅ Yes — they live in Shopify, not the theme |
| Your menus | ✅ Yes — menus live in Shopify |
| Your policies, payment settings, markets | ✅ Yes — all Shopify |
| **Theme settings** — colors, fonts, layout, cart, search | ❌ No |
| **Section content and arrangement** on every template | ❌ No |
| **Header and footer configuration** | ❌ No |
| **Theme content edits** — reworded "Add to cart" and similar | ❌ No |
| **Custom code** you added | ❌ No |
| **App code injected into the theme** | ❌ No |

So an update is really: install the new version, re-do your configuration, verify, publish.

---

## Before you start

**Do not delete your current theme.** It is your rollback and your reference. Keep it in the
library for at least a few weeks after updating.

**Back it up.** Download a copy: **Online Store → Themes → ⋯ → Download theme file**. Shopify
emails you a `.zip`. Keep it somewhere safe. Do this even though the theme stays in your library
— it costs nothing and it is the only copy that survives an accidental deletion.

**Write down what you configured.** Work through your current theme and record:

- [ ] Every Theme settings panel — screenshots are quickest
- [ ] Header settings, and any Mega menu blocks (position, columns, promotion content)
- [ ] Announcement bar content and settings
- [ ] Home page section order, and each section's content and settings
- [ ] Product template block order and settings
- [ ] Collection, search, cart, blog, article, page, contact and 404 template settings
- [ ] Footer blocks and bottom bar settings
- [ ] Any **Edit default theme content** wording changes
- [ ] Any custom code, and where it was added
- [ ] Which apps have code in the theme

Screenshots of every settings panel are the single most useful thing you can prepare. Ten minutes
now saves an hour later.

**Note your current version.** It is shown in the Theme Editor under **Theme settings**, at the
bottom of the sidebar, or in the theme library. Compare it against the
[changelog](changelog.md).

---

## Updating

**1. Download the new version.** From wherever you obtained the theme.

**2. Upload it as a new theme.** Online Store → Themes → **Add theme → Upload zip file**. It
appears in your library as unpublished, alongside your current theme. Your live store is
untouched.

**3. Configure it.** Work through your notes and screenshots, in the same order as
[Getting started](getting-started.md):

- Theme settings first
- Then header and announcement bar
- Then the home page
- Then each remaining template
- Then the footer
- Then reapply any theme content wording changes
- Then reapply custom code — carefully, and only if still needed

**4. Re-enable your apps** on the new theme. App embeds are per-theme. Apps that inject code will
need reinstalling or re-enabling against the new theme; check each app's own instructions.

**5. Compare the two side by side.** Open your live store in one browser tab and the preview of
the new theme in another, and walk the same pages in both:

- [ ] Home page — every section present and correct
- [ ] A collection page — grid, filters, sorting
- [ ] A product page — media, variants, blocks, add to cart
- [ ] Cart and drawer
- [ ] Search
- [ ] Blog and an article
- [ ] Contact page
- [ ] Footer
- [ ] All of the above on a phone

**6. Test the full purchase flow** on the preview: add to cart, open cart, reach checkout.

**7. Publish.** When everything matches or is deliberately improved.

**8. Verify on the live site.** Repeat the key checks on your real domain, then watch your orders
and any error reports for a day or two.

---

## Rolling back

If something is wrong after publishing:

1. Go to **Online Store → Themes**.
2. Find your previous theme in the library.
3. Click **Publish**.

You are back within seconds, with all its settings intact. This is why you keep the old theme.

---

## If you have customized the code

Custom code does not carry across, and reapplying it is where updates go wrong.

**Do not** copy your old theme files over the new ones. File contents change between versions, and
overwriting a new file with an old one reintroduces the bugs the update fixed — often silently.

**Do** reapply each change individually to the new version, checking each one still makes sense.
Some may now be unnecessary because the update covers them natively.

If your customizations are extensive, ask whoever made them to handle the update. And read
[Custom code](custom-code.md) for how to make future customizations easier to carry forward.

---

## A note on frequency

There is no need to update the moment a release appears. A reasonable approach:

- **Read the changelog** for every release
- **Update promptly** for a fix that affects something you rely on, or a compatibility fix
- **Otherwise, update when it suits you** — not during a sale, not the week before a launch, and
  never on a Friday afternoon

---

## Summary

1. Keep the old theme. Download a backup.
2. Screenshot every settings panel.
3. Upload the new version as a separate, unpublished theme.
4. Reconfigure it from your notes.
5. Re-enable apps.
6. Compare side by side, on desktop and mobile.
7. Test checkout.
8. Publish, verify, and keep the old theme for a few weeks.
