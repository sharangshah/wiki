# Setup Guide — Sharang's Personal Wiki

Total time: ~10 minutes. No coding required.

---

## What You Have

A complete wiki project, ready to deploy. The folder `sharang-wiki/` contains everything — branded pages, custom styling, domain structure, version history. You just need to connect two free services.

---

## Step 1 — Upload to GitHub (5 minutes)

You already have a GitHub account. Now create a repository to hold the wiki:

1. Go to **github.com/new**
2. Fill in:
   - Repository name: `sharang-wiki` (or whatever you prefer)
   - Description: `Personal knowledge base`
   - Visibility: **Private** (important — keeps source files private)
   - Do NOT initialise with a README (we already have files)
3. Click **Create repository**
4. You'll see a page with setup instructions. **Don't do anything on that page yet** — come back to me and I'll push the files for you.

Alternatively, if you'd like to upload manually:
1. On the empty repo page, click **"uploading an existing file"**
2. Drag and drop the entire contents of the `sharang-wiki` folder
3. Click **Commit changes**

---

## Step 2 — Connect Cloudflare Pages (5 minutes)

1. Go to **dash.cloudflare.com** and sign up / log in
2. In the sidebar, click **Workers & Pages**
3. Click **Create** → **Pages** → **Connect to Git**
4. Authorise Cloudflare to access your GitHub account
5. Select the `sharang-wiki` repository
6. Configure the build:
   - **Build command**: `pip install mkdocs mkdocs-material && mkdocs build`
   - **Build output directory**: `site`
   - **Root directory**: `/` (leave default)
7. Click **Save and Deploy**

Cloudflare will build and deploy your wiki. It takes about 60 seconds.

---

## Step 3 — Your Wiki is Live

After deployment, Cloudflare gives you a URL like:

    https://sharang-wiki-abc.pages.dev

This is your wiki. It's:
- **Not indexed** by search engines (robots.txt + noindex meta tags block all crawlers)
- **Accessible to anyone** with the exact link (unlisted model)
- **Auto-deploys** whenever files are updated on GitHub

---

## How to Share a Page

1. Open any page on your wiki
2. Copy the URL from the browser address bar
3. Send the link to whoever you want — they can read it immediately, no login needed

---

## How to Edit in the Browser

1. Go to your GitHub repository (github.com/YOUR_USERNAME/sharang-wiki)
2. Navigate to `docs/` → find the page you want to edit (e.g., `docs/wealth/equity-research/index.md`)
3. Click the **pencil icon** (Edit this file)
4. Make your changes in the markdown editor
5. Scroll down, write a commit message like "Updated KEI thesis — upgraded conviction"
6. Click **Commit changes**
7. Cloudflare auto-deploys in ~60 seconds — your wiki is updated

---

## How Updates Work via Claude

1. Tell me what's changed in your thinking (e.g., "I want to add a page on KEI Industries equity research")
2. I create or update the markdown files
3. I commit the changes with a descriptive message
4. Cloudflare auto-deploys

The commit history on GitHub becomes your **version control** — every change is logged with a message explaining what shifted and why.

---

## Optional: Custom Domain

If you want a URL like `wiki.sharang.com` instead of `sharang-wiki-abc.pages.dev`:

1. Buy a domain (Cloudflare Registrar is cheapest, ~$10/year for a .com)
2. In Cloudflare Pages → your project → **Custom domains** → Add domain
3. Cloudflare handles DNS and SSL automatically

---

## Folder Structure Reference

```
sharang-wiki/
├── mkdocs.yml              ← Site configuration and navigation
├── requirements.txt        ← Python dependencies
├── robots.txt              ← Blocks search engine indexing
├── overrides/
│   └── main.html           ← Custom theme (noindex meta tags, footer)
└── docs/
    ├── index.md            ← Home page
    ├── changelog.md        ← Version history of thinking
    ├── stylesheets/
    │   └── brand.css       ← Sharang brand design system
    ├── assets/             ← Logo, favicon, images
    ├── wealth/
    │   ├── index.md
    │   ├── equity-research/
    │   ├── portfolio/
    │   └── macro/
    ├── health/
    │   ├── index.md
    │   ├── ayurveda/
    │   ├── nutrition/
    │   └── fitness/
    ├── psychology/
    ├── geopolitics/
    ├── philosophy/
    └── cross-domain/
```
