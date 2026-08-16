# Accessibility

An accessible store is one that people can use with a keyboard, a screen reader, a magnifier, or
simply tired eyes. It is also, in many places, a legal requirement — and it overlaps almost
entirely with good usability.

The theme handles the structural side. Some of it depends on you.

---

## What is built into the theme

### Keyboard navigation

Everything interactive can be reached and operated with a keyboard alone.

| Key | Behavior |
| --- | --- |
| **Tab** / **Shift+Tab** | Move forwards and backwards through interactive elements |
| **Enter** / **Space** | Activate a link or button |
| **Arrow keys** | Move through predictive search suggestions, slideshow slides and menu panels |
| **Escape** | Close the open menu panel, drawer, modal or search panel |

Specific behaviors:

- A **Skip to content** link is the first thing keyboard users reach, letting them jump past the
  header on every page.
- **Drawers and modals trap focus** while open — Tab cycles within them rather than escaping to
  the page behind — and return focus to whatever opened them when closed.
- **Menu panels** close on Escape and return focus to the item that opened them.
- **Inactive mobile menu panels are made inert**, so a keyboard user cannot tab into a panel that
  is off screen.
- Background scrolling is locked while a drawer is open.

### Focus states

Every focusable element has a visible focus indicator. It uses your color scheme, so it stays
visible against your background.

**Do not remove focus outlines with custom CSS.** It is a common "tidying up" change and it makes
the store unusable by keyboard.

### Semantic markup

- One main heading per page, with subheadings nested correctly beneath it
- Real `<button>` and `<a>` elements — nothing that looks clickable but is not focusable
- Navigation, main content and footer marked as landmarks, so screen reader users can jump
  between them
- Lists marked up as lists

### Screen reader support

- Interactive controls have accessible names, including icon-only buttons like the cart, search
  and menu
- Open and closed states are announced for menus, accordions and drawers
- **Live announcements** for things that change without a page load: how many products a filter
  matched, how many search suggestions appeared, that an item was added to the cart
- The current page is marked in navigation menus
- Links that open a new window say so

### Forms

- Every field has a visible, associated label
- Required fields are marked
- Errors are announced and described in words, not color alone
- The correct keyboard appears on mobile for email and number fields
- Success messages are announced after submission

### Motion

Visitors whose device is set to **reduce motion** automatically get a calmer experience:
animations are suppressed, marquees stand still, slideshow autoplay never starts, and background
video stays paused. This happens regardless of your **Enable animations** setting — you do not
need to turn animations off for accessibility.

Slideshow autoplay always provides a pause button.

### Images

Alt text you set in Shopify admin is output on every image. Decorative images — such as the
second image on a product card hover — are correctly marked as decorative so screen readers skip
them rather than announcing the same product twice.

---

## What you control

These are the parts a theme cannot do for you.

### Color contrast — the most important one

**Theme settings → Colors**

Every color scheme needs enough contrast between text and background. The widely used target is
**4.5:1 for body text** and **3:1 for large text and interface elements**.

Check each of your schemes with a free contrast checker (search "WebAIM contrast checker"). Pay
particular attention to:

- Body text on your background color
- Button label on button background
- Accent color used for links, on the background
- Text over hero images — raise **Overlay opacity** if it fails
- Any scheme you designed to look "soft" or "subtle"

Low-contrast gray-on-white is the single most common accessibility failure on Shopify stores, and
the easiest to fix.

### Alt text

Write it for every meaningful image. Describe what the image shows, in a sentence:

- ✅ "Navy merino crew neck sweater, front view"
- ❌ "sweater navy merino wool jumper knitwear men"
- ❌ "IMG_4471.jpg"
- ❌ "Image of a sweater"

Purely decorative images should have empty alt text so screen readers skip them.

### Link and button text

Make it describe the destination.

- ✅ "Shop the winter collection"
- ❌ "Click here", "Read more", "Learn more"

Screen reader users often navigate by pulling up a list of links. A list of eight "Read more"
links tells them nothing.

### Heading structure

Use headings to describe structure, not to control size. If you want a smaller heading, use the
**Heading size** setting — that changes appearance without breaking the outline.

Do not skip levels, and do not use a heading purely because you want bold text.

### Content

- **Write plainly.** Short sentences, everyday words.
- **Do not rely on color alone.** "Items marked in red are on sale" excludes anyone who cannot
  distinguish the color. The theme's sale badges pair color with text for this reason.
- **Caption or transcribe video** if it carries information. The theme's Video **Description**
  field helps, but it is not a transcript.
- **Avoid ALL CAPS in body text.** It is harder to read and some screen readers spell it out.
  Use **Theme settings → Typography → Heading case** if you want capitalized headings — it
  handles letter-spacing properly.

### Menus

Keep them shallow and clearly named. A three-level menu with vague labels is hard for everyone
and disproportionately hard for anyone navigating by keyboard. See
[Navigation best practices](navigation.md).

### Apps

Apps inject their own markup, and the theme has no control over its accessibility. Popups,
review widgets and chat launchers are frequent offenders — trapping focus, missing labels, or
being impossible to dismiss with a keyboard.

Test any app you install with the keyboard. See [Third-party apps](third-party-apps.md).

---

## How to check your store

**Keyboard test.** Put your mouse away. Tab through your home page, a collection page, a product
page and the cart. You should be able to reach everything, always see where you are, open and
close the menu and cart, and complete a purchase.

**Zoom test.** Zoom your browser to 200%. Nothing should be cut off or overlap.

**Contrast test.** Run each of your color schemes through a contrast checker.

**Automated scan.** Free browser extensions such as axe DevTools or WAVE catch a useful
proportion of problems in seconds. They cannot catch everything — an image with meaningless alt
text passes an automated check.

**Screen reader test.** If you can, try VoiceOver (built into macOS and iOS) or NVDA (free, on
Windows). Even ten minutes is instructive.

---

## Honest scope

The theme is built to meet common accessibility standards in its own markup and behavior, and
Shopify's Theme Check passes without offenses. But **accessibility is a property of your finished
store, not of a theme**. Your colors, your content, your images and your apps all contribute.

If accessibility compliance is a legal requirement for your business, commission an audit of your
live store. No theme can certify a store it does not control the content of.
