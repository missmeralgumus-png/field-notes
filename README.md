# Field Notes — your blog with a write-and-publish panel

This is your whole blog. Once it's set up, writing a new post means: go to
`yoursite.netlify.app/admin`, type, and click **Publish**. No files, no code,
no dragging. It saves to GitHub, and Netlify rebuilds the site automatically.

You only do the setup below **once**. Plan about 20–30 minutes.

---

## What you'll need (all free)

1. A **GitHub** account — stores your site and posts. → github.com
2. A **Netlify** account — hosts the live site. → netlify.com
3. A **DecapBridge** account — powers the login for your /admin panel. → decapbridge.com

---

## One-time setup

### 1. Put this project on GitHub
- Create a new **private** repository on GitHub named `field-notes`. (Private is
  fine with Netlify and keeps your source files and any draft posts out of public
  view — only your published website is visible to the world.)
- Upload the contents of this folder into it (the whole thing EXCEPT the
  `node_modules` and `_site` folders — Netlify rebuilds those itself).
  The easiest way: on your new repo's page, click **Add file → Upload files**,
  then drag everything in.

### 2. Connect Netlify to that repo (this is your auto-deploy)
- In Netlify, click **Add new site → Import an existing project → GitHub**.
- Pick your `field-notes` repo.
- Netlify reads `netlify.toml` automatically, so the build settings are already
  correct (build command `npm run build`, publish directory `_site`). Click **Deploy**.
- In a minute you'll have a live site at something like `random-name.netlify.app`.
  Rename it under **Site configuration → Change site name** (e.g. `meral-fieldnotes`).

### 3. Set up the login (DecapBridge)
- Sign up at **decapbridge.com** and choose **Create new site**.
- Enter your repo as `your-github-username/field-notes`.
- It will ask you to create a **GitHub access token** — follow its link, generate
  a *fine-grained* token limited to your `field-notes` repo with **Contents** and
  **Pull requests** set to read & write. Paste the token back into DecapBridge.
- Enter your admin URL: `https://your-site-name.netlify.app/admin/`
- DecapBridge then shows you a short **backend snippet**. Copy it.

### 4. Paste your values into the config
Open `src/admin/config.yml` (edit it right on GitHub — click the file, then the
pencil icon). Replace the top `backend:` block with the snippet from DecapBridge,
and fix the two `REPLACE...netlify.app` lines to your real site address. Commit the
change. Netlify redeploys on its own.

### 5. Write your first post
- Go to `https://your-site-name.netlify.app/admin/`
- Log in with your DecapBridge account.
- Click **New Post**, fill in the title, date, category, summary, and body.
- Click **Publish**. Wait ~1 minute, refresh your homepage — it's there.

That's it. From now on, writing = /admin → type → Publish.

---

## Making it yours (optional, anytime)
- **Blog name & intro:** edit `src/index.njk` — the `<h1>`, the paragraph under it,
  and the two "Field Notes" labels.
- **Your email:** in `src/index.njk`, change `you@example.com` in the footer.
- **Colors:** the palette lives at the top of `src/css/style.css` (the `--accent`,
  `--ideas`, `--daily` values).
- **Delete the sample posts:** remove the files in `src/posts/` (or just delete them
  from the /admin panel once you're in).

Prefer not to touch files? Send any of these to Claude and get an updated version back.

---

## How it fits together (for the curious)
- You write Markdown posts (the /admin panel does this for you) into `src/posts/`.
- **Eleventy** (the build step) turns those into the finished website.
- **Netlify** runs that build and serves the result every time the repo changes.
- **DecapBridge** lets you log in to the panel without running a server yourself.
