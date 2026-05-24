# HealthMetricsTerminal

Terminal-style Monte Carlo dashboard for personal health biomarkers (HRV, VO2max, sleep, recovery) with intervention signals and coach-note sentiment.

## Features

- **Monte Carlo simulation** — Geometric Brownian Motion engine, configurable paths (100 / 1k / 10k) and horizons (5 / 30 / 90 / 252 periods).
- **Metric watchlist** — 10 metrics (HRV, VO2, DEEP, REM, SLP…).
- **Live tick simulation** — synthetic ticks every few seconds with deterministic seed for reproducibility.
- **Strategy signals** — ON-TRACK / INTERVENE / MONITOR derived from Trend MA Cross, Stress MR, Recovery Momentum, Range Skew, Coach Notes.
- **HMT chatter panel** — positive / neutral / negative sentiment with sample posts per metric.
- **Metric KPIs** — aggregate value, P&L, expected return, 95% VaR, Sharpe, sentiment.
- **Custom panel** — 24-hour circadian readiness ring synthesized from HRV and recovery.
- **Accessible by default** — WCAG 2.2 AA: keyboard nav, ARIA live regions, screen-reader chart alternatives, 4.5:1 contrast in dark mode.

## Running

No build step. Live at https://pablowilliams.github.io/HealthMetricsTerminal/.

For local development, any static server works:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Data pipeline

The dashboard reads `data/quotes.json` on load and on each tick. A scheduled GitHub Action (`.github/workflows/refresh-data.yml`) regenerates synthetic close histories every hour so the visible data evolves. Replace the generator with a real data source to go live.

## Architecture

- `index.html` — semantic layout, landmarks, headings
- `app.js` — data, Monte Carlo engine, sentiment, signal logic, rendering
- `styles.css` — dark terminal theme with AA-contrast tokens

## License

Private. All rights reserved.
