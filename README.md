# Deploy to King's Landing — Example

A minimal example showing how to deploy a static site to [King's Landing](https://kingslanding.io) via GitHub Actions.

**Live deploy:** [demo.kingslanding.io](https://demo.kingslanding.io) — redeployed on every push to `main`.

## How It Works

Every push to `main` triggers a GitHub Actions workflow that deploys this directory to King's Landing using the [deploy-to-kingslanding](https://github.com/boxshopio/deploy-to-kingslanding) action.

The deploy step is gated on the `KL_DEPLOY_KEY` secret being present:

```yaml
- name: Deploy to King's Landing
  if: ${{ secrets.KL_DEPLOY_KEY != '' }}
  uses: boxshopio/deploy-to-kingslanding@v1
  with:
    project: demo
    directory: .
    deploy-key: ${{ secrets.KL_DEPLOY_KEY }}
```

If you fork this repo without configuring a deploy key, the workflow will still run successfully — it just skips the deploy step instead of failing.

## Try It Yourself

1. Fork this repo
2. Create a project on [King's Landing](https://kingslanding.io) (or run `kl deploy . -p <name> --create` from the CLI)
3. Generate a deploy key: `kl deploy-key create -p <name>`
4. Add the key as a GitHub secret: Settings > Secrets and variables > Actions > `KL_DEPLOY_KEY`
5. Update `project:` in `.github/workflows/deploy.yml` to match your project name
6. Push a change — your site deploys automatically

## Customize

- Replace `index.html` and `style.css` with your own files
- For Vite/React/Next.js builds, add a build step before the deploy step and set `directory: ./dist`
