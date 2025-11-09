# Render Health Ping Service

A lightweight GitHub Actions-based service that keeps your Render backends awake by periodically pinging their health endpoints.

## Overview

This repository uses GitHub Actions scheduled workflows to ping multiple FastAPI backends hosted on Render's free tier, preventing them from spinning down due to inactivity.

## Configuration

### Monitored APIs

**Persian-Chai (Language Learning Platform)**
- **Backend URL**: `https://language-learning-platform-uyqh.onrender.com`
- **Health Endpoint**: `/health`

**Bahasa-Bali**
- **Backend URL**: `https://bahasa-bali.onrender.com`
- **Health Endpoint**: `/health`

**Ping Frequency**: Every 10 minutes (both APIs)

## How It Works

1. GitHub Actions runs a scheduled workflow every 10 minutes
2. The workflow contains two independent jobs, one for each API
3. Each job makes an HTTP GET request to its respective health endpoint
4. The response status is logged and checked
5. If the status is not 200, that specific job fails (alerting you to potential issues)
6. Jobs run in parallel for efficient monitoring

## Setup

This repository is ready to use! The workflow will automatically start running once you push the `.github/workflows/keep-alive.yml` file to GitHub.

### Manual Testing

You can manually trigger the workflow from the GitHub Actions tab:
1. Go to the "Actions" tab in your repository
2. Select "Keep Render Backends Alive" workflow
3. Click "Run workflow"

## Monitoring

To check if the pings are working:
1. Go to the "Actions" tab in your GitHub repository
2. Click on "Keep Render Backends Alive"
3. View the workflow runs and their logs
4. Each API will show as a separate job ("Ping Persian-Chai API" and "Ping Bahasa-Bali API") for independent status monitoring

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

### Add or Modify Backend URLs

To add a new API or modify existing ones, edit `.github/workflows/keep-alive.yml`:

1. Duplicate an existing job block (e.g., `ping-persian-chai`)
2. Rename the job ID and display name
3. Update the URL in the `curl` command
4. Update the echo messages to reflect the new API name

Example:
```yaml
ping-your-api:
  name: Ping Your API
  runs-on: ubuntu-latest
  steps:
    - name: Ping Your API Health Endpoint
      run: |
        echo "Pinging Your API health endpoint at $(date)"
        response=$(curl -s -o /dev/null -w "%{http_code}" https://your-api.onrender.com/health)
        # ... rest of the configuration
```

## License

MIT
