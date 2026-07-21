# Website Improvement Plan — sagarmarthandan.github.io

Generated 2026-07-21. The site is already well-crafted: clean minimal design, good typography (Instrument Serif + Inter + JetBrains Mono), dark/light toggle, responsive, 6 pages (home, repos, resume, contact, blog, uses), 23 repos, 1 blog post. These additions layer on top without redesigning.

---

## High-impact visual additions

### 1. Profile photo in the hero
`images/sagar.jpg` (287KB) exists but isn't used on the homepage. The hero right column is a badge wall — add a small circular or rounded-rect photo above or beside the badges for instant personality.

### 2. Open Graph social preview image
Meta tags have `og:title`, `og:description`, `og:url` but **no `og:image`**. LinkedIn/Twitter/Discord shares get text-only preview. Add a 1200×630 image with name, title, and stack. Single highest-ROI addition for a job seeker.

### 3. Subtle hero background texture
Page is very flat (solid `#0f0f0f`). Add a barely-visible radial gradient, noise texture, or faint grid pattern in the hero:
```css
.hero {
  background-image: radial-gradient(circle at 50% 0%, rgba(96,165,250,0.06), transparent 60%);
}
```

### 4. Scroll progress bar
2px accent-colored bar at top that fills as you scroll. Pure CSS + 5 lines of JS.

---

## Content that adds personality & freshness

### 5. "Now" section (nownownow.com style)
Short section or separate page showing what you're currently doing:
- Currently building: Chicago Data Pipeline
- Currently learning: Airflow 3.x migration
- Currently reading: Designing Data-Intensive Applications
- Currently exploring: dbt Fusion

Signals you're active and current — recruiters look for this.

### 6. GitHub live stats
Repos page lists 23 projects but no aggregate social proof. Add via GitHub API or github-readme-stats:
- Total repos, total stars, languages breakdown
- Contribution heatmap (like GitHub profile graph)

Makes the repos page feel alive rather than static.

### 7. Project thumbnails / architecture diagrams
Every project is text-only. Add a small thumbnail — screenshot of a dashboard, architecture diagram, or generated OG image per project. `precision_recall_curve.png` in the fraud detection project is an example of the kind of visual that draws the eye.

### 8. More blog posts
Blog has 1 post and an empty-state design. 13+ portfolio writeups exist in `okf/portfolio/` (F1 pipeline, weather analytics, YouTube E2E, Bitcoin dbt, Chicago crime, etc.) — convert 3-4 into blog posts to fill out the blog page and increase SEO surface for recruiter discovery.

---

## Polish & UX details

### 9. Active nav highlighting
CSS defines `.nav-links a.active` but no JS sets it. Add:
```js
const path = location.pathname;
document.querySelectorAll('.nav-links a').forEach(a => {
  if (a.getAttribute('href') === path || (path === '/' && a.getAttribute('href') === '/'))
    a.classList.add('active');
});
```

### 10. Copy-to-clipboard on email
Clicking email should copy to clipboard with a tiny "copied!" tooltip, in addition to `mailto:`. Reduces friction on mobile.

### 11. Command palette (Cmd+K)
Keyboard-triggered overlay for quick navigation — search pages, projects, social links. Popular on developer portfolios (Josh Comeau, Lee Robinson). Fits the aesthetic, adds a "wow" moment.

### 12. Keyboard shortcuts
`g h` → home, `g r` → repos, `g b` → blog, `g c` → contact. GitHub-style. Pairs well with command palette.

### 13. Reading progress bar on blog posts
Thin progress bar at top of `blog/algorithmic-monoculture-and-okf-cv.html` that fills as you read.

### 14. Back-to-top button
On repos page (23 items) and resume page (long) — small floating ↑ button that appears after scrolling.

### 15. Print stylesheet for resume page
`@media print` CSS on `resume.html` for direct printing with proper page breaks, hidden nav/footer, clean typography — instead of downloading PDF.

---

## Technical / SEO additions

### 16. RSS feed (rss.xml)
Standard for blogs. Lets people subscribe in feed readers. Generate manually or with a tiny script since the blog is static.

### 17. sitemap.xml + robots.txt
Neither exists. Sitemap helps Google index all 7 pages. robots.txt that allows all + points to sitemap. 2 minutes, real SEO impact.

### 18. Custom 404 page
GitHub Pages serves a default 404. Add a branded one with monogram, a message, and links back to main pages.

### 19. Favicon set
One SVG favicon exists. Add `apple-touch-icon.png` (180×180), `favicon-32x32.png`, `favicon-16x16.png`, and `site.webmanifest` for proper iOS/Android/browser tab support.

### 20. Privacy-friendly analytics
Plausible or Umami — lightweight, no cookies, GDPR-safe. Learn which pages recruiters visit most, which referral sources work, what countries traffic comes from. Essential for optimizing presence.

---

## Top 5 if prioritizing

| Priority | Addition | Why |
|----------|----------|-----|
| 1 | OG image | Every LinkedIn/Twitter share has no preview — biggest visual gap |
| 2 | Profile photo in hero | Asset exists, just not used — instant personality |
| 3 | "Now" section | Signals active and current — recruiters look for this |
| 4 | More blog posts | 13 portfolio writeups ready to convert — biggest content gap |
| 5 | GitHub live stats on repos page | Social proof + dynamism on most content-rich page |

---

## Notes for implementation
- Don't change typography, color system, or layout — the design is already strong.
- All additions layer on top of existing structure.
- Repo is at `C:/Users/sagar/Documents/sagarmarthandan.github.io`.
- Pages: `index.html`, `repos.html`, `resume.html`, `contact.html`, `blog.html`, `uses.html`, `blog/algorithmic-monoculture-and-okf-cv.html`.
- Shared CSS is inline in each page's `<head>` (no external stylesheet) — changes to shared styles need to be applied across all pages.
- Theme toggle JS is inline at the bottom of each page.
