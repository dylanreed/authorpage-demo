<!-- ABOUTME: Project README and complete setup guide for AuthorPage. -->
<!-- ABOUTME: Covers both CLI and browser-based setup paths for fiction authors. -->

# AuthorPage

**A free, beautiful website for authors — set up in minutes, hosted forever on GitHub Pages.**

No coding required. Seriously.

---

## What is this?

AuthorPage gives you a professional author website with your books, bio, blog, and contact info. Pick a theme, fill in your details, and you're live. Free hosting via GitHub Pages — no monthly fees, no subscriptions, no catch.

---

## Choose Your Adventure

There are two ways to get started. Pick whichever feels comfortable:

- **The Terminal Way** — For folks who are comfortable with a command line. Fast and automated.
- **The Browser Way** — For everyone else. You never leave your web browser. No software to install.

Both paths end up in the same place: your author website, live on the internet.

---

## Quick Start: The Terminal Way

This path uses a setup script that walks you through everything interactively.

### Prerequisites

- [Git](https://git-scm.com/downloads) installed on your computer
- [GitHub CLI](https://cli.github.com/) (`gh`) installed and authenticated

### Steps

1. **Clone the template and create your repo:**

   ```bash
   gh repo create my-author-site --template YOUR-TEMPLATE-ORG/authorpage --public --clone
   cd my-author-site
   ```

2. **Run the setup script:**

   ```bash
   ./setup.sh
   ```

3. **Follow the prompts.** The script will ask for your name, tagline, bio, and which theme you want. It fills in the config files for you.

4. **Push and you're live.** The script commits your changes and pushes. GitHub Actions builds your site automatically.

That's it. Your site will be available at `https://YOUR-USERNAME.github.io/my-author-site/` within a couple of minutes.

---

## Quick Start: The Browser Way

You can set up your entire site without leaving GitHub's website. No software to install, no terminal, no command line.

### Prerequisites

- A GitHub account ([sign up here](https://github.com/signup) — it's free)

### Step 1: Create your site from the template

At the top of this repository's page, look for the green **"Use this template"** button. Click it, then choose **"Create a new repository."**

### Step 2: Name your repository

- Give it a name like `my-author-site` (or anything you want)
- Make sure it's set to **Public** (required for free GitHub Pages hosting)
- Click **"Create repository"**

### Step 3: Open the setup checklist

In your brand new repository:

- Click the **Issues** tab (near the top of the page, next to "Code")
- You should see an issue called **"Set up my author site"**
- Open it — this is your step-by-step checklist

### Step 4: Follow the checklist

The issue walks you through everything:

- Picking a theme
- Adding your name, bio, and photo
- Adding your books
- Uploading cover images

Each step tells you exactly which file to edit and what to change. You can check off each task as you complete it.

### Step 5: Visit your site!

Once you've made your first edit, GitHub automatically starts building your site. Give it about 60 seconds, then visit:

```
https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/
```

If you see a 404 error, go to your repository's **Settings** > **Pages** and make sure the Source is set to **"GitHub Actions"**.

---

## Choosing a Theme

AuthorPage comes with three themes. You can always switch later.

### Inkwell

Clean, literary, lots of white space. Serif fonts give it a bookish feel. Perfect for literary fiction and poetry.

### Paperback

Bold and eye-catching. Your book covers take center stage. Great for genre fiction — romance, thriller, sci-fi, fantasy.

### Typewriter

Dark and moody with a retro vibe. Monospace fonts and vintage textures. Ideal for horror, noir, or anyone who wants personality.

### How to switch themes

Open `config.yaml` and change the `theme:` line to one of: `inkwell`, `paperback`, or `typewriter`.

```yaml
theme: "paperback"
```

Save the file (or click "Commit changes" if you're in the browser), and your site will rebuild with the new look.

---

## Customizing Your Site

### Your Profile

Open `data/site.yaml` to edit your personal information. Here's what each field does:

- **name** — Your full name as you want it displayed on the site
- **tagline** — A short line shown under your name on the home page (e.g., "Author of The Midnight Garden")
- **bio** — A paragraph about you, shown on the About page
- **photo** — Path to your author photo (upload the image to `static/images/` and set this to `/images/your-photo.jpg`)
- **social** — Links to your social media profiles. Delete any you don't use.
- **contact_email** — Your email address, shown on the Contact page

### Your Books

Open `data/books.yaml` to manage your book catalog. Books appear on both the home page (if `featured: true`) and the Books page.

See [Adding a New Book](#adding-a-new-book) below for a copy-paste template.

### Your Blog

Blog posts live in the `content/blog/` folder. Each post is a Markdown file (`.md`) with a small block of metadata at the top.

See [Writing a Blog Post](#writing-a-blog-post) below for a copy-paste template.

---

## Adding a New Book

Copy the block below, paste it at the top of `data/books.yaml` (right after the comment lines), and fill in your details:

```yaml
- title: "Your Book Title"
  # Path to the cover image (upload to static/images/ first)
  cover: "/images/your-cover.jpg"
  # A short one-line hook
  tagline: "A story about..."
  # A longer description (2-3 sentences work well)
  description: "What your book is about. This shows up on the Books page."
  # The year your book was published
  published: 2025
  # Where people can buy it (add as many links as you want)
  buy_links:
    - label: "Amazon"
      url: "https://amazon.com/dp/your-book-id"
    - label: "Bookshop.org"
      url: "https://bookshop.org/p/books/your-book-id"
  # Set to true for the ONE book you want featured on the home page
  featured: false
```

Newest books should go at the top of the file. To remove a book, delete its entire block (from the `-` to the next `-`).

---

## Writing a Blog Post

Create a new file in the `content/blog/` folder. Name it something descriptive with dashes, like `my-new-release.md`. Paste this template and fill it in:

```markdown
---
title: "Your Post Title"
date: 2025-01-15
description: "A short summary shown in post listings."
---

Write your post here. You can use **bold**, *italics*, and all the usual
Markdown formatting.

## Subheadings work too

Just use ## for sections. Keep writing, and when you save (or commit),
your site updates automatically.
```

Posts show up on the Blog page sorted by date, newest first.

---

## FAQ

**Can I use my own domain?**

Yes! GitHub Pages supports custom domains. Go to your repository's **Settings** > **Pages** > **Custom domain** and follow the instructions. GitHub has a [step-by-step guide](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site).

**Can I switch themes later?**

Yes, just change the `theme:` line in `config.yaml`. Your content stays the same — only the look changes.

**How do I preview my site locally?**

Install [Hugo](https://gohugo.io/installation/) and run:

```bash
hugo server
```

Then open `http://localhost:1313` in your browser. Changes show up instantly.

**How do I delete a book?**

Open `data/books.yaml` and remove the entire block for that book — from the `-` line all the way to just before the next `-` line.

**Something broke!**

No worries — open an [issue](../../issues) and describe what you see. We'll help you sort it out.

---

## For Developers: Adding a Theme

Want to create a new theme? Every theme must implement the same set of layouts and partials defined in the theme contract. See [`themes/README.md`](themes/README.md) for the full specification, including required directory structure, template variables, and the theme manifest format.

Themes are auto-discovered from `themes/*/theme.yaml` — drop in a folder that follows the contract, and it just works.

---

*Built with [Hugo](https://gohugo.io/). Hosted free on [GitHub Pages](https://pages.github.com/).*
