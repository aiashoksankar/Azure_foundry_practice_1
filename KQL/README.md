# KQL Demos — Monitoring Microsoft Foundry with Azure Log Analytics

These demos teach you how to use **Kusto Query Language (KQL)** to monitor and troubleshoot your Microsoft Foundry agents using Azure Application Insights and Log Analytics.

## Prerequisites

- A Microsoft Foundry project with Application Insights enabled
- Access to the Log Analytics workspace connected to your Application Insights resource
- At least one Foundry agent that has been called (so there is telemetry data to query)

## Where to Run These Queries

1. Open the **Azure Portal**
2. Navigate to your **Log Analytics workspace** (the one connected to your Application Insights resource)
3. Click **Logs** in the left menu
4. Copy-paste each query block into the query editor
5. **Select** just the lines you want to run, then click **Run**

> **Tip:** You can also run these queries directly inside Application Insights under **Logs**.

## Demo Files

| # | File | What You Learn |
|---|------|---------------|
| 01 | `KQL-Basics.kql` | Core KQL operators: `take`, `where`, `project`, `sort`, `count`, `extend`, `distinct`, `ago()` |
| 02 | `Exploring-Model-Calls.kql` | How Foundry logs AI model calls in `AppDependencies`, extracting `gen_ai.*` properties |
| 03 | `Token-Usage-Analysis.kql` | Token consumption analysis with `summarize`, `bin()`, `render timechart/columnchart/piechart` |
| 04 | `Agent-Tracing.kql` | End-to-end tracing with `OperationId`, `union`, `let`, span hierarchies |
| 05 | `Error-Analysis.kql` | Finding errors in `AppExceptions`, failed calls, success rates, `countif()`, `contains`, `strcat()`, `startswith` |
| 06 | `Monitoring-Dashboard.kql` | Production dashboard queries: percentiles, health scorecards, chart rendering, `dcount()`, `format_datetime()` |

## Key Tables Used

These are the standard Application Insights tables that Microsoft Foundry populates:

| Table | What It Stores |
|-------|---------------|
| `AppRequests` | Incoming requests to your agent application |
| `AppDependencies` | Outbound calls: AI model calls, tool executions, agent invocations |
| `AppTraces` | Log messages, evaluation results, prompt/completion content |
| `AppExceptions` | Errors and exceptions thrown during processing |
| `AppMetrics` | Custom numeric metrics (not queried in these demos) |

## Key GenAI Properties (in AppDependencies)

When Foundry calls an AI model, these OpenTelemetry attributes are stored in the `Properties` column:

| Property | Example | Description |
|----------|---------|-------------|
| `gen_ai.system` | `"openai"` | AI provider |
| `gen_ai.operation.name` | `"chat"` | Operation type |
| `gen_ai.request.model` | `"gpt-5.1"` | Model requested |
| `gen_ai.response.model` | `"gpt-5.1"` | Model that responded |
| `gen_ai.usage.input_tokens` | `14` | Prompt tokens used |
| `gen_ai.usage.output_tokens` | `91` | Completion tokens generated |
| `gen_ai.agent.name` | `"fitness-coach"` | Agent name |
| `gen_ai.tool.name` | `"search_tool"` | Tool name |
