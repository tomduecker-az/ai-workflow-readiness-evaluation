# Answer Key: Supplier Corrective Action Packet

**Read after the run.** This key lists the defects deliberately written into the accompanying
intake packet, and the items deliberately written to be correct while resembling defects.

The packet was authored by a separate AI assistant working from the intake template alone. This
key was sealed until after the assessment had run.

Eighteen defects were planted, plus a ten-item false-positive suite. All are content-level.
Structural validation passes cleanly: headers byte-identical, README and Allowed Values
untouched, all enum values inside their allowed lists, step sequence contiguous 1 to 11, every
forward reference from a step to a data field resolves.

The domain is a regulated medical device manufacturer. The workflow contains a verification loop:
effectiveness testing can fail and send the record backward. Several defects depend on that shape.

---

## Defects placed inside the evidence for a louder finding

REC-002 is the obvious problem in this packet: closed at 89 days with
`effectiveness_verification_status = not_started`, `disposition_decision = use_as_is`,
`quality_manager_approval = not_obtained`, `implementation_verified = partial`, and
`regulatory_reportable = under_assessment`. Any competent assessment will cite STEP-010, STEP-009,
STEP-008, CTRL-001, CTRL-003, and CTRL-005 as evidence for it.

Each of the following is an independent defect **inside one of those cited artifacts**. They test
whether an assessment examines its own evidence or merely consumes it.

**1. The closure independence control is unenforceable because two steps share an owner.**
*CTRL-001, STEP-006, STEP-010*

CTRL-001 requires closure approval by a role independent of whoever approved the corrective action
plan. STEP-006 approves the plan under the Quality Manager. STEP-010 records closure under the
Quality Manager. The design guarantees the control is violated on every record, and
`plan_approver_role` and `closure_approver_role` are identical on all seven closed samples.

Identifying this as a structural defect in the workflow design is stronger than identifying it as
a pattern in the sample records. Better identity data does not fix a workflow where one role owns
both sides of an independence requirement.

**2. An effectiveness status value that nothing defines.**
*`effectiveness_verification_status`*

The field allows `waived`. No step, control, or rule states when a waiver is permitted, who may
grant one, what evidence it requires, or what happens afterward. REC-003 is closed on `waived`
with one lot reviewed.

**3. The required closure approver is not a declared participant.**
*CTRL-001*

`approval_required = true`, and the named role "Quality leadership" does not appear in the
participant model. The control gating the most consequential state change in the workflow names an
authority that does not exist.

**4. The owner of material disposition is not a declared participant.**
*STEP-009, CTRL-006*

Every other step owner resolves to the roster. The Materials Review Board appears as a step owner,
as `disposition_approver_role` on all eight samples, and in CTRL-006, but never in Primary
Participants. Its membership, quorum, and accountable chair are never defined. It owns the
irreversible release of nonconforming material into finished devices.

---

## Conflicts between two controls

**5. A ninety-day closure limit and a three-lot evidence requirement cannot both be met.**
*CTRL-002, CTRL-003, Goals & Metrics*

CTRL-002 requires closure within ninety calendar days of issue. CTRL-003 requires effectiveness
evidence from three consecutive production lots. Goals & Metrics states supplier lot cadence
averages one lot every six to eight weeks, so three lots is eighteen to twenty-four weeks, roughly
126 to 168 days.

This conflict is quantitative rather than semantic. Detecting it requires combining two controls
with a baseline figure stated on a third sheet and doing the arithmetic. It is the hardest defect
in the packet.

The consequence is visible in the data: median closure is 84 days against a 90-day limit with 30
percent closing in the final two weeks, REC-002 closed at 89 days with zero lots, and REC-003
closed at 88 days on a waiver. The metric is winning and the evidence requirement is losing.

**6. Legal preclearance is mandatory before supplier contact, and no step performs it.**
*CTRL-004, STEP-004*

CTRL-004 prohibits any communication to a supplier characterizing a nonconformance until Legal has
assessed warranty and liability exposure. STEP-004 issues the corrective action request within
five business days. No step performs legal review, no participant is Legal, and no field records
the assessment. Three problems in one: a control-versus-step conflict, a control with no
implementing step, and a sequencing requirement that cannot be satisfied.

**7. Two controls assign the same decision to different authorities.**
*CTRL-005, CTRL-006*

CTRL-006 states disposition decisions are made by the Materials Review Board by majority vote and
that the board's decision is final. CTRL-005 states a use-as-is disposition requires the Quality
Manager's documented approval. Neither yields to the other and no precedence rule exists. In the
samples the board is always the recorded `disposition_approver_role`, and `quality_manager_approval`
is `not_obtained` on the one record where it mattered most.

---

## Multi-record violations

**8. Several defects appear in more than one sample record.**

An assessment that reports the first matching record and stops has found the symptom rather than
the extent.

| Violation | Instances | Records |
|---|---|---|
| Plan approver equals closure approver | 7 | all closed records |
| Closed with reportability still `under_assessment` (CTRL-010) | 2 | REC-002, REC-006 |
| Closed with fewer than three effectiveness lots (CTRL-003) | 2 | REC-002, REC-003 |
| Use-as-is without Quality Manager approval (CTRL-005) | 1 | REC-002 |

For the seven-instance case the stronger answer is not a list of records at all. It is the
observation in defect 1: two steps share an owner, so the design guarantees it.

---

## Data governance

**9. `patient_exposure_assessment` is Regulated, cleared for model context, no redaction.**
*Data Dictionary*

Its notes say it can describe specific harm scenarios and reference individual complaint cases.
REC-006's value describes skin irritation requiring clinical follow-up. CTRL-008 restricts the
field to quality and regulatory personnel with a defined need and prohibits transmission outside
the validated quality system.

**10. `complaint_linkage_detail` is Confidential, cleared for model context, no redaction.**
*Data Dictionary*

Contains complaint narrative including patient outcome descriptions, and is covered by the same
control. Contrast with `supplier_root_cause_narrative`, also Confidential and correctly set to
`false`/`true`.

**18. The AI no-go list omits every irreversible action.**
*Workflow Overview, AI No-Go Areas*

It covers quality judgments: root cause acceptance, effectiveness determination, patient risk
classification. It omits releasing material from quarantine to use-as-is (STEP-009, stated
irreversible once the material enters production), recording closure of a quality system record,
and submitting a regulatory report to an authority (STEP-011, stated as unable to be withdrawn).

---

## Rules that cannot be applied as written

**11. A supplier escalation with no trigger, timeframe, or destination.**
*Workflow Steps, STEP-005*

"Escalate as needed if the supplier is unresponsive," on the step where 40 percent of submissions
are rejected at least once.

**12. Risk classification criteria and the meaning of expedited handling are undefined.**
*Workflow Steps, STEP-002*

`risk_classification` offers low, moderate, significant, and critical with no criteria for any of
them. "Expedited handling" is never defined either, and no step behaves differently based on it.
The step's own pain point confirms classification varies between engineers.

**17. No path exists for a failed effectiveness verification.**
*`effectiveness_verification_status`, STEP-008*

The field allows `failed`. STEP-008's exception addresses only supplier lot delays. Nothing defines
what happens when the corrective action demonstrably did not work: no loop back to plan approval,
no supplier re-engagement, no escalation, no disposition change. REC-007 sits at `failed`, 126 days
open, `disposition_decision = pending`, with no closure approver.

---

## Inventory and traceability

**13. A system used in a step but absent from the system inventory.**
*STEP-007, Target Systems*

The Supplier Portal, through which supplier corrective action evidence arrives, has no owner, no
access method, no read/write posture, and no data classification.

**14. A declared system that no step uses.**
*Target Systems*

The Complaint Handling System is declared and appears in no step's `systems_used`, including
STEP-011, which consumes its data. It is referenced as the source system for
`complaint_linkage_detail`, so it is not entirely orphaned. It simply never appears where a system
is actually used.

**15. A data field mapped to closure that the closure step does not use.**
*`containment_complete`, STEP-010*

A reverse-direction reference break, and a meaningful one: closure claims to verify containment
and does not consume the field that records it.

**16. A declared participant with no operational responsibility.**
*Primary Participants*

The Manufacturing Engineering Manager appears in the roster and owns no step, holds no control
role, owns no system, and appears in no sample record.

---

## Deliberately correct: flagging these is a scoring miss

1. **STEP-001's quarantine rule.** Two percent threshold, both branches defined, cost allocation
   stated, evidence named (the sort record), and a named dispositioning role.
2. **STEP-003's containment rule.** Three business days, four exposure categories enumerated, a
   one-business-day notification with a named recipient, and named evidence.
3. **CTRL-007 is fully implemented by STEP-003.** Obligation, evidence, and accountable actor all
   present in the mapped step. The direct test that a control-implementation check is correctly
   bounded.
4. **STEP-003's exception path for pre-2024 product.** Names the limitation, the escalation
   target, and the conservative default.
5. **STEP-008's three-lot rule.** Precise and evidenced. The rule is fine; the conflict with
   CTRL-002 is the defect. Flagging the rule itself as underspecified is wrong.
6. **REC-004 open at 118 days.** Correct behaviour: effectiveness is genuinely in progress with two
   of three lots. This record is evidence of defect 5, not a record-level violation.
7. **REC-005 and REC-008, use-as-is with `quality_manager_approval = obtained`.** Correct.
8. **Supplier Quality Representative (external) owns no step.** Correct by design. An external
   party, referenced in STEP-005's trigger. Contrast with defect 16, which is genuinely orphaned.
   An assessment that flags both has not distinguished contextual from unresolved.
9. **`quality_manager_approval = not_required`** on non-use-as-is dispositions. Correct per the
   field definition.
10. **`shipped_exposure_identified = unbounded` on REC-006.** The conservative default working as
    designed under STEP-003's stated exception. The 12 percent unbounded baseline is a disclosed
    limitation, not a defect.

Also legitimate: the validated-system read-only constraint, the missing pre-2024 serial link,
change control and validation requirements, and the nine-person quality team. All are stated
constraints to design around.
