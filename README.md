# Songs of the Summer

A website of song reviews, built and published entirely from your browser —
**no software to install.** You'll do all of your work on GitHub.com: click a
file, click the pencil icon to edit it, type your review in Markdown, and
commit. A few seconds later, the live site updates itself automatically.

The site has:
- A home page listing every song.
- Ten song pages (`_songs/song-01.md` through `song-10.md`), one per song.

Each song page has the same four things: a **title**, a **performer**, your
**review** (a couple of paragraphs, written by you), and a **star rating**
from 0–5.

## Editing a song page on GitHub.com

1. In this repository, open the `_songs` folder and click one of the files
   (for example `song-01.md`).
2. Click the pencil icon (✏️) in the top-right of the file view to start
   editing.
3. Edit the text — see [The content model](#the-content-model-front-matter)
   below for exactly what to change.
4. Scroll to the bottom of the page. GitHub will ask how you want to save
   your change:
   - **Commit directly to the `main` branch** — the simplest option. Your
     change goes live as soon as the build finishes.
   - **Create a new branch and start a pull request** — use this if your
     class wants changes reviewed before they go live. Someone (an
     instructor, a partner) reviews your pull request and merges it when
     it's ready.
5. Click **Commit changes** (or **Propose changes**).

That's it — no downloads, no terminal, no local setup.

## The content model (front matter)

Open any file in `_songs/` and you'll see something like this at the top:

```markdown
---
song_number: 1
title: "Song Title 1"
performer: "Performer Name"
rating: 0
---

Write a first paragraph introducing the song...

Write a second paragraph going deeper...
```

The part between the two `---` lines is called **front matter** — think of
it as a small settings form for the page. Replace the placeholder values:

| Field | What it means | Example |
|---|---|---|
| `song_number` | Controls the order songs appear in on the home page. Leave as-is unless you want to reorder the list. | `song_number: 3` |
| `title` | The song's title. Keep the quotation marks. | `title: "Cruel Summer"` |
| `performer` | Who performs the song. Keep the quotation marks. | `performer: "Taylor Swift"` |
| `rating` | Your rating, a whole number from 0 (unrated) to 5. | `rating: 4` |

Everything **below** the second `---` is your review. Write as many
paragraphs as you like, in plain Markdown — no special formatting is
required to make the page work.

### Quick Markdown reference

You don't need to know much Markdown to write a review:

| You type | You get |
|---|---|
| `**bold text**` | **bold text** |
| `*italic text*` | *italic text* |
| `[link text](https://example.com)` | a clickable link |
| A blank line between lines | a new paragraph |

## Checking your build

Every commit — whether it's pushed straight to `main` or added to a pull
request — automatically triggers a **build check** in the "Actions" tab of
this repository. It catches typos in the front matter (like a missing
`---` or a stray quotation mark) before they can break the live site.

- ✅ Green check = the site built successfully.
- ❌ Red X = something's wrong. Click into the failed run and read the
  error — it usually points straight at the line that needs fixing.

Only commits that land on `main` actually publish to the live site; a
pull-request build is just a check, so it's safe to experiment on a branch.

## Customizing the site's look with an LLM

The site's colors, fonts, and other visual details are controlled by one
small block of settings near the top of
[`assets/css/main.scss`](assets/css/main.scss), called the **`:root`
block**. It looks like this:

```css
:root {
  --color-ocean: #00b4d8;
  --color-ocean-deep: #0077b6;
  --color-lagoon: #90e0ef;
  --color-sand: #fdf3dd;
  --color-sand-dark: #f4e2b8;
  --color-coral: #ff6b5b;
  --color-sun: #ffc857;
  --color-ink: #123544;
  --color-ink-soft: #3c6470;
  --color-white: #ffffff;

  --font-body: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  --font-display: Georgia, "Times New Roman", serif;

  --radius: 16px;
  --shadow: 0 10px 30px rgba(18, 53, 68, 0.12);
}
```

Every color and font on the site is built from these values, so changing
them re-skins the whole site — without touching any other file. You don't
need to know CSS to do this; you can ask an LLM (ChatGPT, Claude, Gemini,
etc.) to redesign it for you.

**Steps:**

1. Open `assets/css/main.scss` on GitHub.com and copy the `:root { ... }`
   block shown above.
2. Paste it into your LLM chat along with a prompt like this one:

   > I have a Jekyll website's CSS custom properties, shown below, for a
   > "Songs of the Summer" themed site. I want the site to feel more like
   > `[describe the look you want — e.g. "a retro sunset", "a minimalist
   > record store", "a neon 80s boardwalk"]`.
   >
   > Please give me back the exact same `:root { ... }` block, with the
   > same variable names, but with new values that achieve that look. Keep
   > `--font-body` and `--font-display` as web-safe font stacks (no
   > external font files). Briefly explain what each variable controls.
   >
   > ```css
   > [paste the :root block here]
   > ```

3. Copy the LLM's updated `:root` block.
4. Back on GitHub.com, click the pencil icon on `assets/css/main.scss`,
   select and delete the old `:root { ... }` block, and paste in the new
   one. **Keep the variable names exactly as they are** — only the values
   after each colon should change — otherwise the rest of the stylesheet
   won't know what to use.
5. Commit your change and check the Actions tab for the green checkmark.
   Once it passes, refresh the live site to see the new look.

## Publishing settings (for the repository owner)

This site deploys to GitHub Pages automatically via the workflow in
`.github/workflows/pages.yml`. Before your first publish:

1. In `_config.yml`, set `url` to your own GitHub Pages domain (e.g.
   `"https://<your-username>.github.io"`) — the shipped value is just a
   placeholder. `baseurl` should already match this repo's name; update it
   too if you rename or fork the repo.
2. In this repository, go to **Settings → Pages**.
3. Under **Source**, choose **GitHub Actions**.

After that, every commit to `main` builds and publishes the site with no
further action needed.

## Provenance

This repository — the site's structure, theme, and this README — was built
with [Claude](https://claude.ai/code), Anthropic's AI coding assistant.
