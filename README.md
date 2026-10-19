# New site — "Ink & Cobalt"

A zero-dependency five-page static site: five sibling HTML pages sharing one
`styles.css`, plus a few lines of vanilla JS inlined in each page. No build step,
no external fonts, no frameworks, no network requests. Light and dark themes
follow the visitor's OS setting and can be overridden with the toggle in the nav
(the choice is remembered in `localStorage`).

```
index.html      Home — short intro, contact, and landscape photo
research.html   Seven projects titled by their paper, each with its status
talks.html      Three conference talks and two posters
teaching.html   Nine courses, by campus
cv.html         Resume — education and selected research experience (web only)
styles.css      Shared design tokens and all layout
```

The home page is deliberately bare: everything else is one click away in the nav.

## Publishing

Edit the files at the repo root and push to `master`; GitHub Pages serves them
as authored. `.nojekyll` is what stops Pages from trying to run Jekyll over them,
so leave it in place. A push usually appears on hanlongchen.com within a minute
or two — hard-reload if you still see the old stylesheet.

To preview locally, open `index.html` in a browser. Everything is relative, so it
works from the filesystem with no server.

Keep `CNAME` (it holds the custom domain) and the presentation slides in `files/`.
The resume is available only as a web page; do not publish a resume PDF.

## Editing content

- **The intro** — the three paragraphs inside `<div class="home-intro">` in
  `index.html`, including the contact line.
- **A project or paper** — these are the same entry. Copy an
  `<article class="project">` block in `research.html` and title it with the
  paper's title. The list is deliberately not grouped: each entry carries its
  own `<p class="status">` line instead ("Under review", "Manuscript under
  internal review", "Completed"). Equal-contribution and corresponding-author
  marks use `<span class="mark">&lowast;</span>` and
  `<span class="mark">&dagger;</span>`, respectively.
- **The resume** — update the education and experience entries directly in
  `cv.html`. All "Resume" navigation links point to this web page. The PDF
  download sentence and `files/Hanlong_Chen_CV.pdf` have been removed from the
  published site. The previous PDF is backed up locally under
  `local/private-resume/`, which is ignored by Git and must stay out of any
  deployment. Do not restore a public PDF without an explicit request.
  The detailed interview-only CV is private: do not add it to this repository.
- **The photo** — `images/vancouver.jpg` appears in the home page's
  `<figure class="home-photo">`. Update its alt text and dimensions if replacing it.

Two things are duplicated on purpose and must be edited on all five pages or
none: the `<script>` block at the bottom, and the small theme script in `<head>`
(it has to run before the stylesheet loads, otherwise the page flashes the wrong
theme).

## The eyebrow numerals

The cobalt `01` / `02` / `03` above each section heading are section indices, in
page order — not counts. Research has no such numerals because it is one
ungrouped list. They mean one thing everywhere and never need updating
when content is added, so renumber them only if you reorder or add a section.
Page heroes carry a plain text eyebrow with no numeral.

## Design tokens

Colours, fonts, spacing, and the container width are CSS custom properties in
the four `:root` blocks at the top of `styles.css` — light, OS-dark,
forced-dark, forced-light. Change a token once and it applies everywhere in both
themes. The accent (`--accent`, cobalt) is deliberately used in only a few
places: the eyebrow numerals, the talk numerals, links, the monogram dot, and
focus rings.
