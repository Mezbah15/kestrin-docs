# Performance

A fast store sells more and ranks better. The theme is built to be light; most of what happens
to your store's speed after that is in your hands.

---

## What the theme does for performance

You do not need to configure any of this.

**Assets load per page.** Each section loads only the CSS and JavaScript it actually needs. A
page without a slideshow does not download slideshow code.

**No framework and no build step.** There is no large JavaScript library to download and parse
before the page becomes interactive.

**Responsive images.** Every image is offered in a range of sizes and the browser downloads the
one that fits the screen. A phone never downloads a desktop-sized image.

**Lazy loading.** Images below the first screen are fetched as the shopper scrolls.

**Fonts are preloaded** from Shopify's CDN, and text remains visible while they load rather than
flashing invisible.

**Interactions avoid full page loads.** Adding to cart, changing quantities, filtering, sorting
and switching variants all update just the part of the page that changed.

**Third-party video is deferred.** A YouTube or Vimeo embed loads its player and scripts only
after a visitor presses play. An unplayed embed costs nothing.

**Maps are deferred.** The contact page map is fetched only when a visitor taps the button.

---

## What affects your store's speed

In rough order of impact:

### 1. Images

Almost always the largest thing on a page.

- **Do not upload 8MB photographs.** Aim for under 500KB per image, under 1MB for a full-width
  hero.
- **Do not upload undersized images either** — the theme scales down but cannot scale up.
  2000–2400px is right for products; 2400–3000px for full-width heroes.
- **Use JPEG for photography**, PNG only where you need transparency.
- Shopify converts and serves modern formats automatically, so you do not need to do that
  yourself.

See [Images and media](images-and-media.md).

### 2. Apps

**This is the biggest variable on most stores, and the one merchants most often overlook.**

Every app that adds something to your storefront adds code to every page — often its own
JavaScript, its own CSS, and requests to its own servers. Five apps can easily outweigh the
entire theme.

- **Audit what you have.** Go through your installed apps and ask what each one earns you.
- **Uninstall what you do not use.** Uninstalling is not always enough — some apps leave code
  behind. Check **Online Store → Themes → Edit code** for leftover snippets, or ask the app's
  support to confirm removal.
- **Prefer Shopify's native features** where they exist. Search & Discovery instead of a search
  app. Shopify Email instead of a marketing app. Discounts and Shopify Functions instead of a
  discount app.
- **Prefer apps that use app blocks** — they load only on the pages where you have placed them,
  rather than on every page.
- **Measure before and after.** Run a speed test, install the app, run it again.

See [Third-party apps](third-party-apps.md).

### 3. Third-party scripts

Analytics, chat widgets, heat maps, pixels, A/B testing tools. Each one is another download and
another connection.

- Keep the list short and know what each one is for.
- Use Shopify's **Customer events** (Settings → Customer events) for tracking pixels rather than
  pasting them into the theme — Shopify manages the loading.
- Remove scripts for tools you no longer use. Old pixels linger for years.

### 4. Video

- Prefer Shopify-hosted video to an embed where you can.
- Keep it short and upload at 1080p, not 4K.
- Use background video sparingly — one is fine, three is not.

### 5. Page weight

- **Six to eight home page sections** is a reasonable ceiling.
- **16–24 products per collection page.** 48 makes the first load noticeably slower on mobile.
- Two or three slideshow slides, not eight.

### 6. Custom code

Every line you add is code that has to be downloaded and run. See
[Custom code](custom-code.md).

---

## How to test

### Shopify's own report

**Shopify admin → Online Store → Themes → Store speed**

A score based on real visits to your store, with a comparison against similar stores. It updates
over time, so use it to watch trends rather than to judge a single change.

### Google PageSpeed Insights

https://pagespeed.web.dev/

Test your **live** store, not a preview link — a preview runs extra editor code and will always
score worse.

Test at minimum: the home page, a collection page, and a product page. Check the **Mobile** tab
first; it is the harder test and the one that matters most.

Focus on the diagnostics, not the number. "Properly size images" and "Reduce unused JavaScript"
tell you what to actually do.

### Real device testing

Load your store on a phone, on mobile data rather than wifi. This is the experience many of your
customers have, and no lab test reproduces it exactly.

---

## About performance scores

**This documentation does not claim a specific Lighthouse or PageSpeed score for the theme.**

Scores are measured on a finished store, not a theme, and depend on your images, your apps, your
scripts, your content and the testing conditions. A theme that scores well empty can score poorly
once loaded with a dozen apps — and that is not a fault in the theme.

What you can rely on is that the theme adds a small, page-scoped amount of CSS and JavaScript,
serves images responsively, and defers the expensive third-party things until they are needed.
The rest is what you put on top.

---

## A practical checklist

- [ ] No image over about 1MB
- [ ] Product images 2000–2400px, heroes 2400–3000px
- [ ] Photography saved as JPEG
- [ ] Every installed app is one you actually use
- [ ] Apps you removed left no code behind
- [ ] Tracking pixels installed via Customer events, not pasted into the theme
- [ ] Home page is six to eight sections
- [ ] Collection pages show 16–24 products
- [ ] No more than two or three slideshow slides
- [ ] Videos are short, and long ones are embeds rather than backgrounds
- [ ] Tested on the live site with PageSpeed Insights, mobile tab
- [ ] Tested on a real phone on mobile data
