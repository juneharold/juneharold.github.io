# juneharold.github.io

Personal portfolio for Juneha Hwang (Harold). Static site on GitHub Pages.

## Tech Stack
- **Astro 5** — static site generator with content collections
- **Tailwind CSS 4** — utility-first CSS via `@tailwindcss/vite`
- **KaTeX** — math rendering via `remark-math` + `rehype-katex`
- **GitHub Actions** — automated build/deploy (`.github/workflows/deploy.yml`)

## Design
- Dark theme (bg `#0a0a0b`, accent `#e23636` red)
- Typography: Space Grotesk (display/body) + JetBrains Mono (mono)
- Editorial-brutalist aesthetic with scroll animations (IntersectionObserver)
- Film grain overlay, decorative grid lines
- Mobile-first responsive

## Site Structure
- **/** — homepage: hero, about, featured projects, blog preview, footer with socials
- **/blog** — blog listing page (content collections)
- **/blog/[slug]** — individual blog posts (markdown with KaTeX math support)
- **/juneha_resume.pdf** — resume (static asset in `public/`)

## Key Files
- `src/layouts/Layout.astro` — base layout (fonts, meta, KaTeX CSS, scroll observer)
- `src/pages/index.astro` — homepage with all sections
- `src/pages/blog/[slug].astro` — blog post template with prose styling
- `src/content.config.ts` — blog collection schema (title, date, excerpt, tags)
- `src/content/blog/` — markdown blog posts
- `src/styles/global.css` — Tailwind theme, animations, KaTeX fix, grain overlay
- `astro.config.mjs` — site config, Tailwind plugin, remark/rehype plugins

## Known Issues
- npm cache has root-owned files — always use `NPM_CONFIG_CACHE=/tmp/npm-cache`
- KaTeX + Tailwind 4 conflict: must include `<style is:inline>.katex-mathml{display:none !important;}</style>` in blog post template
- GitHub Pages source must be set to "GitHub Actions" (not "Deploy from a branch") in repo settings

## Content Notes
- Bio: CS @ KAIST, data engineer at Linq Alpha, competitive programming (SCPC/UCPC finalist)
- Socials: GitHub, LinkedIn, Instagram, email (no Facebook)
- Keep the Manchester United reference + lingard.gif
- Project cards are placeholders — fill in with real projects later

## Constraints
- Static site only, must deploy to GitHub Pages
- Small bundle size, fast load times
- All content version-controlled in this repo
