# Foundry Workflows — Progressive Demo Series

Three hands-on demos that teach you how to build workflows in Microsoft Foundry.
Each demo builds on the previous one, progressing from basic to expert level.

| # | Demo | Difficulty | Key Concepts |
|---|------|-----------|--------------|
| 1 | [Email Summarizer](Email-Summarizer/email-summarizer.ipynb) | Easy | Single agent, workflow registration, CSDL YAML, `SetVariable`, `InvokeAzureAgent` |
| 2 | [Customer Support Router](Customer-Support-Router/customer-support-router.ipynb) | Medium | JSON structured output, `responseObject`, `ConditionGroup` branching, multi-agent routing, human-in-the-loop with `Question` |
| 3 | [Hiring Pipeline](Hiring-Pipeline/hiring-pipeline.ipynb) | Expert | Early exit gates, `ConditionGroup`, composite scoring, three-way branching, 5-agent pipeline |

## Prerequisites

- Complete the **[course-wide Setup notebook](../Setup/setup.ipynb)** first
- Create a `.env` file in this folder with your `FOUNDRY_PROJECT_ENDPOINT` and `MODEL_DEPLOYMENT_NAME`
- Be logged in with `az login`

## How to Use

1. Work through demos 1-3 in order — each builds on prior concepts
2. Each demo is a Jupyter notebook — run cells top to bottom
3. Every demo registers agents and workflows in the Foundry portal
4. Each demo includes test cases so you can verify everything works
