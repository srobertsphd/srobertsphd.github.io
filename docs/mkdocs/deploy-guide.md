# Deploying MkDocs to your GitHub Pages domain

Every GitHub account gets one special domain for hosting web content. It follows the format `yourusername.github.io`. The cool thing is you can use this domain to host an MkDocs site without having to add your repository name to the URL.

I recently figured out how to do this properly, and wanted to document the process for anyone else trying to deploy an MkDocs site to their main GitHub Pages domain.

Here's what you need to know:

## Prerequisites

- A GitHub account
- A repository named `username.github.io` (replace username with your GitHub username)
- MkDocs installed locally

## Step 1: Configure Your MkDocs Site

Ensure your `mkdocs.yml` file has the correct site URL:

```yaml
site_name: Your Site Name
site_description: Your site description
site_url: https://username.github.io/
```

## Step 2: Deploy to GitHub Pages

Deploy your site using the MkDocs gh-deploy command:

```bash
mkdocs gh-deploy --force
```

This command:
- Builds your site to a temporary directory (usually `site/`)
- Creates or updates a branch called `gh-pages`
- Places all built files at the root of the `gh-pages` branch
- Pushes the changes to GitHub

The `--force` flag ensures a clean deployment by completely replacing the contents of the `gh-pages` branch.

## Step 3: Configure GitHub Pages Settings

1. Go to your GitHub repository
2. Click on "Settings"
3. In the left sidebar, click on "Pages"
4. Under "Build and deployment" > "Source", select:
   - Deploy from a branch
   - Branch: gh-pages
   - Folder: / (root)
5. Click "Save"

## Step 4: Wait for Deployment

GitHub will start building your site. This typically takes a few minutes. Once complete, your site will be available at `https://username.github.io`.

## Troubleshooting

- **404 Error**: Make sure your GitHub Pages settings are correctly pointing to the gh-pages branch
- **Cache Issues**: Try clearing your browser cache or using incognito mode
- **Deployment Errors**: Check the Actions tab in your GitHub repository for any error messages

## Updating Your Site

Whenever you make changes to your site:

1. Make your changes locally
2. Test with `mkdocs serve`
3. When ready, run `mkdocs gh-deploy --force` again
4. Wait a few minutes for GitHub to update your site

That's it! Your MkDocs site should now be available at your GitHub username domain. 