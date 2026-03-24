# CLAUDE.md — EA at UCLA Site

## Project Overview

Multi-page static site for Effective Altruism at UCLA. No framework — plain HTML + Vanilla JS + Vite. Each page is a standalone `.html` file at the project root.

## Dev Server

```bash
npm run dev    # starts Vite at localhost:5173
```

Pages are served directly by filename: `localhost:5173/community.html`, etc.

## Key Conventions

- **Tailwind via CDN** — no build step for styles. Tailwind config lives in a `<script>` block at the top of each HTML file.
- **No shared components** — each page is self-contained. Copy patterns from existing pages when adding new sections.
- **Static assets in `public/`** — anything referenced as `Media/foo.jpg` in HTML must live in `public/Media/`. The root `Media/` folder is source storage only.
- **`.heic` images won't render in Chrome/Firefox** — always convert to `.jpg` first: `sips -s format jpeg input.heic --out public/Media/output.jpg`

## RSS Feed Logic (index.html)

- Feed sources: `RSS_FEEDS` array (~line 1170)
- Deduplication: `titlesAreSimilar()` — exact match, first-15-char prefix match, or 60% substring overlap. Substack is preferred over EA Forum for cross-posts.
- CORS proxies: `fetchWithProxyFallback()` cycles through fallback proxies if primary fails
- Caching: results stored in `localStorage` with keys `eaatucla_recent_works_cache`, `eaatucla_images_cache`, `eaatucla_ea_forum_cache`

## Color Tokens (Tailwind theme)

| Token | Hex | Usage |
|-------|-----|-------|
| `cardinal` | `#2D68C4` | UCLA blue, CTAs, accents |
| `eablue` | `#0C87C9` | EA brand blue |
| `bg` | `#F8FAFC` | Page background |
| `dark` | `#0F172A` | Dark sections |

Note: The token is still named `cardinal` in the Tailwind config for compatibility with existing class names (`text-cardinal`, `bg-cardinal`, etc.), but the hex value is now UCLA blue.

## Team Photos (`community.html`)

Photos are in `public/Media/`. The card pattern is a `<div class="group">` wrapping a rounded card with `aspect-square` image, name, role, and bio. See existing cards for reference.

## Logos

Logo files are at the project root: `EAAUCLAlogo.png`, `EAAUCLALogoBlue.png`, `EAAUCLALogoBlueSquare.png`. Replace these with actual UCLA EA logos when available. The square variant is used as the favicon across all pages.

## Git

- `node_modules/`, `dist/`, `.DS_Store`, `*.zip`, `._*` are gitignored
- Default branch: `main`
