# Penvar

One page static site. No build step, no JavaScript, no tracking, no cookies.

```
index.html          the whole page
styles.css          all styling, design tokens at the top as CSS custom properties
favicon.svg         wordmark initial, ink on transparent
favicon-square.svg  alternative: paper initial on an ink square (avatars, dark tabs)
.nojekyll           tells GitHub Pages to serve the files as they are
```

## Run it locally

Open `index.html` in a browser, or:

```sh
python3 -m http.server 8000
```

## Deploy on GitHub Pages

1. Create a repository and push these files to the root of `main`.
2. Repository Settings, Pages, Source: **Deploy from a branch**, branch `main`, folder `/ (root)`.
3. The site publishes at `https://<user>.github.io/<repo>/`.

### Custom domain (penvar.com)

1. Settings, Pages, Custom domain: enter `penvar.com`, save. GitHub writes a `CNAME` file.
2. At the DNS registrar, point the apex domain at GitHub Pages with four A records:
   `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   (and `www` as a CNAME to `<user>.github.io` if you want the www form).
3. Wait for the DNS check to pass, then tick **Enforce HTTPS**.

## Before it goes live

- [ ] Replace `[Company number to follow.]` in the footer with the real Companies House number.
- [ ] Confirm `craig@penvar.com` is receiving mail.
- [ ] Optional: self-host the two fonts to remove the request to Google Fonts. Download Source Serif 4 and Public Sans, add `@font-face` rules at the top of `styles.css`, and delete the three `fonts.googleapis.com` / `fonts.gstatic.com` links from `index.html`. The fallbacks (Georgia, Helvetica) already hold the layout if the webfonts never load.

## Identity

Wordmark only: **Penvar** set in Source Serif 4 Semibold, mixed case, tight default tracking. There is no logo mark. Where a square icon is needed, the initial is used (`favicon-square.svg`).

Ink is the only brand colour. The page has no gradients, shadows, rounded cards, or images by design. The single flat rule under the opening statement, a short thick block running into a hairline, is the one abstract element: a headland and a long sightline. It is decorative and marked `aria-hidden`.

### Tokens (`styles.css`, `:root`)

| Token | Value | Use |
| --- | --- | --- |
| `--ink` | `#16232E` | wordmark, headings, rules, footer ground |
| `--paper` | `#F6F5F2` | page ground, type on ink |
| `--body` | `#22303C` | body copy |
| `--label` | `#5F6A74` | section labels, descriptor |
| `--rule` | `#DEDBD4` | hairlines between sections |
| `--number` | `#9AA1A8` | section numerals |

Type: Source Serif 4 (600) for the wordmark, opening statement, and email address. Public Sans (400/500/600) for body copy, labels, and legal text. Body copy is fluid, `clamp(17px,1.5vw,19px)`, line-height 1.72, measure capped at 66 characters. Section labels are 10.5px, uppercase, 0.16em tracking.

Layout: 1040px maximum width, fluid side padding `clamp(22px,5vw,56px)`. Each section is a two column grid, a 200px label column and the text column, collapsing to one column under 760px.

## Copy rules

Kept deliberately plain, and worth keeping that way in any future edit:

- British English. Short sentences. No em dashes.
- No superlatives and none of: unlock, empower, supercharge, transform, journey, cutting-edge.
- Nothing invented. No testimonials, client logos, statistics, or case studies. If a fact is not confirmed, leave it as a bracketed placeholder like the company number.
- The page is a credibility anchor, not a funnel: no newsletter capture, no chat widget, no calendar embed, no pricing.

## Accessibility

Ink on paper is roughly 13:1. The lightest text, `--label` on paper, is about 5:1. Headings run h1 then h2 in order, the decorative rule is hidden from assistive tech, focus styles are visible, and `prefers-reduced-motion` disables smooth scrolling. Keep contrast above 4.5:1 if the palette is ever adjusted.

## Design source

The design lives as a Design Component alongside this folder: `Penvar Website v2.dc.html`. These files are the production translation of it, hand written rather than exported. Logo exploration and specimens, including the one colour and reversed versions, are in `Penvar Logo Directions.dc.html` (direction 1a is the chosen one).
