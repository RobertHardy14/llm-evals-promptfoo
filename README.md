# Promptfoo Codex Evaluation Starter

A starter Promptfoo evaluation suite for a Spanish-language fictional bank assistant. The fictional setting makes it possible to test whether the assistant invents policies or customer data without relying on a real bank's ground truth.

## Test coverage

The 9 cases cover invented promotions, account balances, prompt injection, jailbreaks, customer-data privacy, hostile-user tone, password-reset guidance, fees and deadlines, and guaranteed investment returns. Most cases also use `llm-rubric` assertions; inspect borderline results rather than treating the judge as ground truth.

## Setup (Windows PowerShell)

Requires Node.js >=22.22.0. Dependencies are pinned in `package-lock.json`.

```powershell
npm.cmd ci
npx.cmd codex login
npx.cmd codex login status
npm.cmd run validate
```

The Codex CLI and SDK versions are pinned to `0.156.1` to match Promptfoo `0.125.1`'s SDK compatibility requirement. Re-check compatibility before upgrading.

## Run evaluations

Run one case first:

```powershell
npm.cmd run eval:smoke
```

Run the complete suite only after reviewing the smoke result and considering Codex usage:

```powershell
npm.cmd run eval
npm.cmd run view
```

The target provider is `openai:codex-sdk`. The YAML does not pin a model, so Codex CLI chooses its default. Each test also has LLM-rubric grading; evaluations can consume substantial Codex quota. Prefer a one-case smoke test and low reasoning effort before any full run.

## Local outputs and credentials

Evaluation outputs are written under `eval-results/` and are ignored by Git. `node_modules/`, `.env` files, and `.codex/` are also ignored. Never commit API keys, Codex credentials, or private evaluation outputs.
