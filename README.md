# AI Workflow Readiness Evaluation

This repository contains public evaluation artifacts for an AI Workflow Readiness Assessment.

The assessment is designed to evaluate whether a documented workflow appears ready for AI-assisted automation: where AI may help, what should remain human-controlled, and which workflow, data, control, ownership, exception-handling, or evidence gaps should be addressed before building.

This is not a production-readiness certification. It is not a legal, compliance, security, or operational approval. It is also not a replacement for process owners, compliance teams, security teams, legal teams, or operational experts.

It is a structured first pass.

## Why I built this

A lot of AI automation conversations start with the model or the tool.

In practice, the harder questions often come earlier:

- Is the workflow clearly documented?
- Are the systems and data sources known?
- Are controls actually implemented in the workflow?
- Are human review points defined?
- Are exception paths documented?
- Are high-consequence actions kept out of AI control?
- Is there enough evidence to support automation decisions?
- What is the safest first build?

This project is my attempt to make those questions more structured, testable, and inspectable.

## What is included

- A blank workflow packet template
- Completed synthetic workflow packets
- Generated assessment reports
- Evaluation summaries
- Results summary

## What is not included

The assessment code is not public at this stage.

The synthetic packets, evaluation summaries, and generated reports are public so the results can be reviewed directly.

## Current public evaluation

### Employee Offboarding and Access Revocation

The current public example uses a synthetic employee offboarding and access revocation workflow.

The test packet included:

- 17 deliberately planted workflow defects
- 10 deliberately correct lookalike items

Assessment result:

- 14 planted defects found
- 1 planted defect partially caught
- 2 planted defects missed
- 0 false positives against the lookalike items
- 2 additional real issues found that were not intentionally planted

See:

- `evaluations/offboarding/offboarding_workflow_packet.xlsx`
- `evaluations/offboarding/offboarding_evaluation_summary.pdf`
- `evaluations/offboarding/offboarding_assessment_report.pdf`
- `evaluations/offboarding/offboarding_assessment_report.md`

## How to interpret the results

The evaluation summary maps the generated assessment report back to the known synthetic test packet.

The number of findings in the final report may not match the scoring table exactly. A report can merge related issues, partially capture a planted defect, miss a planted defect, or identify issues that were not intentionally planted.

The point is not to claim the assessment is perfect.

The point is to make the result inspectable: what it found, what it missed, where it was partially right, and whether it created false positives.

## Data handling

Synthetic or de-identified workflow packets only.

Do not submit PHI, PII, customer-identifiable data, employee-identifiable data, supplier-confidential terms, trade secrets, credentials, access tokens, material non-public information, raw system exports, or real regulated records.

See `data_handling.md`.

## Current limitation

The public test packets were synthetic and authored by one person. That is useful for controlled evaluation, but it is still a limitation.

A stronger test is a workflow packet completed by someone else, using synthetic or de-identified data only.

## Repository structure

templates/
  workflow_packet_template.xlsx

evaluations/
  offboarding/
    offboarding_workflow_packet.xlsx
    offboarding_evaluation_summary.pdf
    offboarding_assessment_report.pdf
    offboarding_assessment_report.md

data_handling.md
results_summary.md
README.md
