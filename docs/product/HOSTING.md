# Hosting & local preview

Product documentation is built with [MkDocs Material](https://squidfunk.github.io/mkdocs-material/).

## Published site (public)

Because the main `social-hr` repository is **private**, GitHub Pages is hosted from a separate **public** repository:

| Item | Value |
|------|--------|
| Public repo | [Social-Team-Organization/social-hr-docs](https://github.com/Social-Team-Organization/social-hr-docs) |
| Live URL | [https://social-team-organization.github.io/social-hr-docs/](https://social-team-organization.github.io/social-hr-docs/) |
| Source content | `docs/product/` in the private `social-hr` repo |

### Publish updates

From the private `social-hr` repository root:

```bash
./scripts/sync-product-docs.sh
cd social-hr-docs
git add -A
git commit -m "Sync product docs"
git push
```

The public repo’s GitHub Actions workflow deploys automatically on push to `main`.

### One-time setup (public repo)

1. Create a **public** GitHub repository named `social-hr-docs`.
2. Run the sync script and push (see [`social-hr-docs/README.md`](https://github.com/Social-Team-Organization/social-hr/blob/main/social-hr-docs/README.md)).
3. **Settings → Pages → Source:** **GitHub Actions**.

## Local preview

From the private repository root:

```bash
pip install -r requirements-docs.txt
mkdocs serve
```

Open [http://127.0.0.1:8000/social-hr/](http://127.0.0.1:8000/social-hr/) (path prefix from `site_url` in `mkdocs.yml`).

Build without serving:

```bash
mkdocs build --strict
```

To preview the **public** site config:

```bash
./scripts/sync-product-docs.sh
cd social-hr-docs
pip install -r requirements-docs.txt
mkdocs serve
# http://127.0.0.1:8000/social-hr-docs/
```

## CI in the private repo

The workflow [`.github/workflows/docs.yml`](https://github.com/Social-Team-Organization/social-hr/blob/main/.github/workflows/docs.yml) **validates** the MkDocs build only — it does not deploy (Pages requires a public repo on the free plan).

Developer (technical) documentation lives in [`docs/README.md`](https://github.com/Social-Team-Organization/social-hr/blob/main/docs/README.md) on GitHub and is not included in the published product site.
