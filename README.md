# Wealthsimple AI Builder — Behavioural Drift Detection

A concept and front-end design exploration for Wealthsimple's AI Builder program: how AI-assisted
behavioural analysis *could* live inside Wealthsimple's existing product without adding friction,
compromising user autonomy, or requiring any new data collection.

**Scope, up front:** this is a front-end flow built on **mocked data** — not a working product. I
designed and built the experience (onboarding, the in-app analytics and check-in views, the
notification moment, the budget and advisor screens) to show how the idea would look, feel, and flow
end to end. There is no live backend, model pipeline, or real account data behind it. The value here
is the **idea and the direction**, demonstrated concretely.

---

## The idea

Most fintech AI is built around prediction or prescription — tell users what to do, when to do it,
and why they're wrong. This takes a different approach.

The premise: Wealthsimple already captures everything it would need — transaction data, portfolio
actions, savings patterns, account activity. The gap isn't data, it's *interpretation*. This concept
sits between the data and the user, surfaces patterns they might not have noticed, and **asks
questions rather than giving orders.**

The result is a check-in that feels like a conversation with someone who's been paying attention —
not a compliance warning or a sales pitch. It notices when a person's **own financial behaviour
drifts** (spending creeping up, savings slipping off-track, reactive portfolio moves) and reflects
that back, plainly.

---

## What the flow shows

- **Onboarding** — goal → time horizon → risk tolerance → investment experience → profile review;
  optional personalisation (life stage, financial stress, check-in frequency).
- **Budget setup** — a 50/30/20 framework scaffolded to the user's income, fully editable.
- **Home** — a quiet dashboard; a notification card triggers the 90-day check-in only when drift is
  detected. No noise when nothing needs attention.
- **Analysis view** — savings actual-vs-on-track, category-level spending shifts, a portfolio
  activity log, and a plain-language AI summary in three parts: *what we noticed, what it might mean,
  one thing to consider.* A soft advisor prompt is available but never pushed.
- **Budget screen** — live allocation editing, lockable categories (so suggestions never touch what
  the user protects), and paginated pattern detection.
- **Advisor view** — an internal-only screen with a behavioural-signal breakdown, a confidence
  score, and risk flags, framed around **client-initiated** contact only.

Design principles throughout: **no new data collection, the user stays in control, and intervention
is opt-in, not imposed.**

---

## Stack

- **App / UI:** Streamlit + a custom CSS design system (Wealthsimple dark theme)
- **Plain-language summaries:** Claude (Anthropic) via API, run over mocked behavioural signals
- **Charts:** Plotly

All transactions, signals, and patterns are **mocked** and intentionally realistic (a recurring
purchase, home-maintenance spend miscategorised as shopping, a new subscription appearing two months
running). In production these would come from Wealthsimple's existing pipeline — no new collection
required.

---

## Where this could go

The same loop should generalise from people to AI agents. Swap dollars for tokens and compute: what
is an agent actually spending its budget on, and is that what it was asked to do? How far does it
drift from its original goal across a long task? Same machinery — establish a baseline, measure
divergence, surface it legibly, keep a human in the loop — applied as an oversight signal for
agentic systems. That's the direction I'm most interested in carrying forward.

---

## License

MIT
