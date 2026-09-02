# Supplier CAPA Evaluation

This folder contains synthetic evaluation artifacts for a supplier corrective action and nonconforming material disposition workflow.

## Role of this test

This is not a cold first-run validation test.

The same packet was run four times, with targeted architectural changes between runs. The value of this example is the run history: it shows where the assessment initially missed important categories, what changed in the architecture, and how those changes improved the result.

The final publication run should be read as an architecture-improvement result, not as a blind perfect score.

## Included files

* `supplier_capa_workflow_packet.xlsx`
* `answer_key_supplier_capa.md`
* `supplier_capa_assessment_report.md`
* `supplier_capa_evaluation_summary.md`
* `supplier_capa_evaluation_summary.pdf`

## Result

Final publication run:

* 18 planted defects
* 18 found
* 0 partially caught
* 0 missed
* 10 deliberately correct lookalike items
* 0 false positives
* 7 unplanted valid findings

The run history matters. The first run scored 9.5 of 18. The final run scored 18 of 18 after three targeted architecture changes.

## Important limitation

This result should not be read as a cold-run generalization test. The same packet was used across multiple runs to identify and fix architectural blind spots.

That makes it useful for showing system improvement, but not as the headline proof of first-run performance.

## Notes

This is a synthetic workflow packet. It does not contain real supplier, product, patient, company, regulatory, or confidential data.

The assessment evaluates the submitted packet. It does not verify a real operating process, legal compliance, security posture, validation posture, or production readiness.
