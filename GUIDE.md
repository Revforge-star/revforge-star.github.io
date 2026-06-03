# Modern Revenue Blog — Owner's Guide

A plain-language guide to how this blog is set up and how to use it day-to-day. Written for someone new to web development. Last updated 2026-06-03.

---

## 1. The 90-second overview

You have:

- A **website** live at https://revforge.blog/
- A **GitHub repository** at https://github.com/Revforge-star/revforge-star.github.io that holds the source code (the blog's "raw materials")
- A **domain name** (`revforge.blog`) registered at Porkbun
- A **local copy** of the code on your Mac at `~/Desktop/revforge-star.github.io/`

Whenever you change the code (on the website or your laptop), GitHub automatically rebuilds and republishes the site within ~1-2 minutes. You don't have to "deploy" manually.

---

## 2. How the pieces fit together

```
You edit a file
      │
      ▼
  Save to GitHub  ──────►  GitHub Actions builds the site  ──────►  GitHub Pages serves it
      │                          (runs npm build for you)              at revforge.blog
      │
   Two paths to save to GitHub:
      ├─ via the GitHub website (easiest, no terminal needed)
      └─ via your Mac (git commit + push from VS Code or terminal)
```

You always go *through* GitHub — but "going through GitHub" doesn't mean "using the terminal." There are several ways to edit, listed in section 4.

**Why this design:**
- The website is **static** (just HTML/CSS/JS files, no database, no server) — so it's fast, free to host, and very secure.
- GitHub holds the source files and rebuilds the site automatically when you change them. This is called a "Jamstack" architecture.

---

## 3. Key terms (one-line each)

| Term | What it means here |
|---|---|
| **Repository / repo** | A folder of code, tracked by Git, hosted on GitHub. |
| **Git** | A tool that tracks changes to files (commits). |
| **Commit** | A saved snapshot of changes with a short message describing what changed. |
| **Push** | Send your local commits to GitHub. |
| **Pull** | Bring down GitHub's latest commits to your laptop. |
| **GitHub Pages** | A free service from GitHub that hosts your website. |
| **GitHub Actions** | Automated workflow that runs every time you push — builds and publishes your site. |
| **Astro** | The framework your blog is built with. Turns markdown files into a website. |
| **Markdown** | A simple text format with headings, lists, links etc. (`.md` files). All blog posts are markdown. |
| **DNS** | The internet's phone book — maps `revforge.blog` to GitHub's servers. |
| **CNAME file** | A file (`public/CNAME`) that tells GitHub Pages which custom domain to use. |
| **HTTPS** | The encrypted, padlocked version of HTTP. Yours is automatic and free. |

---

## 4. Adding a new blog post

You have three ways. Pick whichever is most comfortable.

### Option A — GitHub website (no terminal, recommended for now)

1. Go to https://github.com/Revforge-star/revforge-star.github.io
2. Click into the folder path: `src` → `content` → `blog`
3. Click the **"Add file"** button (top right) → **"Create new file"**
4. In the filename box, type something like `my-first-post.md` (use dashes, lowercase, end with `.md`)
5. In the editor below, paste this template and edit:

   ```markdown
   ---
   title: 'My First Real Post'
   description: 'Short description shown on the homepage card and in search results.'
   pubDate: 'Jun 03 2026'
   category: 'Salesforce CPQ'
   readingTime: '5 min read'
   ---

   Write your post here in markdown.

   ## A section heading

   - bullet
   - another bullet

   [A link](https://example.com)
   ```

6. Scroll down → write a "Commit message" like `Add my first post` → click **"Commit changes"** → confirm.
7. Wait ~1-2 minutes. Your post appears on https://revforge.blog/ automatically.

### Option B — VS Code on your Mac (some setup, easier for big edits)

1. Open VS Code
2. **File → Open Folder** → pick `~/Desktop/revforge-star.github.io`
3. In the file tree on the left, navigate to `src/content/blog/`
4. Right-click on the `blog` folder → **New File** → name it `my-post.md`
5. Paste the template from Option A, edit it, save (`Cmd+S`)
6. Click the **Source Control icon** in the left sidebar (looks like a branching tree)
7. Type a commit message at the top, click the **✓ Commit** button
8. Click **... → Push** (or click the sync arrows in the bottom-left status bar)

### Option C — Terminal

```bash
cd ~/Desktop/revforge-star.github.io
# Create your post:
code src/content/blog/my-post.md   # or use any editor
# Once edited and saved:
git add -A
git commit -m "Add my first post"
git push
```

**Frontmatter fields explained** (the stuff between the `---` lines at the top of a post):

| Field | Required? | Example |
|---|---|---|
| `title` | yes | `'What is Salesforce CPQ?'` |
| `description` | yes | `'A beginner-friendly explanation.'` |
| `pubDate` | yes | `'Jun 03 2026'` |
| `category` | no | `'Salesforce CPQ'` (shows as colored label on homepage cards) |
| `readingTime` | no | `'5 min read'` |
| `updatedDate` | no | `'Jun 10 2026'` (shows if a post has been updated) |
| `heroImage` | no | `'./hero.jpg'` (image at top of the post) |

---

## 5. Embedding a video

You do **not** upload video files to GitHub. The right pattern is:

1. **Upload your video to YouTube or Vimeo** (free, they handle the streaming).
2. On YouTube, click the **Share** button → **Embed** → copy the `<iframe>` HTML.
3. Paste that `<iframe>` directly into a blog post markdown file, or into the `src/pages/videos.astro` file.

Example — inside a blog post:

```markdown
Here's a walkthrough video:

<iframe
  width="560"
  height="315"
  src="https://www.youtube.com/embed/VIDEO_ID_HERE"
  frameborder="0"
  allowfullscreen></iframe>
```

Save, commit, push (or use the GitHub web editor) — your video appears on the page.

---

## 6. Previewing changes locally (optional)

This is **optional** but useful for bigger changes — it lets you see your site update in real-time as you save files, without pushing anything to GitHub.

```bash
cd ~/Desktop/revforge-star.github.io
npm run dev
```

This opens a local preview at http://localhost:4321/. Edit files → save → browser auto-refreshes. Press `q` then Enter in the terminal to stop.

When you're happy, commit and push as usual.

---

## 7. Updating things that aren't blog posts

| What | Where to edit it |
|---|---|
| Site title (browser tab + header brand) | `src/consts.ts` → `SITE_TITLE` |
| Site description (SEO + social previews) | `src/consts.ts` → `SITE_DESCRIPTION` |
| Brand tagline under the title | `src/consts.ts` → `SITE_TAGLINE` |
| Big hero heading on the homepage | `src/consts.ts` → `HERO_HEADING` |
| Hero subtitle on the homepage | `src/consts.ts` → `HERO_SUBTITLE` |
| "About Me" short bio on the homepage | `src/consts.ts` → `ABOUT_BIO` |
| Hero image (the desk/laptop photo) | URL in `src/pages/index.astro` — find `HERO_IMAGE` and change it |
| Profile photo (avatar) | Replace `public/images/profile-placeholder.svg` with your photo, or change the `src=` references in `src/pages/index.astro` and `src/pages/about.astro` |
| Navigation links (Home / Blog / Videos / About) | `src/components/Header.astro` |
| Footer links and copyright | `src/components/Footer.astro` |
| About page content | `src/pages/about.astro` |
| Videos page content | `src/pages/videos.astro` |
| Colors / fonts / general styling | `src/styles/global.css` and the `<style>` block at the bottom of each `.astro` page |

---

## 8. Account security (already done — keep it that way)

- ✅ **GitHub 2FA** is on. Don't disable it.
- ✅ **Porkbun 2FA** is on. Don't disable it.
- ✅ The repo is **public** but **only you can push** to it (writes require your GitHub login).

**Things to do periodically:**
- Save your 2FA recovery codes somewhere safe if you haven't (lose your phone → these get you back in).
- Don't share your GitHub password.
- Don't paste the contents of `~/.gitconfig` or your terminal output containing tokens anywhere public.

---

## 9. Domain renewal — important

Your domain expires **2027-06-03**. If you let it expire, the site stops loading at revforge.blog.

**Action:** Sign in to Porkbun → Account → Domains → make sure **Auto-Renew is ON** for revforge.blog. Keep your credit card on file current.

Porkbun emails you reminders ~30 days before expiry. Don't ignore those.

---

## 10. What's in this folder (file map)

```
revforge-star.github.io/
├── .github/
│   └── workflows/
│       └── deploy.yml          ← The auto-deploy workflow (don't edit unless you know what you're doing)
├── public/
│   ├── CNAME                   ← Tells GitHub Pages your domain is revforge.blog (one line)
│   ├── favicon.svg             ← The little icon in the browser tab
│   └── images/
│       └── profile-placeholder.svg   ← Replace with your headshot
├── src/
│   ├── assets/                 ← Images you reference from inside posts
│   ├── components/
│   │   ├── Header.astro        ← Site header / nav
│   │   ├── Footer.astro        ← Site footer
│   │   └── ...
│   ├── content/
│   │   └── blog/
│   │       ├── what-is-salesforce-cpq.md       ← Placeholder post — edit me
│   │       ├── the-complete-quote-to-cash-process.md
│   │       └── how-ai-is-transforming-deal-desk.md
│   ├── layouts/
│   │   └── BlogPost.astro      ← The template every blog post is rendered in
│   ├── pages/
│   │   ├── index.astro         ← Homepage
│   │   ├── about.astro
│   │   ├── videos.astro
│   │   └── blog/
│   │       ├── index.astro     ← Blog listing page
│   │       └── [...slug].astro ← Renders an individual post
│   ├── styles/
│   │   └── global.css          ← Global styling
│   ├── consts.ts               ← Site title, description, headings — edit me often
│   └── content.config.ts       ← Schema for blog post frontmatter (the available fields)
├── astro.config.mjs            ← Astro framework config (site URL, integrations)
├── package.json                ← Lists the project's dependencies
└── GUIDE.md                    ← This file
```

---

## 11. Common problems

### "I committed but the site didn't change"

- Wait 1-2 minutes. The deploy isn't instant.
- Check the workflow status: https://github.com/Revforge-star/revforge-star.github.io/actions — if the latest run shows a red ✗, click into it and read the error.
- Hard refresh your browser: `Cmd+Shift+R` (Mac) — sometimes the old version is cached.

### "The deploy workflow failed"

- 99% of the time it's a YAML formatting issue or a problem in a blog post's frontmatter.
- Click into the failed run on GitHub → click the failing step → read the error message. It'll usually quote the exact line.

### "I broke something and want to undo it"

- On GitHub: open the repo → Commits → find the commit before things broke → click "..." → "Revert this commit". This creates a new commit that undoes the bad one.
- Or in terminal: `git revert HEAD` undoes the most recent commit.

### "I forgot my git config — when I try to commit it complains about identity"

```bash
git config --global user.name "Rushikesh Kotwal"
git config --global user.email "282337102+Revforge-star@users.noreply.github.com"
```

### "I changed the domain in Porkbun and the site doesn't load anymore"

- Don't change the DNS records you set up. The 4 A records + the `www` CNAME need to stay exactly as they are. If you accidentally deleted them, re-add them (see Section 12 below).

---

## 12. DNS records reference (in case you ever need to re-enter them)

At Porkbun → revforge.blog → DNS:

| Type | Host | Answer |
|---|---|---|
| A | (blank or `@`) | 185.199.108.153 |
| A | (blank or `@`) | 185.199.109.153 |
| A | (blank or `@`) | 185.199.110.153 |
| A | (blank or `@`) | 185.199.111.153 |
| CNAME | www | revforge-star.github.io |

These are GitHub Pages' official IPs (same for every Pages user).

---

## 13. Helpful links

- Astro docs: https://docs.astro.build/
- Markdown reference: https://www.markdownguide.org/cheat-sheet/
- Your repo: https://github.com/Revforge-star/revforge-star.github.io
- Your deploy history: https://github.com/Revforge-star/revforge-star.github.io/actions
- GitHub Pages status: https://www.githubstatus.com/
- Porkbun: https://porkbun.com

---

## 14. Open follow-ups

Things mentioned during setup that aren't built yet:

- **Newsletter signup** — the form on the homepage currently just shows an alert. Wire it to a service like Buttondown ($0 free tier), ConvertKit, or Mailchimp when you're ready.
- **Profile photo** — currently a generic silhouette. Replace `public/images/profile-placeholder.svg` with your headshot.
- **Hero image** — currently a stock Unsplash photo. Swap by editing `HERO_IMAGE` in `src/pages/index.astro`.
- **First real blog post** — the three current posts are placeholders. Edit or delete them.

When you're ready for any of these, ask and we'll do them in a focused session.
