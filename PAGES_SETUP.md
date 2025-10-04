<!--
# SPDX-License-Identifier: Apache-2.0
# SPDX-FileCopyrightText: 2025 The Linux Foundation
-->

# 🌐 GitHub Pages Setup Guide

This guide explains how to enable GitHub Pages for the `gerrit-reports` repository to automatically serve the generated reports as web pages.

## Prerequisites

- Repository admin access to `modeseven-lfit/gerrit-reports`
- GitHub Pages workflow already configured (see `.github/workflows/pages.yaml`)

## Setup Steps

### 1. Enable GitHub Pages

1. Navigate to the repository: <https://github.com/modeseven-lfit/gerrit-reports>
2. Go to **Settings** → **Pages** (in the left sidebar)
3. Under **Source**, select **GitHub Actions**
4. Click **Save**

### 2. Verify Permissions

Ensure the repository has the following permissions configured:

**Repository Settings** → **Actions** → **General**:

- ✅ **Workflow permissions**: "Read and write permissions"
- ✅ **Allow GitHub Actions to create and approve pull requests**: Enabled

### 3. Run Initial Deployment

After enabling GitHub Pages:

1. Go to **Actions** tab
2. Select the "🌐 Deploy to GitHub Pages" workflow
3. Click **Run workflow** → **Run workflow**
4. Wait for the workflow to complete

### 4. Access Your Site

Once deployed, your reports will be available at:

- **Main site**: <https://modeseven-lfit.github.io/gerrit-reports/>
- **Individual reports**: <https://modeseven-lfit.github.io/gerrit-reports/projects/[project-slug]/report.html>

## How It Works

### Automated Workflow

The Pages workflow (`.github/workflows/pages.yaml`) automatically:

1. **Triggers** on every push to the `main` branch (when new reports are published)
2. **Scans** the `projects/` directory for available reports
3. **Updates** the README.md with current project links
4. **Builds** the site using Jekyll
5. **Deploys** to GitHub Pages

### Index Generation

The workflow automatically maintains the project index by:

- Scanning all `projects/*/report.html` files
- Reading project names from `.provenance.json` files
- Generating GitHub Pages URLs for each report
- Updating the README.md with the current project list

### Site Structure

```
https://modeseven-lfit.github.io/gerrit-reports/
├── /                           # Main index (README.md)
├── /projects/onap/report.html  # ONAP project report
├── /projects/opendaylight/report.html  # OpenDaylight report
└── /projects/[slug]/report.html  # Other project reports
```

## Troubleshooting

### Pages Not Updating

If GitHub Pages isn't updating after new reports are published:

1. Check the **Actions** tab for workflow failures
2. Verify the Pages workflow ran after the report publishing
3. Check **Settings** → **Pages** for deployment status

### Reports Not Loading

If report HTML files show as source code:

1. Verify GitHub Pages is enabled with "GitHub Actions" source
2. Check that the `.html` files are in the `projects/` directory
3. Ensure the Pages workflow completed successfully

### Permission Issues

If the workflow fails with permission errors:

1. Check **Settings** → **Actions** → **General**
2. Ensure "Read and write permissions" is enabled
3. Verify the `GITHUB_TOKEN` has sufficient permissions

### Missing Reports in Index

If reports exist but don't appear in the index:

1. Verify `.provenance.json` files exist alongside `report.html`
2. Check the Pages workflow logs for scanning issues
3. Manually trigger the Pages workflow to refresh the index

## Manual Operations

### Force Index Refresh

To manually refresh the project index:

1. Go to **Actions** → "🌐 Deploy to GitHub Pages"
2. Click **Run workflow** → **Run workflow**
3. This will rescan projects and update the index

### Update Site Configuration

To modify the site appearance or behavior:

1. Edit `_config.yml` for Jekyll settings
2. Modify `.github/workflows/pages.yaml` for build logic
3. Update `README.md` template in the workflow for index structure

## Security Notes

- The workflow uses `GITHUB_TOKEN` with minimal required permissions
- Only the `contents: write` permission is used to update the README
- Pages deployment uses the standard GitHub Pages action
- No external tokens or credentials are required

## Maintenance

The GitHub Pages setup requires minimal maintenance:

- **Automatic**: Index updates happen on every report publish
- **Periodic**: Review the Pages workflow logs occasionally
- **As needed**: Update Jekyll configuration or workflow logic

For any issues or questions, refer to:

- [GitHub Pages documentation](https://docs.github.com/en/pages)
- [Jekyll documentation](https://jekyllrb.com/docs/)
- [Project Reports repository](https://github.com/modeseven-lfit/project-reports)
