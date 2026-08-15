# Notes & Thoughts

```sh
# Create a note
hugo new content posts/my-note.md

# Create a paper summary
hugo new content reading/paper-title.md

# Create another standalone page
hugo new content page-name.md
```

A small personal website and digital notebook built with [Hugo](https://gohugo.io/) and the [Risotto](https://github.com/joeroe/risotto) theme. It contains notes, research-paper summaries, current interests, and links to ongoing work.

## Writing

New content is created as a draft. Edit its front matter and set `draft = false` when it is ready to publish. Use a short, lowercase filename with hyphens; Hugo turns it into the page URL.

The main content lives in:

- `content/posts/` — notes and longer writing
- `content/reading/` — paper summaries and reading notes
- `content/_index.md` — homepage copy
- `data/currently.toml` — the shared “Currently” entries

## Local preview

```sh
# Include drafts while writing
hugo server --buildDrafts

# Check the production build
hugo --gc --minify
```

The development server is available at `http://localhost:1313/`. Generated output is written to `public/` and intentionally ignored by Git.

## Site configuration

- `hugo.toml` contains the site URL, navigation, theme, and analytics token.
- `static/` contains the custom domain, favicons, and custom CSS.
- `layouts/` contains local Risotto overrides, including breadcrumbs and content lists.
- `themes/risotto/` is the theme submodule.

## Deployment

Pushes to `main` trigger `.github/workflows/hugo.yaml`, which builds the site with Hugo and deploys the generated artifact to GitHub Pages. The production domain is [erikxu.me](https://erikxu.me/).
