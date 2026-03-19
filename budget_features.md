# Budgeting Features Implementation Plan for the Agentic Personal Finance Advisor

## 1. Overview

This document describes the implementation plan for the **budgeting features** of the Agentic Personal Finance Advisor. The goal is to define how budgeting will work inside the system, what files and modules are needed, how the database should be structured, what skills the agent should have, and how the components interact.

The budgeting system is the operational core of the project because it transforms raw financial data into structured plans, alerts, summaries, and personalized recommendations.

---

## 2. Budgeting Objectives

The budgeting subsystem should allow the agent to:

- Log income, expenses, liabilities, assets, and recurring payments
- Categorize and track spending
- Build multiple budget plans depending on user goals
- Compare actual spending versus planned spending
- Detect overspending or unusual behavior
- Forecast future cash flow and monthly outcomes
- Support goal-based planning such as saving for travel, emergencies, rent, or investing
- Generate personalized advice depending on the user's current financial condition
- Persist data so the system can adapt over time

---

## 3. High-Level Budgeting Architecture

The budgeting system will be composed of five main layers:

1. **Data Layer**
   - SQLite database
   - schemas for users, transactions, budgets, goals, assets, liabilities, recommendations, and outcomes

2. **Budgeting Logic Layer**
   - expense categorization
   - budget generation
   - budget comparison
   - alerts and warnings
   - forecasting

3. **Agent Skills Layer**
   - specialized budgeting skills described in `skills.md`
   - each skill handles a defined task

4. **Research and Market Context Layer**
   - web/news/research tools
   - trading APIs or market data APIs
   - used only when the user asks for financial questions or investment context

5. **Agent Orchestration Layer**
   - decides what budgeting tasks to run
   - coordinates the budgeting modules
   - merges results into a final answer

---

## 4. Proposed Repository Structure

```text
finance-agent/
├── app/
│   ├── main.py
│   ├── config.py
│   ├── orchestrator.py
│   ├── api/
│   │   ├── routes_users.py
│   │   ├── routes_budget.py
│   │   ├── routes_transactions.py
│   │   ├── routes_goals.py
│   │   ├── routes_reports.py
│   │   └── routes_research.py
│   ├── agents/
│   │   ├── budgeting_agent.py
│   │   ├── forecasting_agent.py
│   │   ├── advisory_agent.py
│   │   ├── investment_agent.py
│   │   ├── monitoring_agent.py
│   │   └── learning_agent.py
│   ├── skills/
│   │   ├── skills.md
│   │   ├── categorize_expense.py
│   │   ├── create_budget_plan.py
│   │   ├── compare_budget_vs_actual.py
│   │   ├── detect_budget_deviation.py
│   │   ├── forecast_cashflow.py
│   │   ├── summarize_finances.py
│   │   ├── answer_finance_qa.py
│   │   ├── generate_spending_advice.py
│   │   ├── evaluate_investment_readiness.py
│   │   └── record_outcome_feedback.py
│   ├── services/
│   │   ├── transaction_service.py
│   │   ├── budget_service.py
│   │   ├── goal_service.py
│   │   ├── forecast_service.py
│   │   ├── advisory_service.py
│   │   ├── market_research_service.py
│   │   ├── recommendation_service.py
│   │   └── monitoring_service.py
│   ├── db/
│   │   ├── database.py
│   │   ├── schema.sql
│   │   ├── migrations/
│   │   │   ├── 001_init.sql
│   │   │   ├── 002_budget_tables.sql
│   │   │   ├── 003_recommendations.sql
│   │   │   └── 004_feedback_learning.sql
│   │   └── repositories/
│   │       ├── users_repo.py
│   │       ├── transactions_repo.py
│   │       ├── budgets_repo.py
│   │       ├── goals_repo.py
│   │       ├── assets_repo.py
│   │       ├── liabilities_repo.py
│   │       ├── recommendations_repo.py
│   │       └── outcomes_repo.py
│   ├── models/
│   │   ├── user.py
│   │   ├── transaction.py
│   │   ├── budget.py
│   │   ├── goal.py
│   │   ├── asset.py
│   │   ├── liability.py
│   │   ├── forecast.py
│   │   ├── recommendation.py
│   │   └── outcome.py
│   ├── research/
│   │   ├── web_search.py
│   │   ├── news_client.py
│   │   ├── market_data_client.py
│   │   └── instrument_monitor.py
│   ├── automations/
│   │   ├── alert_scheduler.py
│   │   ├── budget_monitor_runner.py
│   │   └── market_watch_runner.py
│   └── utils/
│       ├── dates.py
│       ├── money.py
│       ├── categories.py
│       ├── validators.py
│       └── scoring.py
├── tests/
│   ├── test_budget_creation.py
│   ├── test_budget_alerts.py
│   ├── test_cashflow_forecast.py
│   ├── test_expense_categorization.py
│   └── test_investment_readiness.py
├── docs/
│   ├── architecture.md
│   ├── budgeting.md
│   ├── database.md
│   ├── research.md
│   └── learning-loop.md
├── requirements.txt
├── README.md
└── .env
