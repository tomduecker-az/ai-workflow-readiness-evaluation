# Public Records Request Intake and Fulfillment — AI Workflow Assessment

## Executive Brief

**Recommendation:** Proceed only with a bounded, read-only pilot after correcting the receipt-date model and excluding unresolved control states from trusted reporting. The first release should use approved operational metadata or de-identified exports and should not process request text or responsive record content. No AI component should make legal or commercial classifications; apply redactions; assess or waive fees; approve, release, deny, abandon, reopen, deliver, communicate externally, close, or update production systems.

**First build:** A Public Records Operations and Control Integrity View that calculates factual age from a verified receipt anchor, displays stage and queue status, and flags contradictory or incomplete control evidence for human investigation.

**Why this first:** It addresses the documented lack of daily visibility while avoiding the highest-risk content. It also turns packet-quality defects into operational value: REC-002 shows that status alone cannot prove legal or payment readiness, and the current receipt-date definition can understate age. Correcting those defects is a prerequisite to trustworthy prioritization.

**Estimated effort:**

- Duration: Approximately 10–13 weeks, consistent with the documented one-quarter pilot window.
- Confidence: Medium. Export-based delivery is supported, but effort depends on data quality, export frequency, approval turnaround, and the unresolved source for original City receipt.
- Workstreams:
  - Reconcile receipt dates, sample contradictions, ownership, and reporting rules.
  - Define the approved metadata schema, exclusions, access, output retention, and audit evidence.
  - Build an offline/read-only export pipeline, integrity checks, factual aging calculations, and reviewer interface.
  - Run parallel validation, document user decisions, and measure operational usefulness before any expansion.

**Estimated cost:**

- Range: $100,000–$225,000 in order-of-magnitude planning guidance; this is not a vendor quote.
- Confidence: Low to medium because technical architecture, procurement model, data remediation volume, and recurring operating costs are not documented.
- Assumptions:
  - One-quarter, read-only pilot using existing exports rather than a supported system-of-record write integration.
  - Scope limited to metadata validation, factual aging, control-state anomaly detection, a lightweight reviewer experience, testing, and documentation.
  - Production request text, responsive records, law-enforcement material, redaction processing, external communications, fee execution, and workflow writes are excluded.
  - Range excludes recurring model or software licenses, new hosting infrastructure, procurement, remediation of historical records at scale, system replacement, and broader process redesign.
  - Refinement requires export samples, record counts by stage, data-cleanup volume, security and legal review requirements, hosting decisions, interface expectations, and available internal delivery capacity.

**ROI / value hypothesis:**

- Confidence: Low for financial ROI; medium for the relative value ranking because documented volumes and pain-point baselines are available.
- Expected value:
  - Near-term value is better visibility and earlier detection of aging or contradictory workflow states; the packet does not provide enough labor data to convert this into a financial forecast.
  - Theoretical future screening ceiling: 1,400 annual requests multiplied by 3.5 screening hours equals approximately 4,900 staff hours; achieving the stated 50% reduction would represent up to 2,450 hours. This is a value ceiling, not a forecast, and content screening is excluded from the first build.
  - Theoretical routing opportunity: roughly 20% of 1,400 annual requests, or about 280 requests, receive corrected first-pass routing. Avoidable effort and delay per correction are not quantified.
  - Approximately 35% of requests, or about 490 annually, require clarification. AI could reduce City drafting latency after content handling is approved, but it cannot control requester response time.
- Not counted yet:
  - Litigation-risk reduction, avoided improper disclosure, public-trust effects, and challenge avoidance.
  - Time saved preparing the aging view and annual transparency reporting because current preparation effort is not supplied.
  - Benefits from fee consistency, denial-letter drafting, or exemption pre-screening because those capabilities are not currently implementable from the documented rules and data boundaries.
  - Software, hosting, support, data remediation, review overhead, and change-management costs.
- Inputs needed to quantify:
  - Loaded labor cost by workflow activity and reviewer type.
  - Current time spent preparing aging and annual reports.
  - Effort and elapsed delay caused by rerouting, clarification drafting, and incomplete withholding logs.
  - Request and page volumes by record class, exemption class, department, and legal-review path.
  - Pilot acceptance, correction, false-negative, and review-time results.
  - Recurring technology, hosting, support, and governance costs.

**Executive decisions needed:**

- Authorize remediation and a read-only metadata pilot, not production content processing.
- Require correction or formal exception classification for REC-001, REC-002, and REC-005 before using samples for training, evaluation, or workflow logic.
- Approve a comprehensive AI action boundary and model-context data contract before exposing live data.
- Assign accountable owners for receipt-date integrity, aging response rules, system access, waiver authority, and packet corrections.

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

### Public Records Review Copilot

**Pitch:** A reviewer-facing workspace that makes request age, evidence gaps, routing suggestions, and—only after later approvals—candidate review flags visible without taking governed actions.

**Target users:**

- City Clerk Records Coordinator
- Records team or its reconciled accountable role
- Department Records Custodian
- Records Analyst
- Assistant City Attorney

**Workflow moment:**

Used when staff review intake and open-request exports, prioritize work, validate workflow evidence, and prepare human decisions.

**Before:**

The Clerk assembles aging information manually, department work can remain invisible, routing depends on institutional knowledge, and status fields can obscure missing legal, payment, approval, or retention evidence.

**After:**

Staff receive a traceable, read-only worklist showing factual age, data-quality warnings, workflow stage, missing evidence, and later-stage recommendations, with every disposition recorded as a human decision.

**Sample assistant output:**

- **Age-data warning:** Original City receipt date is unavailable; displayed age is unverified. Do not use this record for promptness conclusions until the receipt anchor is reconciled.
- **Control-state anomaly:** REC-002 is marked released while legal review is pending and the fee is invoiced. Investigate as a control exception; released status is not evidence of valid authorization.
- **Reviewer action:** Confirm source dates and authoritative evidence. The assistant has not changed status, sent a message, or determined legal timeliness.

**What AI does:**

- Calculates factual age from approved date fields and highlights missing or contradictory metadata.
- Organizes open requests by documented stage and presents evidence-backed integrity warnings.
- Later, after separate approval gates, ranks possible routing destinations or prepares drafts for human review.
- Captures recommendation sources, reviewer disposition, and correction reasons for evaluation.

**What AI does not do:**

- It does not determine legal outcomes or execute workflow actions; accountable staff retain all decisions and actions.

**Demo moment:**

Show REC-002 on a dashboard: instead of trusting the released status, the product exposes the pending legal review and unsettled fee as separate evidence failures, then shows an unverified-age warning where the original City receipt date is missing.

## Packet Quality Findings

### Critical: REC-002 is also marked released while its fee remains invoiced rather than paid, waived, or not applicable.

**Evidence reference:** REC-002; Approve release; fee-status definition.

**Why it matters:** The documented payment gate is bypassed, so release status cannot demonstrate that financial prerequisites were satisfied.

**Recommended resolution:** Require authoritative cashiering evidence and permit release eligibility only for paid, validly waived, or not-applicable states; reconcile the sample.

**Detection source:** Adversarial

### Critical: REC-002 is marked released while mandatory legal review remains pending.

**Evidence reference:** REC-002; Legal review of withholdings; Approve release; recorded-approval control.

**Why it matters:** The sample normalizes irreversible release without a completed legal prerequisite and proves that current status cannot be trusted as authorization evidence.

**Recommended resolution:** Investigate REC-002 and require final linked legal determination, durable release approval, approver, timestamp, and validated package version before release eligibility can be recognized.

**Detection source:** Adversarial

### Critical: Requester email is classified as PII but is allowed into model context without redaction.

**Evidence reference:** Data Dictionary: requester_contact_email.

**Why it matters:** The packet's handling rule is internally inconsistent and cannot serve as an approved model allowlist.

**Recommended resolution:** Block the field, require redaction, or document and approve a minimum-necessary transformation and business rationale.

**Detection source:** Deterministic

### High: A request forwarded by a department can be aged from the later Clerk receipt instead of original City receipt.

**Evidence reference:** Receive and log request; Data Dictionary: request_received_date and days_open.

**Why it matters:** The proposed aging view could systematically understate age and suppress high-risk requests.

**Recommended resolution:** Store immutable original City receipt, Clerk logging, and forwarding dates separately; approve the aging anchor and reconcile historical records.

**Detection source:** Adversarial

### High: Clarification drafting requires request text that the Data Dictionary prohibits from model context.

**Evidence reference:** AI clarification goal; Data Dictionary: request_text; Acknowledge and clarify scope.

**Why it matters:** The production use case lacks a permitted input and cannot be implemented under current rules.

**Recommended resolution:** Define an approved transformed-request field, preprocessing and quality review, approved environment, retention, and human message review; use synthetic or manually de-identified text until then.

**Detection source:** Adversarial

### High: Confidential withholding rationale is treated as model-context eligible without a minimum-necessary representation.

**Evidence reference:** Data Dictionary: withholding_rationale; release or denial letter goal.

**Why it matters:** Internal rationale may reveal privileged, medical, witness, investigative, or security-sensitive facts in generated correspondence or telemetry.

**Recommended resolution:** Separate internal rationale from an approved public-facing code and explanation; default internal text out of context and require legal review of generated withholding language.

**Detection source:** Adversarial

### High: Exemption pre-screening conflicts with protected-identity and law-enforcement content restrictions.

**Evidence reference:** AI screening goal; protected-identity control; law-enforcement handling control; Screen for exemptions and apply redactions.

**Why it matters:** Some content must be protected before model access, while law-enforcement content cannot leave its network; no compliant content architecture is documented.

**Recommended resolution:** Exclude production content initially; later define in-boundary deployment, pre-ingestion controls, document lineage, chain of custody, provenance, class-specific evaluation, and mandatory human confirmation.

**Detection source:** Adversarial

### High: Full denial is a stated completion outcome but has no distinct executable workflow branch.

**Evidence reference:** Completion criteria; legal review; approve release; deliver and close.

**Why it matters:** The post-legal-review path assumes a release package and omits denial authority, approval evidence, communication, retention, closure, and challenge handling.

**Recommended resolution:** Add a full-denial branch covering trigger, final authority, legal linkage, letter review, communication, evidence, retention, closure, challenge, and correction.

**Detection source:** Adversarial

### High: REC-001 conflicts with the claim that exemption decisions belong to the City Attorney's Office.

**Evidence reference:** REC-001; AI no-go statement; exemption screening and legal-review steps.

**Why it matters:** The packet does not establish whether analysts can finalize some exemption categories or merely recommend them.

**Recommended resolution:** Define final authority, mandatory legal-review conditions, evidence, and release effect for every exemption code; correct or classify REC-001 as an exception.

**Detection source:** Adversarial

### High: REC-005 is abandoned even though the documented abandonment trigger cannot occur for an anonymous requester with no contact channel.

**Evidence reference:** REC-005; Acknowledge and clarify scope; prompt-response control.

**Why it matters:** The sample could normalize abandonment as a substitute for processing or formally resolving an unsearchable anonymous request.

**Recommended resolution:** Create a distinct no-contact/unsearchable branch with search effort, authority, evidence, timing, review, status, and disposition; correct or explain REC-005.

**Detection source:** Adversarial

### High: Requester name and requester email have the same PII classification but opposite model-context and redaction rules without explanation.

**Evidence reference:** Data Dictionary: requester_contact_name and requester_contact_email.

**Why it matters:** The field allowlist may reflect inconsistent assumptions rather than an approved handling decision.

**Recommended resolution:** Require the accountable data owner to reconcile both rules and document any justified difference.

**Detection source:** Deterministic

### High: The data model cannot prove the required per-document withholding rationale.

**Evidence reference:** Per-document rationale control; request-level redaction flag; free-text withholding rationale.

**Why it matters:** AI and human reviewers cannot reliably link a rationale and legal disposition to a document, page, redaction instance, or package version.

**Recommended resolution:** Create a document/redaction ledger with package version, document and location, exemption, rationale, provenance, legal disposition, reviewer, timestamp, and public-facing explanation.

**Detection source:** Adversarial

### High: The exemption-screening exception says only “Escalate as needed.”

**Evidence reference:** Screen for exemptions and apply redactions; legal-review turnaround baseline.

**Why it matters:** A low-confidence or high-risk model flag would have no deterministic owner, timing, evidence package, status, or return path.

**Recommended resolution:** Define triggers, accountable legal queue, priority, required evidence and provenance, decision record, rework, re-review, and release-blocking behavior.

**Detection source:** Adversarial

### High: The fee-waiver control names “Department leadership” as approver, but that role is not declared as a workflow participant.

**Evidence reference:** Fee-waiver control; Primary Participants.

**Why it matters:** Approval cannot be reliably routed, enforced, or audited without a declared accountable role.

**Recommended resolution:** Replace it with a declared accountable role or add the role and its responsibilities to the operating model.

**Detection source:** Deterministic

### High: The prompt-response control requires aging requests to be surfaced but defines no enforceable response path.

**Evidence reference:** Prompt-response control; optional response target; archive and legal-review delay statements.

**Why it matters:** A dashboard can display dates but cannot validly determine legal promptness, assign risk, or trigger a controlled intervention.

**Recommended resolution:** Define monitoring cadence, accountable queue, path-sensitive criteria, warning and escalation thresholds, evidence, communication effects, and resolution states.

**Detection source:** Adversarial

### High: The proposed fee-estimate capability lacks authoritative inputs and decision criteria.

**Evidence reference:** Fee AI goal; fee step; commercial-purpose control; fee fields.

**Why it matters:** Without schedule versions, rates, quantities, rounding, waiver thresholds, or classification authority, an estimate would be a prediction rather than an auditable calculation.

**Recommended resolution:** Define the complete fee policy and data model; use deterministic calculation after human classification, with AI limited to candidate input extraction and explanation.

**Detection source:** Adversarial

### High: The recurring response target is structurally misaligned with permitted clarification and mandatory legal-review durations.

**Evidence reference:** REC-001, REC-004, REC-006; clarification rule; legal-review range.

**Why it matters:** Some valid workflow paths can exceed the target before search, screening, approval, and delivery occur, producing misleading escalation signals.

**Recommended resolution:** Define path-specific targets and stage expectations, display statutory age separately from operational forecasts, and flag infeasible paths at intake.

**Detection source:** Artifact-pair

### High: The stated AI boundary covers legal determinations but omits other consequential and irreversible actions.

**Evidence reference:** AI no-go statement; Deliver records and close request; portal, redaction, and cashiering write capabilities.

**Why it matters:** Literal compliance would still permit unauthorized financial, communication, redaction, lifecycle, or delivery actions.

**Recommended resolution:** Adopt a comprehensive action policy covering all governed decisions, external actions, production writes, and human review requirements.

**Detection source:** Adversarial

### High: Waiver authority and release-gate evidence are inconsistent across the control, workflow, data model, and REC-006.

**Evidence reference:** Fee-waiver control; fee and release steps; fee_status; REC-006.

**Why it matters:** A generic waived status cannot prove whether a schedule, de minimis, or exception waiver had the correct authority.

**Recommended resolution:** Define waiver classes, precedence, criteria, authority, approval sequence, schedule version, approver, timestamp, and evidence validated at release.

**Detection source:** Artifact-pair

### Medium: Closure is not linked to the retention disposition evidence required by the retention control.

**Evidence reference:** Request-file retention control; Deliver records and close request; current_status; REC-006.

**Why it matters:** Closed can be interpreted as compliant completion even when required file components and disposition evidence are absent.

**Recommended resolution:** Add a pre-close retention validation and a delivered-pending-retention state; capture package reference, required components, schedule, responsible person, and timestamp.

**Detection source:** Artifact-pair

### Medium: Records Center Archive is used in record collection but is absent from the declared target systems.

**Evidence reference:** Search and collect responsive records; Target Systems.

**Why it matters:** Its owner, access, read/write posture, security boundary, and pilot treatment are unknown.

**Recommended resolution:** Add the archive to the system inventory before designing support for physical-record retrieval.

**Detection source:** Deterministic

### Medium: The Cashiering System owner “Finance” does not resolve to a declared participant role.

**Evidence reference:** Target Systems: Cashiering System; Primary Participants.

**Why it matters:** Fee evidence, write authority, and support ownership are not aligned with the declared operating model.

**Recommended resolution:** Reconcile Finance ownership with the participant and approval models.

**Detection source:** Deterministic

### Medium: The Data Dictionary maps notes to department routing, but that step does not list notes among its used data.

**Evidence reference:** Data Dictionary: notes; Route to custodian departments.

**Why it matters:** It is unclear whether confidential staff commentary influences routing decisions.

**Recommended resolution:** Reconcile the mapping and document any approved use and handling controls.

**Detection source:** Deterministic

### Medium: The Data Dictionary maps notes to legal review, but that step does not list notes among its used data.

**Evidence reference:** Data Dictionary: notes; Legal review of withholdings.

**Why it matters:** The legal-review input set and confidential-data boundary are not fully traceable.

**Recommended resolution:** Correct the field mapping or explicitly document its legal-review use and access restrictions.

**Detection source:** Deterministic

### Medium: The Data Dictionary maps notes to scope clarification, but that step does not list notes among its used data.

**Evidence reference:** Data Dictionary: notes; Acknowledge and clarify scope.

**Why it matters:** The discrepancy weakens field-level traceability for a confidential field.

**Recommended resolution:** Correct the mapping, add the field to the step, or explain why it is retained but not consumed.

**Detection source:** Deterministic

### Medium: The Departmental Shared Drives owner “Department Directors” is not declared as a workflow participant.

**Evidence reference:** Target Systems: Departmental Shared Drives; Primary Participants.

**Why it matters:** Source access, search quality, and integration boundaries lack aligned accountability.

**Recommended resolution:** Add or reconcile the owner role and its responsibilities.

**Detection source:** Deterministic

### Medium: The Email Archive owner “IT Operations” is not declared as a workflow participant.

**Evidence reference:** Target Systems: Email Archive; Primary Participants.

**Why it matters:** The packet does not align archive access and operational ownership with the workflow participant model.

**Recommended resolution:** Add or reconcile the owner role and document access and support responsibilities.

**Detection source:** Deterministic

### Medium: The fee and commercial-classification dispute path does not identify a distinct adjudicator or an executable resolution process.

**Evidence reference:** Classify purpose and estimate fees; REC-003; participant list.

**Why it matters:** A disputed estimate can remain in awaiting-payment status without clear authority, evidence, timing, communication, or return path.

**Recommended resolution:** Name the adjudicator; define dispute status, evidence, timing, decision record, communication, and transitions to revision, payment, waiver, withdrawal, or continued processing.

**Detection source:** Adversarial

### Medium: The owner “Records team” for routing does not resolve to a declared participant.

**Evidence reference:** Route to custodian departments; Primary Participants.

**Why it matters:** Routing recommendations lack a clearly accountable human reviewer and escalation owner.

**Recommended resolution:** Use a declared role or add Records team to the participant model with explicit responsibilities.

**Detection source:** Deterministic

### Medium: The Public Records Portal owner “City Clerk” does not resolve to a declared participant role.

**Evidence reference:** Target Systems: Public Records Portal; Primary Participants.

**Why it matters:** Access, data quality, and integration accountability are ambiguous.

**Recommended resolution:** Reconcile the system-owner role with the participant model and document responsibilities.

**Detection source:** Deterministic

### Medium: The Records Management System owner “City Clerk” does not resolve to a declared participant role.

**Evidence reference:** Target Systems: Records Management System; Primary Participants.

**Why it matters:** Ownership of the system of record and export quality is not clearly assigned.

**Recommended resolution:** Reconcile the owner role and define accountability for exports, evidence, access, and data correction.

**Detection source:** Deterministic

### Medium: The Redaction Tool owner “City Clerk” does not resolve to a declared participant role.

**Evidence reference:** Target Systems: Redaction Tool; Primary Participants.

**Why it matters:** Accountability for a consequential write-capable system is ambiguous.

**Recommended resolution:** Reconcile the owner role and explicitly assign access, control, and evidence responsibilities.

**Detection source:** Deterministic

### Medium: The structural packet review independently confirms that the exemption escalation placeholder is not operationally testable.

**Evidence reference:** Screen for exemptions and apply redactions: “Escalate as needed.”

**Why it matters:** This is a process-definition defect distinct from the broader AI handoff risk and prevents consistent routing and audit.

**Recommended resolution:** Replace the placeholder with trigger, accountable role, action, evidence, timing, system of record, disposition, and rework requirements.

**Detection source:** Deterministic

### Medium: The under-three-day clarification target conflicts with a ten-business-day requester response period.

**Evidence reference:** Clarification target and baseline; Acknowledge and clarify scope.

**Why it matters:** AI can accelerate City drafting but cannot control requester response time; an end-to-end target may encourage premature abandonment or misleading attribution.

**Recommended resolution:** Measure City drafting/send latency separately from requester-response latency and use an appropriate distribution for end-to-end performance.

**Detection source:** Artifact-pair

### Low: Finance Cashier is listed as a primary participant but has no explicit operational responsibility.

**Evidence reference:** Primary Participants; workflow steps, controls, and system ownership.

**Why it matters:** The participant list may be incomplete or may overstate this role's involvement.

**Recommended resolution:** Assign an explicit responsibility or remove the role if it is not operationally involved.

**Detection source:** Deterministic

## Non-Obvious Insights

- The safest first value is operational integrity rather than content generation: the packet reveals that status fields can conceal missing legal, payment, and retention evidence.
- An aging dashboard built immediately could increase risk because the documented receipt field may use a later Clerk date and understate true City-held age.
- The largest theoretical labor opportunity—up to 2,450 screening hours at the stated target—sits behind the most difficult content, lineage, and disclosure controls.
- The clarification target measures an outcome partly controlled by the requester; AI performance should be judged on City drafting latency, not the full response cycle alone.
- Improving the withholding evidence model is valuable even without AI because the current request-level fields cannot prove the City's stated per-document standard.

## Highest-Value AI Use Cases

### Factual aging and control-integrity visibility

**Why it matters:** Median closure is 24 days, the slowest decile exceeds 60 days, and the Clerk lacks daily visibility. It also addresses misleading dates and contradictory terminal states.

**Recommended autonomy:** Read-only calculation and anomaly detection after receipt-date remediation; humans decide priority and escalation.

**Business value:** Faster operational awareness, less manual reporting, and stronger detection of records whose status is not supported by evidence.

### Ranked department and record-series suggestions

**Why it matters:** Approximately 20% of requests are rerouted, and routing knowledge is concentrated in two long-tenured staff.

**Recommended autonomy:** Recommendation only, with ranked choices, evidence, confidence, and recorded human correction.

**Business value:** Potentially reduces hundreds of annual rerouting events, but labeled historical outcomes and a reconciled owner are needed first.

### Sanitized clarification drafting

**Why it matters:** About 35% of requests require clarification and average eight days before search begins.

**Recommended autonomy:** Draft only after an approved transformation and legal sign-off; staff control content and transmission.

**Business value:** Can reduce City drafting latency, although requester response time must be measured separately.

### Candidate exemption and redaction pre-screening

**Why it matters:** Screening averages 3.5 hours per request and represents the largest documented effort pool.

**Recommended autonomy:** Future recommendation-only capability for approved non-law-enforcement record classes, followed by complete human page-level review.

**Business value:** Largest theoretical labor ceiling, but also the highest disclosure risk and not suitable for the first build.

## Where Agents Are Not Ready Yet

- Request-specific clarification is blocked because request text is prohibited from model context and no approved transformed field or sanitization process exists.
- Responsive-record pre-screening lacks an approved content boundary, document lineage, pre-ingestion protection, and evaluation by exemption class; law-enforcement material has an additional network restriction.
- Exemption authority is inconsistent between the narrative, workflow steps, controls, and REC-001, preventing reliable reviewer routing.
- Release eligibility cannot be inferred from current status; REC-002 demonstrates missing legal and payment prerequisites in a released state.
- Fee assistance lacks authoritative classification criteria, calculation inputs, schedule versions, waiver classes, and a complete dispute path.
- Abandonment, full denial, aging escalation, and retention completion do not have complete executable lifecycle branches.
- The system-of-record cannot support a write integration in the pilot period, and durable approval storage outside it is not defined.

## Recommended First Build

### Operations and Control Integrity View

An offline or read-only reviewer tool built from approved exports. It separates original receipt, Clerk logging, and forwarding dates; calculates factual age; displays stage and operational target; and flags missing or contradictory legal, payment, waiver, approval, and retention evidence. Initial testing should use de-identified or expressly approved metadata.

**Why this first:** This build can create immediate operational visibility while directly testing whether the City's source data can support trustworthy AI assistance. It also establishes the evidence discipline required before routing, clarification, or screening recommendations are credible.

**What it should not do:** It should not label a request legally timely or overdue, prioritize based on the defective receipt field, process free-text content, or treat status as proof that a governed prerequisite was satisfied.

**Expected user experience:** The Clerk opens a daily worklist, sees verified factual age and current stage, filters incomplete or aging records, reviews the evidence behind each warning, and records a human disposition without the tool changing any source system.

## Controls and Human Review

### Production action boundary

**Recommendation:** Technically disable external communications, portal delivery, redaction execution, fee actions, release or denial actions, abandonment, reopening, closure, status changes, and other production writes.

**Reason:** The current no-go statement is incomplete, several systems are write-capable, and delivery is irreversible.

### Model-context gate

**Recommendation:** Use an approved allowlist and transformation specification. Block request text, contact name, email, commercial-purpose statement, notes, internal withholding rationale, and record content unless specifically transformed and approved.

**Reason:** The packet contains direct context conflicts and no approved production content architecture.

### Law-enforcement and protected-content exclusion

**Recommendation:** Reject law-enforcement sources and record series before export; exclude privileged, protected-identity, medical, and other unapproved content from the first build.

**Reason:** These categories have explicit network or pre-model protection requirements.

### Receipt and aging integrity

**Recommendation:** Require separate original City receipt, Clerk logging, and forwarding dates; display factual age and operational targets without making legal timeliness determinations.

**Reason:** The current field can reset the response clock and aging rules lack enforceable thresholds.

### Human recommendation review

**Recommendation:** Require the named workflow reviewer to accept, revise, or reject every recommendation and preserve the source evidence, output, reviewer, disposition, and timestamp.

**Reason:** Routing, drafting, screening, and prioritization remain assistive capabilities with unresolved authority and exception rules.

### Release evidence separation

**Recommendation:** Maintain distinct durable evidence for legal determination, payment or authorized waiver, package version, per-document withholding rationale, release approval, delivery, and retention.

**Reason:** REC-002 and the current data model show that terminal status does not prove prerequisite completion.

### Monitoring and stop rule

**Recommendation:** Track restricted-data attempts, boundary violations, unsupported conclusions, reviewer corrections, and data-quality failures; stop affected processing when a boundary breach or improper release is detected.

**Reason:** The documented risk tolerance treats improper release as unacceptable, and the first build must prove containment before expansion.

## Implementation Roadmap

### 1. Packet and data remediation

**Focus:** Correct receipt-date semantics; investigate REC-001, REC-002, and REC-005; reconcile roles; and define aging, waiver, denial, abandonment, escalation, and retention rules.

**Outcome:** A validated metadata schema and operating rules suitable for factual read-only reporting.

### 2. Offline build and validation

**Focus:** Create export ingestion, allowlist enforcement, data-quality checks, factual age calculation, control-state anomaly rules, reviewer workflow, and audit evidence using de-identified or approved metadata.

**Outcome:** A working prototype that cannot access restricted content or change production systems.

### 3. One-quarter parallel pilot

**Focus:** Run the view alongside current operations, compare calculated values with human review, investigate anomalies, measure reporting effort and adoption, and correct false signals.

**Outcome:** Evidence that the view is useful, traceable, and operationally reliable without changing governed workflow actions.

### 4. Expansion decision

**Focus:** Use pilot evidence to decide whether to prepare recommendation-only routing, sanitized clarification, or controlled non-law-enforcement screening; require separate data and process approvals for each.

**Outcome:** A prioritized next-stage business case grounded in measured value and resolved controls rather than assumed automation readiness.

## Success Metrics

- 100% of records included in trusted aging reporting have a verified original City receipt anchor or a visible unverified-data warning.
- Daily aging and integrity view is produced without hand assembly, with preparation effort measured against a documented baseline.
- All detected legal, payment, waiver, approval, status, and retention anomalies receive a recorded human disposition.
- No restricted content enters the pilot and no production write or external communication is executed by the tool.
- Clerk users regularly use the view for operational review; usage and rejected or corrected findings are measured.
- Age calculations and stage classifications agree with human-validated records at an agreed acceptance level established before pilot launch.
- If routing is later tested, first-pass accuracy is measured against the documented target above 90%, with corrections retained.
- If content screening is later approved, analyst review time and false negatives are measured by exemption class, with any improper release triggering a stop.

## Open Questions

- What date is the authoritative anchor for City receipt, and can original receipt and forwarding timestamps be recovered from each intake channel?
- Why is REC-002 released with pending legal review and an invoiced fee, and does it represent stale data, an exception, or a control failure?
- Which exemption categories can the Records Analyst finalize, and which require Assistant City Attorney determination?
- What operational criteria, cadence, owner, and escalation path should govern aging without implying a fixed statutory deadline?
- What hosting, access, logging, deletion, retention, and incident requirements apply to metadata, request text, record content, prompts, and outputs?
- Who has final authority for commercial classification, fee disputes, each waiver class, full denial, and no-contact/unsearchable requests?
- What document-level structure and storage process will retain withholding instances, legal decisions, release approvals, package versions, and retention evidence?
- What are the authoritative fee schedules, calculation inputs, revision rules, and retention periods needed for later workflow support?
