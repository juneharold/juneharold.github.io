---
title: "How I made this website"
date: 2023-02-21
excerpt: "A walkthrough of building a personal site from scratch — from planning to deployment on GitHub Pages."
tags: ["Web Development", "HTML", "CSS", "GitHub Pages"]
---

Building a personal website from scratch is one of the most rewarding projects you can undertake as a developer. It's a space that's entirely yours — a digital canvas to showcase your work, share your thoughts, and establish your online presence. In this post, I'll walk you through how I built my first personal website using HTML and CSS, and deployed it on GitHub Pages.

## Planning the Site

Before writing any code, I spent time thinking about what I wanted the site to accomplish. For me, it was simple:

- A place to introduce myself
- Showcase my projects
- Share occasional blog posts
- Provide ways to contact me

I sketched out a rough wireframe on paper, mapping out the sections: a hero area, about section, projects grid, blog preview, and footer. This planning phase is crucial — it saves you from aimlessly coding without direction.

## Choosing the Right Tools

For my first iteration, I kept things minimal:

- **HTML5** for structure
- **CSS3** for styling
- **No frameworks** — just vanilla code

This might seem old-school in 2023, but there's immense value in understanding the fundamentals before reaching for React or Vue. You learn how the web actually works.

I used **Visual Studio Code** as my text editor, which comes with excellent HTML/CSS support out of the box. Extensions like Live Server made development smooth by auto-refreshing the browser on save.

## Building the HTML Structure

I started with a semantic HTML structure. Here's a simplified version of my `index.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Juneha Hwang</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <nav>
    <!-- Navigation links -->
  </nav>

  <section id="hero">
    <h1>Juneha Hwang</h1>
    <p>CS student at KAIST</p>
  </section>

  <section id="about">
    <!-- About content -->
  </section>

  <section id="projects">
    <!-- Project cards -->
  </section>

  <footer>
    <!-- Contact info and links -->
  </footer>
</body>
</html>
```

Using semantic tags like `<nav>`, `<section>`, and `<footer>` not only makes the code more readable but also improves accessibility and SEO.

## Styling with CSS

This is where the site comes to life. I wanted a clean, modern aesthetic with good typography and subtle animations. Here's my approach:

### Typography

I chose **Inter** for body text and **JetBrains Mono** for code snippets. Google Fonts makes this trivial:

```html
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
```

### Color Scheme

I opted for a light theme with a limited color palette:
- Primary: `#1a1a1a` (near black)
- Accent: `#3b82f6` (blue)
- Background: `#ffffff`
- Muted text: `#666666`

### Responsive Design

Mobile-first CSS was essential. I used Flexbox and CSS Grid for layouts, and media queries to adjust for larger screens:

```css
.projects {
  display: grid;
  grid-template-columns: 1fr;
  gap: 2rem;
}

@media (min-width: 768px) {
  .projects {
    grid-template-columns: repeat(2, 1fr);
  }
}
```

### Animations

Subtle animations enhance user experience without being distracting. I added a fade-in effect using CSS animations:

```css
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.fade-in {
  animation: fadeIn 0.6s ease-out;
}
```

## Testing Across Devices

I tested the site on:
- Chrome, Firefox, and Safari
- Desktop, tablet, and mobile viewports
- Different screen sizes using Chrome DevTools

This revealed spacing issues on mobile and font sizes that needed adjustment. Testing early and often saves headaches later.

## Deploying to GitHub Pages

GitHub Pages offers free hosting for static sites, perfect for personal portfolios. Here's how I deployed:

1. Created a repository named `juneharold.github.io`
2. Pushed my HTML/CSS files to the `main` branch
3. Enabled GitHub Pages in the repository settings
4. Accessed the site at `https://juneharold.github.io`

The process is remarkably smooth. Any push to `main` automatically updates the live site.

## What I Learned

Building this site taught me:

- **Start simple**: Don't over-engineer. A static HTML/CSS site is often enough.
- **Design matters**: Even basic CSS can create a polished look with attention to spacing, typography, and color.
- **Mobile-first is essential**: Most visitors will view on mobile.
- **Iteration is key**: Version 1 doesn't need to be perfect. You can always refine.

## Next Steps

I'm already thinking about improvements:
- Adding a dark mode toggle
- Migrating to a static site generator like Astro
- Implementing a proper blog with Markdown support
- Improving accessibility with ARIA labels

If you're thinking about building your own site, just start. Pick a text editor, write some HTML, and see where it takes you. The web is your canvas.

---

Thanks for reading! If you have questions or want to share your own site-building journey, feel free to reach out.
