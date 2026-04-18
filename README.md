# EU ETS Market Intelligence Dashboard

> Real-time carbon pricing intelligence: Analyst forecasts validated against futures market expectations

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Version](https://img.shields.io/badge/version-1.0.0-green.svg)

## 🎯 Overview

A professional market intelligence dashboard tracking **15+ analyst forecasts** for EU ETS carbon prices (2026-2031) with **futures curve validation**. Designed for maritime compliance teams, carbon traders, and sustainability analysts.

**Novel Insight:** Compares analyst model predictions against ICE/EEX futures prices (traders with real money at stake) to identify alignment or divergence - your signal for confidence or caution.



### Option 1: GitHub Pages (Free Hosting)

1. **Fork this repository**
2. Go to **Settings → Pages**
3. Source: Deploy from branch `main`
4. Save

Your dashboard will be live at: `https://YOUR_USERNAME.github.io/eu-ets-tracker/`

### Option 2: Local Development

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/eu-ets-tracker.git
cd eu-ets-tracker

# Open in browser
open index.html  # macOS
start index.html # Windows
xdg-open index.html # Linux
```

### Option 3: Netlify Deploy

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/YOUR_USERNAME/eu-ets-tracker)

1. Click the button above
2. Connect your GitHub account
3. Deploy (takes 30 seconds)

### Option 4: WordPress Integration

See [WORDPRESS_INSTALL.md](WORDPRESS_INSTALL.md) for plugin installation

## 📊 Data Sources

### Analyst Forecasts
- **Banks**: ABN AMRO, ING, BNP Paribas, Société Générale
- **Industry**: BloombergNEF, ICIS, Refinitiv, S&P Global Platts
- **Academic**: PIK Potsdam, Bruegel, Öko-Institut, Enerdata
- **Trade**: IETA, Carbon Pulse, Reuters Survey

### Market Data
- **Spot**: ICE Endex (European Energy Exchange)
- **Futures**: EEX (European Energy Exchange)
- **Update frequency**: Daily settlement prices

## 🎓 Understanding the Dashboard

### What is Contango?

**Contango** occurs when futures prices are higher than spot:
```
Spot: €87.50
Dec-26 Futures: €91.20 (+4.2%)
→ CONTANGO = Market expects rising prices
```

**Backwardation** (opposite) means futures < spot → falling price expectations

### Novel Insight: Market vs Analyst Validation

**The Core Principle:**
- **Analysts** forecast using models (supply/demand, policy scenarios)
- **Traders** price futures with real capital at risk
- **When aligned** (<3% divergence) → High confidence
- **When divergent** (>5%) → Risk/opportunity signal

**Current Status (Apr 2026):**
- Futures: €138.40 (2030)
- Analyst median: €135.00
- Divergence: +2.5%
- **Signal**: ✅ Strong alignment = High confidence

### Use Cases

**For Maritime Compliance:**
- FuelEU Maritime carbon pooling strategy
- BioLNG vs VLSFO breakeven analysis
- 2030 compliance budget forecasting
- Risk-adjusted procurement timing

**For Carbon Trading:**
- Arbitrage opportunity detection
- Hedge position validation
- Market sentiment analysis
- Policy impact assessment

## 🔧 Customization

### Update Prices

Edit `index.html` around line 550:

```html
<div class="stat-card">
    <h3>Spot Price (ICE)</h3>
    <div class="value">€87.50</div> <!-- UPDATE THIS -->
</div>
```

### Change Theme Colors

Find the CSS section (line 7):

```css
background: #0a0e1a;  /* Dark background */
color: #60a5fa;       /* Accent blue */
color: #10b981;       /* Green (bullish) */
color: #ef4444;       /* Red (bearish) */
```

### Add Your Logo

In the header section:

```html
<div class="header">
    <img src="your-logo.png" alt="Logo" style="height: 50px; margin-bottom: 15px;">
    <h1>EU ETS Market Intelligence Dashboard</h1>
    ...
</div>
```
