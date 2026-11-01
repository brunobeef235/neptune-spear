# NEPTUNE SPEAR — PROJECT BIBLE

**Project Name:** Neptune Spear  
**Repository:** `brunobeef235/neptune-spear`  
**Project Status:** Early Development  
**Document Version:** 1.0  
**Project Owner:** Project Director

---

## 1. PROJECT VISION

Neptune Spear is a local-first intelligent code analysis and authorized security testing system.

Its long-term objective is to analyze software structures, understand program behavior, identify potential security weaknesses, formulate testable hypotheses, conduct controlled experiments, and produce evidence-based findings.

The system is designed to operate primarily on local hardware without depending on hosted AI services, cloud infrastructure, or large pretrained language models as its core reasoning engine.

## 2. CORE PRINCIPLES

1. Local-first operation.
2. Evidence-based analysis.
3. Explainable reasoning.
4. Modular and extensible architecture.
5. Reproducible testing.
6. Resource-aware execution.
7. Strict authorization and sandbox boundaries.
8. Human approval for major architectural decisions.
9. No unsupported claims about capabilities or accuracy.
10. Continuous improvement through validated feedback.

## 3. SYSTEM COMPONENTS

### 3.1 ARGUS — Code Analysis Engine

Argus is responsible for static code analysis and program understanding.

Its intended capabilities include:

- Multi-language source parsing.
- Universal intermediate representation.
- Symbol and scope analysis.
- Control-flow analysis.
- Data-flow and provenance tracking.
- Memory and state modeling.
- Interprocedural analysis.
- Semantic and mathematical reasoning.
- Vulnerability hypothesis generation.
- Evidence collection and reporting.

Argus must distinguish between a potential vulnerability and a confirmed exploitable vulnerability.

### 3.2 ABABIL — Controlled Testing Engine

Ababil receives hypotheses and test plans from Argus.

Its intended capabilities include:

- Mathematical test-case generation.
- Input and payload generation.
- Controlled experiment execution.
- Runtime behavior observation.
- Evidence collection.
- Result reporting to Argus and Thoth.

Ababil must only test systems for which explicit authorization exists. Testing must use isolated sandboxes or approved replicas with defined resource and execution limits.

### 3.3 THOTH — Independent Audit Engine

Thoth independently reviews Argus findings and Ababil experiment results.

Its intended capabilities include:

- Reviewing evidence and reasoning.
- Identifying false positives and missed cases.
- Checking reproducibility.
- Evaluating confidence and limitations.
- Producing human-readable audit reports.
- Proposing improvements to Argus and Ababil.

Thoth may recommend changes, but must not unilaterally modify core architecture or approve its own proposed changes.

## 4. DEVELOPMENT ARCHITECTURE

The system is intended to contain:

- Argus
- Ababil
- Thoth
- Shared Core
- Knowledge and Rule Store
- Communication Interfaces
- Experiment and Evidence Store
- Reporting System

The architecture will evolve through versioned technical specifications and approved design decisions.

## 5. DEVELOPMENT ENVIRONMENT

Initial target environment:

- Operating System: Windows 11
- Programming Language: Python
- Python Version: 3.13
- RAM: 8 GB
- CPU: Intel Core i5-8365U
- Integrated Graphics: Intel UHD Graphics 620

The implementation must consider limited hardware resources.

Large pretrained models, cloud inference, and dedicated GPU infrastructure must not be required for the core runtime.

Open-source libraries may be used for parsing, mathematics, storage, and other supporting functions, subject to project approval.

## 6. DEVELOPMENT HISTORY

### v0.1 — Initial Argus Prototype

Implemented:
- Versioned opcode registry.
- Basic intermediate representation.
- Python AST adapter.
- Basic graph representation.
- Initial intraprocedural taint candidate detection.
- JSON and Markdown reporting.
- CLI interface.

Known limitations:
- Basic name-based dataflow.
- Incomplete control-flow analysis.
- Limited sink and source coverage.
- No comprehensive interprocedural taint propagation.

### v0.2 — Structural Intelligence Prototype

Introduced:
- Basic symbol and scope representation.
- Basic block control-flow graph.
- Initial conditional and loop structures.

Known limitations:
- Incomplete handling of complex control flow.
- No comprehensive reaching-definitions analysis.
- No complete alias or memory model.

### v0.3 — Semantic and Interprocedural Prototype

Introduced:
- Syntactic static call graph.
- Basic function summaries.
- Call resolution status classification.

Known limitations:
- No complete interprocedural dataflow propagation.
- Limited dynamic dispatch and import resolution.
- No comprehensive alias or memory analysis.

These historical versions are prototypes, not production-ready security analysis systems.

### v0.4 — Planned Development

The next planned development area is Dataflow and Memory Intelligence.

It must be specified, implemented, tested, and independently reviewed before being considered complete.

## 7. DEVELOPMENT GOVERNANCE

The Project Director has final authority over:

- Project direction.
- Architecture approval.
- Feature priorities.
- Dependency approval.
- Release approval.
- Major design changes.

AI agents must follow the approved Neptune Spear Development Protocol (NSDP).

No AI agent may unilaterally redefine core architecture, remove important project files, or claim a feature is complete without supporting evidence.

## 8. SECURITY AND ETHICAL BOUNDARIES

Neptune Spear is intended for defensive code analysis and authorized security testing.

All dynamic testing must respect:

- Explicit authorization.
- Defined scope.
- Isolated execution environments.
- Resource and time limits.
- Evidence preservation.
- Safe cleanup and recovery procedures.

Unauthorized testing against third-party systems is outside project scope.

## 9. SOURCE OF TRUTH

The GitHub repository is the authoritative source of project information.

Approved architecture, specifications, development status, decisions, code, tests, and handoff documents must be maintained in this repository.

Chat conversations are supporting discussions, not the authoritative project record.

## 10. DEFINITION OF DONE

A feature is not complete merely because its code has been written.

A feature can be marked complete only when:

1. Its specification and acceptance criteria are defined.
2. Implementation is available in the repository.
3. Relevant automated tests have been executed.
4. Test results are documented.
5. Known limitations are recorded.
6. Required documentation is updated.
7. Independent review is completed when required.
8. The Project Director approves the result.

---

**End of Project Bible**

