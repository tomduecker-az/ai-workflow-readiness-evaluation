# Supplier Corrective Action and Nonconforming Material Disposition — AI Workflow Assessment

## Executive Brief

**Recommendation:** Proceed only with a gated, read-only decision-support pilot. The workflow has a strong AI opportunity, but the packet is not ready for broad AI deployment: sample records show control-bypass states, status labels cannot be treated as evidence of compliant completion, and sensitive-data permissions conflict with documented restrictions.

**First build:** A source-linked Containment Trace Workbench using approved Quality Management System and Enterprise Resource Planning reporting data. It should assemble the four required exposure categories, show query criteria and retrieval time, link underlying records, and visibly preserve any unbounded exposure. Patient, complaint, and supplier-proprietary narratives must be excluded from the pilot context.

**Why this first:** Containment is a documented bottleneck: it averages 4.5 business days against a three-day requirement, and the manual trace takes most of a day. The use case can be isolated from unreliable closure, effectiveness, reportability, and disposition statuses. It also fits the documented read-only integration posture and the stated tolerance for over-flagging.

**Estimated effort:**

- Duration: Planning guidance: approximately 10–16 weeks for scoped design, data mapping, prototype, representative testing, change control, and intended-use validation.
- Confidence: Medium-low; connector details, validation expectations, source-data quality, environments, and internal resource availability are not provided.
- Workstreams:
  - Approved-boundary and data-exclusion design
  - Read-only QMS and ERP data mapping
  - Four-category trace logic and source provenance
  - Reviewer interface and unbounded-exposure handling
  - Representative test set, validation evidence, and operating procedures
  - Pilot measurement and reviewer training

**Estimated cost:**

- Range: Planning guidance only, not a vendor quote: approximately US$200,000–$450,000 for the bounded pilot.
- Confidence: Low-medium. Refine with architecture, connector effort, security review, validation depth, delivery rates, environment costs, and expected pilot volume.
- Assumptions:
  - Scope is limited to QMS and ERP read-only reporting access, a reviewer-facing interface, audit logging, and validation documentation.
  - No system-of-record writes, hold actions, external communications, patient or complaint narratives, supplier submissions, or Supplier Portal integration are included.
  - Existing enterprise identity, hosting, and reporting access can be reused.
  - The estimate includes external delivery capacity because the nine-person quality team has no dedicated technical resource.
  - Excludes recurring model or platform licenses, internal staff time, procurement, serial-link remediation, historical data cleansing, procedure remediation, and production-scale support.

**ROI / value hypothesis:**

- Confidence: Low for financial ROI; medium-high that the pilot addresses a documented cycle-time and evidence-quality problem.
- Expected value:
  - Theoretical value ceiling, not a forecast: convert a trace that currently takes most of a day into a reviewer-ready package produced in hours across a workflow handling about 210 records annually.
  - Improve the likelihood of meeting the three-business-day containment requirement and the stated target of 90 percent on-time performance.
  - Reduce manual evidence assembly and make trace limitations visible rather than allowing missing links to appear complete.
  - Create reusable provenance and consistency-check components for later status monitoring and audit-narrative support.
- Not counted yet:
  - Avoided patient or quality events, regulatory findings, certification impact, or quarantine carrying cost; the packet does not provide defensible valuation inputs.
  - The target to halve 160 annual audit-preparation hours, because audit narrative generation is not part of the first build.
  - Benefits from root-cause scoring, disposition prioritization, or recurring-failure detection, because those use cases have unresolved data or rule dependencies.
- Inputs needed to quantify:
  - Average labor time and loaded cost for current containment traces by record type
  - Percentage of records requiring each trace category and reviewer correction rates
  - Cost of delayed containment and engineering over-flag review
  - Pilot run volume, adoption, and time saved after human review
  - Build, validation, hosting, support, and change-management costs

**Executive decisions needed:**

- Authorize a bounded discovery and validation phase, not production deployment.
- Approve a default-deny data scope excluding patient exposure narratives, complaint details, and supplier-proprietary submissions.
- Assign business ownership for source-data validation, containment review, and unbounded-exposure escalation.
- Require remediation or formal disposition of the critical sample contradictions before status fields are reused for broader AI assistance.
- Expand the governance boundary to prohibit AI-controlled decisions, approvals, material release or movement, holds, record writes, closure or reopening, supplier/customer communications, and regulatory determinations or submissions.

## Packet Completeness and Evidence Sufficiency

**Overall status:** partial

**Assessment confidence:** Limited confidence in areas where the submitted packet has partial evidence.

The submitted packet supports a limited AI readiness assessment, but some areas are only partially documented. Recommendations should identify uncertainty and avoid inferring facts not present in the packet.

### Areas that limit assessment confidence

- **Sample records (partial):** Limits confidence in whether documented controls, statuses, data fields, and lifecycle paths appear in realistic workflow examples.
- **Goals and metrics (partial):** Limits confidence in business value, prioritization, success metrics, and whether the proposed AI use case is worth building.

### Recommended packet improvements

- Provide synthetic or de-identified sample records that show normal, exception, incomplete, delayed, and edge-case states where applicable.
- Define AI goals, success metrics, baseline performance, desired improvement, risk tolerance, and measurement approach.

## Recommended Product Concept

### Containment Evidence Workbench

**Pitch:** Turns lot-genealogy data into a reviewable, source-linked exposure package without deciding that containment is complete.

**Target users:**

- Manufacturing Quality Lead
- Quality Manager
- Authorized quality reviewers

**Workflow moment:**

After human risk classification, when exposure must be traced across on-hand inventory, work in process, finished goods, and shipped product.

**Before:**

A reviewer manually runs ERP traces, reconstructs exposure categories, and may spend most of a day resolving incomplete shipped-product links.

**After:**

The reviewer receives a timestamped draft showing each exposure category, source records, query criteria, missing links, and explicit unbounded status for confirmation and governed follow-up.

**Sample assistant output:**

- **Trace coverage:** On-hand inventory, work in process, finished goods, and shipped product shown as separate evidence sections.
- **Evidence provenance:** Each result includes source record, retrieval time, and query criteria.
- **Limitation:** Pre-2024 shipped-device linkage unavailable; exposure remains unbounded and requires human escalation.
- **Reviewer action:** Confirm source coverage and determine governed containment actions; the workbench does not mark containment complete.

**What AI does:**

- Organizes approved structured data into the required four-category containment view.
- Summarizes source-linked results and separates missing evidence from a negative finding.
- Flags inconsistent or absent source evidence and preserves known trace limitations.
- Produces an auditable draft for human review.

**What AI does not do:**

- The product contains no execution path; it does not make quality conclusions or change workflow state.

**Demo moment:**

A reviewer selects a suspect lot and receives a four-part exposure package in hours rather than manually assembling it across systems, with the pre-2024 serial-link limitation displayed as unbounded rather than silently treated as complete.

## Packet Quality Findings

### Critical: Patient and complaint narratives are marked as allowed in model context despite a validated-system restriction.

**Evidence reference:** patient_exposure_assessment and complaint_linkage_detail permit model context without redaction; CTRL-008 restricts them by need and prohibits transmission outside the validated quality system.

**Why it matters:** Read-only access does not authorize onward transmission to an undeclared AI environment.

**Recommended resolution:** Default-deny both fields; define approved hosting, validation, access, logging, retention, vendor use, deletion, and a validated minimum-necessary transformation if needed.

**Detection source:** Adversarial

### Critical: REC-002 and REC-003 bypass the mandatory three-lot effectiveness requirement.

**Evidence reference:** REC-002 is closed with effectiveness not started and zero lots; REC-003 is closed as waived after one lot; CTRL-003 requires three consecutive qualifying lots.

**Why it matters:** Closed and waived labels cannot safely ground completion checks or audit narratives.

**Recommended resolution:** Block closure without three linked passing lots; remove waived or establish a formally approved alternate-verification control with authority and evidence.

**Detection source:** Adversarial

### Critical: REC-002 and REC-006 are closed while regulatory reportability remains under assessment.

**Evidence reference:** Both records show regulatory_reportable=under_assessment and scar_status=closed; CTRL-010 requires conclusion and reasoning before closure.

**Why it matters:** Closed status cannot prove regulatory obligations were resolved, particularly where REC-006 also shows critical risk and unbounded exposure.

**Recommended resolution:** Create an accountable Regulatory Affairs assessment step, hard-block closure while under assessment, and define submission-state sequencing and evidence.

**Detection source:** Adversarial

### Critical: REC-002 shows use-as-is disposition without required Quality Manager approval.

**Evidence reference:** REC-002: disposition_decision=use_as_is, quality_manager_approval=not_obtained, scar_status=closed; CTRL-005 requires approval before release.

**Why it matters:** Use-as-is release is irreversible, and AI relying on the closed or disposition status could normalize a demonstrated control bypass.

**Recommended resolution:** Investigate and correct REC-002; require identified approver, timestamp, signature, disposition-specific approval, and a system-enforced release gate.

**Detection source:** Adversarial

### High: Failed effectiveness has no defined corrective lifecycle.

**Evidence reference:** The data model permits failed; STEP-008 defines only delayed-lot handling; REC-007 is failed, pending disposition, and open at 126 days.

**Why it matters:** A monitor can identify failure but cannot ground a compliant next action.

**Recommended resolution:** Define ownership, containment and risk-reassessment triggers, supplier response, plan reapproval, new dates, status transitions, and restart criteria.

**Detection source:** Adversarial

### High: Final board authority conflicts with mandatory Quality Manager approval for use-as-is disposition.

**Evidence reference:** CTRL-006 calls the board decision final; CTRL-005 separately requires Quality Manager approval before use-as-is release.

**Why it matters:** The packet does not define authority order, veto effect, or the state following disagreement.

**Recommended resolution:** Define the board vote as the decision and Quality Manager concurrence as a separate release prerequisite, including denial and reconsideration handling.

**Detection source:** Artifact-pair

### High: Independent closure cannot be enforced or audited from role-only approval evidence.

**Evidence reference:** CTRL-001 requires independence; STEP-006 and STEP-010 are both owned by Quality Manager, and the data captures roles rather than individual actors.

**Why it matters:** The packet cannot prove that different individuals performed plan approval and closure.

**Recommended resolution:** Capture immutable identity, role at action time, timestamp, and signature; define eligible independent approvers and enforce same-individual exclusion.

**Detection source:** Adversarial

### High: Materials Review Board majority-vote authority is absent from the evidence model.

**Evidence reference:** CTRL-006 requires majority vote and minutes; STEP-009 records only an approver role and Quality Manager approval, and the board is not a declared participant.

**Why it matters:** A role label cannot prove attendance, quorum, vote, or authorized disposition.

**Recommended resolution:** Declare the board and coordinator; define membership, quorum, votes, ties, recusals, signed minutes, and linkage to disposition.

**Detection source:** Adversarial

### High: Partial implementation conflicts with the verified-implementation trigger for effectiveness testing.

**Evidence reference:** STEP-007 and the data model permit partial implementation, while STEP-008 requires verified implementation and CTRL-003 depends on a valid implementation date.

**Why it matters:** The qualifying start date for the three-lot sequence is indeterminate.

**Recommended resolution:** Define partial as a blocker or controlled exception; require action-level evidence, identified approval, authoritative implementation date, and explicit status conversion.

**Detection source:** Artifact-pair

### High: Quality Engineer disposition after a one-hundred-percent sort conflicts with exclusive board authority.

**Evidence reference:** STEP-001 assigns sort-outcome disposition to the Quality Engineer; CTRL-006 and STEP-009 assign nonconforming-material disposition to the Materials Review Board.

**Why it matters:** Automation cannot determine the correct authority for sorted material.

**Recommended resolution:** Separate authorization to sort from final disposition and route results to the board, or formally document a scoped procedural exception.

**Detection source:** Artifact-pair

### High: Risk classification criteria and the operational meaning of expedited handling are undefined.

**Evidence reference:** STEP-002 names four classes and says significant cases are expedited, while noting inconsistent classification and providing no class-specific route.

**Why it matters:** Assistants would consume inconsistent labels and cannot safely calculate urgency or explain routing.

**Recommended resolution:** Approve a classification matrix, examples, rationale standard, reviewer qualifications, and class-specific timing, evidence, notification, and closure gates.

**Detection source:** Adversarial

### High: Root-cause scoring depends on content explicitly barred from model context.

**Evidence reference:** supplier_root_cause_narrative is confidential, requires redaction, and has model_context_allowed=false; CTRL-009 restricts external-boundary transmission.

**Why it matters:** The scoring goal is not implementation-ready even as an advisory feature.

**Recommended resolution:** Exclude it until an approved in-boundary architecture, contract basis, Supplier Portal lineage, and utility-preserving validated transformation exist.

**Detection source:** Adversarial

### High: Sequential numbering conflicts with the requirement to disposition material independently of effectiveness verification.

**Evidence reference:** STEP-009 follows STEP-008, although disposition must not wait; three lots at six-to-eight-week cadence imply at least 12–16 weeks between lot intervals versus the under-30-day dwell target.

**Why it matters:** A queue cannot overcome a structural dependency that keeps material waiting behind verification.

**Recommended resolution:** Model disposition as a parallel branch after risk classification and containment, with its own queue, deadline, escalation, approvals, and closure join.

**Detection source:** Artifact-pair

### High: The documented AI no-go statement omits the workflow's highest-consequence actions.

**Evidence reference:** The no-go text names three quality judgments but omits disposition, release, reportability, approvals, writes, closure, external communications, and regulatory submission.

**Why it matters:** Implementers could interpret general AI assistance as permission for consequential action.

**Recommended resolution:** Expand the formal boundary to cover all consequential decisions, release actions, writes, closures, external contacts, and submissions, with visible AI provenance.

**Detection source:** Adversarial

### High: The independence control is not implementable from workflow ownership and approval evidence.

**Evidence reference:** CTRL-001, STEP-006, and STEP-010 use the same owner role and role-level approval fields.

**Why it matters:** This structural defect prevents enforcement even apart from whether any particular sample used the same person.

**Recommended resolution:** Assign an eligible independent queue, capture immutable actor evidence, and add a same-individual exclusion before closure.

**Detection source:** Deterministic

### High: The ninety-day closure mandate conflicts with mandatory three-lot evidence when supplier cadence is insufficient.

**Evidence reference:** CTRL-002 requires closure within 90 days; CTRL-003 requires three lots; normal lot cadence is six to eight weeks, and REC-004 remains in verification at 118 days.

**Why it matters:** There is no safe optimization objective: timeliness pressure can reward premature closure, while evidence compliance can force lateness.

**Recommended resolution:** Define controlled extensions or an approved alternate method, including authority, rationale, evidence, revised date, and management reporting.

**Detection source:** Adversarial

### High: The required 'Quality leadership' closure approver is not a declared participant.

**Evidence reference:** CTRL-001 approval_role versus Primary Participants.

**Why it matters:** The approval control cannot be reliably routed, enforced, or audited.

**Recommended resolution:** Resolve the label to declared eligible roles or add the role and its authority to the participant model.

**Detection source:** Deterministic

### High: The supplier-communication step does not implement mandatory Legal preclearance.

**Evidence reference:** CTRL-004 requires Legal assessment; STEP-004 issues the request but lists no Legal actor, input, evidence, precondition, or denial path.

**Why it matters:** Faster drafting could accelerate discoverable communication past a paper-only control.

**Recommended resolution:** Add a Legal assessment step, accountable role, linked evidence, approval/revise/deny outcomes, and timing reconciled with the five-day deadline.

**Detection source:** Adversarial

### High: The supplier-request deadline can become infeasible because its prerequisite chain lacks a classification deadline.

**Evidence reference:** STEP-004 requires completed containment and issue by day five from record creation; STEP-003 allows three days after classification; STEP-002 sets no classification deadline.

**Why it matters:** Deadline calculation and escalation cannot be reliable when the request may not become issuable before it is due.

**Recommended resolution:** Set classification within two business days, rebase the request deadline, or define a controlled preliminary-request path.

**Detection source:** Artifact-pair

### High: Unbounded shipped exposure has no executable resolution path.

**Evidence reference:** STEP-003 requires escalation and continued unbounded treatment; REC-006 is nevertheless containment_complete=true and closed while exposure is unbounded.

**Why it matters:** The current state model can conceal unresolved external exposure.

**Recommended resolution:** Define alternate trace requirements, accountable owner, Regulatory Affairs involvement, deadlines, evidence, closure gate, and criteria for bounded or formally unresolved status.

**Detection source:** Adversarial

### Medium: Complaint Handling System data lineage is not reflected in workflow-step system usage.

**Evidence reference:** complaint_linkage_detail cites Complaint Handling System, but no workflow step lists that system.

**Why it matters:** The point of use, access control, and AI boundary for sensitive complaint data are unclear.

**Recommended resolution:** Map the system to the reviewing step or document it as a background source with owner and access controls.

**Detection source:** Deterministic

### Medium: containment_complete is mapped to closure in the Data Dictionary but not listed as closure-step data.

**Evidence reference:** Data Dictionary mapping for containment_complete versus STEP-010 data_used.

**Why it matters:** A possible control input has inconsistent traceability.

**Recommended resolution:** Add it to the closure step, correct the mapping, or document why closure does not consume it.

**Detection source:** Deterministic

### Medium: Quarantine prioritization lacks required inputs and an approved operational rule.

**Evidence reference:** AI goal names age, value, and risk; days_open is not quarantine age, and no material-value or quarantine-entry field exists.

**Why it matters:** A ranking would require invented weights and could distort attention away from human-assigned quality risk.

**Recommended resolution:** Add authoritative age and value sources and approve priority, tie, override, owner, due-date, and queue behavior.

**Detection source:** Adversarial

### Medium: Supplier-unresponsiveness escalation is not operationally executable.

**Evidence reference:** STEP-005 says only 'escalate as needed'; STEP-004 has a defined acknowledgement escalation, while supplier_response_due_date has no overdue escalation state.

**Why it matters:** An assistant can detect lateness but has no grounded trigger, recipient, cadence, evidence, or resolution path.

**Recommended resolution:** Define the overdue trigger, accountable owner, destination, contact cadence, evidence, status effect, consequences, and resolution or abandonment path.

**Detection source:** Adversarial

### Medium: The Materials Review Board owner does not resolve to a declared participant.

**Evidence reference:** STEP-009 owner versus the Primary Participants list.

**Why it matters:** Accountability, escalation, and human-review routing remain ambiguous.

**Recommended resolution:** Add the board and accountable coordinator to the operating model or assign a declared accountable role.

**Detection source:** Deterministic

### Medium: The Supplier Portal is used but not declared as a target system.

**Evidence reference:** STEP-007 lists Supplier Portal; the target-system inventory does not.

**Why it matters:** Ownership, access, validation, and integration boundary are unknown.

**Recommended resolution:** Add the system with owner, access method, read/write posture, validation status, and data boundary.

**Detection source:** Deterministic

### Low: Manufacturing Engineering Manager is declared without an operational responsibility.

**Evidence reference:** Primary Participants list compared with step owners, controls, systems, and operational text.

**Why it matters:** The operating model may be incomplete or overstate participation.

**Recommended resolution:** Document the role's input, review, notification, or ownership responsibility, or remove it from the participant list.

**Detection source:** Deterministic

## Non-Obvious Insights

- The highest-value first build is not the most language-intensive use case. Structured containment evidence is safer and more measurable than supplier-document scoring because the latter depends on prohibited proprietary content.
- The workflow's main AI risk is not hallucinated prose alone; it is treating administrative status as proof of control satisfaction. Evidence-level retrieval is therefore more valuable than status summarization.
- The 90-day metric is a design risk. An assistant optimized on historical closure behavior could learn and reinforce the exact premature-closure pattern the workflow is intended to prevent.
- Disposition delay is partly a process-model defect, not only a prioritization problem: the numbered sequence places disposition after a months-long verification stage despite an explicit parallel-path requirement.
- Over-flagging is acceptable for containment, making a conservative evidence-retrieval tool unusually well aligned with the documented risk tolerance.

## Highest-Value AI Use Cases

### Source-linked containment trace

**Why it matters:** Containment averages 4.5 business days against a three-day requirement, and the manual ERP trace takes most of a day.

**Recommended autonomy:** Read-only draft with mandatory Manufacturing Quality Lead review; unresolved shipped exposure remains explicitly unbounded.

**Business value:** Faster evidence assembly, more consistent four-category coverage, and clearer trace limitations.

### Metadata-only stalled-record monitor

**Why it matters:** Records waiting for supplier lots look the same as forgotten records, and supplier cadence can leave verification open for months.

**Recommended autonomy:** Detect and display age, lot count, failed checks, and documented blockers; no invented escalation or status change.

**Business value:** Earlier management attention and better separation of legitimate waiting from inactive work.

### Evidence-completeness checker

**Why it matters:** Sample records demonstrate that closed, approved, waived, and containment-complete labels do not reliably prove control satisfaction.

**Recommended autonomy:** Deterministic read-only checks against underlying evidence, presented as exceptions rather than quality conclusions.

**Business value:** Reduces the chance that reviewers or later AI features rely on misleading status fields.

### Source-cited audit narrative draft

**Why it matters:** Audit preparation consumed an estimated 160 hours last year, and current reconstruction spans multiple systems.

**Recommended autonomy:** Later-phase drafting only after data boundaries and evidence checks are validated; every material statement linked to source evidence.

**Business value:** Supports the target to halve audit-preparation effort without masking missing or conflicting records.

## Where Agents Are Not Ready Yet

- Supplier root-cause scoring is blocked because the necessary narrative is explicitly barred from model context and contains proprietary supplier information; the Supplier Portal boundary is also undeclared.
- Closure assistance cannot rely on current status labels because closed examples lack required effectiveness evidence, completed reportability assessment, or use-as-is approval.
- Disposition prioritization lacks material value, quarantine-entry date, an approved ranking rule, and a clear operational consequence for priority.
- Effectiveness monitoring can count evidence, but partial implementation, waiver authority, failed-effectiveness handling, and the valid implementation date are unresolved.
- Escalation assistance is under-specified for unbounded exposure and supplier nonresponse, while expedited handling has no class-specific route or deadline.
- Approval verification is not feasible from role-only fields and cannot establish board authorization or independent closure.

## Recommended First Build

### Read-Only Containment Trace Pilot

Build a reviewer-facing trace package over approved QMS and ERP reporting views. Limit context to permitted structured lot, part, inventory, work-order, shipment, and workflow metadata. Show all four containment categories, provenance, failed checks, and source limitations.

**Why this first:** It targets the most time-sensitive documented bottleneck while avoiding the packet’s unreliable completion labels and prohibited sensitive narratives. It can be tested against objective source coverage and reviewer corrections.

**What it should not do:** Do not add workflow execution, sensitive narrative processing, completion inference, external routing, or downstream decision recommendations to this pilot.

**Expected user experience:** The Manufacturing Quality Lead receives a draft trace, inspects linked evidence, corrects or confirms it, and handles holds, escalation, documentation, and completion through the existing governed process.

## Controls and Human Review

### Read-only architecture and no-go enforcement

**Recommendation:** Use reporting views only and provide no model-controlled credentials or execution paths. Block quality judgments, approvals, disposition or release, holds, physical movement, record writes, closure or reopening, external communications, and regulatory determinations or submissions.

**Reason:** All declared target systems are read-only in scope, and consequential actions are governed, irreversible, or require revalidation.

### Protected-data context filter

**Recommendation:** Default-deny patient exposure, complaint linkage, supplier root-cause narratives, and supplier implementation documents unless a separately approved and validated transformation exists.

**Reason:** Current field permissions conflict with validated-system and confidentiality restrictions.

### Evidence provenance

**Recommendation:** Show source record, retrieval time, query criteria, transformation, model/version provenance, and unresolved limitations for every generated statement.

**Reason:** Status fields cannot be trusted as evidence of compliant completion.

### Containment review gate

**Recommendation:** Require the Manufacturing Quality Lead to confirm all four exposure categories; require Quality Manager review when shipped exposure remains unbounded.

**Reason:** The serial link is missing for pre-2024 product, and missing data must not be represented as no exposure.

### Deterministic evidence checks

**Recommendation:** Test underlying lot, approval, reportability, disposition, and actor evidence separately from AI-generated narrative. Failed checks must remain visible.

**Reason:** REC-002, REC-003, and REC-006 demonstrate contradictions between status and mandatory evidence.

### Human authority evidence

**Recommendation:** Capture identified actors, role at action time, timestamp, signature, board-vote evidence, and approval independence through the validated process.

**Reason:** Role-only fields cannot demonstrate board authorization, use-as-is approval, or independent closure.

### Change control and validation

**Recommendation:** Document intended use, prohibited use, representative test cases, acceptance thresholds, source limitations, human review, failure handling, version control, monitoring, and rollback before operational use.

**Reason:** The workflow and computerized systems require documented change control and validation evidence.

### Audit logging and fail-closed behavior

**Recommendation:** Log source retrieval, generated artifacts, reviewer changes, approvals, blocked data, and attempted out-of-scope actions; fail closed when evidence, boundary, or reviewer requirements are missing.

**Reason:** Every record may become an inspection artifact, and the pilot must not conceal missing evidence.

## Implementation Roadmap

### 1 — Remediate and bound

**Focus:** Investigate critical sample contradictions; approve the AI data boundary, intended use, no-go policy, source scope, and containment review procedure.

**Outcome:** A controlled pilot design that excludes sensitive narratives and does not rely on status as proof.

### 2 — Build and validate

**Focus:** Connect read-only QMS and ERP reporting views, implement four-category trace logic, provenance, unbounded handling, and representative validation tests.

**Outcome:** A validated prototype with measurable source coverage and reviewer correction behavior.

### 3 — Run a supervised pilot

**Focus:** Operate in parallel with the current process, retain human review evidence, measure time, corrections, coverage, and containment timeliness.

**Outcome:** Evidence for an expansion decision without changing systems of record or governed actions.

### 4 — Consider adjacent read-only capabilities

**Focus:** Add metadata aging and deterministic evidence checks; evaluate audit-narrative drafting only after data and control defects are resolved.

**Outcome:** Incremental workflow intelligence with each use case separately scoped and validated.

## Success Metrics

- Median elapsed time to produce a reviewer-ready containment trace versus the current manual process.
- Percentage of records with containment completed within three business days, measured toward the documented 90 percent target.
- Reviewer correction rate by exposure category and reason.
- Percentage of trace outputs with source links, retrieval timestamps, and query criteria for all reported results.
- Percentage of post-2024 traces with bounded shipped-product exposure, subject to source-link validation.
- Number of outputs incorrectly representing missing evidence as no exposure or compliant completion; target zero.
- Reviewer adoption and trust, measured by use, acceptance with edits, and documented rejection reasons.
- Number of prohibited-data or out-of-scope execution attempts blocked and logged; all such attempts should be blocked.

## Open Questions

- What AI hosting and processing environment is proposed, and is it within the approved company and validated-system boundaries?
- What evidence confirms the completeness of the post-2024 serial link, and what governed branch applies when exposure remains unbounded?
- Will 'waived' and 'partial' remain valid states; if so, what authority, evidence, implementation date, and transition rules govern them?
- How will the 90-day requirement be reconciled with normal supplier cadence and mandatory three-lot effectiveness evidence?
- Who performs the initial reportability assessment, and must submission confirmation exist before a reportable record closes?
- Which identified roles are eligible for independent closure, and how will actor identity and same-individual exclusion be captured?
- What is the authority sequence between the Materials Review Board and Quality Manager, including sort outcomes and use-as-is disagreement?
- Where are Legal preclearance, supplier nonresponse, failed effectiveness, and expedited-risk actions recorded, and what deadlines and escalation states apply?
