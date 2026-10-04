# 💰 Personal Budget Coach — 个人预算教练

**课程作业项目**：能输入一句话提问的预算分析 AI Agent（BSU Economics Class，中英双语）。

---

## 🤖 Microsoft 365 Copilot Agent 版（主推）

用 **Microsoft 365 Copilot**（Agent Builder，学校账号）创建的双语智能体：
一句话说出收入与支出 → 自动分析储蓄率、超支项、削减建议；带**主题边界**（与预算无关的问题一律拒绝）。

- 📄 **Agent 完整定义存档**：👉 [`docs/copilot_agent_definition.md`](docs/copilot_agent_definition.md)
- 🖥️ **展示页（GitHub Pages，打开即是）**：👉 https://2273414587zx-dev.github.io/personal-budget-coach/
- 🔗 **打开 Agent 开始对话**：https://copilot.cloud.microsoft/agents （登录学校账号 → 我的智能体 → Personal Budget Coach）

**实测结果**（2026-10-04 全部通过）：

| 测试 | 输入 | 结果 |
|---|---|---|
| 中文整句分析 | 我月收入 $4,000，房租 $1,500，吃饭 $800，交通 $350，其他 $500 | 储蓄率 21.25% → 优化建议；房租超 $300、吃饭超 $200 |
| 中文多轮追问 | 我存的钱够吗？ | 记住数据；应急基金 3–6 个月建议 |
| 英文提问 | How much should I spend on rent if I earn $5000? | 推荐 ≤ $1,500（30%） |
| ✅ 主题边界 | 今天天气怎么样？ | 拒绝："这个问题超出了个人预算教练的范围" |

---

## 🌐 网页版（规则引擎，同规则）

纯规则计算、无外部 API、中英双语对话：https://2273414587zx-dev.github.io/personal-budget-coach/webapp.html

## 📁 仓库结构

```
personal-budget-coach/
├── index.html                    # ⭐ Copilot Agent 展示页（GitHub Pages 根页面，一打开就是）
├── webapp.html                   # 网页版（规则引擎，首页含 Copilot 入口）
├── docs/
│   ├── copilot_agent_definition.md    # ⭐ Copilot Agent 完整定义存档
│   ├── personal_budget_coach_copilot_agent.md  # 创建过程与测试记录
│   ├── copilot_studio_agent_config.md # Copilot Studio 版配置（备查）
│   └── demo_script_oct8.md           # 课堂演示脚本
```

## 📊 健康预算规则

| 类别 | 健康上限（占月收入） |
|---|---|
| 住房 Housing | 30% |
| 债务还款 Debt | 20% |
| 吃饭 Food | 15% |
| 交通 Transportation | 15% |
| 其他类别 | 各 10% |
| 目标储蓄率 | ≥ 10% |

三档结论：储蓄率 < 0% → **EMERGENCY 紧急**；0–10% → **AGGRESSIVE CUTS 需要削减**；≥ 10% → **OPTIMIZATION 优化建议**。

---

*Built by Nancy (Zhang, X.) · BSU Economics Class Project · 2026-10-04*
