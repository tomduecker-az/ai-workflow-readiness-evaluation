# Public Records Request Workflow - Evaluation Summary

*All data in the accompanying packet is synthetic. No real requester, record, or municipal information is included.*

## Purpose

This document accompanies a synthetic public records request intake and fulfillment workflow packet, modeled on a mid-size Arizona municipality and used as a controlled test of an AI workflow readiness assessment.

The assessment evaluates whether a documented workflow is a good candidate for AI-assisted automation: where AI may help, what should stay human-controlled, and which gaps to address first. It also reports on the completeness of the submitted packet. It had no access to this summary.

## Evaluation result

| Planted defects | Found | Partially caught | Missed | Correct lookalike items | False positives | Findings not planted |
|---|---|---|---|---|---|---|
| 10 | 10 | 0 | 0 | 4 | 0 | ~24 |

The packet passed spreadsheet validation cleanly. Nothing found was a formatting error or a broken reference. These are workflow, data, control, and AI-readiness issues a team would need to understand before pursuing automation.

The evaluation maps the report back to the planted-defect key. It is not the report's finding count, which merges some defects and adds unplanted ones.

## This packet is the development baseline, not a blind test

This was the first packet ever built, and the system was developed against it. An early version scored 90 percent here and then scored 44 percent on the first packet it had never seen, which is what prompted rebuilding the detection architecture rather than tuning prompts.

A perfect score on this packet therefore says nothing about generalization. It is a regression check: confirmation that four rounds of architectural change did not break anything that previously worked.

For results on material the system had not been corrected against, see the offboarding evaluation, which scored 14.5 of 17 on a first run with zero false positives.

One item is worth noting. Defect 8, the absence of any appeal or challenge path for a denied request, was missed in three consecutive early runs. It was the clearest evidence of a structural blind spot: the system could find contradictions between things that existed, but not the absence of a process stage that no control or data field pointed at. It is caught here.

## The 10 planted defects

| # | Defect | Result |
|---|---|---|
| 1 | Confidential withholding rationale marked available to a model with no redaction | Found |
| 2 | Requester email classified as PII but cleared for model context, with the adjacent name field correctly restricted | Found |
| 3 | The AI no-go list omits the workflow's only irreversible external disclosure | Found |
| 4 | A sample record shows records released while mandatory legal review is still pending | Found |
| 5 | A routing step owned by a group rather than an accountable role | Found |
| 6 | A fee-waiver control whose named approver is not a declared participant | Found |
| 7 | A fee-waiver rule with no threshold, no definition, and no named decision-maker | Found |
| 8 | No appeal or challenge path exists anywhere for a denied request | Found |
| 9 | A repository used in the search step but absent from the system inventory | Found |
| 10 | The highest-cost step's escalation stated only as "escalate as needed" | Found |

## Findings beyond the evaluation key

Roughly two dozen findings were not planted. Four are worth naming:

- **An aging dashboard could increase legal exposure.** Requests forwarded by departments are logged on the Clerk's receipt date rather than the City's. Displaying age from the later date produces a more confident wrong answer than the current manual process. The assessment argued against a feature the packet itself proposed.
- **The most attractive AI use cases depend on blocked data.** Clarification drafting requires request text, and exemption pre-screening requires protected-identity content. Both are prohibited from model context by the packet's own rules.
- **A sample record contradicts the stated exemption authority.** One record shows a redaction applied with legal review marked not required, against a rule reserving exemption decisions to the City Attorney's Office. The original answer key listed this as correct behavior. The assessment read the rule more literally and was right; the key was wrong.
- **An abandonment rule that cannot fire.** One record is marked abandoned for failure to respond to a clarification request, but it is an anonymous request with no contact channel, so no clarification could have been sent.

## Precision, and a granularity problem

None of the four deliberately correct items were reported. The assessment did not treat the internal response target as a statutory deadline, did not flag anonymous records as missing data, and did not report the read-only records system as a defect. Its open questions explicitly ask how to govern aging "without implying a fixed statutory deadline," which is the distinction most human readers get wrong about Arizona public records law.

Precision on planted traps is not the whole picture, though. This run produced 35 findings against 10 planted defects, a much higher ratio than the other published tests. Some of that is real. Some is over-decomposition:

- Six separate findings report that a target system's owner string does not resolve to a declared participant. That is one issue reported six times.
- Three separate findings report that one data field is mapped to three steps that do not list it. That is one issue reported three times.
- The escalation placeholder is reported twice, once by each detection layer.

Every one of these is technically correct and none is a false positive. But eleven findings covering three underlying issues is noise, and a reader triaging this report would feel it. Merging on defect identity rather than on instance is the clearest remaining improvement.

## Reading the result

Ten of ten on the packet the system was built against is the expected outcome, not a claim. The useful signals here are narrower: a blind-spot class that failed three times now succeeds, no regression on anything that previously worked, and a granularity problem that is visible precisely because the detection side has gotten good enough for it to surface.

The assessment evaluates what the packet says, not what an organization does. It cannot know what was never documented, and its output needs review by people who know the process.
