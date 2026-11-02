# CAUSAL_ENGINE_ARCHITECTURE.md
# Neptune Spear — Causal Reasoning Engine Architecture

**Status:** Proposed — Architecture Specification  
**Version:** 0.1  
**Parent:** AI_ARCHITECTURE.md  
**Foundation:** UCR_ARCHITECTURE.md and UCR_DATA_MODEL.md  
**Consumers:** Argus, Ababil, Thoth

---

## 1. Purpose

The Causal Reasoning Engine (CRE) is the shared reasoning foundation of Neptune Spear.

Its purpose is to construct, evaluate, and verify causal explanations of program behavior using formal semantics, mathematical models, symbolic reasoning, logical inference, and experimental evidence.

The engine must not depend on pretrained AI models, neural networks, large language models, or similarity-based inference.

Its conclusions must be derived from explicit mechanisms and inspectable reasoning processes.

## 2. Core Principles

1. Causal mechanisms must be explicit.
2. Every causal conclusion must have traceable justification.
3. Program dependency must not automatically be interpreted as causation.
4. Correlation must not automatically be interpreted as causation.
5. Static deductions must be distinguished from experimentally observed behavior.
6. Interventions must respect the semantics of the program and its execution environment.
7. Counterfactual conclusions must identify their assumptions.
8. Incomplete information must produce explicit uncertainty.
9. Every reasoning operation must be reproducible.
10. All reasoning must execute locally.

## 3. High-Level Architecture

CRE consists of the following components:

1. Causal Variable Manager.
2. Causal Mechanism Builder.
3. Causal Graph Engine.
4. Structural Causal Model Engine.
5. Symbolic Reasoning Engine.
6. Intervention Engine.
7. Counterfactual Reasoning Engine.
8. Constraint and Mathematical Solver.
9. Evidence Evaluation Engine.
10. Causal Verification Engine.
11. Reasoning Trace and Explanation Engine.

The components must use common data contracts defined by Shared Core and UCR.

## 4. Causal Variable Manager

### Purpose

Identifies and manages variables that participate in program behavior.

### Responsibilities

- Identify program variables.
- Identify input and output values.
- Represent program states.
- Identify environmental variables.
- Identify execution conditions.
- Track variable transformations.
- Distinguish observed, derived, inferred, and unknown values.

### Required attributes

- Variable identifier.
- Variable type.
- Value domain.
- Source reference.
- State reference.
- Origin.
- Resolution status.
- Relevant assumptions.

Variables must preserve their relationship with the corresponding UCR entities.

## 5. Causal Mechanism Builder

### Purpose

Constructs explicit mechanisms explaining how one or more conditions produce an effect.

### Responsibilities

- Analyze program operations.
- Interpret assignment and transformation semantics.
- Analyze conditional execution.
- Analyze function behavior.
- Analyze data and control dependencies.
- Identify side effects.
- Construct mathematical descriptions of operations.
- Record preconditions and postconditions.

A mechanism must describe more than the existence of a relationship.

It must explain how the relationship operates.

### Example

If a program computes:

`result = input_value + 10`

The mechanism must represent the operation, input domain, transformation, output, and applicable type semantics.

It must not infer unrelated security properties without additional evidence.

## 6. Causal Graph Engine

### Purpose

Represents causal mechanisms and their relationships.

### Graph elements

- Causal variables.
- Causal mechanisms.
- Directed relationships.
- Conditions.
- Intermediate states.
- Evidence references.
- Assumption references.

### Responsibilities

- Construct causal graph candidates.
- Validate graph references.
- Identify dependency paths.
- Detect unresolved relationships.
- Identify cycles.
- Support conditional and state-dependent relationships.
- Preserve source provenance.

A dependency graph and a causal graph must remain distinct structures.

A data dependency may provide evidence for a causal relationship, but it is not sufficient by itself to establish one.

## 7. Structural Causal Model Engine

### Purpose

Represents causal mechanisms using explicit mathematical equations and structural relationships.

A candidate structural model may use:

`X_i = f_i(PA_i, U_i)`

Where:

- `X_i` represents a causal variable.
- `PA_i` represents its modeled parent variables.
- `U_i` represents external or unmodeled influences.
- `f_i` represents the structural mechanism.

### Responsibilities

- Construct structural equations.
- Define variable domains.
- Evaluate deterministic mechanisms.
- Represent conditional behavior.
- Track assumptions.
- Detect incomplete models.
- Validate mathematical consistency.

Structural equations must be derived from program semantics, documented specifications, or validated observations.

The engine must not invent equations to fill missing information.

## 8. Symbolic Reasoning Engine

### Purpose

Performs logical and symbolic analysis without relying on neural-network inference.

### Responsibilities

- Symbolic expression construction.
- Expression simplification.
- Logical deduction.
- Type-aware evaluation.
- Path-condition analysis.
- Constraint derivation.
- Equivalence checking.
- Mathematical consistency checking.

The engine must preserve programming-language semantics, including integer overflow, floating-point behavior, type conversions, and language-specific evaluation rules where relevant.

## 9. Intervention Engine

### Purpose

Evaluates the effects of deliberately changing selected variables or conditions.

### Responsibilities

- Define an intervention target.
- Validate intervention preconditions.
- Apply controlled mathematical changes.
- Recalculate affected mechanisms.
- Evaluate downstream consequences.
- Compare the original and modified states.
- Record the intervention and its results.

An intervention must be distinguished from ordinary observation.

The engine must not treat an arbitrary input substitution as a valid causal intervention without considering execution context and program semantics.

## 10. Counterfactual Reasoning Engine

### Purpose

Evaluates alternative outcomes under explicitly stated hypothetical conditions.

### Responsibilities

- Define the original scenario.
- Preserve the relevant background assumptions.
- Specify the hypothetical change.
- Recompute affected mechanisms.
- Compare predicted outcomes.
- Identify conditions under which the conclusion changes.
- Record unresolved assumptions.

Counterfactual conclusions must be limited to the validity of the underlying model.

The engine must distinguish proven outcomes, model-derived outcomes, and speculative outcomes.

## 11. Constraint and Mathematical Solver

### Purpose

Solves mathematical and logical conditions generated by the causal model.

### Candidate capabilities

- Constraint satisfaction.
- Symbolic equation solving.
- Boolean satisfiability.
- Path-condition solving.
- Integer and bit-vector reasoning.
- Type constraints.
- State consistency.
- Bounded mathematical optimization.

The solver must report:

- Satisfiable.
- Unsatisfiable.
- Unknown.
- Timeout.
- Unsupported.

An unknown result must never be silently treated as satisfiable or unsatisfiable.

## 12. Evidence Evaluation Engine

### Purpose

Evaluates the strength and origin of evidence supporting causal conclusions.

### Evidence categories

- Source-derived evidence.
- Semantic analysis evidence.
- Formal mathematical derivation.
- Static analysis evidence.
- Dynamically observed evidence.
- Experimentally validated evidence.
- Human-provided assumptions.

### Responsibilities

- Validate evidence provenance.
- Associate evidence with mechanisms.
- Identify conflicting evidence.
- Track missing evidence.
- Record assumptions.
- Distinguish predictions from observations.

Evidence must remain independently inspectable.

## 13. Causal Verification Engine

### Purpose

Determines whether a proposed causal explanation is supported by the available model and evidence.

### Verification checks

- Structural consistency.
- Mathematical consistency.
- Program semantic consistency.
- Dependency consistency.
- Intervention validity.
- Counterfactual validity.
- Evidence sufficiency.
- Assumption completeness.

### Result classifications

- `SUPPORTED`
- `PARTIALLY_SUPPORTED`
- `REFUTED`
- `INCONCLUSIVE`
- `UNVERIFIABLE`

These classifications describe the status of a causal claim, not an absolute guarantee about all possible program executions.

## 14. Reasoning Trace and Explanation Engine

Every reasoning operation must produce an inspectable trace.

A reasoning trace must include:

- Initial input entities.
- Derived variables.
- Applied mechanisms.
- Mathematical expressions.
- Constraints.
- Assumptions.
- Intermediate results.
- Evidence references.
- Final conclusion.
- Uncertainty information.

A reviewer must be able to trace a conclusion back to the original source code and relevant evidence.

## 15. Integration with Argus, Ababil, and Thoth

### Argus

Uses CRE to:

- Construct causal hypotheses.
- Analyze program behavior.
- Identify possible causes of security failures.
- Evaluate data and control dependencies.
- Produce evidence-linked findings.
- Generate test specifications.

### Ababil

Uses CRE to:

- Evaluate test hypotheses.
- Determine relevant interventions.
- Predict possible outcomes.
- Execute approved experiments.
- Compare observations with predicted outcomes.
- Return evidence to the shared reasoning system.

Execution must remain bounded by explicit authorization, sandbox isolation, and resource limits.

### Thoth

Uses CRE to:

- Independently inspect causal claims.
- Verify assumptions.
- Recalculate selected derivations.
- Compare predictions with observations.
- Identify unsupported reasoning.
- Audit evidence completeness.
- Report contradictions and uncertainty.

Thoth must not automatically accept another system's conclusion.

## 16. Local Execution Architecture

CRE must operate without mandatory cloud inference.

The implementation must support:

- CPU-based computation.
- Memory-bounded reasoning.
- Incremental evaluation.
- Lazy model construction.
- Configurable analysis depth.
- Computation time limits.
- Deterministic execution where applicable.

Initial target hardware:

- Windows 11.
- Python 3.13.
- Intel Core i5-8365U.
- Intel UHD Graphics 620.
- 8 GB RAM.

The system must benchmark computational complexity and memory consumption using actual workloads.

## 17. Open-Source Infrastructure

Open-source libraries may be used for:

- Symbolic mathematics.
- Constraint solving.
- Graph algorithms.
- Formal analysis.
- Parsing and semantic processing.
- Serialization and storage.

Libraries must not introduce prohibited pretrained AI models or replace Neptune Spear's custom reasoning foundation.

Dependency selection requires separate evaluation and approval.

## 18. Testing Requirements

CRE must be tested against:

1. Simple deterministic assignments.
2. Conditional execution.
3. Nested branches.
4. Loops and state transitions.
5. Function calls.
6. Data transformations.
7. Type conversions.
8. Exceptions.
9. Memory and alias relationships.
10. Unknown external influences.
11. Contradictory evidence.
12. Invalid causal assumptions.
13. Intervention scenarios.
14. Counterfactual scenarios.
15. Resource exhaustion and solver timeouts.

Tests must verify both correct reasoning and appropriate uncertainty reporting.

## 19. Acceptance Criteria

CRE is not considered complete until:

1. Causal variables are represented consistently.
2. Mechanisms are explicit and traceable.
3. Causal graphs are validated.
4. Structural equations preserve program semantics.
5. Symbolic reasoning produces reproducible results.
6. Interventions respect model assumptions.
7. Counterfactual reasoning is assumption-aware.
8. Evidence provenance is preserved.
9. Causal conclusions can be independently verified.
10. All three systems can use the shared engine.
11. Local resource requirements are measured.
12. Tests pass on the target environment.

## 20. Governance

This document defines the proposed Causal Reasoning Engine architecture.

It does not authorize unrestricted implementation.

Specific algorithms, mathematical methods, dependencies, and performance trade-offs must be evaluated in technical specifications and approved through NSDP.

The Project Director retains final authority over major architecture changes and implementation approval.
