# Employee Offboarding Evaluation

This folder contains synthetic evaluation artifacts for an employee offboarding and access revocation workflow.

## Role of this test

This is the strongest cold first-run validation example currently in the public evaluation set.

The workflow packet was authored by a separate AI assistant working from the intake template alone. The assessment system did not have access to the answer key during the run.

The packet was designed to test whether the assessment could identify workflow, control, ownership, exception-handling, data-governance, inventory, traceability, and evidence gaps in a workflow it had not seen before.

## Included files

* `offboarding_workflow_packet.xlsx`
* `answer_key_offboarding.md`
* `offboarding_assessment_report.md`
* `offboarding_assessment_report.pdf`
* `offboarding_evaluation_summary.pdf`

## Result

* 17 planted defects
* 14 found
* 1 partially caught
* 2 missed
* 10 deliberately correct lookalike items
* 0 false positives
* 2 unplanted valid findings

## Important limitation

This was a synthetic workflow packet. It is useful as a controlled validation test, but it is still not the same as evaluating a workflow packet completed by a real workflow owner or subject matter expert.

The assessment also did not catch everything. Two planted defects were missed, and one was only partially captured. Those misses are documented in the evaluation summary.

## Notes

This is a synthetic workflow packet. It does not contain real employee, customer, company, credential, system-access, HR, legal, or confidential data.

The assessment evaluates the submitted packet. It does not verify a real operating process, legal compliance, security posture, access-control posture, HR policy compliance, or production readiness.
