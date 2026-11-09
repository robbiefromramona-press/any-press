# Any-Press website

The marketing site for **Any-Press** (any-press.com) — website design and
digital marketing for small businesses in Ramona and San Diego County.

It is a plain static site. No frameworks, no npm, no build step. If you can
open a text file, you can edit this site.

## The files

| File | What it is |
| --- | --- |
| `index.html` | The whole home page: hero, services, pricing, how it works, contact form. |
| `thanks.html` | The page people land on after sending the contact form. |
| `legal.html` | Terms of Service, Privacy Policy and Disclaimer, all on one page. |
| `style.css` | Every style for all three pages. |
| `favicon.svg` | The little AP logo in the browser tab. |
| `netlify.toml` | Tells Netlify there is no build step and the site is at the repo root. |

## How to change the prices

Open `index.html` and search for `EDIT PRICES HERE`. Each plan is one block
that looks like this:

```html
<article class="price-card">
  <p class="plan-name">Fresh Coat</p>
  <p class="plan-price"><small>one-time</small><strong>$800–1,500</strong></p>
  <p class="plan-desc">A new site for a business that needs one that actually works on a phone.</p>
  <ul>
    <li><span>✓</span>New 3–5 page website</li>
    ...
  </ul>
</article>
```

- **Plan name** — the text inside `<p class="plan-name">`.
- **Price** — the text inside `<strong>`. The `<small>` bits either side are
  the little grey labels ("one-time", "from", "/ month").
- **The five ticks** — each `<li>` line is one bullet. Keep the
  `<span>✓</span>` at the start; that is the orange tick.

The card marked `price-card featured` is the middle one with the orange
MOST POPULAR ribbon. To move the ribbon to a different plan, move both the
word `featured` and the `<div class="price-ribbon">` line.

The orange banner above the cards is the line starting
`<p class="price-banner">`. Change that text when the founding-client offer
ends, or delete the whole line to remove the banner.

## How to change the contact details

Open `index.html` and search for `EDIT CONTACT INFO HERE`. The email address
appears three times on the page (the big link, the form backup line, and the
`"email"` line in the schema block up in the `<head>`) and the phone number
appears twice. Search and replace is the safe way to catch all of them.

The phone number in the `<head>` schema block is written as
`+1-760-907-1099`. That format is for Google, not for people — keep the
dashes if you change it.

Both also appear in `legal.html` and `thanks.html`.

## The contact form

The form uses **Netlify Forms**. There is no server and no code to maintain.

- Submissions appear in the Netlify dashboard under **Forms → contact**.
- To get them emailed to you: Netlify → Forms → contact → Settings → Form
  notifications → Add notification → Email notification.
- A hidden `bot-field` catches most spam bots automatically.
- After sending, people are redirected to `thanks.html`.

The form only works on the live Netlify site. On your own machine the Send
button will not do anything useful — that is normal.

## Seeing the site on your own machine

The site is just files, so you can double-click `index.html` to open it in a
browser. For a closer match to the real thing, serve it on a local address:

```bash
python -m http.server 8808 --directory C:/Users/robbi/GitHub/Repos/any-press
```

Then open http://localhost:8808 in your browser. Press Ctrl+C in the terminal
to stop it.

If you edit a file and the browser does not seem to change, hold Shift and
click reload. The browser caches the stylesheet hard.

## Still to do

- **Share image.** There is no `og-image.png` yet, so links shared on
  Facebook, LinkedIn or in a text message show the title and description but
  no picture. Once you have a 1200×630 image, save it here as `og-image.png`
  and follow the TODO comment near the top of `index.html` to switch the two
  tags on.
- **Legal page placeholders.** `legal.html` is generic small-business text,
  not custom legal advice, following the same pattern as the BIM-Press legal
  pages. It names **Any-Press LLC** and leaves `[State]` to fill in. Both
  need a look once the company paperwork is settled.

## Where the design came from

The look, layout and wording started as a ChatGPT-built page at
`any-press.silkykitten4.chatgpt.site`. That page was a Next.js app shipping a
136 KB Tailwind stylesheet. It was rebuilt here as plain HTML and CSS: the
framework scripts are gone, the mobile menu works without JavaScript, and the
unused 102 KB of Tailwind utilities were dropped. The design itself is
unchanged apart from the fixes recorded in the git history.
