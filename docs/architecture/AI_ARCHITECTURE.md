# AI_ARCHITECTURE.md
# Neptune Spear — AI Architecture

**Status:** Proposed — awaiting Project Director's approval for implementation  
**Architecture direction:** Local-First, Custom Causal AI  
**Applies to:** Argus, Ababil, Thoth, and Shared Core

## 1. Vision

Neptune Spear will use a custom-built Causal AI foundation shared by Argus, Ababil, and Thoth.

The system will not depend on pretrained language models, large language models, neural-network models, or pattern-similarity-based inference.

Its intelligence will be developed around mathematical reasoning, program semantics, symbolic computation, causal modeling, logical inference, and evidence-based verification.

All core intelligence and processing must run locally on the user's computer.

## 2. Core Principles

1. Local-first execution: no cloud inference or external AI service is mandatory.
2. Custom intelligence: the causal reasoning engine and its core knowledge representation are developed specifically for Neptune Spear.
3. No pretrained AI models: no pretrained LLM, neural network, or externally trained AI model as the reasoning foundation.
4. No similarity-based inference: conclusions must not depend on retrieving similar examples as their primary justification.
5. Causal reasoning: conclusions must be supported by explicit causal mechanisms, logical relationships, or validated evidence.
6. Explainability: reasoning paths and supporting evidence must be inspectable.
7. Uncertainty awareness: insufficient evidence must result in an uncertainty classification, not an invented conclusion.
8. Controlled evolution: no automatic self-modification or unreviewed changes to the reasoning engine.

## 3. Shared AI Foundation

Argus, Ababil, and Thoth will use the same underlying custom AI foundation.

The shared foundation includes:

- Code and information representation.
- Numerical and mathematical representation.
- Symbolic reasoning.
- Causal graph construction.
- Causal model evaluation.
- Counterfactual reasoning.
- Constraint solving.
- Evidence and uncertainty management.
- Result reconstruction and serialization.

The three systems will have separate responsibilities, execution policies, and task-specific configurations. Sharing the foundation does not mean sharing every operational decision or security permission.

## 4. Processing Architecture

The intended processing pipeline is:

1. Input acquisition.
2. Parsing and structural interpretation.
3. Conversion into an intermediate representation.
4. Extraction of program semantics and relationships.
5. Construction of numerical, symbolic, and causal representations.
6. Mathematical and causal reasoning.
7. Constraint and consistency verification.
8. Evidence evaluation and confidence assessment.
9. Reconstruction into findings, hypotheses, test specifications, or code representations.
10. Reporting and audit trail generation.

Numerical conversion must preserve relevant program structure and meaning. A simple character-to-number encoding is insufficient.

The representation must preserve, where applicable:

- Syntax tree structure.
- Types and values.
- Variable relationships.
- Data dependencies.
- Control flow.
- Function calls.
- State transitions.
- Memory and alias relationships.
- Program semantics.

## 5. Causal Reasoning Foundation

Candidate mathematical and logical techniques include:

- Structural Causal Models (SCM).
- Causal Graphs.
- Intervention analysis.
- Counterfactual reasoning.
- Symbolic reasoning.
- Abstract interpretation.
- Constraint solving.
- Program semantics.
- Formal verification techniques.

These are candidate techniques, not yet a finalized dependency list.

The system must distinguish between:

- Observed relationships.
- Statically derived relationships.
- Experimentally validated causal relationships.
- Hypotheses requiring further evidence.
- Unknown or unresolved relationships.

A causal claim must identify its assumptions and supporting evidence.

## 6. No Training Dataset Dependency

The system must be able to analyze previously unseen source code without requiring a dataset of prior vulnerabilities or code examples.

Its primary reasoning foundation must come from:

- Language specifications.
- Formal program semantics.
- Structural analysis.
- Explicit logical rules.
- Mathematical models.
- Causal relationships derived from program behavior.
- Controlled experiments and their evidence.

This does not eliminate the need for language specifications, formal rules, test cases, or execution evidence.

The system must not claim that every causal relationship can be inferred from source code alone. When information is insufficient, it must report uncertainty or request a controlled experiment.

## 7. Responsibilities of Each AI

### 7.1 Argus — Causal Code Analysis

Argus uses the shared foundation to:

- Understand source-code structure and semantics.
- Construct program and dependency graphs.
- Analyze data and control flow.
- Identify possible causal paths to security failures.
- Generate explainable hypotheses.
- Provide bounded test specifications to Ababil.

### 7.2 Ababil — Causal Experimentation

Ababil uses the shared foundation to:

- Evaluate hypotheses received from Argus.
- Generate controlled test cases.
- Assess expected outcomes.
- Execute only authorized tests in isolated environments.
- Collect raw evidence.
- Compare observed behavior with predicted behavior.

Ababil must enforce scope, sandbox, resource, and execution limits independently of the reasoning engine.

### 7.3 Thoth — Independent Causal Verification

Thoth uses the shared foundation to:

- Audit Argus findings.
- Verify Ababil evidence.
- Examine assumptions and causal claims.
- Identify unsupported conclusions.
- Detect logical inconsistencies.
- Assess false positives and potential false negatives.
- Produce independent audit reports.

Thoth must not blindly accept the conclusions of Argus or Ababil.

## 8. Custom Model and Mathematical Parameters

Neptune Spear must distinguish neural-network parameters from mathematical parameters.

Neural-network weights and pretrained model parameters are excluded from the architecture.

Mathematical coefficients, constants, constraints, and parameters in explicit causal models may be used when their meaning, source, and assumptions are documented.

Any estimated causal parameter must identify the evidence and estimation method used.

## 9. Open-Source Infrastructure

Open-source libraries may be used for infrastructure, including:

- Parsing and syntax processing.
- Mathematical operations.
- Graph processing.
- Constraint solving.
- Storage and serialization.
- Testing and benchmarking.

Such libraries must not silently introduce pretrained AI models or replace Neptune Spear's custom causal reasoning foundation.

Every dependency must undergo technical, security, licensing, and resource evaluation.

## 10. Hardware and Local Execution

Initial target environment:

- Windows 11.
- Python 3.13.
- Intel Core i5-8365U.
- Intel UHD Graphics 620.
- 8 GB RAM.

The architecture must use bounded memory, incremental processing, efficient data structures, and configurable execution limits.

Performance must be measured through actual benchmarks. The design must not assume that arbitrarily complex mathematical reasoning can run efficiently on the target hardware.

## 11. Learning and Evolution

The initial architecture must not require machine-learning training datasets.

Future improvement may use reviewed evidence, formal rules, verified causal models, and human-approved changes.

No component may automatically rewrite its own source code, modify core reasoning rules, or deploy a changed reasoning model without validation and approval.

## 12. Architecture Acceptance Criteria

The architecture will not be considered implemented until:

1. The shared causal representation is specified and tested.
2. Code-to-representation conversion preserves relevant semantics.
3. Causal reasoning can produce inspectable reasoning traces.
4. Uncertainty and unsupported claims are handled explicitly.
5. All three systems use the same approved foundation.
6. Local execution is verified on the target hardware.
7. No prohibited pretrained or neural-network model is required.
8. Dependencies and their roles are documented.
9. Security and resource boundaries are tested.
10. Independent verification by Thoth is demonstrated.

## 13. Governance

This document defines the proposed architectural direction.

It does not authorize implementation of unapproved algorithms, dependencies, or major architectural changes.

The Project Director retains final approval over architecture changes, dependencies, security boundaries, and releases.

Implementation must follow NSDP and the relevant approved task specifications.
