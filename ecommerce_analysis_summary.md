# E-commerce Marketing Funnel & Conversion Analysis
**Linh Phuong Hoang Nguyen** — Sample analysis project (synthetic dataset, 90 days, 4 acquisition channels)

## Objective
Identify where the conversion funnel leaks revenue, which channels deliver efficient ROAS, and whether a proposed checkout redesign would improve CVR — the same workflow this role requires for live Shopify/GA data.

## Dataset
Synthetic 90-day dataset (Mar 1–May 31, 2026) modeling daily Impressions → Clicks → Sessions → Add to Cart → Checkout Started → Purchase across **Facebook Ads, Google Ads, Email, and Organic/SEO**, with revenue and ad spend. Built to realistic ranges (CTR 1.8–5.6%, CVR 2–4.3%) so the methodology transfers directly to real export data.

## Key Findings

**1. Biggest funnel leak: Checkout Started → Purchase (-83.2%)**
Only ~17% of users who start checkout complete the purchase — a far bigger leak than Sessions→Cart (-68%) or Cart→Checkout (-45.4%). This pinpointed checkout friction, not top-of-funnel traffic quality, as the priority fix.

**2. Channel efficiency varies sharply**
| Channel | CVR | ROAS | Revenue |
|---|---|---|---|
| Email | 4.32% | 38.8x | $61.8K |
| Google Ads | 2.89% | 1.82x | $61.4K |
| Organic/SEO | 2.46% | N/A (no spend) | $41.9K |
| Facebook Ads | 2.07% | 2.20x | $30.4K |

Google Ads and Facebook Ads generate similar or higher revenue than Email but at far lower ROAS — both drive volume, not efficiency. Email is the standout efficiency channel.

**3. A/B test: single-page checkout redesign**
Simulated 14-day test (5,000 sessions/arm) targeting the checkout drop-off:
- Control (multi-step checkout): **16.06%** conversion
- Variant (single-page checkout): **20.18%** conversion
- **+25.7% lift, z = 5.35, p < 0.0001 → statistically significant**
- **Recommendation: ship the single-page checkout.**

## Methodology (SQL logic used for the core metrics)
```sql
SELECT
  channel,
  SUM(sessions)                                   AS sessions,
  SUM(purchases)                                   AS purchases,
  ROUND(SUM(purchases) * 100.0 / SUM(sessions), 2) AS cvr_pct,
  ROUND(SUM(revenue) / SUM(purchases), 2)          AS aov,
  ROUND(SUM(revenue) / NULLIF(SUM(ad_spend), 0), 2) AS roas
FROM funnel_events
GROUP BY channel
ORDER BY roas DESC;
```
Funnel drop-off and the A/B test significance were computed in Python (pandas + scipy two-proportion z-test).

## AI workflow used for this analysis
- **Gemini** — researched eCommerce funnel benchmarks and A/B testing methodology to ground the dataset and metrics in realistic ranges.
- **ChatGPT** — cross-checked the benchmark figures and formulas (CVR, ROAS, statistical test choice) for accuracy and completeness.
- **Claude** — built the dataset, ran the statistical analysis (funnel drop-off, channel comparison, two-proportion z-test), and produced the interactive dashboard and this write-up.

This mirrors the role's expectation: use AI daily to analyze faster, automate reporting, and support decisions — not just describe metrics.

---
*Dashboard file: `ecommerce_funnel_dashboard.html` (open in any browser, fully interactive, channel filter included).*
