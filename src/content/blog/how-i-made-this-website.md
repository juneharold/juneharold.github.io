---
title: "How I rebuilt this website with Claude"
date: 2025-02-07
excerpt: "I used Claude Code to rebuild my personal site from scratch with Astro and Tailwind CSS — here's how the process went."
tags: ["Astro", "Tailwind CSS", "Claude", "AI"]
---

My old personal site was a handful of static HTML files with inline CSS from 2023. It worked, but it looked like it was built by a high schooler — because it was. Now that I'm a CS student at KAIST with actual projects and experience to show, I decided it was time for a rebuild. This time, I used [Claude Code](https://claude.ai) as my pair programmer.

## The old site

The original version was about as basic as it gets: `index.html`, `blog.html`, `contact.html`, a `style.css` file, and a Jesse Lingard GIF. No build step, no components, no responsive design. Just hardcoded HTML with 80px Josefin Sans headings and fixed left margins. It had character, but it wasn't doing me any favors.

## Starting the rebuild

I knew I wanted to move to **Astro** with **Tailwind CSS** — a modern static site generator with component-based architecture and utility-first styling, while still shipping zero JavaScript by default. I set up a `CLAUDE.md` file in the repo with my design direction and constraints:

- Dark theme, creative typography, mobile-first
- Sections: hero, about, projects, blog, footer
- Must deploy to GitHub Pages
- Keep my existing assets (resume PDF, the Lingard GIF — non-negotiable)

Then I told Claude to read through the existing codebase, note what to preserve, and rebuild from scratch.

## How Claude helped

The whole process was conversational. I described what I wanted at a high level and Claude handled the implementation:

1. **Scaffolding** — initialized the Astro project, installed Tailwind CSS 4, set up the directory structure while preserving my `.git` history and assets.

2. **Design** — Claude built the homepage with an editorial-brutalist aesthetic: oversized type in the hero, monospace section labels, a red accent color (a nod to Manchester United), decorative grid lines, and a subtle film grain overlay. The lingard.gif ended up in the About section next to the Man United mention.

3. **Blog infrastructure** — set up Astro content collections with a proper schema, created the blog listing and individual post pages, and wired the homepage to pull from real data instead of hardcoded placeholders.

4. **Deployment** — configured a GitHub Actions workflow to build and deploy to Pages on every push to `main`.

The key thing: I stayed in control of the decisions. Claude asked me before changing personal details (like updating "high school student" to "CS major at KAIST"), and I directed the content — which projects to feature, which social links to include, what tone the About section should have.

## The tech stack

Here's what the site runs on now:

- **Astro 5** — static site generator with content collections for the blog
- **Tailwind CSS 4** — utility-first CSS with the new CSS-based configuration
- **GitHub Actions** — automated build and deploy to GitHub Pages
- **No client-side JavaScript** — except a small IntersectionObserver for scroll animations

The entire site builds in under 500ms.

## What I learned

**AI pair programming works best when you know what you want.** Claude is fast at generating code, but the quality of the output depends heavily on the quality of the input. Having a clear `CLAUDE.md` with design direction, constraints, and site structure made the whole process smooth.

**Review everything.** I tweaked the About section copy, changed nav labels, and adjusted content based on my actual resume. Claude did the heavy lifting, but the editorial decisions were mine.

**Astro is great for this.** Content collections with type-safe schemas, zero-JS by default, and a clean component model — it's exactly what a personal site needs. No React, no hydration, just HTML.

## What's next

- Fill in the project cards with my actual work (Linq Alpha, FABRIC interpreter, emotion recognition CNN)
- Write more blog posts
- Maybe add a `/uses` page

If you're thinking about rebuilding your personal site, I'd recommend the Claude Code + Astro combo. Set up your constraints in a markdown file, be specific about what you want, and let the AI handle the boilerplate while you focus on the content.

---

The source code for this site is on [GitHub](https://github.com/juneharold/juneharold.github.io).
