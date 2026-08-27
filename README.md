# Songs of the Summer

This is a website of song reviews — a home page plus ten song pages, one per
song. You will build the whole thing here, on GitHub.com, in your web
browser. You don't need to download or install anything. Every change you make gets typed and saved directly on this
website.

## A few words you'll see

You don't need to memorize these — just glance back here if one of them
comes up below.

- **Repository** (or "repo") — this project. Everything for the site —
  its pages, its settings, its look — lives in the list of files and
  folders you see when you open this repository on GitHub.
- **File** — one piece of content, like one song's page. You'll open files,
  change their text, and save your changes.
- **Commit** — GitHub's word for "save." Every time you save a change to a
  file, you're making a commit, and you'll type a short note describing
  what you changed (like "Add review for song 3").
- **Front matter** — a small block of settings at the top of a file,
  between two lines that look like `---`. You'll see this in every song
  file — it's covered in detail below.
- **Actions / build** — every time you commit a change, GitHub
  automatically checks that it didn't break anything, then republishes the
  live site. You don't have to do anything to trigger this — it just
  happens.

## The three things you'll do

1. **Set up your site's basic info** — the title, and the address it lives
   at — in one settings file, `_config.yml`.
2. **Write your ten song reviews** — one file per song, in the `_songs`
   folder.
3. **(Optional) Customize the look** — colors and fonts, by prompting an
   LLM.

Each is explained step by step below.

---

## Step 1: Set up your site's basic info (`_config.yml`)

`_config.yml` is the file that holds your site's name, tagline, and web
address. You'll edit it once, near the start.

1. At the top of this repository's file list, click on **`_config.yml`**.
2. On the page that opens, look at the top-right corner of the file and
   click the **pencil icon** (hover over it and it will say "Edit this
   file"). The file becomes editable, with line numbers down the left
   side.
3. Find these lines near the top and change the text after each colon
   (`:`) — leave everything else, including the quotation marks, exactly
   where it is:

   ```yaml
   title: Songs of the Summer
   tagline: A playlist of reviews, one song at a time
   description: >-
     A Jekyll template for building a "Songs of the Summer" review site.
     Each song gets its own page with a title, performer, review, and
     a five-star rating. Replace this description with your own.
   ```

   - `title` — the name of your site, as it will appear in the browser
     tab and at the top of the home page.
   - `tagline` — a one-line subtitle under the title.
   - `description` — a few sentences about your site. This block spans
     several indented lines (notice the `>-` and the indent) — you can
     rewrite all of those lines, just keep each new line indented the
     same amount as the ones you're replacing.

4. A little further down, find these two lines:

   ```yaml
   url: "https://your-username.github.io"
   baseurl: "/songsofthesummer26"
   ```

   These two lines together form your site's web address, and they need
   to match this repository exactly:

   - `url` — look at your browser's address bar right now. It reads
     something like `github.com/YOUR-USERNAME/songsofthesummer26`.
     Replace `your-username` inside the quotes with that `YOUR-USERNAME`
     part (everything right after `github.com/`). Keep the quotation
     marks and the rest of the text (`https://` and `.github.io`) exactly
     as it is.
   - `baseurl` — this should already read `"/songsofthesummer26"`, which
     matches this repository's name, so you can usually leave it alone.
     Only change it if you renamed the repository — in that case, replace
     `songsofthesummer26` with the repository's new name, keeping the
     leading `/` and the quotation marks.

5. Optionally, further down, fill in your own name and email:

   ```yaml
   author: Your Name
   email: your-email@example.com
   ```

6. Scroll all the way to the bottom of the page. You'll see a box titled
   **"Commit changes"**:
   - Type a short note in the first box, like `Set up my site info`.
   - Leave **"Commit directly to the `main` branch"** selected.
   - Click the green **Commit changes** button.

Your site's basic info is now set. A build will start automatically — see
[Checking your build](#checking-your-build) below if you want to watch it
finish.

---

## Publishing settings

This site deploys to GitHub Pages automatically, through a workflow file
already included in this repository. Before your very first publish,
someone with access to this repository's settings needs to turn it on:

1. Go to this repository's **Settings** tab, then click **Pages** in the
   left sidebar.
2. Under **Build and deployment → Source**, choose **GitHub Actions**.

After that, every commit to `main` builds and publishes the site
automatically — no further action needed. (Steps 1 and 2 above already
covered getting `url` and `baseurl` set correctly in `_config.yml`, which
this depends on.)


---

## Step 2: Write your ten song reviews

Each song has its own file in the `_songs` folder: `song-01.md` through
`song-10.md`. You'll repeat the same steps for each one.

### Editing one song page

1. In this repository, click the **`_songs`** folder to open it.
2. Click on a file, for example **`song-01.md`**.
3. Click the **pencil icon** in the top-right corner to start editing.
4. At the top of the file, between the two `---` lines, you'll see the
   **front matter** — the song's settings:

   ```yaml
   ---
   song_number: 1
   title: "Song Title 1"
   performer: "Performer Name"
   rating: 0
   ---
   ```

   Replace the placeholder values, keeping the quotation marks around
   `title` and `performer`:

   | Field | What to put there | Example |
   |---|---|---|
   | `song_number` | Leave this matching the file's number (`song-01.md` → `1`, `song-02.md` → `2`, and so on). It controls the order songs appear in on the home page. | `song_number: 1` |
   | `title` | The song's title, in quotation marks. | `title: "Cruel Summer"` |
   | `performer` | Who performs the song, in quotation marks. | `performer: "Taylor Swift"` |
   | `rating` | Your rating: a whole number from 0 (unrated) to 5. No quotation marks. | `rating: 4` |

5. Below the second `---` line, delete the placeholder paragraphs and
   write your review. Write as many paragraphs as you like — press Enter
   twice between paragraphs to start a new one. See the Markdown
   reference below if you want to bold text or add a link.
6. Scroll to the bottom of the page. In the **"Commit changes"** box:
   - Type a short note, like `Add review for song 1`.
   - Leave **"Commit directly to the `main` branch"** selected (or choose
     **"Create a new branch and start a pull request"** if your class is
     having reviews check work before it goes live).
   - Click the green **Commit changes** (or **Propose changes**) button.

### Repeat for all ten

Do the same for `song-02.md` through `song-10.md`. You can do them in any
order, and in as many separate visits as you like — each file is saved the
moment you commit it.

### Quick Markdown reference

Your review is written in Markdown, a simple way to format text with
plain characters:

| You type | You get |
|---|---|
| `**bold text**` | **bold text** |
| `*italic text*` | *italic text* |
| `[link text](https://example.com)` | a clickable link |
| A blank line between two lines of text | a new paragraph |

---

## Checking your build

Every time you commit a change, GitHub automatically tries to rebuild your
site, whether the commit went straight to `main` or into a pull request.
This catches mistakes — like a missing `---` or a stray quotation mark —
before they can break the live site.

1. Click the **Actions** tab near the top of the repository.
2. Find your commit in the list — it will have the note you typed.
3. Look at the icon next to it:
   - ✅ A green checkmark means the site built successfully.
   - ❌ A red X means something's wrong. Click into that run and read the
     error message — it will usually point at the exact line to fix. Go
     back, edit the file again, and commit the fix the same way.


---

## Step 3 (optional): Customize the look with an LLM

The site's colors, fonts, and other visual details are controlled by one
small block of settings near the top of a file called
**`assets/css/main.scss`**, called the **`:root` block**. It looks like
this:

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
them re-skins the whole site — no other file needs to change. You don't
need to know CSS to do this; you can ask an LLM (ChatGPT, Claude, Gemini,
or whichever one you use) to redesign it for you.

1. In this repository, open **`assets/css/main.scss`** and copy the
   `:root { ... }` block shown above (or however it currently reads).
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
   select the old `:root { ... }` block and delete it, then paste in the
   new one. **Keep the variable names exactly as they are** — only the
   values after each colon should change — otherwise the rest of the
   stylesheet won't know what to use.
5. Scroll down and commit your change, the same way you did in Steps 1
   and 2. Check the Actions tab for the green checkmark, then refresh the
   live site to see the new look.

---


## Provenance

This repository — the site's structure, theme, and this README — was built
with [Claude](https://claude.ai/code), Anthropic's AI coding assistant.
