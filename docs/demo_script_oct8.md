# Personal Budget Coach — Demo Script (Oct 8)

**Agent:** Personal Budget Coach (conversational — you talk to it in plain English)
**Online link (永久):** https://2273414587zx-dev.github.io/personal-budget-coach/ — any computer, any time
**Fallback links:** 隧道版 https://retrieval-examples-licence-thompson.trycloudflare.com (临时) · 豆包版 https://gcnne1vf6apw.doubaoapps.com/app/app_17fbcuvsjz3 (旧表单版，仅备用，未同步对话功能)
**Local files:** `personal_budget_coach.html` (same page) · `personal_budget_coach.py` (same logic, terminal version)
**Time:** ~3 minutes

---

## Opening (30 seconds)

> "Hi everyone. My agent is the **Personal Budget Coach** — and it's a true agent, not a form. You just type a sentence about your budget, like you'd talk to a real coach: *'I earn $5000 a month and spend $1500 on rent, $800 on food.'* It understands that, checks every category against healthy limits, computes your savings rate, and tells you exactly what to change — with numbers."

---

## How it works (30 seconds)

The agent has three parts:

1. **Understands plain English — and Chinese.** Type either "I earn $5000 a month and spend $1500 on rent" or "我月薪5000，房租1500，吃饭800" — it parses income and expenses out of whatever you type, and answers in the same language you used. No forms, no dropdowns.
2. **Applies three budget rules**:
   - **Flag rule** — every category has a healthy limit (% of income): Housing 30%, Debt 20%, Food & Transport 15%, everything else 10%. Anything above the limit gets flagged, with exactly how much it's over.
   - **Savings rate** — `(income − total expenses) ÷ income`.
   - **Branch rule** — below 0% → EMERGENCY; 0–10% → AGGRESSIVE CUTS; ≥10% → OPTIMIZATION TIPS.
3. **Remembers context** — tell it your income first, then ask questions later; it keeps the state across messages.

> "Fully rule-based, no external APIs — same answer every time, easy to test."

---

## Demo walkthrough (2 minutes)

### Case A — type a full budget sentence (Emergency)

**Type:** `我一个月赚4000美元，房租1500，吃饭800，还债600，健康吗？`
(or English: `I earn $4000 a month and spend $1500 on housing, $800 on food, $600 on debt. Am I okay?`)

The agent extracts income $4,000 + 3 categories, runs the analysis, and shows a red **EMERGENCY** verdict: total expenses $5,100, savings rate **−27.5%**, Housing flagged (over by $300), Food flagged (over by $200), Debt flagged (over by $200).

**Say:** "It parsed the sentence, went red, and tells them to stop the bleed first — zero out entertainment and shopping, renegotiate rent. All the advice is specific and numeric."

### Case B — build up the budget over two messages (Aggressive)

**Type 1:** `I make $5000 a month`
**Type 2:** `rent is $1800, food is $800`

**Say:** "Notice it's a conversation — I gave it income first, then expenses, and it remembered. Savings rate is 1%, so it's in **aggressive** mode: free up about $450 a month, cut the flagged categories, and if that's not enough it suggests a small side income."

### Case C — ask questions like a real coach (Healthy)

First **type:** `My income is $6000: housing $1500, food $750, transport $350, debt $400. Am I saving enough?`

Then ask follow-ups:
- `Is $800 on food too much?` — it compares $800 against the 15% limit ($900) using the remembered income.
- `How much should I spend on rent?` — it answers $1,800 (30% of $6,000).
- `Am I saving enough?` — savings rate 18.3% → green, above the 10% line.

**Say:** "The green case flips to optimization: automate savings on payday, review bills once a year, consider investing. And you can interrogate it — ask about any category or rule and it answers from the same transparent rules."

---

## Live testing tips (for "we test each agent together" part)

- **The professor can type anything**: random sentences, weird categories, multiple messages — the parser handles it, and if it can't find a number it politely asks for one.
- **Context is remembered**: try income first, then expenses, then questions — no need to repeat yourself.
- **Transparency**: all thresholds are in the collapsible "Health thresholds" table under the chat; type `reset` to start over.

---

## Closing (15 seconds)

> "The same logic also runs as a Python script (`personal_budget_coach.py`) with a terminal chat — the web page and the script give identical answers. Thanks!"

---

### Threshold rules (reference)

| Category | Limit (% of income) |
|---|---|
| Housing | 30% |
| Debt Payments | 20% |
| Food & Groceries | 15% |
| Transportation | 15% |
| Utilities / Insurance / Entertainment / Shopping / Health / Education / Other | 10% |
| Savings target | ≥ 10% |
