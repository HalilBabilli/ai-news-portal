# İş Dünyası AI Portal

An automatically updating AI news portal that fetches, scores, and ranks the latest AI news every day at 7:00 AM CET.

## Features

- **Daily automatic updates** via GitHub Actions
- **Importance scoring** based on 5 weighted criteria:
  - Capability Inflection (30%) - Does this change what AI can do?
  - Economic Surface Area (25%) - How much of the economy does this touch?
  - Irreversibility (20%) - Does this lock AI into a new path?
  - Timeline Effect (15%) - Does this speed up or slow down AI progress?
  - Systemic Effects (10%) - Does this trigger cascading effects beyond AI?
- **Beautiful dark theme** with responsive design
- **Hosted free** on GitHub Pages

## Setup Instructions

### 1. Create a GitHub Repository

1. Go to [github.com/new](https://github.com/new)
2. Name it `ai-news-portal` (or whatever you prefer)
3. Make it **Public** (required for free GitHub Pages)
4. Click **Create repository**

### 2. Upload Files

Upload all files from this folder to your repository:
- `index.html`
- `scripts/update_news.py`
- `.github/workflows/update-news.yml`
- `README.md`

You can do this by:
- Dragging and dropping files in the GitHub web interface
- Or using git commands

### 3. Add Your Anthropic API Key

1. In your repository, go to **Settings** → **Secrets and variables** → **Actions**
2. Click **New repository secret**
3. Name: `ANTHROPIC_API_KEY`
4. Value: Your Anthropic API key (starts with `sk-ant-`)
5. Click **Add secret**

### 4. Enable GitHub Pages

1. Go to **Settings** → **Pages**
2. Under "Source", select **Deploy from a branch**
3. Select **main** branch and **/ (root)** folder
4. Click **Save**

Your site will be live at: `https://YOUR_USERNAME.github.io/ai-news-portal`

### 5. Run the First Update

1. Go to **Actions** tab in your repository
2. Click on **Update AI News Daily** workflow
3. Click **Run workflow** → **Run workflow**
4. Wait 1-2 minutes for it to complete
5. Your site is now live with fresh news!

## How It Works

1. Every day at 7:00 AM CET, GitHub Actions triggers the workflow
2. The Python script calls Claude API with web search
3. Claude fetches latest AI news and scores each item
4. The script generates a new `index.html` with the news data
5. GitHub Actions commits the updated file
6. GitHub Pages serves the updated site

## Manual Updates

To manually trigger an update:
1. Go to **Actions** → **Update AI News Daily**
2. Click **Run workflow**

## Costs

- **GitHub**: Free (public repository + GitHub Pages)
- **Anthropic API**: ~$0.01-0.03 per daily update (~$1/month)

## Customization

### Change update time
Edit `.github/workflows/update-news.yml` and modify the cron schedule:
```yaml
schedule:
  - cron: '0 6 * * *'  # 6:00 AM UTC = 7:00 AM CET
```

### Change number of news items
Edit `scripts/update_news.py` and modify the prompt to request more/fewer items.

## Troubleshooting

### Workflow fails
- Check **Actions** tab for error logs
- Verify your `ANTHROPIC_API_KEY` secret is set correctly
- Ensure you have API credits in your Anthropic account

### Site not updating
- Check if the workflow ran successfully in **Actions**
- GitHub Pages may take 1-2 minutes to deploy changes

## License

MIT License - feel free to modify and use as you wish.
