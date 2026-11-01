# NEPTUNE SPEAR DEVELOPMENT PROTOCOL (NSDP)

**Protocol Version:** 1.0  
**Project:** Neptune Spear  
**Status:** Initial Protocol  
**Authority:** Project Director

---

## 1. PURPOSE

The Neptune Spear Development Protocol (NSDP) defines how humans and AI agents collaborate to design, implement, test, review, and maintain Neptune Spear.

Its purpose is to ensure consistent architecture, reliable implementation, traceable decisions, reproducible testing, and controlled project development.

GitHub is the single source of truth for approved project information and code.

## 2. TEAM STRUCTURE

### 2.1 Project Director — Human Owner

The Project Director is the owner and final decision-maker of Neptune Spear.

Responsibilities:

- Define project goals and priorities.
- Approve architecture and technical specifications.
- Assign tasks to AI agents.
- Review important implementation results.
- Approve dependencies and major changes.
- Approve releases and merges into the stable branch.

No AI agent may override the Project Director's decisions.

### 2.2 ChatGPT — Chief AI Architect and Consultant

ChatGPT is responsible for consultation, planning, architecture, and technical coordination.

Responsibilities:

- Maintain the overall technical vision.
- Design system architecture.
- Create technical specifications.
- Break large goals into implementable tasks.
- Prepare precise coding instructions for Claude.
- Review implementation reports and code supplied by the Project Director.
- Help design tests and evaluate results.
- Identify architectural conflicts and technical risks.
- Maintain consistency across Argus, Ababil, Thoth, and Shared Core.

ChatGPT does not have automatic authority to modify the GitHub repository or approve its own architectural proposals.

### 2.3 Claude — AI Developer

Claude is primarily responsible for coding and implementation.

Responsibilities:

- Read the approved project documents and task specifications.
- Implement requested features.
- Fix bugs within the assigned scope.
- Create and update automated tests.
- Execute tests when the environment permits.
- Report modified files and implementation details.
- Document actual test results and known limitations.
- Prepare a handoff report after each task.

Claude must not independently redefine core architecture, remove important project components, or introduce unapproved dependencies.

If a task requires an architectural change, Claude must submit a proposal before implementing it.

## 3. AUTHORITY AND DECISION-MAKING

The authority hierarchy is:

1. Project Director.
2. Approved project specifications and decisions.
3. Chief AI Architect's approved technical direction.
4. Developer implementation decisions within the assigned scope.

When documents conflict, the AI agents must identify the conflict and request clarification.

No agent may silently replace an approved design with a different architecture.

## 4. SINGLE SOURCE OF TRUTH

The GitHub repository is the authoritative project record.

AI agents must prioritize:

1. PROJECT_BIBLE.md
2. NSDP.md
3. CURRENT_STATUS.md
4. Relevant architecture specifications.
5. Relevant task specifications.
6. DECISION_LOG.md
7. Actual source code and automated test results.

Conversation history is supporting context, not a replacement for approved repository documentation.

## 5. STANDARD DEVELOPMENT WORKFLOW

Every significant feature follows this process:

### Phase 1 — Requirement Definition

The Project Director and ChatGPT define the problem, objective, scope, and expected outcome.

### Phase 2 — Technical Design

ChatGPT prepares the technical design, interfaces, dependencies, risks, and acceptance criteria.

### Phase 3 — Task Assignment

ChatGPT prepares a clear implementation instruction for Claude.

### Phase 4 — Implementation

Claude implements the approved task without exceeding its scope.

### Phase 5 — Testing

Claude runs relevant tests and reports the actual results.

### Phase 6 — Review and Audit

ChatGPT reviews the submitted work against the specification, architecture, tests, and known limitations.

Independent review must be used for high-impact or security-sensitive changes where practical.

### Phase 7 — Human Approval

The Project Director decides whether to accept, request revisions, or reject the implementation.

### Phase 8 — Integration and Documentation

Approved changes are merged into the appropriate branch. Documentation and project status are updated.

## 6. TASK MANAGEMENT

Every significant development task must have:

- Unique task ID.
- Objective.
- Background and context.
- Scope.
- Allowed files or modules.
- Files and modules that must not be modified.
- Technical requirements.
- Dependencies.
- Acceptance criteria.
- Test plan.
- Security considerations.
- Expected handoff report.

Suggested task statuses:

- PROPOSED
- SPECIFIED
- IN_PROGRESS
- IMPLEMENTED
- TESTING
- AUDIT_PENDING
- APPROVED
- COMPLETED
- BLOCKED
- REJECTED

IMPLEMENTED does not mean COMPLETED.

## 7. GIT AND BRANCH MANAGEMENT

The repository uses the following branch strategy:

- `main`: stable and approved project state.
- `develop`: integration branch for approved development work.
- `feature/*`: new feature implementation.
- `fix/*`: bug fixes.
- `docs/*`: documentation changes.
- `experiment/*`: isolated experiments.

Development work should use a separate branch.

Pull Requests should be reviewed before integration into `main`.

The Project Director controls approval of important merges.

Destructive operations, history rewriting, and deletion of important project data require explicit approval and an appropriate backup.

## 8. CODING RULES

All implementation must follow these rules:

1. Prefer readable and maintainable code.
2. Use clear module and function responsibilities.
3. Avoid unnecessary complexity.
4. Preserve existing interfaces unless a change is approved.
5. Handle errors explicitly.
6. Add tests for new behavior.
7. Avoid hardcoded secrets and credentials.
8. Document important design decisions.
9. Avoid unnecessary dependencies.
10. Consider the project's limited hardware resources.

The target development environment is Windows 11, Python 3.13, 8 GB RAM, Intel Core i5-8365U, and Intel UHD Graphics 620.

Core functionality must remain local-first.

## 9. TESTING AND QUALITY CONTROL

Implementation reports must distinguish between:

- Tests not written.
- Tests written but not executed.
- Tests executed and failed.
- Tests executed and passed.
- Tests not applicable.

Never claim tests passed without actual execution evidence.

Testing should include relevant:

- Unit tests.
- Integration tests.
- Regression tests.
- Error-handling tests.
- Reproducibility checks.

Important security-sensitive features should receive additional review.

## 10. SECURITY POLICY

Neptune Spear is intended for defensive analysis and authorized security testing.

Ababil must operate only within explicitly authorized and controlled environments.

Testing must have:

- Defined scope.
- Explicit authorization.
- Isolated execution environment.
- Resource and time limits.
- Evidence preservation.
- Cleanup and recovery procedures.

AI agents must not expand testing to unauthorized third-party systems.

## 11. DEPENDENCY GOVERNANCE

New external dependencies must be justified.

A dependency proposal must include:

- Name and version.
- Purpose.
- License.
- Maintenance status.
- Security considerations.
- Resource impact.
- Alternatives considered.

Major dependencies require Project Director approval.

## 12. CHANGE MANAGEMENT

Any change affecting core architecture, module boundaries, shared interfaces, security boundaries, or major dependencies requires an explicit proposal.

The proposal must describe:

- Current design.
- Proposed change.
- Reason.
- Benefits.
- Drawbacks.
- Risks.
- Compatibility impact.
- Migration strategy.
- Testing requirements.

The Project Director must approve the change before implementation.

## 13. AI HANDOFF REQUIREMENTS

At the end of each significant task, Claude must provide:

- Task ID.
- Branch and commit information, if available.
- Summary of completed work.
- List of modified and added files.
- Tests executed and actual results.
- Known bugs and limitations.
- Incomplete work.
- Dependencies introduced.
- Decisions requiring approval.
- Recommended next steps.

Handoff documents should be stored in `docs/handoffs/`.

## 14. DEFINITION OF DONE

A task is complete only when:

1. Its acceptance criteria are satisfied.
2. Implementation is available in the repository.
3. Relevant tests have been executed.
4. Results are documented.
5. Known limitations are recorded.
6. Required documentation is updated.
7. Required review is completed.
8. Project Director approval is obtained.

## 15. RELEASE GOVERNANCE

Use semantic versioning:

- MAJOR: incompatible architectural or interface changes.
- MINOR: new backward-compatible functionality.
- PATCH: backward-compatible fixes.

A release requires:

- Completed scope.
- Passing relevant tests.
- Review and audit.
- Updated documentation.
- Recorded limitations.
- Backup and release tag.
- Project Director approval.

## 16. DISAGREEMENT RESOLUTION

If ChatGPT and Claude disagree:

1. Both positions must be documented.
2. Technical evidence must be provided.
3. Risks and compatibility must be evaluated.
4. A small experiment may be conducted when appropriate.
5. ChatGPT provides a recommendation.
6. The Project Director makes the final decision.

Neither AI may silently implement its preferred alternative.

## 17. FINAL GOVERNING PRINCIPLE

Neptune Spear is a human-directed engineering project.

AI agents are collaborators and technical tools, not independent project owners.

Architecture, security, implementation acceptance, and release decisions remain accountable to the Project Director.

---

**End of Neptune Spear Development Protocol**
