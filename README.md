# WRI Operations Portal — GitHub Pages Redirect

GitHub Pages redirect wrapper for the WRI Operations Platform. This bypasses Chrome on iOS intercepting Google account selection when opening `script.google.com` links directly.

## How It Works

1. User opens `https://YOUR_ORG.github.io/wri-ops-portal/?view=field&job=abc123`
2. GitHub Pages serves `index.html` which immediately redirects to the Apps Script URL
3. All query parameters pass through intact
4. ArcGIS OAuth is unaffected — the redirect_uri stays pointed at Apps Script

## Setup

### 1. Push to GitHub

```bash
git remote add origin https://github.com/YOUR_ORG/wri-ops-portal.git
git add .
git commit -m "Initial redirect page"
git push -u origin main
```

### 2. Enable GitHub Pages

- Go to repo **Settings → Pages**
- Source: **Deploy from a branch**
- Branch: **main**, folder: **/ (root)**
- Click **Save**
- Live within ~1 minute

### 3. Update Share URLs

Update the share URLs generated in your Admin.html to use the GitHub Pages base URL instead of the raw Apps Script URL.

## Files

| File | Purpose |
|------|---------|
| `index.html` | Redirect page with loading UI and fallback link |
| `404.html` | Catches sub-path navigation and redirects to index |
| `README.md` | This file |
