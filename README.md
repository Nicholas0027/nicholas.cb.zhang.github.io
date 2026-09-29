# Chengbo (Nicholas) Zhang + Agentic City Lab — website package

Static HTML/CSS/JS. No build step or framework is needed to host it.

```
index.html                  Personal site (Chengbo (Nicholas) Zhang)
cv/ZhangChengbo_CV.pdf      CV linked from the personal site
lab/index.html              Agentic City Lab site
lab/identity/index.html     Identity sheet: the Stencil ACL mark, its construction, colour, glyphs, type, explored options
lab/identity/logos/         SVG files: acl-stencil-ACL-* (mark, lockup), acl-stencil-A-monogram-* (the A alone, for icons),
                            explored-* options and route glyphs; each in dark/light/white/black
assets/fonts/               Self-hosted fonts (Archivo, Instrument Sans, IBM Plex Mono, Source Serif 4; SIL OFL)
assets/favicon.svg          The stencil A on a dark rounded square
assets/data.js              All content: publications, projects, talks, awards, news
assets/base.css, gfx.js     Shared styles, logo options and glyphs (ACL.MARK picks the active logo)
assets/sim.js               Live human–AI interaction city shown on both sites
assets/figures/             Figures from the papers, prepared for the dark theme (<id>.jpg square tile, <id>-full.jpg)
assets/img/                 portrait.jpg (4:5, personal site) and portrait-sq.jpg (square, lab People and link previews)
```

## Preview locally

```
cd website
python3 -m http.server 8000
# open http://localhost:8000
```

## Publish on GitHub Pages (free)

1. Create a repository named `<your-github-username>.github.io` (e.g. `Nicholas0027.github.io`).
2. Upload the contents of this folder (not the folder itself) to the repository root.
3. In the repository: Settings → Pages → Source: "Deploy from a branch", branch `main`, folder `/ (root)`.
4. The personal site will be live at `https://<username>.github.io/` and the lab at `https://<username>.github.io/lab/`.

## Custom domains

- Personal: add a `CNAME` file containing e.g. `chengbozhang.com`, and point the domain's DNS to GitHub Pages.
- Lab on its own domain (e.g. `agenticcity.org`): copy `lab/` and `assets/` into a second repository, move the
  contents of `lab/` to the root, change `../assets/` to `assets/` (and `../../assets/` to `../assets/` in
  `identity/index.html`), point the director links (`../`) to the personal-site URL, and add a `CNAME` there.

## Editing content

All publications, projects, talks, awards and news live in one file, `assets/data.js`, shared by both sites.
Edit the entries there; lists, filters and counts on every page update automatically.
`assets/base.css` holds the shared colour and type tokens; `assets/gfx.js` draws the glyphs and project tiles.
The active logo is Stencil ACL (`ACL.MARK = 'aclStencil'` in `assets/gfx.js`); its proportions live in `ACL.STENCIL` in the same file.
To add a project figure, put `<id>.jpg` (1:1) and `<id>-full.jpg` in `assets/figures/`, add the caption to `figures`
in `data.js`, and set `fig: "<id>"` on the project.
To change the portrait, replace `assets/img/portrait.jpg` (4:5) and `assets/img/portrait-sq.jpg` (1:1) with files of the same names.
