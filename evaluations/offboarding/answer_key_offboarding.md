# Answer Key: Employee Offboarding Packet

**Read after the run.** This key lists the defects deliberately written into the accompanying
intake packet, and the items deliberately written to be correct while resembling defects.

The packet was authored by a separate AI assistant working from the intake template alone. This
key was sealed until after the assessment had run.

Seventeen defects were planted, plus a ten-item false-positive suite. All are content-level.
Structural validation passes cleanly: headers byte-identical, README and Allowed Values
untouched, all enum values inside their allowed lists, step sequence contiguous 1 to 12, every
forward reference from a step to a data field resolves.

The workflow fans out: one dispatch step sends five revocation tasks in parallel to identity,
privileged access, SaaS applications, facilities, and asset recovery. Several defects depend on
that shape.

---

## Controls with no implementing step

**1. Revocation is never verified against the target system.**
*CTRL-003, STEP-004, STEP-006*

The control states outright that a closed task is not evidence that access was removed, and
requires post-change verification against the target system. Neither mapped step verifies
anything. STEP-004 disables accounts, terminates sessions, revokes tokens, and removes group
memberships. STEP-006 removes access and records per-application completion. Both steps' pain
points confirm completion is recorded as task closure. The baseline seals it: seven of twelve
findings in the last quarterly access review involved accounts marked revoked that remained
active.

**2. Manager attestation is required and never captured.**
*CTRL-006, STEP-009*

The control requires the departing worker's manager to attest that access is no longer needed and
that data ownership has transferred, and requires the attestation to identify the attesting
manager. STEP-009 is owned by an IT Service Desk Analyst and its activity says only "confirm the
manager has what they need." No attestation is captured and no manager identity is recorded.

**3. Nothing establishes the litigation hold.**
*Primary Participants, `litigation_hold_flag`, STEP-010*

Legal Counsel appears in the participant list, owns no step, and holds no control role. The only
trace is a note on `litigation_hold_flag` saying Legal Counsel sets it. STEP-010 reads the flag
before deleting a mailbox. No step sets it. A gate exists with nothing that closes it.

---

## Rules that cannot be applied as written

**4. "A documented business need" is the entire standard for retained access.**
*CTRL-007*

No definition of what qualifies, no duration limit, no expiry or re-review, and no disposition
path when the need ends. The field intended to hold the justification,
`retained_access_justification`, is consumed by no step. REC-003's actual justification reads in
full: "Transition support needed." Roughly nine percent of departures carry one of these.

**5. "High-risk departures follow the expedited path," and high risk is never defined.**
*Workflow Steps, STEP-002*

`risk_classification` offers standard, elevated, and high with no criteria for any of them, no
owner of the definition, and no evidence requirement. The step's own pain point states that two
specialists reach different conclusions on similar facts. The expedited path removes access
before the worker has been informed, so an undefined term gates a consequential action.

**6. A four-hour requirement that cannot be measured.**
*CTRL-002*

The control requires privileged access revoked within four hours of "the effective termination
time," and requires the interval be measurable and reportable for every departure. The packet
offers four candidate start points, `notification_date`, `effective_termination_date`,
`last_working_date`, `revocation_start_timestamp`, and never says which starts the clock. No
field records revocation completion, so the interval is not computable under any interpretation.
REC-005 makes it concrete: notification 2026-05-21, effective termination 2026-05-18, dispatch
2026-05-18 07:05, meaning dispatch precedes notification by three days.

**7. A status value that no rule handles.**
*`manager_attestation_status`, STEP-009*

The field allows `no_response`. STEP-009 defines no wait period and no disposition when the
manager does not respond, and its own pain point says so. The samples show two different outcomes
for the same condition: REC-002 closed with `no_response`, REC-008 parked indefinitely at
`awaiting_manager` with `days_to_complete` blank.

---

## Conflicts between two rules

**8. Delete in thirty days versus retain for three years.**
*CTRL-004, CTRL-005*

CTRL-004 requires the mailbox and directory object permanently destroyed within thirty days of
the last working date. CTRL-005 requires all communications retained and retrievable for three
years from the same date. Both cannot hold, and no precedence rule exists. STEP-010 names
litigation hold as the only exception, which resolves a narrow case rather than the general
conflict. Four of eight sample records show `mailbox_disposition_status = deleted`, so in practice
the destruction control wins and the retention requirement is breached on every standard
departure.

**9. The approval design guarantees the separation-of-duties violation.**
*CTRL-007, CTRL-008, REC-002, REC-003*

CTRL-008 requires that whoever requests a revocation exception must not be the person who
approves it. CTRL-007 names the departing worker's manager as the approval authority for retained
access, and the manager is typically the requester. REC-002 shows requester and approver both as
IT Service Desk Analyst; REC-003 shows both as Departing Worker's Manager. Three signals: a
control-versus-control conflict and two sample records. Assembling them into one finding is the
stronger reading; reporting a single record is partial credit.

---

## Process structure

**10. Five parallel branches with nothing that brings them back together.**
*STEP-003 through STEP-008, STEP-012*

Revocation dispatches simultaneously to five queues. No step confirms all five finished. The case
closes when the service management platform shows no open tasks, which is a statement about one
tool's task states rather than about whether access actually stopped. REC-002 is closed with
`privileged_access_revoked = false` and `hardware_returned = false`.

This is the hardest defect in the packet. No control and no data field asserts that the join
should exist, so the only signals are the shape of the workflow and one contradictory record.

---

## Data governance

**11. `termination_reason_detail` is Confidential, cleared for model context, no redaction.**
*Data Dictionary*

Its own notes say it can describe investigation outcomes and allegations involving other named
workers, and REC-002's value does exactly that. CTRL-009 states the field must not be disclosed to
IT personnel and must not leave the HR Information System, and Known Constraints repeats the
restriction. The field's handling flags contradict all three.

**12. `personal_contact_email` is PII, cleared for model context, no redaction.**
*Data Dictionary*

Contrast with `retained_access_justification`, also sensitive and correctly set to `false`/`true`.

**13. The AI no-go list omits every irreversible action.**
*Workflow Overview, AI No-Go Areas*

It covers employment decisions and judgments about a worker's conduct. It omits permanent mailbox
and account destruction (STEP-010, stated irreversible), revocation execution, badge
deactivation, payroll deduction, and case closure. Six of the nine declared systems are
write-capable.

---

## Inventory and traceability

**14. An approval authority that does not exist.**
*CTRL-001*

The control gating the expedited path requires approval by "Security leadership."
`approval_required = true`, and no such role appears in the participant list.

**15. A declared system that no step uses.**
*Target Systems*

The Security Awareness Platform is in the system inventory and appears in no step.

Note that this packet contains only the declared-but-unused direction. No step uses an undeclared
system, so reporting one is a false positive.

**16. A field claiming use by a step that does not use it.**
*`retained_access_justification`, STEP-003*

The Data Dictionary maps the field to STEP-003; the step's data list omits it. This interlocks
with defect 4, since the field meant to document the business need is consumed by nothing.

---

## Sample evidence contradicting stated rules

**17. A mailbox deleted while under legal hold.**
*REC-004, STEP-010*

`litigation_hold_flag = true` with `mailbox_disposition_status = deleted`. STEP-010's exception
says accounts under hold are skipped. The action is irreversible. The tell is the contrast:
REC-005 also carries a hold and correctly shows `retained_on_hold`. One record follows the rule
and one destroyed evidence.

---

## Deliberately correct: flagging these is a scoring miss

The packet contains four fully specified rules and one fully implemented control written to draw
a wrong flag. Over-reporting is as damaging as under-detection: an assessment that flags
everything trains people to ignore it.

1. **STEP-008's hardware rule.** Fourteen calendar days, named owner, named action, jurisdiction
   condition, named evidence (a signed deduction authorization retained with the case), and a
   disposition path (write-off with a named approver and a recorded reason).
2. **STEP-005's shared-credential rule.** Rotation within the task, evidenced by the vault change
   record, with a time-bound exception naming a remediation date and service-owner notification.
3. **CTRL-010 is fully implemented by STEP-005.** Obligation, evidence, and accountable actor all
   present in the mapped step. This is the direct test that a control-implementation check is
   correctly bounded.
4. **STEP-011's final pay rule.** A jurisdiction-varying requirement resolved to a named source:
   the jurisdiction table maintained in the Payroll System.
5. **STEP-007's badge rule.** Five business days, named escalation target, defined action.
6. **All twelve step owners resolve to declared participants.** There is no generic step owner in
   this packet.
7. **REC-006's 63-day case with `hardware_returned = written_off`.** The rule working as designed.
8. **REC-005's `retained_on_hold`.** Correct handling, and the deliberate contrast to defect 17.
9. **REC-007.** A clean expedited involuntary departure handled correctly end to end.
10. **Badge tasks dispatched for remote workers who hold no badge.** Disclosed as queue noise in
    STEP-007's pain points. A design observation, not a defect.

Also legitimate and not defects: the SaaS directory's known incompleteness, the nightly HR
extract, the break-glass restriction on production entitlement writes, and business-hours support
coverage against four regions. All are stated constraints to design around.
