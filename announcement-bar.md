# Announcement bar

A slim strip above the header for short, high-value messages: delivery thresholds, returns
policy, a sale that is genuinely running.

**Where to find it:** Theme Editor → **Announcement bar**, above the Header in the left sidebar.
It appears on every page of the store.

---

## Creating announcements

Each message is a **block**. Click **Add block → Announcement**. You can have up to **six**.

| Setting | What it does |
| --- | --- |
| **Text** | The message. Plain text — keep it to one short line. |
| **Link** | Makes the whole announcement clickable. Optional. |
| **Icon** | A small icon before the text: None, Truck, Star, Success, Info or Pin. |
| **Let customers close this announcement** | Shows a close button on this specific announcement. Only appears when the section's **Customers can close** setting is "The announcement they are reading". |
| **Color scheme** | The colors for this announcement. Each announcement carries its own, so a sale message can be a different color from a delivery message. |

To remove an announcement, select the block and click **Remove block**. To reorder, drag the
blocks in the sidebar.

---

## Section settings

### Display

| Setting | Options | What it does |
| --- | --- | --- |
| **Display** | Show all at once, Rotate | **Rotate** cycles through the announcements one at a time. **Show all at once** displays them side by side. Rotating needs more than one announcement. |
| **Change every** | 3–12 seconds | How long each announcement stays before the next one. Rotate mode only. |
| **Alignment** | Left, Center, Right | Where the text sits in the bar. |

**Recommended:** Rotate with two or three announcements at six seconds. Showing four messages at
once is unreadable on anything narrower than a laptop.

### Dismissal

| Setting | Options | What it does |
| --- | --- | --- |
| **Customers can close** | Nothing — no close button; The announcement they are reading; The whole announcement bar | Decides whether a close button appears and what it hides. |
| **Remember the choice** | Not at all; Until the browser closes; For a set number of days; Forever | How long a dismissal lasts. |
| **Days before it returns** | 1–90 days | Only shown when "For a set number of days" is selected. |

Notes on dismissal behavior:

- **Not at all** means the bar reappears on the next page view — the close button is essentially
  cosmetic. Rarely what you want.
- **Until the browser closes** is a reasonable default for a persistent message.
- **For a set number of days** suits an evergreen message like a delivery threshold.
- Customers whose browser blocks local storage always see the bar again on the next page. This is
  not something the theme can work around.
- **Rewording an announcement shows it again** to customers who closed the old version. Editing
  the text is how you re-surface a message.

### Visibility

| Setting | Default |
| --- | --- |
| **Show on desktop** | On |
| **Show on mobile** | On |

Turning off mobile is worth considering if your bar carries a long message — on a narrow screen
it can take two lines and push the header down. A shorter message is usually the better fix.

### Appearance

| Setting | Notes |
| --- | --- |
| **Top padding** / **Bottom padding** | 0–40px each. Default 8px. Keep the bar slim. |

There is no section-level color scheme — **each announcement carries its own**, set on the
block.

---

## Mobile behavior

The bar is full width and the text wraps if it has to. Rotation and dismissal work exactly as
they do on desktop. If you find the bar taking too much vertical space on a phone, shorten the
message or turn **Show on mobile** off.

---

## Recommended usage

**Good announcements:**

- `Free delivery on orders over $75` — a fact, backed by an actual shipping rate
- `30-day returns on every order` — a policy you honour
- `Summer sale — up to 40% off` — while the sale is running

**Announcements to avoid:**

- Anything with a deadline you will not enforce. If the bar says the sale ends Sunday, end it
  Sunday. Use the [Countdown section](homepage.md#countdown) if you want a visible timer, and set
  a real end date.
- Stock claims the bar cannot verify — "Only 3 left!" in a global banner is not true for every
  product a shopper is looking at.
- More than three messages. Shoppers stop reading the bar entirely once it feels like noise.

**Keep the bar honest.** Announcements are the first thing a shopper reads and the easiest thing
to make untrue. If the message and the store disagree, the message loses.

---

## Troubleshooting

**Announcements do not rotate.** Rotation needs more than one announcement block, and **Display**
must be set to Rotate.

**The close button does not appear.** Check both: the section's **Customers can close** must not
be "Nothing", and — if it is set to "The announcement they are reading" — the individual block's
**Let customers close this announcement** must be on.

**The bar keeps coming back after closing it.** Either **Remember the choice** is set to "Not at
all", or the browser is blocking local storage (common in private browsing modes and with some
privacy extensions).

**The bar disappeared.** Someone closed it and the dismissal is being remembered. Clear your
browser's site data for the store, or open a private window, to see it again.

**A closed announcement reappeared.** The text was edited. That is intended — a reworded message
is treated as a new one.
