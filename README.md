# play-github-environments

A demonstration of GitHub Environments for trunk-based deployments with manual approval gates.

## Overview

This repository demonstrates how to use GitHub Environments to implement trunk-based deployments with a manual approval gate for production deployments.

## Workflow

The workflow defined in `.github/workflows/deploy.yml` implements a two-stage deployment process:

1. **Staging Deployment** - Automatically deploys to the `staging` environment when code is pushed to the `main` branch
2. **Production Deployment** - Deploys to the `production` environment after staging, requiring manual approval

## Setup

To enable manual approval for production deployments:

1. Go to your repository **Settings** → **Environments**
2. Create two environments:
   - `staging`
   - `production`
3. For the `production` environment:
   - Click on the environment name
   - Under **Deployment protection rules**, check **Required reviewers**
   - Add the GitHub users or teams who can approve production deployments
   - Click **Save protection rules**

## How It Works

### Trunk-Based Development

This workflow follows trunk-based development principles:
- All changes are merged to the `main` branch
- Every push to `main` triggers an automatic deployment to staging
- Production deployments require explicit approval from designated reviewers

### GitHub Environments

The workflow uses GitHub Environments to:
- Define deployment targets (`staging` and `production`)
- Set up approval gates (production requires manual approval)
- Track deployment history
- Provide environment-specific URLs

### Workflow Execution

1. Developer pushes code to `main` branch
2. Workflow automatically deploys to `staging` environment
3. Workflow waits for manual approval before deploying to `production`
4. Once approved, workflow deploys to `production` environment

## Triggering the Workflow

The workflow can be triggered in two ways:
1. **Automatically**: Push code to the `main` branch
2. **Manually**: Go to **Actions** → **Trunk-Based Deployment** → **Run workflow**

## Benefits

- **Safety**: Manual approval gate prevents accidental production deployments
- **Traceability**: All deployments are tracked in GitHub
- **Simplicity**: Minimal workflow configuration with maximum safety
- **Flexibility**: Can be extended with additional environments or validation steps