# Images and media

Your images do more for the look of your store than any theme setting. This guide covers what to
upload and how to prepare it.

**Everything below is a recommendation, not a requirement.** The theme accepts any image Shopify
accepts. These are the sizes and ratios that produce the best result.

---

## How the theme handles images

Two things happen automatically, and they change what you need to do:

**1. Images are served responsively.** For every image, the browser is offered a range of sizes
and downloads the one that fits the screen — from around 160px for a small card up to 1100px or
more for a full-width banner. A phone never downloads a desktop-sized file.

**2. Images below the first screen load lazily.** They are fetched as the shopper scrolls, so a
long page does not download everything at once.

**What this means for you:** upload **one good, large image** per slot. Do not prepare multiple
sizes, and do not shrink images to "help performance" — an oversized source is far better than an
undersized one, because the theme can scale down but cannot invent detail.

---

## Recommended image sizes

| Where | Recommended width | Ratio | Notes |
| --- | --- | --- | --- |
| **Product images** | 2000–2400px | Square, or consistent across the catalogue | The most important images in your store. |
| **Slideshow / hero** | 2400–3000px | Landscape (16:9 or wider) | Full width on large screens. |
| **Slideshow / banner mobile image** | 1200–1500px | Portrait or square | Optional, but see [Mobile images](#mobile-images). |
| **Collection images** | 1200–1600px | Matches the ratio you choose for cards | Used in collection banners and cards. |
| **Image with text** | 1200–1600px | Landscape or square | |
| **Before / after images** | 1200–1600px | Identical for both | They must be the same dimensions or the halves will not line up. |
| **Multicolumn images** | 800–1200px | Matches the section's ratio | |
| **Logo** | Twice its display width | Any | 260–640px for a 130–320px display width. |
| **Logo list logos** | 400–600px | Any | Transparent PNG or SVG. |
| **Favicon** | 512 × 512px | Square | Scaled down to 32 × 32px. |
| **Social sharing image** | 1200 × 628px | ~1.91:1 | Theme settings → SEO and sharing. |
| **Video cover image** | Matches the video's ratio | 16:9 usually | |

**File size:** aim for under 500KB per image, and under 1MB for a full-width hero. Shopify
optimizes and re-encodes uploads, but it cannot fix a 12MB source efficiently.

**Format:**

| Format | Use for |
| --- | --- |
| **JPEG** | Photography — products, heroes, lifestyle shots |
| **PNG** | Anything needing transparency — logos, badges |
| **SVG** | Logos and icons, where you have a vector |
| **WebP** | Supported; Shopify converts and serves modern formats automatically, so you do not need to upload WebP yourself |

---

## Product image consistency

This matters more than any single image being perfect.

- **Same background** across the catalogue — white, off-white or one consistent color
- **Same framing** — the product occupying a similar proportion of the frame in every shot
- **Same lighting** and color temperature
- **Same orientation** — pick portrait or square and use it throughout

A grid of consistent images looks professional even when the photography is ordinary. A grid of
inconsistent images looks amateur even when each photo is good.

### Image ratio and the Adapt setting

**Theme settings → Product cards → Image ratio** offers Adapt, Square, Portrait and Landscape.

**Adapt** uses each image's own proportions. It is the right choice **only** when your images
already share a ratio — otherwise rows will be visibly uneven. If in doubt, choose **Square**;
the theme crops to fit and the grid stays tidy.

### Order your product media deliberately

- **Image 1** is the featured image: the card image, the first gallery image, and the image used
  in search results and recommendations.
- **Image 2** is the hover image on product cards. Make it a deliberate choice — a back view, a
  detail, or the product in use.
- **Assign images to variants** so the gallery jumps to the right one when a shopper switches.

### Alt text

Every product image should have alt text describing what it shows. Set it in Shopify admin by
clicking an image and choosing **Add alt text**.

Alt text is read aloud by screen readers and used by search engines. Describe the image
("Navy merino crew neck sweater, front view"), do not stuff keywords, and do not start with
"Image of".

---

## Hero image preparation

Hero images — slideshow slides and image banners — carry the most weight and are the easiest to
get wrong.

**1. Leave room for text.** Compose with empty space where your heading will sit. The
**Content position** setting offers nine positions; pick one and shoot for it, rather than
hoping text will land somewhere clear.

**2. Set the focal point.** In Shopify admin, click an image and choose **Edit → Set focal
point**. This tells the theme what to keep in frame when the image crops for different screen
sizes. It is the single highest-value thing you can do to a hero image, and it takes five
seconds.

**3. Use the overlay.** **Overlay opacity** darkens the image so text stays readable. Busy
photography needs 40–60%; clean photography may need 20% or none. Check on a phone — text that
reads fine at desktop size often does not at phone size.

**4. Choose the overlay color scheme deliberately.** It sets the text color over the image and
the tint of the overlay. A dark-background scheme gives light text.

---

## Mobile images

Slideshow slides and image banners accept a separate **Mobile image**, used below 750px.

Use one when a wide desktop hero would lose its subject on a narrow screen — a landscape shot of
a model, cropped to a phone, often cuts the product out entirely.

If your hero is a simple product on a plain background, the focal point alone is usually enough
and you can skip the mobile image.

Elsewhere in the theme, the same image is used at every size and simply scales — which is
correct, and means less work.

---

## Video

The theme supports video in the **Video** section and in **product media**.

| Source | Notes |
| --- | --- |
| **Shopify-hosted video** | Uploaded to Shopify. Takes priority over a URL, and is the only option that can play as a background video. Best performance and no third-party scripts. |
| **YouTube or Vimeo URL** | Used only when no Shopify-hosted video is set. The player and its scripts load only after a visitor presses play — so an unplayed embed costs nothing. |

### Recommendations

- **Keep it short.** 15–45 seconds for a product or brand video. Attention drops sharply after
  that.
- **Assume no sound.** Most autoplaying video is muted, and background video always is. If the
  message needs words, put them on screen.
- **Upload at 1080p.** 4K is a large file for a benefit almost nobody will see on a storefront.
- **Set a cover image** so the section looks intentional before playback. Shopify-hosted videos
  fall back to their own preview frame if you do not.
- **Write a description.** The Video section's **Description** field is read by screen readers and
  used as the cover image's alt text.
- **Background video** needs a Shopify-hosted video, plays muted and looping with no controls, and
  stays paused for visitors who prefer reduced motion.

### Product video

Add video to a product's **Media** in Shopify admin and it appears in the gallery alongside the
images, with the same thumbnail navigation. **Loop videos** on the product section controls
whether it repeats.

Use it where motion genuinely helps — fabric drape, a mechanism, a product in use.

---

## Practical checklist

Before you publish:

- [ ] Every product has at least two images
- [ ] Product images share a background, framing and ratio
- [ ] Every product image has alt text
- [ ] Variant images are assigned to their variants
- [ ] Hero images have a focal point set
- [ ] Hero text is readable on a phone — overlay adjusted if not
- [ ] Every collection used in a Collections section has a collection image
- [ ] No single image is over about 1MB
- [ ] The logo is sharp on a high-resolution screen
- [ ] A favicon is set
- [ ] A social sharing image is set under Theme settings → SEO and sharing

See [Performance](performance.md) for how image weight affects page speed.
