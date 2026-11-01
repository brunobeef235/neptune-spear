# Argus Architecture

**Project:** Neptune Spear  
**Component:** Argus  
**Document Type:** Architecture Specification  
**Status:** Initial Draft  
**Version:** 0.1.0

---

## 1. Purpose

Argus is the static code analysis and reasoning component of Neptune Spear.

Its primary responsibility is to inspect source code, construct structured representations, analyze program behavior, identify potential security weaknesses, and produce evidence-backed findings.

Argus must distinguish between a confirmed observation, a mathematical or semantic hypothesis, and a verified vulnerability.

## 2. Core Responsibilities

Argus is responsible for:

1. Source code parsing and language adaptation.
2. Construction of a universal intermediate representation.
3. Control-flow and data-flow analysis.
4. Symbol, scope, and dependency analysis.
5. Interprocedural analysis.
6. Semantic and constraint reasoning.
7. Vulnerability hypothesis generation.
8. Test-case and experiment planning.
9. Evidence collection and confidence estimation.
10. Structured reporting.

## 3. Internal Architecture

Argus is organized into the following logical subsystems.

### 3.1 Language Adapter Layer

Converts supported programming languages into Argus-compatible representations.

Responsibilities:
- Source parsing.
- AST extraction.
- Language-specific semantic mapping.
- Source location preservation.
- Unsupported syntax reporting.

Each language adapter must be independently testable.

### 3.2 Universal Representation Layer

Converts language-specific structures into a common intermediate representation.

The representation should preserve:
- Instructions and operations.
- Variables and symbols.
- Types and attributes.
- Source locations.
- Control-flow relationships.
- Data dependencies.
- Function and module boundaries.

### 3.3 Program Graph Engine

Constructs and maintains program graphs.

Planned graph types:
- Control-flow graph (CFG).
- Data-flow graph (DFG).
- Call graph.
- Dependency graph.
- Memory and object relationship graph.

Graph completeness must be documented for each supported language and feature.

### 3.4 Semantic Analysis Engine

Analyzes the meaning and behavior of program operations.

Planned capabilities:
- Symbol resolution.
- Scope analysis.
- Type and value tracking.
- Definition-use relationships.
- Function summaries.
- Interprocedural reasoning.
- State and memory modeling.

### 3.5 Mathematical Reasoning Engine

Uses mathematical methods to analyze program constraints and behavior.

Planned capabilities:
- Constraint solving.
- Symbolic expressions.
- Boundary analysis.
- Invariant discovery.
- Path-condition analysis.
- Numerical reasoning.

Mathematical results must retain their assumptions and derivation evidence.

### 3.6 Security Analysis Engine

Generates security-related hypotheses from program structure and behavior.

It should:
- Identify potential sources and sinks.
- Track relevant data flows.
- Consider validation and sanitization.
- Evaluate trust boundaries.
- Correlate multiple weaknesses.
- Assign evidence-based confidence.

A candidate finding must not automatically be described as an exploitable vulnerability.

### 3.7 Experiment Planning Interface

Prepares structured experiment requests for Ababil.

Each request should contain:
- Experiment identifier.
- Target component and scope.
- Hypothesis.
- Preconditions.
- Proposed input or test case.
- Expected observations.
- Safety constraints.
- Resource and time limits.

Argus does not independently authorize testing. Execution must follow the project authorization policy.

### 3.8 Evidence and Reporting Engine

Stores the reasoning behind every finding.

A finding should include:
- Unique identifier.
- Finding category.
- Severity estimate.
- Source location.
- Relevant code and graph references.
- Data-flow or control-flow explanation.
- Assumptions.
- Confidence level.
- Supporting evidence.
- Uncertainty and limitations.
- Related experiment results.

## 4. Analysis Pipeline

The planned analysis pipeline is:

1. Receive source code.
2. Identify language and project structure.
3. Parse source code.
4. Build intermediate representation.
5. Construct program graphs.
6. Resolve symbols and dependencies.
7. Perform semantic and data-flow analysis.
8. Generate security hypotheses.
9. Plan experiments where appropriate.
10. Receive authorized Ababil results.
11. Update finding confidence.
12. Produce structured reports.

Not every analysis stage must be available in the initial implementation.

## 5. Communication with Other Components

### Ababil

Argus sends experiment plans and receives execution evidence.

Argus must not treat a proposed experiment as proof of a vulnerability.

### Thoth

Thoth independently reviews Argus findings, assumptions, reasoning, and evidence.

Argus must provide sufficient traceability for independent auditing.

### Shared Core

Argus uses shared data structures, registries, protocols, storage interfaces, and common utilities where approved.

## 6. Design Principles

- Modular architecture.
- Local-first execution.
- Reproducible analysis.
- Evidence-based conclusions.
- Explicit uncertainty.
- Extensible language adapters.
- Resource-aware computation.
- Deterministic behavior where practical.
- Human approval for architectural changes.

## 7. Resource Constraints

The initial development target is a Windows 11 environment with Python 3.13, 8 GB RAM, and an Intel Core i5-8365U with integrated graphics.

The initial design must prioritize:
- CPU execution.
- Low memory consumption.
- Incremental analysis.
- Efficient graph storage.
- Avoidance of mandatory cloud services.
- Avoidance of mandatory GPU acceleration.

## 8. Current Implementation Status

The following capabilities have appeared in early Argus prototypes:

- Versioned opcode registry.
- Basic intermediate representation.
- Python AST adapter.
- Basic instruction and dependency graph.
- Basic intraprocedural taint candidate detection.
- Basic symbol and scope analysis.
- Basic control-flow graph construction.
- Syntactic call graph.
- Basic function summaries.

These are prototype capabilities, not complete implementations of the architecture described above.

## 9. Known Limitations

The initial prototypes do not yet provide complete:

- Interprocedural taint propagation.
- Alias and memory analysis.
- Cross-module semantic resolution.
- Dynamic dispatch resolution.
- Exception-flow analysis.
- Framework-specific analysis.
- Formal verification.
- Multi-language semantic equivalence.

All capability claims must be verified against the actual implementation and tests.

## 10. Definition of Done

An Argus feature is complete only when:

1. Its specification is approved.
2. Its implementation meets acceptance criteria.
3. Automated tests pass.
4. Regression risks are evaluated.
5. Evidence and limitations are documented.
6. Independent audit is completed where required.
7. Project Director approval is obtained.
8. Documentation and project status are updated.

---

**Document Governance:** This document is an initial architecture specification. Changes to core architecture require review under the Neptune Spear Development Protocol (NSDP).
