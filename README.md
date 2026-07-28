# Social HR — public product documentation site

This repository hosts the **public** [Social HR product documentation](https://social-team-organization.github.io/social-hr-docs/) on GitHub Pages.

The **source of truth** for documentation content is the private [`Social-Team-Organization/social-hr`](https://github.com/Social-Team-Organization/social-hr) repository (`docs/product/`).

## Why a separate public repo?

GitHub Pages on **private** repositories requires GitHub Enterprise or Pro. This public repo exists only to build and publish the product docs site.

## One-time setup

1. Create a **public** repository on GitHub named `social-hr-docs` under `Social-Team-Organization`.
2. From the private `social-hr` repo, **sync** (copies product docs **and** terminology files), then push:

   ```bash
   ./scripts/sync-product-docs.sh
   cd social-hr-docs
   git init
   git add .
   git commit -m "Initial product docs site"
   git branch -M main
   git remote add origin git@github.com:Social-Team-Organization/social-hr-docs.git
   git push -u origin main
   ```

   **Required in the public repo** (created by the sync script):

   - `docs/product/` (all pages and images)
   - `docs/SOCIAL_HR_TERMS_AR.md`
   - `docs/SOCIAL_HR_TERMS_GLOSSARY.md`

3. On GitHub → **Settings** → **Pages** → set **Source** to **GitHub Actions**.
4. Re-run the **Deploy to GitHub Pages** workflow if needed.

**Live URL:** https://social-team-organization.github.io/social-hr-docs/

## Updating docs

After editing docs in the private `social-hr` repo:

```bash
# From social-hr repository root
./scripts/sync-product-docs.sh
cd social-hr-docs
git add -A
git commit -m "Sync product docs"
git push
```

GitHub Actions rebuilds and deploys automatically on push to `main`.

## Local preview

```bash
pip install -r requirements-docs.txt
mkdocs serve
# http://127.0.0.1:8000/social-hr-docs/
```
