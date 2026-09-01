# Employee Offboarding and Access Revocation — AI Workflow Assessment

## Executive Brief

**Recommendation:** Proceed only with a tightly constrained, read-only monitoring pilot after the model-facing data contract is corrected and contradictory records are excluded from training or compliance conclusions. The workflow offers real value in cross-system visibility, evidence-gap detection, and reviewer preparation, but it is not ready for autonomous execution or compliance-reliant conclusions.

**First build:** A read-only Offboarding Evidence Monitor that consolidates the five operational branches for sources with confirmed authoritative read access, displays source freshness and evidence status, and routes discrepancies to a defined human review queue.

**Why this first:** The largest documented problem is not a lack of narrative generation; it is that task closure can conceal unresolved access and no one has a reliable whole-case view. A read-only monitor addresses that gap without depending on unsafe writes, incomplete prediction data, unknown SaaS log sources, or unresolved disposition logic.

**Estimated effort:**

- Duration: Planning estimate: approximately 12–18 weeks for a constrained pilot, subject to data-access and control-remediation dependencies.
- Confidence: Low to moderate. No dedicated engineering resource is available, and interface specifications, access approvals, evidence formats, and correlation reliability have not been supplied.
- Workstreams:
  - Data allowlist, redaction, identifier tokenization, and contradictory-record quarantine
  - Read-interface validation, source correlation, lineage, and freshness controls
  - Five-branch case view and human-reviewed discrepancy queue
  - Evaluation dataset, reviewer testing, security compliance review, and operating procedures

**Estimated cost:**

- Range: Order-of-magnitude planning guidance: USD 200,000–450,000 for discovery, control design, integration, pilot development, and evaluation. This is not a vendor quote.
- Confidence: Low, because the packet documents system capabilities but not integration complexity, resource availability, procurement constraints, or production architecture.
- Assumptions:
  - The pilot remains read-only and uses three to five existing data interfaces rather than creating production write integrations.
  - Existing identity, workflow, asset, and reporting platforms can provide authorized exports or APIs without major licensing changes.
  - The range includes a small cross-functional delivery team, security review, testing, and limited pilot support.
  - It excludes source-system replacement, remediation of all underlying workflow controls, new regional operating coverage, long-term managed service, audit fees, and broad SaaS-discovery infrastructure.
  - Inputs needed to refine the range include interface documentation, data volumes, authentication requirements, retention architecture, hosting standards, staffing rates, security testing requirements, and expected support levels.

**ROI / value hypothesis:**

- Confidence: Low for a financial forecast; moderate for the direction of value. The packet supports a theoretical value hypothesis, not a business-case commitment.
- Expected value:
  - Theoretical labor-value ceiling includes reducing the approximately 120 hours spent assembling annual quarterly-review evidence; this is a ceiling, not a savings forecast.
  - Earlier detection of cases where task closure conflicts with target-system evidence could move findings from quarterly discovery into operational review.
  - A consolidated view could reduce tool switching across approximately 480 annual departures and focus analysts on overdue or contradictory cases.
  - Transparent hardware-aging triage may support the stated goal of improving fourteen-day recovery without relying on an unvalidated prediction model.
- Not counted yet:
  - Avoided security incidents, customer notifications, examination exceptions, or contractual consequences
  - Benefits from lower median case duration or fewer access-review findings
  - Predictive hardware-recovery benefits or unknown-SaaS discovery benefits
  - Value from broader workflow redesign, because those outcomes cannot be attributed to AI from the current evidence
- Inputs needed to quantify:
  - Fully loaded labor rates and current per-case handling time by branch
  - Time spent reconciling tools, reviewing false closures, and remediating quarterly findings
  - Expected alert volume, precision, recall, and average human-review time
  - Integration, hosting, model, security, and ongoing support costs
  - Representative historical hardware, access-verification, and exception outcomes

**Executive decisions needed:**

- Approve or decline funding for a read-only discovery and pilot phase rather than an autonomous offboarding agent.
- Require remediation of model-context permissions for restricted HR narratives and personal contact data before any model evaluation.
- Assign accountable owners to resolve disposition rules, expedited authorization, retained-access lifecycle, and post-close remediation.
- Confirm that the first build has no access to workflow, entitlement, credential, badge, payroll, communication, disposition, closure, or reopening writes.
- Defer predictive hardware scoring, unknown-SaaS detection, automated compliance conclusions, and all consequential actions until required data and operating controls exist.

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

### Offboarding Evidence Monitor

**Pitch:** A reviewer-facing workspace that shows what each source actually evidences for an offboarding case, highlights contradictions and missing proof, and prepares traceable drafts without changing operational systems.

**Target users:**

- IT Service Desk analysts reviewing open and apparently completed cases
- Identity, privileged-access, facilities, SaaS, and asset operators resolving evidence gaps
- Security compliance reviewers preparing quarterly access-control testing

**Workflow moment:**

From dispatch of the five parallel branches through human closure review, with a separate human-owned queue for discrepancies discovered after closure.

**Before:**

Analysts open multiple tools, rely heavily on task states, reconcile quarterly evidence manually, and may discover persistent access only during later reviews.

**After:**

One read-only view separates task state from verification evidence, identifies source and freshness, and presents unresolved contradictions to the accountable reviewer.

**Sample assistant output:**

- **Closure contradiction:** REC-002 is marked closed while privileged access is recorded as not revoked, hardware is not returned, and manager attestation is no_response. Treat closure as unverified and route for human investigation.
- **Disposition contradiction:** REC-004 combines an active litigation-hold flag with deleted disposition. Quarantine the record from compliant examples and refer the state to the authorized disposition reviewers.
- **Evidence status:** Show each branch as verified, unverified, contradictory, missing, or not applicable, with the source and extraction timestamp. Never translate task closure alone into verified revocation.
- **Quarterly draft:** Prepare an evidence index that cites sources, lists unresolved exceptions and missing verification, and remains explicitly draft pending security compliance review.

**What AI does:**

- Summarizes permitted operational status and organizes reviewer-ready case evidence.
- Flags missing, stale, or contradictory information using documented rules and source lineage.
- Drafts evidence indexes and review narratives that expose unresolved gaps.
- Supports search and explanation across approved workflow and control documentation.

**What AI does not do:**

- Interpret termination reasons, assign departure risk, or select a revocation path.
- Approve exceptions, alter access, rotate credentials, delete data, change payroll, communicate externally, or change case state.
- Declare revocation complete or issue a compliance conclusion from task status alone.

**Demo moment:**

Open REC-002 and show that the product rejects the apparently closed case as sufficient evidence, identifies each conflicting state, cites the source fields, and produces a human review checklist rather than a compliance conclusion.

## Packet Quality Findings

### Critical: Case closure is based on task state rather than the workflow's stated completion criteria.

**Evidence reference:** Workflow Completion Criteria; STEP-012; CTRL-003; REC-002.

**Why it matters:** REC-002 is closed although privileged access is not revoked, hardware is not returned, and manager attestation is no_response. Closed is therefore not a trustworthy compliant label.

**Recommended resolution:** Define evidence-based human closure gates for verified access removal, approved exceptions, hardware outcome, attestation, lawful disposition, final pay, and archived evidence.

**Detection source:** Adversarial

### Critical: REC-004 shows deleted mailbox disposition while the litigation-hold flag is true.

**Evidence reference:** REC-004; STEP-010; litigation_hold_flag definition; documented deletion constraints.

**Why it matters:** The workflow says a hold suspends permanent deletion. The record indicates either a failed gate, stale data, invalid sample, or ambiguous status semantics.

**Recommended resolution:** Investigate and quarantine REC-004; implement a fail-closed, fresh Legal-owned hold check with immutable evidence immediately before any destructive disposition.

**Detection source:** Adversarial

### Critical: Termination reason narratives are marked model-allowed without redaction despite an explicit HR-system confinement requirement.

**Evidence reference:** Data Dictionary: termination_reason_detail; CTRL-009; AI No-Go Areas; REC-002.

**Why it matters:** The field can contain investigations, allegations, and information about other workers. Using the current permission could breach the stated boundary and influence prohibited employment-related judgments.

**Recommended resolution:** Set model-context permission to false, remove the field from extracts and evaluation data, and enforce field-level filtering before model invocation. Quarantine existing samples containing the narrative.

**Detection source:** Adversarial, supported by deterministic data-governance review

### Critical: The personal_contact_email field is classified as PII but marked model-allowed without redaction.

**Evidence reference:** Data Dictionary: personal_contact_email; STEP-011; Sample Records.

**Why it matters:** No proposed monitoring goal requires a worker's personal address in model context, prompts, dashboards, logs, or generated evidence packs.

**Recommended resolution:** Block the field from model context or define an explicitly approved transformation and narrow purpose. Keep correspondence in the established human payroll process.

**Detection source:** Deterministic

### High: CTRL-001 names Security leadership as the required approver, but that role is not a declared workflow participant.

**Evidence reference:** CTRL-001; Primary Participants.

**Why it matters:** An unresolved approver role prevents reliable assignment, authorization, and audit evidence even if a pre-dispatch gate is added.

**Recommended resolution:** Add the role with explicit accountability or replace it with a declared accountable participant.

**Detection source:** Deterministic

### High: Persistent-access findings have no complete reopen and remediation branch.

**Evidence reference:** AI Goals; STEP-012; case_status definition.

**Why it matters:** A reopened status and informal handler are named, but trigger evidence, ownership, containment, task creation, verification, root-cause coding, and reclosure criteria are not.

**Recommended resolution:** Create a human-owned post-close branch with evidence thresholds, accountable owner, containment procedure, system-of-record handling, verification, root-cause capture, and reclosure approval.

**Detection source:** Adversarial

### High: Post-revocation verification exists as policy but not as an operational evidence path.

**Evidence reference:** CTRL-003; STEP-004; STEP-006; identity_access_revoked definition.

**Why it matters:** Current flags reflect task closure or directory coverage rather than confirmed access cessation, leaving no reliable ground truth for monitoring or control conclusions.

**Recommended resolution:** Create per-system verification events with observed state, target checked, timestamp, verifier identity, evidence reference, and failure disposition.

**Detection source:** Adversarial

### High: REC-003 shows the same requester and approver role for retained access, while the data model lacks identity-level evidence.

**Evidence reference:** CTRL-008; REC-003; requester_role and exception_approver_role definitions.

**Why it matters:** Role labels cannot prove that different individuals acted, and the sample appears to violate the stated separation-of-duties requirement.

**Recommended resolution:** Capture immutable requester and approver user identities, reject equality at approval time, and remediate existing self-approval cases.

**Detection source:** Adversarial

### High: Retained access has no complete exception lifecycle.

**Evidence reference:** CTRL-007; STEP-003; STEP-006; REC-003.

**Why it matters:** Scope, prohibited access categories, expiry, maximum duration, reapproval, eventual revocation, verification, and escalation are absent, creating a risk of indefinite post-employment access.

**Recommended resolution:** Define a dedicated lifecycle with entitlement scope, named parties, start and expiry times, maximum duration, reapproval, revocation tasks, verification, and escalation.

**Detection source:** Adversarial

### High: The expedited-path approval requirement is mapped to workflow steps but not implemented as a pre-dispatch gate.

**Evidence reference:** CTRL-001; STEP-002; STEP-003.

**Why it matters:** Expedited tasks are described as dispatched immediately, yet no authorization field, identity, timestamp, or hard gate is defined.

**Recommended resolution:** Define written classification criteria, capture named authorization and timestamp, and enforce approval before dispatch while keeping classification and authorization human-controlled.

**Detection source:** Adversarial

### High: The four-hour privileged-access control cannot be measured from the defined data.

**Evidence reference:** CTRL-002; effective_termination_date; revocation_start_timestamp; STEP-005; REC-005.

**Why it matters:** The start field has no time, the revocation timestamp records dispatch rather than completion, and REC-005 shows dispatch before notification under the documented sequence.

**Recommended resolution:** Define authoritative timezone-aware event timestamps, validate chronology, record corrections separately, and calculate the control only from approved start and completion events.

**Detection source:** Adversarial

### High: The stated AI no-go boundary omits the workflow's highest-consequence actions.

**Evidence reference:** AI No-Go Areas; STEP-005; STEP-010; STEP-011; write-capable target systems.

**Why it matters:** The packet reserves employment judgments but does not explicitly reserve access changes, secret rotation, deletion, payroll actions, communications, exception approval, or case closure.

**Recommended resolution:** Expand the policy boundary to reserve all consequential decisions and writes to accountable humans, and enforce read-only credentials for the first build.

**Detection source:** Adversarial

### High: Thirty-day mailbox destruction and three-year communications retrievability are not reconciled.

**Evidence reference:** CTRL-004; CTRL-005; STEP-009; STEP-010.

**Why it matters:** The packet identifies no preservation repository, sequence, completeness check, retrieval test, or evidence proving that content remains retrievable after deletion.

**Recommended resolution:** Create one disposition decision table defining what is preserved, where, by whom, how completeness and retrieval are verified, and when destruction may occur.

**Detection source:** Adversarial

### High: Unknown-SaaS detection has no documented access-log source or data lineage.

**Evidence reference:** AI Goals; STEP-006; SaaS Application Directory; Target Systems.

**Why it matters:** The spreadsheet can serve as a comparison list but cannot supply the discovery signal. No log owner, matching key, normalization method, coverage, or retention window is defined.

**Recommended resolution:** Identify and authorize the source telemetry, document matching and coverage, and establish human validation and directory-maintenance procedures before treating this use case as buildable.

**Detection source:** Adversarial

### Medium: retained_access_justification is mapped to STEP-003 in the Data Dictionary but is not listed among that step's used data.

**Evidence reference:** Data Dictionary: retained_access_justification; STEP-003.

**Why it matters:** The mismatch weakens traceability for a confidential control input and obscures whether the field has an operational consumer.

**Recommended resolution:** Correct the field-to-step mapping, add it to the documented step, or explain why it is retained but not consumed.

**Detection source:** Deterministic

### Medium: The Security Awareness Platform is listed as a target system but has no documented workflow or data-source use.

**Evidence reference:** Target Systems: Security Awareness Platform; Workflow Steps; AI Goals.

**Why it matters:** Its presence may represent missing lineage, future scope, or an out-of-scope integration and could confuse architecture and cost estimates.

**Recommended resolution:** Reference its intended workflow use and data fields, label it future or contextual, or remove it from the in-scope inventory.

**Detection source:** Deterministic

### Low: Legal Counsel is listed as a primary participant but has no explicit operational responsibility in the documented steps, controls, systems, or records.

**Evidence reference:** Primary Participants; workflow steps and control ownership.

**Why it matters:** The omission leaves ownership of legal-hold input and disposition review unclear despite their operational importance.

**Recommended resolution:** Document Legal Counsel's input, review, approval, or notification role, or remove the role from the participant list if it is contextual only.

**Detection source:** Deterministic

## Non-Obvious Insights

- The first value opportunity is evidence normalization, not sophisticated language generation: the core defect is that workflow states do not reliably represent real-world access outcomes.
- Current closed and revoked fields are unsuitable positive training labels because the packet itself demonstrates control-invalid closed states.
- Source latency and operating coverage may dominate model performance: a nightly HR extract and single-time-zone service desk cannot be assumed to support urgent global departures.
- A useful evidence pack should make missing proof and contradictions more visible, not merely produce a polished narrative from incomplete records.
- Hardware recovery should begin as deterministic aging and receipt-status triage; prediction would add complexity before the required explanatory data and outcomes exist.

## Highest-Value AI Use Cases

### Consolidated five-branch case visibility

**Why it matters:** The service desk currently opens multiple tools to understand one case, while approximately 480 departures occur annually.

**Recommended autonomy:** Read-only aggregation and summarization with visible source freshness; human interpretation and action.

**Business value:** Reduced reconciliation effort and faster identification of overdue, missing, contradictory, or not-applicable branch states.

### Revocation evidence discrepancy detection

**Why it matters:** Seven findings in the last quarterly review involved accounts marked revoked that remained active, and CTRL-003 explicitly rejects task closure as evidence.

**Recommended autonomy:** Deterministic comparison and AI-assisted explanation after per-system verification events exist; every alert reviewed by the responsible operator.

**Business value:** Potentially shifts persistent-access discovery from quarterly testing into operational review and improves evidence quality.

### Draft quarterly evidence pack

**Why it matters:** Evidence assembly consumed an estimated 120 hours last year and currently depends on manual reconciliation.

**Recommended autonomy:** Draft generation only from verified, cited evidence, with completeness checks and security compliance approval.

**Business value:** Lower assembly effort and more consistent visibility into exceptions, missing evidence, and unresolved contradictions.

### Rule-based hardware recovery triage

**Why it matters:** Hardware drives the slowest cases, and only about 55 percent of remote departures meet the fourteen-day recovery target.

**Recommended autonomy:** Transparent aging and missing-receipt prioritization; no predictive score or outreach action.

**Business value:** Earlier human attention using available data while the organization collects the history needed to assess prediction.

## Where Agents Are Not Ready Yet

- Mailbox and account disposition lacks a reconciled rule for thirty-day destruction, three-year retrievability, and litigation holds.
- The four-hour privileged-access control lacks the authoritative start time, completion time, time zone, and chronology needed for reliable measurement.
- Expedited authorization is not represented as an enforceable pre-dispatch gate, and its approver role is unresolved.
- Retained access lacks entitlement scope, expiry, reapproval, eventual revocation, and verification steps.
- Persistent-access findings lack a complete reopen, containment, ownership, verification, root-cause, and reclosure branch.
- Unknown-SaaS detection has no documented access-log source, matching method, coverage statement, or validation process.
- Hardware prediction lacks representative history, remote-worker status, shipment events, outreach history, and approved outcome definitions.

## Recommended First Build

### Read-Only Case and Evidence Review Pilot

Establish a filtered, tokenized data layer and consolidate branch status only from systems with confirmed authoritative reads. Display task state, verification state, source, extraction time, target date, and exception status separately. Add deterministic contradiction checks and a human review queue before introducing narrative generation.

**Why this first:** It directly addresses fragmented visibility and false closure while making packet-quality defects visible in day-to-day work. It can be evaluated against known contradictory cases and does not require the system to infer employment judgments, predict hardware outcomes, or rely on an unidentified SaaS-log source.

**What it should not do:** It should not treat the existing samples as clean labels, calculate the privileged-access SLA before timestamp definitions are fixed, imply complete SaaS coverage, or produce an unqualified access-control conclusion.

**Expected user experience:** An analyst opens a case, sees all available branches and freshness indicators, reviews evidence gaps ranked by operational urgency, and records a disposition through the established human process outside the model. Every generated statement remains traceable to source evidence.

## Controls and Human Review

### Model-facing data boundary

**Recommendation:** Use an explicit field allowlist; exclude termination_reason_detail, retained_access_justification, and personal_contact_email; tokenize unresolved worker identifiers; and inspect prompts, logs, and outputs for prohibited data.

**Reason:** The packet contains critical conflicts between sensitivity, model permission, and operational confidentiality.

### Tool and action boundary

**Recommendation:** Use read-only credentials and deny model access to task dispatch, status changes, entitlement changes, secret rotation, badge changes, payroll or fee actions, external communications, deletion, closure, reopening, release, or final report distribution.

**Reason:** These are consequential or irreversible actions reserved for accountable human operators under the documented workflow and readiness review.

### Source lineage and freshness

**Recommendation:** Display the source, extraction time, correlation confidence, and freshness for every status. Preserve a separate human urgent-handling path for same-day and retroactive departures.

**Reason:** Nightly HR data and incomplete interface documentation make stale or unmatched information operationally significant.

### Revocation verification and discrepancy review

**Recommendation:** Store per-system verification events and route each mismatch to the responsible operator. A human reviewer determines remediation and records the outcome.

**Reason:** Task closure is explicitly insufficient evidence, and the sample packet includes unresolved access in a closed case.

### Privileged-access timing

**Recommendation:** Define timestamp semantics and calculate elapsed time deterministically outside the model. Human reviewers assess exceptions and invalid chronology.

**Reason:** The present fields cannot measure the four-hour requirement reliably.

### Approvals and separation of duties

**Recommendation:** Capture named requester and approver identities, authorization timestamps, and inequality checks for expedited and retained-access exceptions.

**Reason:** Role-level fields cannot prove segregation, and REC-003 shows an apparent self-approval.

### Disposition and legal-hold gate

**Recommendation:** Require current hold status, transfer evidence, manager attestation, approved retention disposition, and authorized human confirmation before destructive disposition.

**Reason:** Deletion is irreversible, the retention controls are unresolved, and REC-004 contradicts the stated hold gate.

### Closure and reporting review

**Recommendation:** Use an evidence-based closure checklist and require security compliance review of every generated control-test narrative, unresolved exception list, and distribution decision.

**Reason:** Neither case status nor generated prose can substitute for verified evidence and accountable review.

## Implementation Roadmap

### 1 — Resolve critical data and process blockers

**Focus:** Approve the field allowlist, quarantine contradictory samples, define timestamp events, reconcile disposition rules, and document exception and post-close branches.

**Outcome:** A controlled data contract and operating design that prevents the pilot from encoding known packet defects.

### 2 — Build the read-only evidence layer

**Focus:** Validate authorized interfaces, establish case correlation, ingest permitted fields, and expose source lineage, freshness, task state, and verification state.

**Outcome:** A usable five-branch view for the subset of systems with proven read access and stable identifiers.

### 3 — Pilot human-reviewed discrepancy and aging queues

**Focus:** Test deterministic contradiction rules, revocation-evidence review, hardware aging, reviewer disposition, and post-close handling against an approved evaluation set.

**Outcome:** Measured recall, false-positive burden, reviewer usefulness, and evidence completeness without operational writes.

### 4 — Add controlled draft reporting and reassess expansion

**Focus:** Generate cited draft evidence packs, measure preparation effort, and reassess SaaS discovery or predictive work only after their data prerequisites are met.

**Outcome:** A security-compliance-reviewed reporting capability and an evidence-based decision on whether further investment is justified.

## Success Metrics

- Zero prohibited fields found in model prompts, logs, outputs, or evaluation datasets.
- Percentage of pilot cases with all available branch states linked to a named source and extraction timestamp.
- Percentage of revocation completion claims supported by defined post-change verification evidence.
- Recall of known persistent-access contradictions in the approved test set, with false negatives reviewed explicitly.
- Median analyst time to understand and disposition a flagged case compared with the current multi-tool process.
- Reduction in evidence-pack preparation time from the documented 120-hour annual baseline, measured without counting unresolved items as complete.
- Percentage of privileged-access cases with valid authoritative start and completion timestamps after the event model is implemented.
- No departure dispatch or revocation delayed by the monitoring pilot.

## Open Questions

- Who will approve and own the model-facing data contract, identifier tokenization, and ongoing field changes?
- Which read interfaces and correlation keys are authoritative for each of the five branches, and what freshness can each guarantee?
- What are the official timezone-aware definitions for notification, effective termination, dispatch, execution completion, and verification?
- How must thirty-day destruction, three-year retrievability, legal holds, and data-subject-rights suspensions be sequenced and evidenced?
- What written criteria govern departure classifications, and which declared role provides expedited-path authorization?
- What scope, expiry, maximum duration, reapproval, revocation, and verification rules govern retained access, and who owns post-close remediation?
- What telemetry will supply unknown-SaaS discovery, what coverage does it have, and who validates and maintains resulting directory changes?
- What representative evaluation dataset, acceptance thresholds, regional urgent-handling model, delivery capacity, and budget will be committed to the pilot?
