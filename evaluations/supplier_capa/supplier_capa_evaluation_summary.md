# Supplier Corrective Action Workflow - Evaluation Summary

All data in the accompanying packet is synthetic. No real supplier, product, patient, or company information is included.

## Purpose

This document accompanies a synthetic supplier corrective action and nonconforming material disposition workflow packet, used as a controlled test of an AI workflow readiness assessment. The domain is a regulated medical device manufacturer, chosen because the governing regime, the process shape, and the irreversible actions all differ from the other published tests.

The assessment evaluates whether a documented workflow is a good candidate for AI-assisted automation: where AI may help, what should stay human-controlled, and which gaps to address first. It also reports on the completeness of the submitted packet.

It had no access to this summary.

## Evaluation result

| Planted defects | Found | Partially caught | Missed | Correct lookalike items | False positives | Unplanted defects found |
|---:|---:|---:|---:|---:|---:|---:|
| 18 | 18 | 0 | 0 | 10 | 0 | 7 |

The packet passed spreadsheet validation cleanly. Nothing found was a formatting error or a broken reference. These are workflow, data, control, and AI-readiness issues a team would need to understand before pursuing automation.

The evaluation maps the report back to the planted-defect key. It is not the report's finding count, which merges some defects and adds unplanted ones.

## This was not a first run

This packet was run four times. The system was modified between runs based on what it missed.

| Run | Planted defects found | What changed before the next run |
|---:|---|---|
| 1 | 9.5 of 18 | Deterministic findings were being absorbed into other findings and dropped when no match existed |
| 2 | 11.5 of 18 | Cross-sheet reference checks ran in only one direction |
| 3 | 14.5 of 18 | No comparison existed between two artifacts that had each already produced a finding |
| 4 | 18 of 18 | - |

The first run is the honest measure of the system before this packet taught it anything. The last run measures it after three targeted architectural changes. Both numbers matter, and neither should be read alone.

For a genuinely cold result on material the system had never been corrected against, see the offboarding evaluation: 14.5 of 17, zero false positives, first run.

## The 18 planted defects

| # | Defect | Result |
|---:|---|---|
| 1 | The closure independence control is unenforceable because two steps share an owner | Found |
| 2 | An effectiveness status value that no rule, authority, or evidence requirement defines | Found |
| 3 | The required closure approver is not a declared participant | Found |
| 4 | The owner of material disposition is not a declared participant | Found |
| 5 | A 90-day closure limit and a three-lot evidence requirement cannot both be met at stated supplier cadence | Found |
| 6 | Legal preclearance is mandatory before supplier contact, and no step performs it | Found |
| 7 | Two controls assign final disposition authority to different parties | Found |
| 8 | Multi-record violations reported for every affected record, not only the first | Found |
| 9 | Patient exposure narrative marked model-available against a stated restriction | Found |
| 10 | Complaint linkage detail marked model-available with no redaction | Found |
| 11 | A supplier escalation with no trigger, timeframe, or destination | Found |
| 12 | Risk classification criteria and the meaning of expedited handling are undefined | Found |
| 13 | A system used in a step but absent from the system inventory | Found |
| 14 | A declared system that no step uses | Found |
| 15 | A data field mapped to closure that the closure step does not use | Found |
| 16 | A declared participant with no operational responsibility | Found |
| 17 | No path exists for a failed effectiveness verification | Found |
| 18 | The AI no-go list omits every irreversible action | Found |

## Findings beyond the evaluation key

Seven findings were not planted. They are defects made while building the packet, which is closer to what real workflow documentation contains, since nobody puts those there on purpose. Three worth naming:

- An AI goal that conflicts with the packet's own data rule. The packet proposes scoring supplier root cause submissions, and separately marks that narrative as barred from model context.
- Step sequence contradicts a stated rule. Disposition is numbered after effectiveness verification while its own rule says disposition proceeds on material risk without waiting.
- A second authority conflict. The low-defect-rate sort path assigns disposition to a Quality Engineer, while a control gives the Materials Review Board exclusive final authority over disposition.

The remaining four concern partial implementation as a trigger for effectiveness testing, an unbounded shipped-exposure state with no resolution path, a request deadline whose prerequisite chain has no deadline of its own, and a prioritization goal with no supporting data.

## Precision

None of the ten deliberately correct items were reported. These included fully specified threshold rules, a control its mapped step genuinely implements, an exception path that names its own limitation, correctly handled sample records, and disclosed operational constraints.

Two are worth calling out because they sit close to real defects. One sample record is open well past the closure limit, which looks like a violation and is in fact the correct behavior that proves defect 5. Another carries an unbounded exposure status that is the packet's own conservative default working as designed. The assessment used the first as evidence and did not flag the second, while still identifying the genuine problem beside it.

## Reading the result

A perfect score on a packet the system has been tuned against is a statement about the fixes, not about general capability. The run history above is the more useful number. What this test shows is that three specific architectural changes closed three specific classes of blind spot, and that precision held at zero false positives across all four runs while detection more than doubled.

The assessment evaluates what the packet says, not what an organization does. It cannot know what was never documented, and its output needs review by people who know the process.
