# Personal Budget Coach

Rule-based AI Agent for a college economics class demo (BSU, Oct 8).

- Input: monthly take-home income + expense breakdown by category
- Flags any category above its healthy threshold (% of income)
- Computes savings rate = (income − total expenses) ÷ income
- Branches: EMERGENCY (< 0%) / AGGRESSIVE CUTS (0–10%) / OPTIMIZATION TIPS (≥ 10%)

Open **index.html** in any browser to use the agent.

## Live demo
https://2273414587zx-dev.github.io/personal-budget-coach/

## Microsoft 365 Copilot Agent version
The same coach also exists as a Microsoft 365 Copilot Agent (bilingual, LLM + code execution). Docs: `docs/personal_budget_coach_copilot_agent.md` (creation steps, test results, topic-boundary setup).
