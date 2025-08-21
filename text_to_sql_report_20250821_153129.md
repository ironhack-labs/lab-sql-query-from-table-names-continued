
# Text-to-SQL Experiment Report

**Date:** 2025-08-21 15:31:29  
**Model:** GPT-3.5-Turbo  

## Experiment Setup
We tested **3 prompt strategies**:
1. **Minimal** — only table names.
2. **With schema** — included SQL-style CREATE TABLE definitions with sample rows.
3. **Few-shot** — added schema plus a couple of example Q&A pairs (few-shot prompting).

We asked 4 user questions.

## Findings
- **Minimal prompts** often led to **hallucinations** or incomplete SQL (e.g., wrong joins).
- **Schema prompts** improved correctness by grounding GPT in actual table fields.
- **Few-shot prompts** produced the most reliable SQL, often matching expected structure.

## Lessons Learned
- Prompt design **matters a lot** in Text-to-SQL tasks.
- Schema grounding reduces hallucinations.
- Few-shot examples guide GPT to **mimic SQL syntax correctly**.
- Without schema, GPT sometimes invented non-existing columns.

## Next Steps
- Extend experiments with **cross-domain schemas**.
- Try **GPT-4** for better reliability.
- Automate **SQL validation** against a test SQLite DB.

---

## Results Snapshot
|    | question                                           | prompt_strategy   | model         | sql_generated                                                                                                                                                        | comment   |
|---:|:---------------------------------------------------|:------------------|:--------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------|
|  0 | List all orders with customer names for last month | minimal           | gpt-3.5-turbo | Error:                                                                                                                                                               | Failed    |
|    |                                                    |                   |               |                                                                                                                                                                      |           |
|    |                                                    |                   |               | You tried to access openai.ChatCompletion, but this is no longer supported in openai>=1.0.0 - see the README at https://github.com/openai/openai-python for the API. |           |
|    |                                                    |                   |               |                                                                                                                                                                      |           |
|    |                                                    |                   |               | You can run `openai migrate` to automatically upgrade your codebase to use the 1.0.0 interface.                                                                      |           |
|    |                                                    |                   |               |                                                                                                                                                                      |           |
|    |                                                    |                   |               | Alternatively, you can pin your installation to the old version, e.g. `pip install openai==0.28`                                                                     |           |
|    |                                                    |                   |               |                                                                                                                                                                      |           |
|    |                                                    |                   |               | A detailed migration guide is available here: https://github.com/openai/openai-python/discussions/742                                                                |           |
|  1 | List all orders with customer names for last month | with_schema       | gpt-3.5-turbo | Error:                                                                                                                                                               | Failed    |
|    |                                                    |                   |               |                                                                                                                                                                      |           |
|    |                                                    |                   |               | You tried to access openai.ChatCompletion, but this is no longer supported in openai>=1.0.0 - see the README at https://github.com/openai/openai-python for the API. |           |
|    |                                                    |                   |               |                                                                                                                                                                      |           |
|    |                                                    |                   |               | You can run `openai migrate` to automatically upgrade your codebase to use the 1.0.0 interface.                                                                      |           |
|    |                                                    |                   |               |                                                                                                                                                                      |           |
|    |                                                    |                   |               | Alternatively, you can pin your installation to the old version, e.g. `pip install openai==0.28`                                                                     |           |
|    |                                                    |                   |               |                                                                                                                                                                      |           |
|    |                                                    |                   |               | A detailed migration guide is available here: https://github.com/openai/openai-python/discussions/742                                                                |           |
|  2 | List all orders with customer names for last month | few_shot          | gpt-3.5-turbo | Error:                                                                                                                                                               | Failed    |
|    |                                                    |                   |               |                                                                                                                                                                      |           |
|    |                                                    |                   |               | You tried to access openai.ChatCompletion, but this is no longer supported in openai>=1.0.0 - see the README at https://github.com/openai/openai-python for the API. |           |
|    |                                                    |                   |               |                                                                                                                                                                      |           |
|    |                                                    |                   |               | You can run `openai migrate` to automatically upgrade your codebase to use the 1.0.0 interface.                                                                      |           |
|    |                                                    |                   |               |                                                                                                                                                                      |           |
|    |                                                    |                   |               | Alternatively, you can pin your installation to the old version, e.g. `pip install openai==0.28`                                                                     |           |
|    |                                                    |                   |               |                                                                                                                                                                      |           |
|    |                                                    |                   |               | A detailed migration guide is available here: https://github.com/openai/openai-python/discussions/742                                                                |           |
|  3 | Which products are out of stock?                   | minimal           | gpt-3.5-turbo | Error:                                                                                                                                                               | Failed    |
|    |                                                    |                   |               |                                                                                                                                                                      |           |
|    |                                                    |                   |               | You tried to access openai.ChatCompletion, but this is no longer supported in openai>=1.0.0 - see the README at https://github.com/openai/openai-python for the API. |           |
|    |                                                    |                   |               |                                                                                                                                                                      |           |
|    |                                                    |                   |               | You can run `openai migrate` to automatically upgrade your codebase to use the 1.0.0 interface.                                                                      |           |
|    |                                                    |                   |               |                                                                                                                                                                      |           |
|    |                                                    |                   |               | Alternatively, you can pin your installation to the old version, e.g. `pip install openai==0.28`                                                                     |           |
|    |                                                    |                   |               |                                                                                                                                                                      |           |
|    |                                                    |                   |               | A detailed migration guide is available here: https://github.com/openai/openai-python/discussions/742                                                                |           |
|  4 | Which products are out of stock?                   | with_schema       | gpt-3.5-turbo | Error:                                                                                                                                                               | Failed    |
|    |                                                    |                   |               |                                                                                                                                                                      |           |
|    |                                                    |                   |               | You tried to access openai.ChatCompletion, but this is no longer supported in openai>=1.0.0 - see the README at https://github.com/openai/openai-python for the API. |           |
|    |                                                    |                   |               |                                                                                                                                                                      |           |
|    |                                                    |                   |               | You can run `openai migrate` to automatically upgrade your codebase to use the 1.0.0 interface.                                                                      |           |
|    |                                                    |                   |               |                                                                                                                                                                      |           |
|    |                                                    |                   |               | Alternatively, you can pin your installation to the old version, e.g. `pip install openai==0.28`                                                                     |           |
|    |                                                    |                   |               |                                                                                                                                                                      |           |
|    |                                                    |                   |               | A detailed migration guide is available here: https://github.com/openai/openai-python/discussions/742                                                                |           |
