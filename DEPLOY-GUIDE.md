# How to Deploy Your Portfolio Site

This guide gets your site live on the internet using GitHub + Cloudflare Pages. You'll need about 15 minutes.

---

## Step 1: Install Node.js (if you don't have it)

1. Open **Terminal** on your Mac (press `Cmd + Space`, type "Terminal", hit Enter)
2. Type this and press Enter:
   ```
   node --version
   ```
3. If you see a version number (like `v20.x.x`), skip to Step 2. If you see "command not found," go to [nodejs.org](https://nodejs.org), download the **LTS** version, and install it.

---

## Step 2: Download and unpack your project

1. Find the file `nick-daly-portfolio.tar.gz` that you downloaded from this session
2. In Terminal, run these commands one at a time (copy and paste each line):
   ```
   cd ~/Desktop
   ```
   ```
   tar -xzf ~/Downloads/nick-daly-portfolio.tar.gz
   ```
   ```
   cd portfolio-site
   ```
   ```
   npm install
   ```

3. To preview the site locally, run:
   ```
   npm run dev
   ```
   Then open your browser to **http://localhost:4321** — you should see your site! Press `Ctrl + C` in Terminal when you're done looking.

---

## Step 3: Push to GitHub

1. Go to [github.com/new](https://github.com/new) in your browser
2. Name the repo: `portfolio-site` (or whatever you like)
3. Leave it as **Public**, don't check any boxes, and click **Create repository**
4. GitHub will show you some commands. Ignore those. Instead, in Terminal, run these one at a time:
   ```
   git init
   ```
   ```
   git add -A
   ```
   ```
   git commit -m "Initial portfolio site"
   ```
   ```
   git branch -M main
   ```
   ```
   git remote add origin https://github.com/YOUR-GITHUB-USERNAME/portfolio-site.git
   ```
   (Replace `YOUR-GITHUB-USERNAME` with your actual GitHub username)
   ```
   git push -u origin main
   ```

   If prompted, enter your GitHub credentials. (If you use two-factor auth, you'll need a [personal access token](https://github.com/settings/tokens) instead of your password.)

---

## Step 4: Connect Cloudflare Pages

1. Go to [dash.cloudflare.com](https://dash.cloudflare.com) and log in
2. In the left sidebar, click **Workers & Pages**
3. Click **Create** then the **Pages** tab then **Connect to Git**
4. Select your GitHub account and the `portfolio-site` repo
5. Configure the build settings:
   - **Framework preset:** Astro
   - **Build command:** `npm run build`
   - **Build output directory:** `dist`
6. Click **Save and Deploy**

Cloudflare will build your site in about 1-2 minutes. When it's done, you'll get a URL like `portfolio-site.pages.dev`.

---

## Step 5: Use your own domain (optional)

If you want this at `nickdalycreative.com` or a subdomain:

1. In Cloudflare Pages, go to your project then **Custom domains**
2. Click **Set up a custom domain**
3. Enter your domain (e.g., `nickdalycreative.com`)
4. If your domain is already on Cloudflare, the DNS records will be added automatically
5. Wait a few minutes for it to propagate then your site is live!

---

## Editing your site later

To update content:

1. Edit the files in `src/pages/` using any text editor (VS Code is free and popular)
2. Preview changes locally with `npm run dev`
3. When you're happy, push to GitHub:
   ```
   git add -A
   ```
   ```
   git commit -m "Update content"
   ```
   ```
   git push
   ```
4. Cloudflare Pages will automatically rebuild and deploy within a minute or two.

---

## What to customize first

- **Your real bio** edit `src/pages/about.astro`
- **Your real projects** edit `src/pages/work.astro`
- **Your real publications** edit `src/pages/publications.astro`
- **Education and affiliations** edit the sidebar in `src/pages/about.astro`
- **Social links** edit `src/pages/contact.astro`
- **Colors and fonts** edit `src/styles/global.css` (the variables at the top)
- **Your CV PDF** drop it in the `public/` folder and update the link in `about.astro`
