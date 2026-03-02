# Wealthsimple AI Builder — Behavioural Drift Detection MVP

A working prototype exploring how AI-assisted behavioural analysis could integrate into Wealthsimple's existing product without adding friction, compromising user autonomy, or requiring new data collection.

Built with Streamlit, Claude (Anthropic), and Plotly.

---

## What This Is

Most fintech AI features are built around prediction or prescription — tell users what to do, when to do it, and why they're wrong. This prototype takes a different approach.

The premise: Wealthsimple already captures everything it needs. Transaction data, portfolio actions, savings patterns, account activity. The gap isn't data — it's interpretation. This tool sits between the data and the user, surfaces patterns they might not have noticed, and asks questions rather than giving orders.

The result is a check-in experience that feels like a conversation with someone who's been paying attention — not a compliance warning or a sales pitch.

---

## Features

### Onboarding
- Full WS-style onboarding flow: goal → time horizon → risk tolerance → investment experience → profile review
- Budget setup fork: users choose to set up budget tracking now or later
- 50/30/20 framework scaffolded to their income, fully editable before saving
- Optional personalisation: life stage, financial stress level, check-in frequency

### Home
- Notification card triggers the 90-day analysis when drift is detected
- Clean dashboard — no noise when nothing needs attention

### Analysis View
- Savings chart: actual vs. on-track, cumulative 3-month view
- Spending shift summary: category-level drift with colour-coded severity
- Portfolio activity log: reactive behaviours flagged plainly
- AI summary: three plain-language sections — what we noticed, what it might mean, one thing to consider
- Soft advisor prompt: available if the user wants it, never pushed

### Budget Screen
- Live allocation bar: syncs in real time as users edit category amounts
- 50/30/20 tabs with market insights for key categories
- Protection settings: lock categories so AI suggestions never touch them (Loose / Moderate / Tight)
- Suggested reallocation cards: reduce X → increase Y, with reasoning
- Activity feed: last 90 days, collapsible
- Pattern detection: one card at a time, paginated — uncategorised recurring spend, over-budget categories, new subscriptions

### Advisor View
- Internal-only screen, clearly marked
- Full behavioural signal breakdown
- AI-generated clinical analysis: drift summary, key signals, confidence score, risk flags
- Advisor recommendation framed around client-initiated contact only

---

## Stack

- **Frontend / App:** Streamlit
- **AI:** Claude claude-opus-4-6 (Anthropic) via API
- **Charts:** Plotly
- **Language:** Python 3.11
- **Design system:** Custom CSS — Wealthsimple dark theme, Inter font, 50px border radius buttons, #00D26A green, #0D0D0D background

---

## Project Structure

```
wealthsimple-prototype/
├── app.py              # Routing and nav
├── onboarding.py       # WS-style onboarding flow
├── budget_setup.py     # Budget setup wizard
├── budget.py           # Budget screen + pattern detection
├── analysis.py         # 90-day snapshot + AI summary
├── home.py             # Home screen + notification card
├── utils.py            # AI calls, budget framework, signals, helpers
├── styles.py           # Full WS design system in CSS
└── .streamlit/
    └── secrets.toml    # ANTHROPIC_API_KEY
```

---

## Setup

```bash
git clone https://github.com/yourname/wealthsimple-prototype
cd wealthsimple-prototype
python3 -m venv venv
source venv/bin/activate
pip install streamlit anthropic plotly
```

Add your Anthropic API key:

```toml
# .streamlit/secrets.toml
ANTHROPIC_API_KEY = "sk-ant-..."
```

Run:

```bash
streamlit run app.py
```

Open `http://localhost:8501`. Use the ↺ button in the nav to reset to onboarding at any time.

---

## Demo Flow

1. Onboarding — goal, horizon, risk, experience, profile review
2. Budget fork — set up now or skip
3. Budget setup — income, accounts, savings target, categories
4. Confirmation screen
5. Home — notification card triggers the check-in
6. Analysis — chart, spending shifts, AI summary, soft advisor prompt
7. Budget — live editing, lock selector, pattern cards, AI reallocation
8. Advisor view — internal analysis, confidence score, risk flags

Total demo time: under 3 minutes.

---

## Notes on Mock Data

All transactions, signals, and behavioural patterns are mocked. In production these would come from Wealthsimple's existing data pipeline — no new data collection required.

The mock data is intentionally realistic: recurring cannabis purchases, home maintenance spend miscategorised as shopping, a new AI subscription appearing two months in a row. These represent the kinds of patterns the system is designed to surface.

---

## License

MIT
