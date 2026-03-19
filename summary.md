# Purpose
- Provide personal finance logging and management for all subscribers
- Create a spending plan for different purposes
- Provide advice on spending based on current personal status
- Use current sources to find basis for investment opportunities or financial questions from the user.
- Learn from the different outcomes of the different actions of the users, adapting to the market

# Functions
- General database on finance, QnA on personal finance
- Warnings or advices on when spending is off budget
- Summarize current finances, net worth, etc., and forecasts
- Investment guidance and forecasts based on like current socioeconomic conditions

# Architecture
- Database + budgeting: sqlite database + skills.md / database schemas
- Research: Web search toolings (selenium/playwright), news APIs, trading APIs (for example, YAHOO)
- Automation: monitor of different investment instruments in real time to show recommendations to the different users
- Iterative: agent learns based on the outcomes of each user, to avoid repeat mistakes
