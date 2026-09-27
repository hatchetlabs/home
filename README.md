# Hatchet Labs

Source for [hatchetlabs.com](https://hatchetlabs.com), a static site built with
[Hugo](https://gohugo.io) (extended, v0.146 or newer).

```sh
hugo server          # preview at http://localhost:1313
hugo --gc --minify   # build into ./public
```

## Files

```
hugo.toml                         site title, tagline, description, nav menu
content/_index.md                 home page intro
content/about.md                  About page
content/contact.md                Contact page
content/projects/_index.md        projects listing intro
content/projects/_content.gotmpl  builds a page for each entry in data/projects.json
data/projects.json                the project list
layouts/                          templates
assets/css/main.css               styles (light and dark)
static/                           logo, favicon, touch icon, share image
archetypes/                       templates for `hugo new`
.github/workflows/deploy.yml      builds and deploys to GitHub Pages on push to main
```

## Projects

Each entry in `data/projects.json` becomes a page at `/projects/<slug>/`.

| field      | required | notes |
|------------|:--------:|-------|
| `slug`     | ✓ | URL segment; lowercase letters, digits and dashes |
| `title`    | ✓ | |
| `summary`  | ✓ | one line, shown on cards |
| `date`     | ✓ | RFC 3339; projects are listed newest first |
| `link`     |   | URL of the live project |
| `status`   |   | `alpha`, `beta`, `live`, `archived` or `research` (default `live`) |
| `tags`     |   | list of tags; each gets a `/tags/<tag>/` page |
| `featured` |   | `true` to show on the home page |
| `repo`     |   | source code URL (shown as "Full experiment" for research) |
| `body`     |   | Markdown for the project page |
| `highlight`|   | research: one-line headline result, shown large and on the card |
| `abstract` |   | research: paper-style abstract |
| `paper`    |   | research: link to the paper PDF |
| `pages`    |   | sub-pages in reading order, each `{slug, title, body}`; served at `/projects/<slug>/<page slug>/` with previous/next links |

The build fails if a required field is missing.

## Pages

To add a page, create `content/<name>.md` with `title` and `summary` front
matter and add a `[[menus.main]]` entry to `hugo.toml`.
