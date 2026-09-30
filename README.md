# Bias-Shift Prediction Snapshots

Timestamped, immutable prediction snapshots from the Bias-Shift multi-model market signal dashboard.

## Purpose

Each snapshot is committed **before** the prediction window resolves. Git's commit history provides a public, immutable timestamp — proof that these predictions existed in advance, not retroactively.

## How to Verify

1. Pick any snapshot in `snapshots/YYYY-MM-DD/`
2. Run `git log --format="%H %ai" snapshots/YYYY-MM-DD/` to see the commit date
3. Compare the prediction window dates against the commit timestamp
4. Check actual SPY performance for resolved windows

## Structure

```
snapshots/
  2026-09-30/
    snapshot.json    # Machine-readable (full data)
    snapshot.md      # Human-readable (tables + summary)
```

## What Each Snapshot Contains

- **Combined MoM Signal** — direction, conviction, score, and model agreement across all models
- **Group A / Group B Consensus** — per-group signals computed independently
- **Per-Model Predictions** — each model's prediction windows with direction, conviction, and verdict
- **Track Record** — cumulative hit rates at time of snapshot

## Methodology

- **Score**: Directional strength from -10 (strong bearish) to +10 (strong bullish), weighted by model conviction
- **Agreement**: Percentage of models aligned on the combined direction
- **Conviction Tiers**: HIGH (|score| > 7), MEDIUM (> 4), LOW (> 1.5), NONE
- **Verdict**: Hit (correct direction by > 2%), Marginal (correct by 0-2%), Miss (wrong direction)
- Asset tracked: **SPY** (S&P 500 ETF)

## Disclaimer

This repository presents model-generated market predictions for educational and informational purposes only. It does not constitute financial advice, investment recommendations, or solicitation to trade. Past performance does not guarantee future results.
