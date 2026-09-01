# Public Records Evaluation

This folder contains synthetic evaluation artifacts for a public records request intake and fulfillment workflow.

## Role of this test

This is a development baseline and regression case, not a blind validation test.

It was the first workflow packet built for this project, and the assessment system was developed against it. An early version scored well on this packet, then performed poorly on a later held-out packet. That failure exposed overfitting and led to architectural changes.

The current result should therefore be read as a regression result: the system now catches the planted issues in this packet without regressing on earlier behavior.

## Result

- 10 planted defects
- 10 found
- 0 partially caught
- 0 missed
- 4 deliberately correct lookalike items
- 0 false positives
- Approximately two dozen findings not planted

## Important limitation

This run produced 35 findings against 10 planted defects. The issue is not false positives; it is granularity. Some findings are technically correct but should be merged because they represent repeated instances of the same underlying issue.

This makes Public Records useful as a baseline and regression case, but not as the headline proof of generalization.

## Included files

- `public_records_workflow_packet.xlsx`
- `public_records_assessment_report.md`
- `public_records_evaluation_summary.md`
- `public_records_evaluation_summary.pdf`

## Notes

This is a synthetic workflow packet. It does not contain real requester, municipal, legal, law-enforcement, or records data.

The assessment evaluates the submitted packet. It does not verify a real operating process, legal compliance, security posture, or production readiness.
