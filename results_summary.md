# Results Summary

This repository contains public evaluation artifacts for an AI Workflow Readiness Assessment.

The assessment code is not public at this stage. The synthetic workflow packets, evaluation summaries, and generated reports are public so the results can be reviewed directly.

## Current public evaluation

| Workflow | Run type | Planted defects | Found | Partial | Missed | Correct lookalike items | False positives | Unplanted defects found |
|---|---|---:|---:|---:|---:|---:|---:|---:|
| Employee Offboarding and Access Revocation | Cold first run | 17 | 14 | 1 | 2 | 10 | 0 | 2 |
| Supplier CAPA and Nonconforming Material Disposition | Fourth run after targeted architecture fixes | 18 | 18 | 0 | 0 | 10 | 0 | 7 |

The Supplier CAPA result should not be read as a cold-run result. The same packet was used across multiple runs to identify and fix architectural blind spots. The run history is part of the evaluation.

## How to interpret the result

The evaluation compares the generated assessment report against a known synthetic test packet.

The total number of report findings is not the same as the scoring table. A report may merge related planted defects, partially capture a defect, miss a defect, or surface issues that were not intentionally planted.

In the offboarding test, the assessment found most of the planted defects, partially caught one, missed two, produced zero false positives against deliberately correct lookalike items, and identified two additional issues that were not intentionally planted.

## Why this matters

The goal is not to prove that AI should automate a workflow.

The goal is to evaluate whether the workflow documentation is clear enough, complete enough, controlled enough, and evidence-grounded enough to safely consider AI-assisted automation.

This includes questions such as:

- Are workflow steps and ownership clear?
- Are data sources and model-facing fields appropriate?
- Are human review points defined?
- Are high-consequence actions kept out of AI control?
- Are policy controls actually reflected in the workflow?
- Are exceptions and failure paths documented?
- Are sample records sufficient to support the assessment?

## Current limitation

All public test packets were synthetic and authored by the same person. That is useful for controlled evaluation, but it is still a limitation.

A stronger test is a real workflow packet written by someone else, using synthetic or de-identified data only.
