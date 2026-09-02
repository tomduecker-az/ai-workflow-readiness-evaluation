# AI Workflow Readiness Evaluation

This repository contains public evaluation artifacts for an AI Workflow Readiness Assessment.

The assessment is designed to evaluate whether a documented workflow appears ready for AI-assisted automation: where AI may help, what should remain human-controlled, and which workflow, data, control, ownership, exception-handling, evidence, or human-review gaps should be addressed before building.

This is not a production-readiness certification. It is not a legal, compliance, security, or operational approval. It is also not a replacement for process owners, compliance teams, security teams, legal teams, or operational experts.

It is a structured first pass.

## Why I built this

A lot of AI automation conversations start with the model or the tool.

In practice, the harder questions often come earlier:

* Is the workflow clearly documented?
* Are the systems and data sources known?
* Are controls actually implemented in the workflow?
* Are human review points defined?
* Are exception paths documented?
* Are high-consequence actions kept out of AI control?
* Is there enough evidence to support automation decisions?
* What is the safest first build?

This project is my attempt to make those questions more structured, testable, and inspectable.

## What is included

* A blank workflow packet template
* Completed synthetic workflow packets
* Answer keys for the synthetic packets
* Generated assessment reports
* Evaluation summaries
* Results summary

## What is not included

The assessment code is not public at this stage.

The synthetic packets, answer keys, evaluation summaries, and generated reports are public so the results can be reviewed directly.

## Current public evaluation

The current public evaluation includes three synthetic workflow packets:

| Workflow                                             | Run type                                     | Planted defects | Found | Partial | Missed | Correct lookalike items | False positives | Unplanted valid findings |
| ---------------------------------------------------- | -------------------------------------------- | --------------: | ----: | ------: | -----: | ----------------------: | --------------: | -----------------------: |
| Employee Offboarding and Access Revocation           | Cold first run                               |              17 |    14 |       1 |      2 |                      10 |               0 |                        2 |
| Supplier CAPA and Nonconforming Material Disposition | Fourth run after targeted architecture fixes |              18 |    18 |       0 |      0 |                      10 |               0 |                        7 |
| Public Records Request Intake and Fulfillment        | Development baseline / regression case       |              10 |    10 |       0 |      0 |                       4 |               0 |                      ~24 |

## How to interpret the results

The evaluation summaries map the generated assessment reports back to the known synthetic test packets and answer keys.

The number of findings in the final report may not match the scoring table exactly. A report can merge related issues, partially capture a planted defect, miss a planted defect, or identify issues that were not intentionally planted.

The point is not to claim the assessment is perfect.

The point is to make the result inspectable: what it found, what it missed, where it was partially right, whether it created false positives, and what changed as the assessment architecture improved.

## Notes on each example

### Employee Offboarding and Access Revocation

This is the strongest cold first-run validation example.

The packet was authored by a separate AI assistant working from the intake template alone. The answer key was sealed until after the assessment had run.

The packet included 17 deliberately planted workflow defects and 10 deliberately correct lookalike items.

The assessment found 14 planted defects, partially caught 1, missed 2, produced 0 false positives against the lookalike items, and identified 2 additional valid findings that were not intentionally planted.

See:

* `evaluations/offboarding/offboarding_workflow_packet.xlsx`
* `evaluations/offboarding/answer_key.md`
* `evaluations/offboarding/offboarding_assessment_report.md`
* `evaluations/offboarding/offboarding_assessment_report.pdf`
* `evaluations/offboarding/offboarding_evaluation_summary.pdf`

### Supplier CAPA and Nonconforming Material Disposition

This is not a cold-run result.

The same synthetic packet was run four times as the assessment architecture improved. The progression was 9.5/18, 11.5/18, 14.5/18, and finally 18/18, with 0 false positives in the final run.

The value of this example is the run history. It shows where the assessment initially missed important categories, what architectural changes were made, and how those changes improved the result.

See:

* `evaluations/supplier_capa/supplier_capa_workflow_packet.xlsx`
* `evaluations/supplier_capa/answer_key.md`
* `evaluations/supplier_capa/supplier_capa_assessment_report.md`
* `evaluations/supplier_capa/supplier_capa_evaluation_summary.md`
* `evaluations/supplier_capa/supplier_capa_evaluation_summary.pdf`

### Public Records Request Intake and Fulfillment

This is a development baseline and regression case, not a blind validation test.

It was the first workflow packet built for this project, and the assessment system was developed against it. The current run found 10 of 10 planted defects with 0 false positives.

The important limitation is granularity. The run produced 35 findings against 10 planted defects. Some findings were technically valid but should be consolidated because they represented repeated instances of the same underlying issue.

This case is included because it explains why later held-out testing mattered.

See:

* `evaluations/public_records/public_records_workflow_packet.xlsx`
* `evaluations/public_records/answer_key.md`
* `evaluations/public_records/public_records_assessment_report.md`
* `evaluations/public_records/public_records_evaluation_summary.md`
* `evaluations/public_records/public_records_evaluation_summary.pdf`

## Data handling

Synthetic or de-identified workflow packets only.

Do not submit PHI, PII, customer-identifiable data, employee-identifiable data, supplier-confidential terms, trade secrets, credentials, access tokens, material non-public information, raw system exports, or real regulated records.

See `data_handling.md`.

## Current limitation

All current public test packets are synthetic. They were useful for controlled evaluation because the packets were created separately from the assessment logic and the answer keys were held back until after the runs.

That is still a limitation.

A stronger test is a workflow packet completed by someone else, using synthetic or de-identified data only.

## Repository structure

templates/
workflow_packet_template.xlsx

evaluations/
offboarding/
README.md
offboarding_workflow_packet.xlsx
answer_key.md
offboarding_assessment_report.md
offboarding_assessment_report.pdf
offboarding_evaluation_summary.pdf

supplier_capa/
README.md
supplier_capa_workflow_packet.xlsx
answer_key.md
supplier_capa_assessment_report.md
supplier_capa_evaluation_summary.md
supplier_capa_evaluation_summary.pdf

public_records/
README.md
public_records_workflow_packet.xlsx
answer_key.md
public_records_assessment_report.md
public_records_evaluation_summary.md
public_records_evaluation_summary.pdf

data_handling.md
results_summary.md
README.md
