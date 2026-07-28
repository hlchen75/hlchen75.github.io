# New site — "Ink & Cobalt"

A zero-dependency five-page static site: five sibling HTML pages sharing one
`styles.css`, plus a few lines of vanilla JS inlined in each page. No build step,
no external fonts, no frameworks, no network requests. Light and dark themes
follow the visitor's OS setting and can be overridden with the toggle in the nav
(the choice is remembered in `localStorage`).

```
index.html      Home — name, short intro, research interests, contact
research.html   Seven projects titled by their paper, each with its status
talks.html      Three conference talks and one poster
teaching.html   Nine courses, by campus
cv.html         Education and experience, plus a link to the CV PDF
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

Keep `CNAME` (it holds the custom domain) and `files/` (the CV and slides, which
every page links to relatively).

## Editing content

- **The intro** — the single `<p class="bio">` in `index.html`. The research
  interests below it are one line in `<p class="interests">`.
- **A project or paper** — these are the same entry. Copy an
  `<article class="project">` block in `research.html` and title it with the
  paper's title. The list is deliberately not grouped: each entry carries its
  own `<p class="status">` line instead ("Submitted to …", "Manuscript in
  progress", "Completed"). Equal-contribution and corresponding-author marks use
  `<span class="mark">&lowast;</span>`.
- **A new CV** — overwrite `files/Hanlong_Chen_CV.pdf`, then update the date in
  the one sentence that links to it, in `cv.html`:

  ```html
  <p class="lede reveal">My most recent CV is available as a
    <a href="files/Hanlong_Chen_CV.pdf">PDF</a>, last updated 27 July 2026.</p>
  ```

  That sentence is the only place the PDF is linked, so the filename and the
  date live in exactly one spot. Everywhere else, "CV" points at `cv.html`.
- **A photo** — there is no photo slot by design; the site is text-first. Ask
  Claude to add a portrait to the hero if you later want one.

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
