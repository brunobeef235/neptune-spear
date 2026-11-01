# NEPTUNE SPEAR — DECISION LOG

**Document Version:** 1.0  
**Project:** Neptune Spear  
**Authority:** Project Director

---

## 1. PURPOSE

This document records important technical, architectural, organizational, and development decisions made during the Neptune Spear project.

Its purpose is to:

- Preserve the reasoning behind important decisions.
- Prevent conflicting architectural directions.
- Maintain consistency across AI agents.
- Provide historical traceability.
- Make future changes easier to evaluate.

This document is the authoritative record of approved project decisions.

## 2. DECISION STATUS

Every decision must have one of the following statuses:

- PROPOSED — awaiting evaluation.
- APPROVED — formally accepted.
- REJECTED — evaluated and declined.
- SUPERSEDED — replaced by a newer approved decision.
- DEFERRED — postponed for later consideration.

Only APPROVED decisions are binding.

## 3. DECISION AUTHORITY

The Project Director has final authority over project decisions.

ChatGPT may prepare recommendations and technical evaluations.

Claude may propose implementation-related improvements.

Neither AI may independently approve a major architectural change.

## 4. APPROVED INITIAL DECISIONS

### ADR-001 — Local-First Architecture

**Status:** APPROVED  
**Decision Owner:** Project Director

Decision:

Neptune Spear must prioritize local execution and must not depend on hosted AI services, cloud inference, or large pretrained models as its core reasoning engine.

Reason:

The project targets constrained local hardware and requires independence from external AI infrastructure.

Consequences:

- Core functionality must be designed for local operation.
- Dependencies must be evaluated for resource impact.
- External services must not become mandatory core dependencies.

### ADR-002 — Three-System Architecture

**Status:** APPROVED  
**Decision Owner:** Project Director

Decision:

Neptune Spear is organized around three primary systems:

- Argus — code analysis and program understanding.
- Ababil — controlled and authorized testing.
- Thoth — independent audit and evidence review.

Reason:

Analysis, experimentation, and independent review should have clearly separated responsibilities.

Consequences:

- Each system requires defined interfaces.
- Shared data structures must be documented.
- No system should silently assume another system's responsibilities.

### ADR-003 — Hybrid Two-AI Development Model

**Status:** APPROVED  
**Decision Owner:** Project Director

Decision:

The project uses two primary AI agents:

- ChatGPT — Chief AI Architect and Consultant.
- Claude — AI Developer.

The human Project Director retains final authority.

Reason:

The project needs consistent architectural direction while keeping coding execution focused.

Consequences:

- ChatGPT prepares technical designs and coding instructions.
- Claude implements assigned coding tasks.
- ChatGPT reviews submitted implementation evidence.
- The Project Director approves important changes and integration.

### ADR-004 — GitHub as the Single Source of Truth

**Status:** APPROVED  
**Decision Owner:** Project Director

Decision:

GitHub is the central repository for approved code, specifications, documentation, decisions, tests, and project status.

Reason:

Multiple AI agents and development sessions must work from consistent information.

Consequences:

- Important decisions must be documented.
- AI agents must read current repository documents.
- Conversation history is supporting context, not the authoritative project record.

### ADR-005 — Human Approval for Major Changes

**Status:** APPROVED  
**Decision Owner:** Project Director

Decision:

Major architectural changes, security boundary changes, important dependency additions, and release decisions require explicit human approval.

Reason:

AI-generated recommendations and implementations must remain under human project governance.

Consequences:

- Proposed changes must include risks and alternatives.
- No AI agent may silently change core architecture.
- Approved changes must be documented.

### ADR-006 — Authorized Security Testing Only

**Status:** APPROVED  
**Decision Owner:** Project Director

Decision:

Ababil may only conduct testing within explicitly authorized and controlled environments.

Reason:

The project is intended for defensive analysis and legitimate security validation.

Consequences:

- Testing scope must be defined.
- Sandboxes or approved replicas must be used.
- Resource and execution limits must be enforced.
- Evidence must be preserved.

## 5. PROPOSED DECISIONS

New proposals must be added here with status PROPOSED.

No proposal becomes binding until approved by the Project Director.

## 6. DECISION TEMPLATE

Use this structure for every new decision:

### ADR-XXX — Decision Title

**Status:** PROPOSED / APPROVED / REJECTED / SUPERSEDED / DEFERRED  
**Date:** YYYY-MM-DD  
**Decision Owner:** Project Director

**Context:**

Describe the problem or situation requiring a decision.

**Options Considered:**

List the alternatives.

**Decision:**

Describe the selected approach.

**Reason:**

Explain why the approach was selected.

**Consequences:**

Describe benefits, drawbacks, risks, and compatibility effects.

**Approval:**

Record who approved the decision and when.

---

## 7. CHANGE HISTORY

| Version | Description |
|---|---|
| 1.0 | Initial decision log and approved foundational decisions |

---

**End of Decision Log**
