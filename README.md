# Sajid Mahadi Bhuiyan — Portfolio

An interactive graphic-designer portfolio built with **React**, **Vite**, **TypeScript** and **Tailwind CSS**.

🔗 **Live demo:** https://`<your-username>`.github.io/`<your-repo-name>`/

---

## Local development

```bash
npm install
npm run dev     # start the dev server
npm run build   # production build → dist/
npm run preview # preview the production build locally
```

---

## Deploy to GitHub Pages (free hosting)

The repo is pre-configured with a GitHub Actions workflow that builds and publishes the site automatically every time you push to `main`.

### 1. Create the repository on GitHub

1. Go to https://github.com/new
2. Repository name — anything you like, e.g. `portfolio`
3. Set it to **Public** (required for free GitHub Pages)
4. **Do not** initialise with README, .gitignore, or licence (this repo already has them)
5. Click **Create repository**

### 2. Push this project

From this folder on your computer:

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/<YOUR-USERNAME>/<YOUR-REPO>.git
git push -u origin main
```

### 3. Turn on GitHub Pages

1. Open your repository on GitHub
2. **Settings → Pages**
3. Under **Build and deployment → Source**, select **GitHub Actions**
4. That's it — no branch selection needed

### 4. Your site is live 🎉

After the first push, GitHub Actions will build and deploy automatically.
You'll find the live URL at the top of the Pages settings page, typically:

```
https://<YOUR-USERNAME>.github.io/<YOUR-REPO>/
```

Every subsequent push to `main` triggers a fresh deploy.

---

## Important: choose the right URL type

There are two kinds of GitHub Pages sites. The workflow works for both — you just need one small change for the first type.

### Option A — Project site (default)  →  `https://<user>.github.io/<repo>/`

✅ **Already configured** — no changes needed.
The workflow reads your repo name and sets the base path automatically.

### Option B — User/organization site  →  `https://<user>.github.io/`

This requires a repository named **exactly** `<your-username>.github.io`.

To use this, edit `.github/workflows/deploy.yml` and change the Build step to:

```yaml
- name: Build
  run: npm run build
  env:
    BASE_PATH: /
```

---

## Using a custom domain (optional)

1. In **Settings → Pages → Custom domain**, enter your domain (e.g. `sajidmahadi.com`)
2. In your DNS provider, create a **CNAME** record pointing to `<your-username>.github.io`
3. Update the workflow so `BASE_PATH` is `/`:
   ```yaml
   env:
     BASE_PATH: /
   ```
4. Create a file `public/CNAME` containing your domain (one line, no trailing slash):
   ```
   sajidmahadi.com
   ```
   Vite will copy it to `dist/CNAME` on every build, which is what GitHub Pages needs.

---

## Updating the content

**Contact links** — edit `src/components/Contact.tsx`:
- `EMAIL_LINK` — Gmail compose URL
- `WHATSAPP_LINK` — WhatsApp chat URL

**Projects** — edit `src/data/projects.ts`. Each entry is a self-contained object:
```ts
{
  id: "my-new-project",
  title: "Project name",
  category: "Branding",
  year: "2025",
  summary: "One-line summary",
  description: "Longer overview…",
  cover: "images/my-cover.jpg",
  gallery: [ /* up to ~4 images */ ],
  tags: ["Identity", "Packaging"],
  featured: true,
}
```
Drop new images into `public/images/` and reference them via `images/<name>.jpg`.

---

## Tech stack

- **React 19** with TypeScript
- **Vite 7** (bundled to a single `dist/index.html`)
- **Tailwind CSS 4**
- **motion/react** for animations
- **Lenis** for smooth scrolling
- **Inter** + **Inter Tight** from Google Fonts
