# Portfolio – GitHub Pages

Personal portfolio for Syed Muhammad Hamza, Cloud & DevOps Engineer.
Static site hosted on **GitHub Pages** and deployed by **GitHub Actions** on every push to `main`.

```
site/index.html                         the website
site/404.html                           sends broken links back to the home page
site/images/                            portrait, architecture diagrams, link-preview image
.github/workflows/deploy-pages.yml      GitHub Actions deployment pipeline
```

Only the `site/` folder is published. This README and the workflow stay out of the live site.

---

## 0. Before you publish

Open `site/index.html` and search for `EDIT:` (two places):

1. **Contact section** – replace `you@example.com` and the LinkedIn link with your own.
2. **Link-preview tags** – replace `https://YOUR-DOMAIN` (canonical, `og:url`, `og:image`) with your final address, e.g. `https://<your-username>.github.io` or your own domain. LinkedIn uses these for the preview card.

## 1. Repository

Live site: **https://syedhamza161.github.io/portfolio/**

## 1a. (Reference) Creating the repository

Name the repository **`<your-username>.github.io`** (exactly your GitHub username).
Your site is then served at `https://<your-username>.github.io/` with no extra path.
Any other name works too, but the address becomes `https://<your-username>.github.io/<repo-name>/`.

Make it **Public**. GitHub Pages on a private repository needs a paid plan (GitHub Pro or above).

## 2. Push the files

From this folder:

```bash
git init
git add .
git commit -m "Portfolio site"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-username>.github.io.git
git push -u origin main
```

Make sure the hidden `.github` folder is included.

## 3. Turn on GitHub Pages

Repository → **Settings → Pages** → under **Build and deployment**, set **Source** to **GitHub Actions**.

Then go to **Actions → Deploy portfolio to GitHub Pages → Run workflow** (or push any change).
When it shows a green tick, the run summary shows your live URL.

## 4. Add your own domain (optional, free HTTPS)

Buy a domain (e.g. `syedhamza.dev`). Then in **Settings → Pages → Custom domain**, enter it and click **Save**.
No `CNAME` file is needed when deploying with GitHub Actions.

At your domain provider, add:

| Type | Name | Value |
|---|---|---|
| CNAME | `www` | `<your-username>.github.io` |
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| AAAA | `@` | `2606:50c0:8000::153` |
| AAAA | `@` | `2606:50c0:8001::153` |
| AAAA | `@` | `2606:50c0:8002::153` |
| AAAA | `@` | `2606:50c0:8003::153` |

When the DNS check passes, tick **Enforce HTTPS** (can take up to 24 hours to become available).
Recommended: verify the domain under your GitHub profile **Settings → Pages** so nobody else can claim it.

Then update `https://YOUR-DOMAIN` in `site/index.html` and push.

## 5. Updating the site

Edit `site/index.html` or add images → commit → push to `main`. GitHub Actions redeploys in about a minute.

## Notes

- GitHub Pages can't send custom HTTP headers, so the security policy (CSP) is set with a `<meta>` tag inside `index.html`.
- The site is fully static: no server, database or cost.
