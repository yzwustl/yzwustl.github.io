# yzwustl.github.io

Personal academic website — static HTML and one stylesheet, no build step, no dependencies.

```
index.html      Home: photo, affiliation, fields, contact, 2–3 headline papers
research.html   Working papers, publications, work in progress
teaching.html   Courses taught, TA work, materials
cv.html         Download button + embedded PDF
style.css       All styling. Change --accent and --measure at the top to restyle.
files/          PDFs: CV, papers, slides
images/         Headshot
.nojekyll       Tells GitHub Pages to serve files as-is (no Jekyll processing)
```

## Editing

Open any `.html` file in a text editor. Everything in `[square brackets]` is a
placeholder to replace. `<!-- TODO -->` comments mark the spots that matter most.
Double-click a file to preview it in your browser — no server needed.

The four pages each repeat the header and nav block. When you change the nav
(add a page, rename one), change it in all four. That duplication is the price
of having no build step; with four pages it is cheaper than a static site
generator.

To change the whole site's look, edit the variables at the top of `style.css`:

```css
--accent:  #1f4d38;   /* deep green — try #1e3a5f navy, #7a1c2e maroon */
--measure: 46rem;     /* content width */
```

## Deploying

1. Create a repo on GitHub named exactly **`yzwustl.github.io`** (public, empty —
   no README, no .gitignore).
2. From this folder:

```bash
git init -b main
git add -A
git commit -m "Initial site"
git remote add origin https://github.com/yzwustl/yzwustl.github.io.git
git push -u origin main
```

3. Pages turns on automatically for a `<username>.github.io` repo. The site is
   live at <https://yzwustl.github.io> within a minute or two.

Later updates are just:

```bash
git add -A && git commit -m "Update research" && git push
```

## Adding a paper

Copy a `.paper` block in `research.html` and edit it:

```html
<div class="paper">
  <h3 class="title"><a href="files/my-paper.pdf">Title of the Paper</a></h3>
  <p class="authors">with Jane Doe (MIT)</p>
  <p class="status">Revise and resubmit, Journal of Finance</p>
  <p class="links">
    <a href="files/my-paper.pdf">Paper</a>
    <a href="https://ssrn.com/abstract=...">SSRN</a>
  </p>
  <details>
    <summary>Abstract</summary>
    <p class="abstract">…</p>
  </details>
</div>
```

Drop the PDF in `files/`. Use hyphenated lowercase filenames — no spaces, since
spaces become `%20` in URLs.

## Custom domain (optional)

Buy a domain, add a file named `CNAME` in this folder containing just the domain
(e.g. `yingzexu.com`), push, then point a CNAME DNS record at
`yzwustl.github.io`. Keep the `.github.io` address working as a fallback.
