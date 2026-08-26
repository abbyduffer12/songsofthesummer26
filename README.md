# Songs of the Summer

A Jekyll template for a "Songs of the Summer" review site, served with GitHub
Pages. It ships with an attractive beach/tropical theme, a home page listing
your songs, and ten placeholder song pages ready for you to fill in with your
own Markdown content.

## Content model

Each song lives in `_songs/` as one Markdown file with this front matter:

```yaml
---
song_number: 1        # controls ordering on the home page
title: "Song Title"   # the song's title
performer: "Performer Name"
rating: 0              # your rating, 0-5 (whole number)
---

Your review goes here, in Markdown. Write as many paragraphs as you like.
```

The layout renders `title`, `performer`, a five-star rating built from
`rating`, and then your Markdown body as the review.

## Getting started

1. Open each file in `_songs/` (`song-01.md` through `song-10.md`) and
   replace the placeholder front matter and body text with your own song,
   performer, rating, and review. Rename the files if you'd like nicer slugs
   (the URL is based on the filename, e.g. `song-01.md` → `/songs/song-01/`).
2. Update `_config.yml`: `title`, `tagline`, `description`, `author`,
   `email`, and especially `url`/`baseurl` (see below) — the shipped
   values are placeholders and won't point at your site.
3. Edit `index.md` with your own homepage introduction.
4. Add or remove songs by adding/removing files in `_songs/` — the home page
   picks up everything in the collection automatically, sorted by
   `song_number`.

## Running locally

```bash
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000/songsofthesummer26/.

## Publishing to GitHub Pages

This repo deploys via the GitHub Actions workflow in
`.github/workflows/pages.yml`, which builds the Jekyll site and publishes it
with `actions/deploy-pages`.

1. In the repo settings, under **Pages**, set **Source** to **GitHub
   Actions**.
2. Push to `main` — the workflow builds and deploys automatically.

Before publishing, set `url` in `_config.yml` to your own GitHub Pages
domain (e.g. `"https://<your-username>.github.io"`). If you rename the
repository, or fork it under a different name, also update `baseurl` to
match (`"/<repo-name>"`).

## Theme

Colors, spacing, and other design tokens live at the top of
`assets/css/main.scss` as CSS custom properties — edit those to re-skin the
site without touching the layouts.
