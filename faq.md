# Frequently asked questions

Why does the header show my store name as text instead of a logo?

No logo has been uploaded yet. Until one is set, the header falls back to the store name rendered
as a wordmark, and the same fallback applies on the password page and the gift card page. Upload a
transparent PNG or SVG under Theme settings, then Logo. A file around 640 pixels wide is plenty at
the default logo width.

Why is my mega menu not appearing?

The mega menu is driven by the shape of the menu itself rather than by a setting. A menu item needs
children and grandchildren, three levels in total, before the full width panel appears. Two levels
produce a dropdown, and a flat menu produces plain links. Build the nesting in the Shopify admin
under Navigation, then reload the storefront.

Why are there no filters on my collection pages?

Storefront filters are configured in the Shopify admin, not in the theme. Install the free Shopify
Search and Discovery app and define the filters you want, including availability, price, product
type, vendor and your own product options. Until you do, the collection page shows sorting on its
own and gives the full width to the product grid. That is intended, not a fault.

Why do color swatches appear on some product cards and not others?

An option becomes swatches only when **every one of its values** resolves to a color. The theme
tries your swatch value first, then the value name read as a color name, then a built-in list of
retail color words. If a single value cannot be resolved — a SKU code, or something like
`Black/White` — the whole option falls back to a dropdown rather than showing a row of blank
circles. Setting a swatch value on that one variant is usually all it takes.

Swatch data is no longer required: an option named Color holding ordinary color names shows
swatches with no setup at all. Set swatch values under Settings, then Products, or with the
taxonomy color attribute when you need your exact colors, or artwork for a print or pattern. An
option carrying swatch data on every value shows as swatches whatever it is named; without it, the
option has to be named as a color for the theme to read it as one.

Where is the size chart button on my product pages?

It appears only when a page has been selected on the variant picker block and that page has content
in it. Open the product template in the Theme Editor, select the variant picker block, choose your
size guide page, and confirm the page is not empty. An empty page renders no button at all. The
button takes its label from the page title, so name the page well.

Why does my homepage show gray placeholder images after I install the theme?

A newly installed theme has none of your images or products to display, so it draws placeholders in
their place. Open the Theme Editor and set your own images on the slideshow and on the image with
text section, then choose a collection for the featured collection and a set of collections for the
category list. Each placeholder disappears as soon as real content is selected behind it.

How do I get back to the original design after changing a lot of settings?

The theme ships a style named Kestrin that holds the settings it was released with. Selecting that
style in the Theme Editor restores the original colors, typography, spacing and layout in one step.
Your products, pages, menus and images are untouched, because a style covers theme settings only.

Does Kestrin need any apps to work?

No. Every feature described in this documentation is built into the theme. The Shopify Search and
Discovery app is worth installing if you want storefront filters, because filtering is a Shopify
platform feature rather than a theme feature, but nothing in the theme breaks without it.

Will I lose my settings when the theme updates?

Updating means installing a fresh copy of the theme, and a fresh copy arrives with default
settings. Your products, pages, blog posts and menus live in your store and are never affected.
Theme settings and section arrangement do not carry across on their own, so install the new version
as an unpublished theme, set it up to match, check it, and publish only when you are satisfied. The
updating page walks through the full procedure.

Why is my countdown section invisible on the storefront?

The end date has to be a real date given as year, month and day. If it is missing or malformed the
section renders nothing at all on the live storefront, and shows a warning only inside the Theme
Editor, which is why it can look fine while you are editing and absent to customers. Open the
section and set the date again.

Why does my cart open as a panel rather than its own page?

The cart type is set to drawer by default. Change it under Theme settings, then Cart, if you would
rather send customers to a full cart page instead.

Why do my product cards not swap to a second image on hover?

The card swaps to the second image of the product, so a product with only one image has nothing to
swap to. Add at least two images to any product where you want the effect. The setting itself lives
under Theme settings, then Product cards.

Can I use one license on more than one store?

A license covers a single store. A second store needs a second license. Development stores and
unpublished copies inside the same store are fine, since neither is a separate live storefront.

My question is not here.

Work through [Troubleshooting](troubleshooting.md) first, which covers the most common problems by
symptom, then get in touch through [Support](support.md).
