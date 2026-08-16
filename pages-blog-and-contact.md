# Pages, blog and contact

Everything in your store that is not a product, collection or cart. Each of these is a template
you customize in the Theme Editor, filled with content you create in Shopify admin.

---

## Standard pages

For About, Shipping, FAQ, Size guide, Terms — anything that is simply content.

### Creating a page

**Shopify admin → Content → Pages → Add page**

Give it a title and write the content in the rich text editor. Under **Search engine listing**,
set the page title and meta description — see [SEO](seo.md).

Pages are reachable at `/pages/your-page-handle`. Link to them from your menus.

### The Page template

**Theme Editor → template dropdown → Page**

| Setting | Options | Notes |
| --- | --- | --- |
| **Content width** | Reading, Narrow, Full | **Reading** keeps lines short enough to scan comfortably — the right choice for text-heavy pages. **Full** uses the theme's standard page width, not the full width of the screen. |
| **Show breadcrumbs** | On / off | On by default. |
| **Show the page title** | On / off | When off, the title is still there for screen readers and search engines but hidden from view. Useful when you have built your own heading with sections below. |
| **Heading size** | h2, h1, h0 | Only shown when the title is displayed. |
| **Heading alignment** | Left, Center | |
| **Color scheme**, padding | | Standard section settings. |

The Page template also accepts **app blocks**.

### Adding sections to a page

You can add any home page section beneath your page content — an image banner, a multicolumn
block of features, a contact form, an FAQ accordion. Click **Add section** on the Page template.

To give one page a different layout, create a **template variant**: in the template dropdown
choose **Create template**, base it on `page`, name it, customize it, then assign it to the page
from the page's **Theme template** field in Shopify admin.

---

## Contact page

The theme ships a ready-made contact template.

### Setting it up

1. In **Shopify admin → Content → Pages**, create a page called `Contact`.
2. In its **Theme template** field, select **contact**.
3. Customize it in **Theme Editor → template dropdown → Contact**.

Messages sent through the form arrive at the email address set under
**Shopify admin → Settings → General → Store contact email**.

### Contact form settings

| Setting | Options | Notes |
| --- | --- | --- |
| **Layout** | Split, Stacked | **Split** puts your content blocks beside the form. It needs at least one content block — without one the form is always stacked. |
| **Content side** | Left, Right | Split layout only. |
| **Use a narrower page width** | On / off | |
| **Show a phone number field** | On / off | On by default. |
| **Show an order number field** | On / off | An optional text field so shoppers can quote an order they have already placed. Off by default. |
| **Order number field label** | Text | Also used as the field name in the email you receive, so keep it short. The field stays hidden while this is empty. |
| **Button label** | Text | Leave blank for "Send message". |

The form always collects a name, an email address and a message. Email format is validated before
sending, and a confirmation message is shown after a successful send.

### Contact page blocks

| Block | Limit | Contents |
| --- | --- | --- |
| **Heading** | 1 | Subheading, heading, heading size. |
| **Text** | 2 | Rich text. |
| **Details** | 1 | Up to three rows, each with an icon (Mail, Phone, Pin, Truck, Info), a label, a value and an optional link. Use for email, phone and address. |
| **Map** | 1 | See below. |
| **Social** | 1 | Places your social icons on the page. The icons come from Theme settings → Social media; this block only decides where they sit. |
| **App blocks** | — | Any contact-related app block. |

### The map block

| Setting | Notes |
| --- | --- |
| **Heading** | Optional. |
| **Map embed URL** | In Google Maps choose **Share → Embed a map**, and paste only the address inside `src=""`. The block stays hidden until this is filled in. |
| **Button label** | Default "View map". |
| **Image** | Shown in place of the map until a visitor taps the button. A generic placeholder is used while this is empty. |
| **Image ratio** | Square, Landscape, Wide. |

**The map is only fetched once a visitor taps the button**, so it costs nothing on page load —
which matters, because embedded maps are among the heaviest third-party elements a page can carry.

---

## Blog

### Creating blog content

**Shopify admin → Content → Blog posts**

Shopify stores can have several blogs (for example "News" and "Guides"). Each post belongs to
one. For each post, set:

- **Title** and content
- A **featured image** — used on blog cards and at the top of the article
- An **excerpt** — used on cards. Without one, Shopify uses the opening of the post.
- **Tags** — used by the tag filter and to pick related articles
- **Author** and **visibility** (publish now or schedule)

Comments are configured per blog in Shopify admin, under the blog's settings. The theme renders
them when they are turned on.

### Blog listing page

**Theme Editor → template dropdown → Blog posts**

| Setting | Options | Notes |
| --- | --- | --- |
| **Blog description** | Rich text | Shown under the blog title. It is stored in the theme, not with the blog in Shopify admin — so it is the same for every blog using this template. |
| **Heading alignment** | Left, Center | |
| **Show tag filter** | On / off | Lists every tag used in this blog. Nothing appears until at least one article is tagged. |
| **Posts per page** | 3–24 | Default 9. |
| **Columns on desktop** | 1–4 | Default 3. |
| **Image ratio** | Adapt, Square, Portrait, Landscape, Wide | |
| **Show featured image**, **Show date**, **Show author**, **Show excerpt**, **Show tags on cards**, **Show comment count** | On / off | Card content. Comment count needs comments enabled for the blog in Shopify admin. |
| **Show breadcrumbs** | On / off | |

### Article page

**Theme Editor → template dropdown → Blog post**

Section settings:

| Setting | Options | Notes |
| --- | --- | --- |
| **Content width** | Reading, Narrow | Applies to the article text and everything around it. The featured image has its own width setting. |
| **Show breadcrumbs** | On / off | |
| **Show previous and next links** | On / off | Links to the articles either side of this one. Only one link appears on the first and last article. |
| **Show related articles** | On / off | Picks articles from the same blog sharing this article's first tag. Untagged articles fall back to the most recent posts. |
| **Related articles to show** | 2–6 | Default 3. |

Article blocks, each usable once, reorderable:

| Block | Settings |
| --- | --- |
| **Featured image** | Image width (Reading, Wide, Full) and image ratio (Adapt, Square, Landscape, Wide). |
| **Title** | Heading size (h2, h1, h0), alignment, and a link back to the blog. |
| **Meta** | Show date, author, reading time and comment count, plus alignment. Reading time is calculated from the article length. |
| **Content** | The article body. No settings — it renders what you wrote. |
| **Tags** | The article's tags, linking to filtered listings. |
| **Share** | A share button. Configurable label. |
| **App blocks** | Any article-related app block. |

A sensible order: Featured image, Title, Meta, Content, Tags, Share.

---

## Search page

Covered separately in [Search](search.md).

---

## 404 page

Shown when someone reaches a URL that does not exist — a mistyped address, an old link, a deleted
product.

**Theme Editor → template dropdown → 404 page**

| Setting | Notes |
| --- | --- |
| **Heading** | Leave blank for "Page not found". |
| **Text** | Leave blank for the theme's default wording. |
| **Show a search box** | On by default. |
| **Collection** | Products from this collection appear below the message, giving shoppers somewhere to go. Nothing appears while it is empty. |
| **Products heading** | Leave blank to use the collection's own title. |
| **Products to show** (2–12), **Columns on desktop** (2–5), **Image ratio** | Grid settings, shown once a collection is chosen. |

**Recommended:** point the collection setting at your best sellers or new arrivals. A 404 with a
search box and a row of products recovers visits that would otherwise be lost.

---

## Password page

Shown while your store is password-protected (**Online Store → Preferences → Restrict access**).

**Theme Editor → template dropdown → Password page**

| Setting | Notes |
| --- | --- |
| **Show logo** | Uses the logo from Theme settings → Logo. Your store name is shown as text until one is uploaded. |
| **Heading** | Leave blank to use your store name. |
| **Text** | Only used when the password page message under **Online Store → Preferences** is empty. |
| **Background image**, **Overlay opacity** | Optional background. |
| **Show the sign-up form** | On by default. Sign-ups are saved as customers in your admin, tagged `newsletter`. |
| **Newsletter heading**, **Newsletter text** | Form copy. |
| **Show social icons** | From Theme settings → Social media. |

Useful before launch: collect email addresses from interested visitors while you finish setting
up.

---

## Customer accounts

Sign-in, registration, order history and the account menu are handled by **Shopify's own hosted
account experience**. The theme renders Shopify's account component in the header and styles it to
match your color scheme — it does not ship its own account pages or sign-in form.

**What this means for you:**

- Enable accounts under **Shopify admin → Settings → Customer accounts**. The account icon
  appears in the header once you do.
- The **Customer account menu** setting on the Header section chooses what appears in the panel
  after a shopper signs in. It defaults to Shopify's `customer-account-main-menu`.
- There are no theme settings for the account pages themselves, because Shopify owns them. They
  are configured in Shopify admin.
- Shopify keeps these pages up to date and accessible, and they inherit your store branding.

---

## Gift cards

When you sell a gift card, Shopify generates a gift card page for the recipient. The theme styles
it — no configuration is needed.

If you want shoppers to be able to send a gift card directly to someone else, enable **Let
shoppers send gift cards to someone else** on the product page's **Buy buttons** block. It adds
recipient name, email and message fields, and appears only on gift card products. See
[Product page](product-page.md).
