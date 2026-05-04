# CLAUDE.md - deploy-to-kingslanding-example

## Project Overview
Minimal example demonstrating static site deployment to King's Landing via GitHub Actions. Reference repo -- not a library or application.

## Structure
- `index.html` / `style.css` -- sample static site
- `.github/workflows/deploy.yml` -- deploys to King's Landing on push to `main`
- `.github/workflows/pr-size.yml` -- labels PRs by size (managed by `bs hooks`)
- `.pre-commit-config.yaml` -- gitleaks + conventional commits

## How It Works
On every push to `main`, the deploy workflow checks out the repo and runs `boxshopio/deploy-to-kingslanding@v1`, which uploads the site directory to King's Landing using the `KL_DEPLOY_KEY` secret.

## Conventions
- Commit messages follow conventional commits (`feat`, `fix`, `chore`, etc.)
- No build step -- files are deployed as-is from the repo root

## Before Committing
- `pre-commit run --all-files`
- Commit messages must pass `conventional-pre-commit`
