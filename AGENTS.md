# Project context for assistants (humans & AI)

Use this document when editing or improving the repository so changes stay aligned with the real business and hosting setup.

## What this is

- **Public website** for **Willawan Thaimassage** (massage salon in Sköndal, Stockholm area).
- **Single-page marketing site**: services, about, photo gallery, team intro, contact, and links to **online booking** (Bokadirekt).
- **Language**: All user-facing copy is **Swedish** (`lang="sv"` on `<html>`). Prefer keeping tone professional, warm, and consistent with existing sections.

## Hosting and domain

- Deployed as **GitHub Pages** from this repo (`username.github.io` pattern).
- **Custom domain** is configured via `CNAME`: `www.willawanthaimassage.se` (do not remove or rename casually; DNS/GitHub Pages depends on it).
- Site is served from the **repository root** (no Jekyll/Hugo subfolder; `index.html` at root is the homepage).

## Tech stack (intentionally simple)

- **Static files only**: `index.html` + `style.css` + assets. No build step, no bundler, no framework unless the maintainer explicitly chooses to add one.
- **Fonts**: Google Fonts — `Poppins` (see `<link>` in `index.html`).
- **Local preview**: `npm install` then `npm start` (serves the repo root, typically on port 3000).

## File layout

| Path | Role |
|------|------|
| `index.html` | Full page structure, sections, nav anchors (`#home`, `#services`, …). |
| `style.css` | All layout and visual design (greens/gold spa-like palette, hero, cards, gallery). |
| `favicon.ico` | Site icon. |
| `CNAME` | Custom hostname for GitHub Pages. |
| `images/gallery/` | Salon and treatment photos referenced in the gallery grid. |
| `images/personal/` | Team/personal images (e.g. founder photo). |
| `images/README.md` | Notes for image assets (if present). |

Gallery filenames in HTML include e.g. `rum1.jpeg`, `vantrum.jpg`, `reception.jpg`, `jobb1.jpg`, `jobb3.jpg`, `jobb5.jpg`. If images are missing locally, `onerror` handlers show placeholder SVGs.

## External integrations

- **Booking**: Primary CTA URLs use Bokadirekt:  
  `https://www.bokadirekt.se/places/willawan-thaimassage-56244`  
  Keep booking links consistent when adding buttons or duplicate CTAs.

## Factual content (verify with owner before changing)

- **Address**: Bagarfruvägen 26, 128 67 Sköndal  
- **Phone** (as shown on site): 076-0505 88 90  
- **Services/prices** and **opening hours** are business data in `index.html`; update only when the business confirms changes.

## Design and UX expectations

- **Brand feel**: Calm spa/wellness, greens and warm accents (`#2d5016`, `#4a7c59`, `#f4e4bc`-style highlights in CSS).
- **Navigation**: Fixed header; in-page anchor links. Any new section should get matching nav + footer links and an `id` for anchors.
- **Responsive behavior** is handled in `style.css`; new components should match existing breakpoints and spacing patterns.
- **Accessibility**: Favor semantic HTML, meaningful `alt` on images, visible focus states, sufficient contrast. External links to booking should use `target="_blank"` with `rel="noopener noreferrer"` where appropriate.

## Quality and maintenance hints

- Run an **HTML validator** on `index.html` when doing larger edits; the contact block has historically had **markup issues** (e.g. unclosed `<p>` / `</div>` around the phone line) — fix structural bugs when touching nearby code.
- **Copyright year** in the footer may need periodic updates.
- Watch for **typos in asset paths** (e.g. accidental trailing spaces in `src` URLs) — they break images silently except for placeholders.
- Avoid committing secrets; there should be none in a static public site.

## What “good improvements” look like

- Faster loads (font loading strategy, image sizing, lazy loading where safe).
- Clearer mobile navigation if the nav overflows on small screens.
- SEO/meta (Open Graph, canonical URL) without misrepresenting the business.
- Small HTML/CSS fixes over large rewrites unless requested.

When in doubt, preserve the **static, root-hosted GitHub Pages** model and **Swedish** copy unless the project owner asks otherwise.
