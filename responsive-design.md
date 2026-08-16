# Mobile and responsive design

The theme adapts to every screen size automatically. There is no separate mobile theme to
configure — the same content reflows, and a number of sections give you explicit control over how.

Most stores see more than half their traffic on phones. Treat the mobile view as the primary one.

---

## Where the layout changes

The theme uses three breakpoints:

| Width | Applies to |
| --- | --- |
| Below **750px** | Phones |
| **750px** and up | Large phones and tablets |
| **990px** and up | Laptops and desktops — full navigation, sidebars, hover effects |
| **1400px** and up | Large desktops — wider grids and spacing |

You do not set these. They are what "mobile", "tablet" and "desktop" mean in the rest of this
documentation.

---

## Mobile navigation

The header collapses to a menu button, your logo, and the action icons.

Tapping the menu button opens a full-height **drawer**. It shows one level at a time: tapping a
parent slides in a new panel of its children, with a **Back** button and a **View all** link.

Why one panel per level rather than expanding accordions: a shopper never has to scroll past
dozens of opened items to find the one they want, and the current level is always obvious.

**Mega menu promotions — image, heading, text, button — do not appear on mobile.** The links do.
If a promotion carries information shoppers need, put it somewhere else as well.

Full details in [Header and navigation](header-and-navigation.md).

---

## Mobile header

- The logo is automatically capped at **120px wide**, whatever your desktop logo width, so it
  never crowds the icons.
- Your chosen header layout (logo left, logo center) applies on desktop; mobile always uses the
  same compact arrangement.
- **Sticky** and **Reveal** scroll behaviors work on mobile. Reveal is particularly good here,
  since screen space is scarce.
- With **Search: Icon**, the icon opens the same full-screen search drawer as on desktop. With
  **Search: Field**, the field moves to its own full-width row below the logo — which is tidy, but
  does make the mobile header taller.

---

## Mobile announcement bar

Full width, with text wrapping if needed. Rotation and dismissal work as on desktop.

**Show on mobile** lets you hide the bar on phones. Consider it if your message is long — but a
shorter message is usually the better answer. See [Announcement bar](announcement-bar.md).

---

## Responsive grids

Sections that show a grid give you separate desktop and mobile column counts.

| Section | Desktop | Mobile |
| --- | --- | --- |
| Collection page | 2–5 | 1 or 2 |
| Featured collection | 2–5 | 1 or 2 |
| Search results | 2–5 | 1 or 2 |
| Collections list | 2–5 | 1 or 2 |
| Collections (home page section) | 2–5 | 1 or 2 |
| Multicolumn | 2–6 | 1 or 2 |
| Product recommendations | 2–6 | 1 or 2 |
| Blog listing | 1–4 | stacks |
| Testimonials | 2–4 | grid or carousel |

**Recommended:** two columns on mobile for products, one column for content-heavy sections like
Multicolumn and Testimonials.

### Carousels and scroll rows

Several sections offer a **Carousel** or **Scroll** mobile layout instead of a grid. This puts
items in a swipeable row rather than a tall stack:

- Featured collection, Collections — **Grid** or **Scroll**
- Multicolumn, Testimonials, Featured blog — **Grid/Stacked** or **Carousel**

Use a carousel when a section is a highlight the shopper can skim past. Use a grid when it is the
main content of the page and you want every item seen.

---

## Responsive images

You do not need to prepare separate mobile images. Every image in the theme is served
responsively: the browser downloads a size appropriate to the screen, so a phone never downloads
a desktop-sized file.

Where a different **crop** is genuinely needed, two sections accept a separate mobile image:

- **Slideshow** — each slide has a **Mobile image**
- **Image banner** — a **Mobile image** used below 750px

Use these when a wide hero would lose its subject on a narrow screen. A landscape hero cropped to
a phone often cuts out the product entirely.

The **focal point** set in Shopify's image editor decides what stays in frame when an image
crops. Setting it on your hero images is quicker than making mobile crops.

See [Images and media](images-and-media.md).

---

## Mobile product pages

- The gallery sits at the top. Choose **Carousel** (swipeable, compact) or **Stacked** (every
  image down the page) with **Mobile gallery layout**.
- All product blocks stack in one column, in the order you set.
- Buy buttons are full width and comfortably tappable.
- Image zoom opens full screen when enabled.
- Collapsible rows are especially valuable here — they keep the page short enough to reach the
  buy button.

**Recommended:** carousel gallery, and put the description in a collapsible row so shipping and
returns are reachable without a long scroll.

---

## Mobile collection pages

- Filters and sort collapse into a **drawer** behind a button, whichever desktop layout you chose.
  A sidebar is not workable on a phone.
- The product grid uses your mobile column setting.
- The collection banner stacks: image, then title and description.
- Pagination controls are sized for touch.

---

## Mobile cart

- The **drawer** takes nearly the full screen width and scrolls internally, with the checkout
  button always reachable.
- The **cart page** stacks each line vertically, with touch-sized quantity and remove controls.
- Recommendations become a swipeable row.

Test a real add-to-cart and a real checkout on a phone before publishing.

---

## Mobile footer

Every footer column becomes a **collapsible accordion row**, so the footer is a short list of
headings rather than a long scroll. The bottom bar stacks and centers.

This is automatic, and it is why a five-column footer does not become a problem on a phone.

---

## How to check your store on mobile

**1. Use the Theme Editor's device toggles as you build.** Fast, and catches most problems.

**2. Then use a real phone.** The Theme Editor preview cannot reproduce touch, real network
speed, or how a page feels held in one hand. Send yourself the preview link
(**Online Store → Themes → ⋯ → Share preview**) and open it on your own phone.

**3. Check both orientations.** Landscape on a phone is a genuinely different layout.

**4. Try a tablet if you can.** Tablets fall between the layouts and occasionally surprise you.

### What to check

- [ ] Header is not crowded; the logo is legible
- [ ] The menu drawer opens, every level is reachable, Back and View all work
- [ ] The announcement bar is one line, or acceptably two
- [ ] Hero text is readable over the image — raise the overlay opacity if not
- [ ] No section requires horizontal scrolling
- [ ] Product images fill the width without distortion
- [ ] Buttons are easy to tap without hitting neighbours
- [ ] Forms are usable and the right keyboard appears for email and number fields
- [ ] The product page reaches Add to cart without an unreasonable scroll
- [ ] Cart and checkout complete end to end
- [ ] Footer accordions open and close

---

## Common mobile problems and their fixes

| Problem | Usual cause | Fix |
| --- | --- | --- |
| Text unreadable over a hero image | Overlay too light for busy photography | Raise **Overlay opacity**, or use a calmer image |
| Hero looks wrong / subject cut off | A wide desktop image cropped to a narrow screen | Add a **Mobile image**, or set the image's focal point |
| A section feels endlessly tall | Too many items in a stacked grid | Switch **Mobile layout** to Carousel or Scroll, or reduce items |
| Product grid cramped | Two columns with long titles | Use one column, or shorten titles |
| Page scrolls sideways | Almost always custom code or an app | Disable recent custom code or apps one at a time |
| Header takes too much space | Sticky header plus a tall announcement bar | Use **Reveal** behavior, reduce header padding, or shorten the bar |
| Buttons hard to tap | Rarely the theme — usually an app's injected element | Test with the app disabled |

If the layout looks wrong on mobile and you have added custom code or installed an app recently,
that is the first thing to rule out. See [Troubleshooting](troubleshooting.md) and
[Third-party apps](third-party-apps.md).
