
# Day 3 — Finance Insights Analyst Project

## Today's Goal

Generate AI-powered natural language insights from the statistical
summary, and build a final visual dashboard to complete the project.

## What I Did

### 1. AI Integration Setup

- Initially planned to use OpenAI/Claude API, but both require paid
  billing (no reliable free tier as of 2026)
- Switched to Google Gemini API — genuinely free tier, no credit card
  required
- Faced a model deprecation error (`gemini-2.5-flash` no longer
  available to new users) — resolved by switching to `gemini-flash-latest`

### 2. Data Re-validation

- Reloaded the cleaned dataset and re-ran Day 2's core steps
  (imputation, Z-score anomaly detection, forecasting)
- Cross-verified the anomaly count (94) using three independent
  methods to ensure consistency before using it in the final report

### 3. AI-Powered Insight Generation

- Converted the statistical summary (category spend, anomalies,
  forecast) into a JSON payload
- Prompted Gemini to generate plain-language, actionable insights and
  a warning based on the data — not just repeat numbers, but explain
  what they mean for spending behavior
- The AI correctly flagged the anomaly count as a fraud/error-check
  warning, and identified the "Unknown" category as a data-quality gap
  worth investigating

### 4. Final Dashboard

- Built a 4-panel dashboard: category-wise spend, monthly trend,
  anomaly scatter plot, and forecast comparison (with vs. without anomalies)
- Saved as a single PNG for easy sharing in the README and on LinkedIn

## Formulas/Functions Used

| Function                                       | Purpose                                             |
| ---------------------------------------------- | --------------------------------------------------- |
| `genai.GenerativeModel().generate_content()` | Sending prompt + data to the Gemini API             |
| `json.dumps()`                               | Converting pandas summaries into AI-readable format |
| `plt.subplots(2,2)`                          | Building a multi-panel dashboard                    |

## Key Learnings

- Learned that AI model names change frequently — always check current
  model availability rather than assuming a tutorial's model name still works
- Learned to independently verify calculated results using multiple
  methods before trusting them in a final report
- Learned how to structure a prompt with clean, labeled JSON data to
  get focused, non-repetitive AI insights rather than a generic summary
- Learned to adapt a project plan when a paid tool isn't accessible —
  finding a genuinely free, capable alternative rather than stalling

## Challenges Faced

- OpenAI/Claude API required paid billing with no reliable free option —
  solved by switching to Google Gemini's free tier
- `gemini-2.5-flash` model was deprecated — solved using `gemini-flash-latest`

## Project Status

Core analysis pipeline (Excel → SQL → Python/Statistics → AI insights →
Dashboard) is now complete across Days 1–3.

## Key Results Summary

- Total transactions analyzed: 10,000
- Total anomalies detected: 94 (Z-score > 3, ~0.9%)
- Highest anomaly: ₹1,99,607 (Entertainment category)
- Top spend category: Food (₹56.3L)
- Missing values imputed: 507 (~5%), flagged via `Is_Imputed`
- Final forecast for next month's spend: ₹21,66,594.80

## Tomorrow's Plan

Package the project as a live, deployable version (Day 4).

## Links

- Project Repo: https://github.com/mmtiwari222/finance-insights-analyst-project
