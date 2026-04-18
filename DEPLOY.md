# GitHub Deployment Guide

## Step 1: Create GitHub Repository

### Option A: Via GitHub Website (Easiest)

1. **Go to GitHub**: https://github.com
2. **Sign in** (or create account if needed)
3. **Click the '+' icon** (top right) → "New repository"
4. **Fill in details**:
   - Repository name: `eu-ets-tracker`
   - Description: `EU ETS Market Intelligence Dashboard - Analyst forecasts vs futures validation`
   - Public ✅ (so it can be hosted on GitHub Pages)
   - Add README: ❌ (we have our own)
5. **Click "Create repository"**

### Option B: Via Command Line (For Developers)

```bash
# Create new repository on GitHub first, then:
git init
git add .
git commit -m "Initial commit: EU ETS Market Intelligence Dashboard"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/eu-ets-tracker.git
git push -u origin main
```

---

## Step 2: Upload Files

### Option A: GitHub Web Interface (Easiest)

1. **In your new repository**, click **"uploading an existing file"**
2. **Drag and drop ALL files**:
   - `index.html`
   - `README.md`
   - `LICENSE`
   - `.gitignore`
   - `focused_scraper.py` (optional)
3. **Scroll down**, add commit message: "Add dashboard files"
4. **Click "Commit changes"**

### Option B: Command Line

```bash
# From the eu-ets-tracker folder:
cd /path/to/eu-ets-tracker

# Initialize git
git init

# Add all files
git add .

# Commit
git commit -m "Initial commit: EU ETS Dashboard with futures validation"

# Connect to GitHub (replace YOUR_USERNAME)
git remote add origin https://github.com/YOUR_USERNAME/eu-ets-tracker.git

# Push
git branch -M main
git push -u origin main
```

---

## Step 3: Enable GitHub Pages (Free Hosting)

1. **In your repository**, go to **Settings** (top menu)
2. **Scroll down** to **Pages** (left sidebar)
3. **Under "Source"**, select:
   - Branch: `main`
   - Folder: `/ (root)`
4. **Click "Save"**
5. **Wait 1-2 minutes**

Your site will be live at:
```
https://YOUR_USERNAME.github.io/eu-ets-tracker/
```

Example: `https://johndoe.github.io/eu-ets-tracker/`

---

## Step 4: Verify Deployment

1. **Go to your GitHub Pages URL**
2. **You should see**:
   - Header: "EU ETS Market Intelligence Dashboard"
   - Stats: Spot €87.50, Dec-26 Futures €91.20
   - Futures curve analysis
   - Analyst forecast table
   - Strategic insights

3. **If you see "404 Page Not Found"**:
   - Wait 5 more minutes (GitHub Pages can be slow)
   - Check Settings → Pages shows "Your site is live at..."
   - Verify `index.html` exists in repository root

---

## Step 5: Share Your Dashboard

### Get the URL
After GitHub Pages is enabled, your URL is:
```
https://YOUR_USERNAME.github.io/eu-ets-tracker/
```

### Share Options

**1. Add to README Badge:**
```markdown
[![Live Demo](https://img.shields.io/badge/demo-live-success)](https://YOUR_USERNAME.github.io/eu-ets-tracker/)
```

**2. Custom Domain (Optional):**
- Buy domain (e.g., `ets-tracker.com`)
- In Settings → Pages → Custom domain
- Add your domain
- Update DNS records at your registrar

**3. QR Code:**
Generate at https://qr-code-generator.com with your GitHub Pages URL

---

## Step 6: Future Updates

### Update Data Weekly

**Option 1: Via GitHub Web Interface**
1. Click on `index.html` in your repository
2. Click the **pencil icon** (Edit this file)
3. Update the prices/data
4. Scroll down → "Commit changes"

**Option 2: Via Git**
```bash
# Make changes to index.html locally
vim index.html

# Commit and push
git add index.html
git commit -m "Update carbon prices for week of Apr 18, 2026"
git push
```

**Changes go live automatically** within 1-2 minutes.

### Automated Updates (Advanced)

Set up GitHub Actions:

Create `.github/workflows/update-data.yml`:
```yaml
name: Update Dashboard Data
on:
  schedule:
    - cron: '0 2 * * 1'  # Every Monday at 2 AM
  workflow_dispatch:  # Manual trigger

jobs:
  update:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Run scraper
        run: python focused_scraper.py
      - name: Commit changes
        run: |
          git config user.name "GitHub Actions"
          git config user.email "actions@github.com"
          git add index.html
          git commit -m "Auto-update: $(date)"
          git push
```

---

## Troubleshooting

### "404 - Page Not Found"
- ✅ Verify `index.html` exists in repository root
- ✅ Check Settings → Pages is enabled
- ✅ Wait 5 minutes after enabling GitHub Pages
- ✅ Clear browser cache (Ctrl+Shift+R)

### "Site Not Updating"
- ✅ Hard refresh: Ctrl+Shift+R (Windows) or Cmd+Shift+R (Mac)
- ✅ Check Actions tab for build errors
- ✅ Verify commit was pushed: `git log`

### "Styling Looks Broken"
- ✅ Check browser console (F12) for errors
- ✅ Verify all CSS is inline (no external files)
- ✅ Test in different browser

### "Want Custom Domain"
1. Buy domain (Namecheap, GoDaddy, etc.)
2. Settings → Pages → Custom domain
3. Add your domain (e.g., `ets-tracker.com`)
4. At your registrar, add DNS records:
   ```
   Type: A
   Host: @
   Value: 185.199.108.153
   
   Type: CNAME
   Host: www
   Value: YOUR_USERNAME.github.io
   ```
5. Wait 24 hours for DNS propagation

---

## Advanced: Make Repository Private

If you want to keep code private but site public:

**GitHub Pro Required** (free for students/researchers)

1. Settings → Danger Zone → Change visibility → Private
2. GitHub Pages will still work for Pro accounts
3. Only invited collaborators can see code

---

## Analytics (Optional)

### Add Google Analytics

In `index.html` before `</head>`:
```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

Replace `G-XXXXXXXXXX` with your tracking ID.

---

## Security Best Practices

1. **Never commit API keys** (use environment variables)
2. **Use .gitignore** for sensitive files
3. **Keep dependencies updated** (if you add JavaScript libraries)
4. **Enable Dependabot** (Settings → Security → Dependabot)

---

## Next Steps

Once deployed:

1. ⭐ **Star your own repo** (top right) to bookmark it
2. 📝 **Edit README** with your GitHub Pages URL
3. 🔗 **Share** with your team
4. 📊 **Set up weekly scraper** to automate data updates
5. 🎨 **Customize** colors/branding to match your company

---

## Support

**Having issues?**
- Check: https://docs.github.com/pages
- Ask: Open an issue in your repository
- Community: https://github.community

**Want to contribute?**
- Fork the repo
- Make improvements
- Submit a Pull Request

---

**Congratulations! Your EU ETS dashboard is now live on GitHub! 🎉**
