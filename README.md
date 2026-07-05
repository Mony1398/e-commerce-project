# eCommerce Funnel & Conversion Analytics

Interactive dashboard analyzing a 90-day synthetic eCommerce dataset across 4 acquisition channels to identify funnel drop-offs and validate a checkout optimization via A/B testing.

## Key Findings

- **Critical drop-off point**: Checkout → Purchase (−83.2%) — the largest leak in the funnel, not top-of-funnel traffic
- **Channel efficiency**: Email delivered the highest ROAS (38.8x); Google Ads generated revenue comparable to Email, while Facebook Ads underperformed both in revenue and efficiency
- **A/B test result**: Single-page checkout redesign increased CVR by +25.7%, statistically significant (z = 5.35, p < 0.0001)

## Files

| File | Description |
|---|---|
| [`ecommerce_funnel_dashboard.html`](https://mony1398.github.io/e-commerce-project/ecommerce_funnel_dashboard.html) | Interactive dashboard — KPIs (CTR/CVR/AOV/ROAS), funnel visualization, channel comparison, A/B test results, channel filter |
| [`ecommerce_analysis_summary.md`](https://github.com/Mony1398/e-commerce-project/blob/main/ecommerce_analysis_summary.md) | Write-up: methodology, SQL queries, findings, and AI-assisted workflow description |

## Methodology

- Funnel and channel metrics computed via SQL (aggregation, window functions)
- A/B test evaluated using a two-proportion z-test
- Dashboard built in HTML/JavaScript for interactive filtering

## Tools

Python (pandas, scipy), SQL, HTML/JavaScript, AI-assisted workflow (Gemini for research, ChatGPT for cross-checking, Claude for analysis and build)

## How to View

Open [`ecommerce_funnel_dashboard.html`](https://mony1398.github.io/e-commerce-project/ecommerce_funnel_dashboard.html) directly in a browser, or view via GitHub Pages.
