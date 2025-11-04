# Render Health Ping Service

A lightweight GitHub Actions-based service that keeps your Render backend awake by periodically pinging its health endpoint.

## Overview

This repository uses GitHub Actions scheduled workflows to ping a FastAPI backend hosted on Render's free tier, preventing it from spinning down due to inactivity.

## Configuration

- **Backend URL**: `https://language-learning-platform-uyqh.onrender.com`
- **Health Endpoint**: `/health`
- **Ping Frequency**: Every 10 minutes

## How It Works

1. GitHub Actions runs a scheduled workflow every 10 minutes
2. The workflow makes an HTTP GET request to the health endpoint
3. The response status is logged and checked
4. If the status is not 200, the workflow fails (alerting you to potential issues)

## Setup

This repository is ready to use! The workflow will automatically start running once you push the `.github/workflows/keep-alive.yml` file to GitHub.

### Manual Testing

You can manually trigger the workflow from the GitHub Actions tab:
1. Go to the "Actions" tab in your repository
2. Select "Keep Render Backend Alive" workflow
3. Click "Run workflow"

## Monitoring

To check if the pings are working:
1. Go to the "Actions" tab in your GitHub repository
2. Click on "Keep Render Backend Alive"
3. View the workflow runs and their logs

## Free Tier Limits

- **Public repositories**: Unlimited GitHub Actions minutes ✅
- **Private repositories**: 2,000 minutes/month (sufficient for this use case)

## Customization

### Change Ping Frequency

Edit the cron schedule in `.github/workflows/keep-alive.yml`:

```yaml
schedule:
  - cron: '*/10 * * * *'  # Every 10 minutes
  # Examples:
  # - cron: '*/5 * * * *'   # Every 5 minutes
  # - cron: '*/14 * * * *'  # Every 14 minutes
  # - cron: '0 * * * *'     # Every hour
```

### Change Backend URL

Update the `curl` command in `.github/workflows/keep-alive.yml` with your new endpoint URL.

## License

MIT
