# Achievement Goblin — Legal Pages

This folder contains three static, self-contained HTML files with no external
dependencies (no CDN scripts, no tracking):

- `index.html` — small landing page linking to the two documents
- `terms.html` — Terms of Service
- `privacy.html` — Privacy Policy

These are what Discord's Developer Portal wants for the **Terms of Service URL**
and **Privacy Policy URL** fields on your app's *General Information* page.

## Publishing with GitHub Pages

1. Create a new repository on GitHub (see the note on public vs. private below),
   e.g. `achievement-goblin-legal`.
2. Add these three files to the repo root (or to a `/docs` folder — either
   works, you just pick the matching option in step 4).
3. Commit and push.
4. In the repo, go to **Settings → Pages**. Under "Build and deployment",
   set Source to "Deploy from a branch", pick the `main` branch and the root
   (or `/docs`) folder, then Save.
5. GitHub will give you a URL like:
   `https://<your-username>.github.io/achievement-goblin-legal/`
   - Terms: `https://<your-username>.github.io/achievement-goblin-legal/terms.html`
   - Privacy: `https://<your-username>.github.io/achievement-goblin-legal/privacy.html`
6. Paste those two URLs into the Discord Developer Portal → your app →
   General Information → Terms of Service URL / Privacy Policy URL.

It can take a minute or two for Pages to build after your first push.

## About the "private repo" question

GitHub Pages sites are **publicly viewable on the internet** once published —
that's the whole point, Discord needs a link anyone (including Discord's
reviewers) can open without logging in.

The one thing that differs by plan is whether the *source repo* itself can be
private while still publishing a Pages site from it:

- **GitHub Free (personal accounts):** Pages can only be built from a
  **public** repository. If the repo is private, Pages won't build from it.
- **GitHub Pro, Team, or Enterprise Cloud:** Pages can be built from a
  **private** repository — the source stays private, but the published site
  is still public at its `github.io` URL.

Since `terms.html` and `privacy.html` don't contain anything sensitive (no
bot token, no code, no user data — just policy text), the simplest and
recommended approach is:

**Create one small, dedicated public repo that holds only these two/three
files** (nothing else from your bot project). That gets you a public Pages
site with zero cost and no plan requirements, while your actual bot code
(`D:\GitHub\achibot`) stays wherever it already is — this repo never needs to
touch it.

If you'd strongly prefer to keep even this repo private, options are:

- Upgrade to GitHub Pro (paid) and enable Pages from a private repo.
- Use a different free static host that *can* deploy a public site from a
  private-ish workflow without a paid plan, e.g. **Netlify** or **Vercel** —
  drag-and-drop these three files into Netlify Drop
  (https://app.netlify.com/drop) for an instant public URL with no GitHub
  repo at all.

Either way, only the two rendered pages become public — never your bot's
source code, database, or token.
