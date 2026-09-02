# Answer Key: Public Records Request Packet

**Read after the run.** This key lists the defects deliberately written into the accompanying
intake packet, and the items deliberately written to be correct while resembling defects.

The packet was authored by a separate AI assistant working from the intake template alone. This
key was sealed until after the assessment had run.

Ten defects were planted. All are content-level. None violate the schema, the dropdown
validations, the header names, or the cross-sheet keys, so the packet passes structural
validation cleanly and can only fail on judgment.

Defects 1, 2, and 3 are the ones that matter most. An AI readiness assessment that misses those
is not doing its job.

---

## Data governance

**1. `withholding_rationale` is cleared for model context and marked no-redaction.**
*Data Dictionary*

The field is classified `Confidential` and holds analyst-authored free text that, by definition,
describes the content of material the City decided to withhold, including privileged advice and
witness identity. It is set `model_context_allowed = true` and `redaction_required = false`. The
one field that describes exempt content is the field cleared to enter a model.

**2. `requester_contact_email` is PII, cleared for model context, no redaction.**
*Data Dictionary*

Classified `PII`, set `model_context_allowed = true`, `redaction_required = false`. The adjacent
field `requester_contact_name` carries the same classification and is correctly set to
`false`/`true`. The inconsistency between two neighbouring fields of the same class is the tell.

**3. The AI no-go list omits the workflow's only irreversible external action.**
*Workflow Overview, AI No-Go Areas*

The stated boundary covers legal determinations only. STEP-009 delivers records to a member of
the public, which cannot be undone and carries statutory consequence. It is not named as a no-go
anywhere.

---

## Sample evidence contradicting stated rules

**4. A record is released while legal review is still pending.**
*Sample Records, REC-002*

`current_status = released` while `legal_review_status = pending`. CTRL-001 states no record may
be delivered until the legal determination is complete. This is a live control violation sitting
in the evidence, on the highest-profile request in the sample set: a media requester with
privilege asserted. Noticing that it is the only record where this occurs, and treating that as
evidence the control is not enforced in the system, is the stronger reading.

---

## Accountability and authority

**5. A routing step is owned by a group rather than an accountable role.**
*Workflow Steps, STEP-004*

Owner is `Records team`. Every other step names a specific role. STEP-004 assigns work to
departments and sets internal due dates, so nobody owns the routing decision or the aging clock
at the point where the workflow most often goes wrong.

**6. A control requiring approval names an approver who does not exist.**
*Policy Controls, CTRL-008*

`approval_required = true` with `approval_role = Department leadership`. Not a named role, and
not reconcilable against the participant list in Workflow Overview. A control with an
unidentifiable approver cannot be automated or audited.

---

## Rules that cannot be applied as written

**7. The fee waiver rule has no threshold and no authority.**
*Workflow Steps, STEP-003*

"Fees may be waived when the cost of processing is minimal." No dollar threshold, no definition
of minimal, no named decision-maker. This pairs with defect 6: the control and the step are both
vague about the same decision, from opposite directions.

**10. The highest-cost step's escalation path is stated as "escalate as needed."**
*Workflow Steps, STEP-006*

No trigger, no threshold, no destination, on the step that consumes the most staff time and
carries the most risk. Every other step names a specific escalation condition.

---

## Coverage gaps

**8. No appeal or challenge path exists anywhere in the workflow.**
*Workflow Steps and Policy Controls, all*

`current_status` includes `denied`, CTRL-007 references deemed-denial exposure, and Goals &
Metrics states roughly 6 percent of denials draw a formal challenge. No step, no control, and no
role covers what happens when a requester challenges a denial.

This is the hardest defect in the packet. Nothing in the packet asserts the path should exist, so
there is no artifact to contradict and no reference to dereference. It can only be found by
comparing the documented process against what a request-handling workflow requires.

**9. A repository used in the search step is absent from the system inventory.**
*Workflow Steps, STEP-005*

`Records Center Archive` appears in the step and is absent from Target Systems and from the
Systems Involved list in Workflow Overview. An undeclared repository with no stated owner, no
access method, and no read/write posture, in the step that touches the most content.

---

## Deliberately correct: flagging these is a scoring miss

These resemble defects and are not.

- **`legal_review_status = not_required` on REC-003 and REC-005.** Both are routine requests with
  no withholdings, which STEP-007's rule explicitly permits to bypass legal review.
- **REC-005 has empty contact fields.** Anonymous requests are accepted by design, as STEP-001
  states. The blank is realistic, not missing data.
- **Arizona sets no fixed statutory day count.** `response_due_target` is an internal service
  target, not a legal deadline. Flagging the City for missing a statutory deadline misreads Known
  Constraints. A.R.S. 39-121.01(D)(1) requires prompt furnishing and 39-121.01(E) treats a failure
  to respond promptly as a denial, but neither sets a day count.
- **The Records Management System is read-only.** Marked `write_access_possible = false` in Target
  Systems and stated in Known Constraints. A genuine constraint to design around, not an oversight.

### Correction to this key

An earlier version of this key also listed `legal_review_status = not_required` on **REC-001** as
correct. That was wrong. REC-001 carries a personal-privacy withholding, and STEP-007's bypass
clause applies only to requests with no withholdings. The assessment flagged the record and read
the rule correctly. The key did not. It is recorded here rather than quietly removed, because a
test is only useful if its own errors are visible.
