# Deploy to King's Landing — Example

A minimal example showing how to deploy a static site to [King's Landing](https://kingslanding.io) via GitHub Actions.

## How It Works

Every push to `main` triggers a GitHub Actions workflow that deploys this directory to King's Landing using the [deploy-to-kingslanding](https://github.com/boxshopio/deploy-to-kingslanding) action.

## Try It Yourself

1. Fork this repo
2. Create a project on [King's Landing](https://kingslanding.io)
3. Generate a deploy key from your project settings
4. Add the key as a GitHub secret: Settings > Secrets > `KL_DEPLOY_KEY`
5. Push a change — your site will deploy automatically

## Customize

- Replace `index.html` and `style.css` with your own files
- Update `project` in `.github/workflows/deploy.yml` to match your King's Landing project name
- For Vite/React/Next.js builds, add a build step before the deploy step and set `directory: ./dist`
