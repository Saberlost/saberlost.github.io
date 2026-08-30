# Project context for assistants (humans & AI)

Use this document when editing or improving the repository so changes stay aligned with the real business and hosting setup.

## What this is

- **Public website** for **Willawan Thaimassage** (massage salon in Sköndal, Stockholm area).
- **Single-page marketing site**: services, about, Nuad Thai Nordic membership, photo gallery, team intro, contact, and links to **online booking** (Bokadirekt).
- **Language**: All user-facing copy is **Swedish** (`lang="sv"` on `<html>`). Prefer keeping tone professional, warm, and consistent with existing sections.
- **Chat language**: Prefer answering the maintainer in **Swedish** unless they write in another language.

## Hosting and domain

- Deployed as **GitHub Pages** from this repo (`username.github.io` pattern).
- **Custom domain** is configured via `CNAME`: `www.willawanthaimassage.se` (do not remove or rename casually; DNS/GitHub Pages depends on it).
- Site is served from the **repository root** (no Jekyll/Hugo subfolder; `index.html` at root is the homepage).

## Tech stack (intentionally simple)

- **Static files only**: `index.html` + `style.css` + assets. No build step, no bundler, no framework unless the maintainer explicitly chooses to add one.
- **Fonts**: Google Fonts — `Poppins` and `Montserrat` (see `<link>` in `index.html`).
- **Local preview**: `npm install` then `npm start` (serves the repo root on port 3000 via `serve`).

## File layout

| Path | Role |
|------|------|
| `index.html` | Full page structure, sections, nav anchors. |
| `style.css` | All layout and visual design (greens/gold spa-like palette, hero, cards, gallery). |
| `favicon.ico` | Site icon. |
| `CNAME` | Custom hostname for GitHub Pages. |
| `package.json` | Dev-only local server (`serve`); not used in production. |
| `images/gallery/` | Salon and treatment photos for the gallery grid. |
| `images/personal/` | Team/personal images (e.g. founder photo). |
| `images/nuad-thai-nordic/` | Nuad Thai Nordic badge / membership imagery. |
| `images/README.md` | Notes for image assets (filenames there may be outdated vs HTML). |
| `AGENTS.md` | This file — project context for future assistants. |

### Page sections (keep nav + footer in sync)

| `id` | Section |
|------|---------|
| `#home` | Hero |
| `#services` | Tjänster / prices |
| `#about` | Om oss |
| `#nuad-thai` | Nuad Thai Nordic |
| `#gallery` | Bilder |
| `#personal` | Personligt / team |
| `#contact` | Kontakt, öppettider, booking CTA |

Gallery filenames in HTML include e.g. `rum1.jpeg`, `vantrum.jpg`, `reception.jpg`, `jobb1.jpg`, `jobb3.jpg`, `jobb5.jpg`. Personal photo: `images/personal/mindreProfil.png`. If images are missing locally, `onerror` handlers show placeholder SVGs.

## External integrations

- **Booking** (keep all CTAs consistent):  
  `https://www.bokadirekt.se/places/willawan-thaimassage-56244`
- **Nuad Thai Nordic**: membership copy + link to `https://www.nuadthai.se`  
  External links should use `target="_blank"` with `rel="noopener noreferrer"`.

## Factual content (verify with owner before changing)

- **Address**: Bagarfruvägen 26, 128 67 Sköndal
- **Phone** (as shown on site): 076-0505 88 90
- **Services/prices** and **opening hours** live in `index.html`; update only when the business confirms changes.
- Do not invent new services, prices, hours, or certifications.

## Design and UX expectations

- **Brand feel**: Calm spa/wellness, greens and warm accents (`#2d5016`, `#4a7c59`, `#f4e4bc`-style highlights in CSS).
- **Navigation**: Fixed header; in-page anchor links. Any new section needs matching nav + footer links and an `id`.
- **Responsive behavior** is in `style.css`; match existing breakpoints and spacing.
- **Accessibility**: Semantic HTML, meaningful `alt`, visible focus states, sufficient contrast.
- Preserve the established visual language; do not rewrite into a different design system unless asked.

## Quality and maintenance hints

- Validate `index.html` after larger edits. The contact phone block has historically had **broken markup** (unclosed `<p>` / missing `</div>`) — fix structural bugs when touching nearby code.
- Watch for **typos in asset paths** (e.g. trailing spaces in `src`) — they break images silently except for placeholders.
- **Copyright year** in the footer may need periodic updates.
- Prefer small HTML/CSS fixes over large rewrites unless requested.
- Avoid committing secrets; there should be none on a static public site.
- Do not commit unless the maintainer explicitly asks.

## What “good improvements” look like

- Faster loads (font loading, image sizing, lazy loading where safe).
- Clearer mobile navigation if the nav overflows on small screens.
- SEO/meta (Open Graph, canonical URL) without misrepresenting the business.
- Consistent `rel="noopener noreferrer"` on all external booking/membership links.
- Markup and accessibility fixes.

When in doubt, preserve the **static, root-hosted GitHub Pages** model and **Swedish** copy unless the project owner asks otherwise.
