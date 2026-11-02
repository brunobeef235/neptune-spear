# CAUSAL_REASONING_ALGORITHMS.md
# Neptune Spear — Causal Reasoning Algorithms Specification

**Status:** Proposed — Technical Specification  
**Version:** 0.1  
**Parent:** CAUSAL_ENGINE_ARCHITECTURE.md  
**Dependencies:** UCR_ARCHITECTURE.md, UCR_DATA_MODEL.md, CAUSAL_DATA_MODEL.md, REASONING_EXECUTION_PIPELINE.md

---

## 1. Purpose

This document defines the candidate mathematical and logical algorithms that power Neptune Spear's custom Causal Reasoning Engine.

The algorithms must support program analysis, mathematical deduction, causal model construction, intervention analysis, counterfactual reasoning, and formal verification.

Neptune Spear must not depend on pretrained neural networks, LLMs, or similarity-based inference.

Each algorithm must have explicit inputs, outputs, assumptions, limitations, validation procedures, and resource constraints.

## 2. Algorithm Design Principles

1. Algorithms must have mathematically defined behavior.
2. Algorithms must preserve programming-language semantics.
3. Every result must be traceable to its inputs and assumptions.
4. Unknown results must remain distinguishable from proven results.
5. Algorithms must support reproducibility.
6. Approximation must be explicitly documented.
7. Resource limits must be enforced.
8. No algorithm may claim stronger conclusions than its formal guarantees permit.
9. Open-source infrastructure libraries may be used after review.
10. The shared algorithm foundation must be usable by Argus, Ababil, and Thoth.

## 3. Symbolic Execution

### Purpose

Symbolically execute program operations to explore possible execution paths.

### Core concepts

- Symbolic variables.
- Symbolic expressions.
- Path conditions.
- Branch conditions.
- Symbolic state.
- Execution transitions.

### Input

- UCR program representation.
- Initial symbolic state.
- Function and operation semantics.
- Execution scope.
- Resource limits.

### Processing

1. Initialize symbolic variables.
2. Process program operations.
3. Update symbolic state.
4. Generate branch conditions.
5. Accumulate path constraints.
6. Check path feasibility.
7. Record reachable and unresolved paths.

### Output

- Symbolic execution traces.
- Path conditions.
- Candidate execution paths.
- Feasibility results.
- Unresolved path records.

### Limitations

Symbolic execution may suffer from path explosion, unsupported operations, external dependencies, and complex memory behavior.

The implementation must support path bounds, timeouts, and explicit incomplete-analysis results.

## 4. Abstract Interpretation

### Purpose

Analyze program behavior using mathematically defined abstract domains.

### Core concepts

- Concrete domain.
- Abstract domain.
- Abstraction function.
- Concretization function.
- Transfer functions.
- Join and meet operations.
- Fixed-point computation.
- Widening and narrowing.

### Candidate abstract domains

- Constant propagation.
- Integer intervals.
- Boolean values.
- Nullability.
- Sign analysis.
- Type information.
- Taint information.
- Finite sets.

### Input

- UCR control flow.
- Transfer semantics.
- Abstract domain definitions.
- Initial abstract state.

### Processing

1. Initialize abstract states.
2. Apply transfer functions.
3. Propagate states through control-flow edges.
4. Join information at merge points.
5. Iterate until convergence or a defined limit.
6. Apply widening when necessary.
7. Optionally apply narrowing for improved precision.

### Output

- Abstract program states.
- Variable value ranges.
- Inferred properties.
- Unreachable conditions where provable.
- Precision and uncertainty information.

### Limitations

Abstract interpretation trades precision for computational tractability.

Results must state the selected abstract domain and its approximation properties.

## 5. Constraint Solving

### Purpose

Solve mathematical and logical constraints derived from program behavior.

### Supported problem classes

- Boolean satisfiability.
- Satisfiability modulo theories.
- Integer constraints.
- Bit-vector constraints.
- Array and memory constraints where supported.
- Logical path conditions.
- Type constraints.

### Input

- Symbolic expressions.
- Path conditions.
- Variable domains.
- Type semantics.
- Solver configuration.

### Processing

1. Validate expression types.
2. Normalize supported expressions.
3. Construct a constraint system.
4. Invoke the appropriate solving algorithm.
5. Interpret the solver result.
6. Record models or contradictions.
7. Record timeout and unsupported conditions.

### Output

- SAT.
- UNSAT.
- UNKNOWN.
- TIMEOUT.
- UNSUPPORTED.
- Satisfying assignments when available.

A satisfying assignment demonstrates a solution to the encoded constraints, not necessarily a feasible real-world execution unless the encoding faithfully represents the program and environment.

## 6. Structural Causal Models

### Purpose

Represent explicit mechanisms connecting variables through structural equations.

### Mathematical form

`X_i = f_i(PA_i, U_i)`

Where:

- `X_i` is a modeled variable.
- `PA_i` represents modeled parent variables.
- `U_i` represents external or unmodeled influences.
- `f_i` is an explicit structural mechanism.

### Input

- Causal variables.
- Mechanism definitions.
- Program semantics.
- Assumptions.
- Evidence.
- Variable domains.

### Processing

1. Identify candidate causal variables.
2. Identify mechanism candidates.
3. Define structural equations.
4. Document external influences.
5. Validate variable domains.
6. Validate model consistency.
7. Identify missing assumptions.
8. Evaluate model limitations.

### Output

- Structural causal model.
- Structural equations.
- Causal graph.
- Model assumptions.
- Validation report.

### Limitations

A structurally consistent model is not automatically a correctly identified causal model.

Causal identification may require explicit assumptions, interventions, experimental evidence, or authoritative semantic specifications.

## 7. Intervention Analysis

### Purpose

Evaluate the consequences of changing a selected causal variable or mechanism.

### Mathematical concept

An intervention replaces the relevant structural assignment with a specified intervention.

For example, an intervention may be represented as:

`do(X = x)`

### Input

- Validated or explicitly provisional causal model.
- Intervention target.
- Intervention value.
- Preconditions.
- Evaluation scope.

### Processing

1. Validate the target variable.
2. Validate the intervention.
3. Replace the relevant structural assignment.
4. Recalculate affected variables.
5. Evaluate downstream mechanisms.
6. Compare the resulting state with the baseline.
7. Record assumptions and limitations.

### Output

- Intervention result.
- Changed variable states.
- Affected mechanisms.
- Comparison report.
- Validity classification.

Intervention simulation must be distinguished from actual program execution.

## 8. Counterfactual Reasoning

### Purpose

Evaluate alternative outcomes under a hypothetical change while preserving the specified background scenario.

### Conceptual procedure

1. Establish the original scenario.
2. Determine the modeled background conditions.
3. Evaluate the original model.
4. Apply the hypothetical intervention.
5. Recalculate the affected mechanisms.
6. Compare the alternative outcome with the original outcome.

### Input

- Causal model.
- Original scenario.
- Hypothetical change.
- Background assumptions.
- Target outcome.

### Output

- Counterfactual result.
- Original and alternative outcomes.
- Changed causal mechanisms.
- Assumption dependencies.
- Uncertainty report.

### Limitations

Counterfactual results depend on the validity and completeness of the causal model.

Unobserved external influences may prevent a unique counterfactual conclusion.

## 9. Formal Verification

### Purpose

Verify program properties against formal specifications.

### Candidate methods

- Hoare logic.
- Preconditions and postconditions.
- Invariants.
- Weakest preconditions.
- Model checking.
- Equivalence checking.
- Proof obligations.

### Input

- Program representation.
- Formal properties.
- Preconditions.
- Postconditions.
- Relevant execution semantics.

### Processing

1. Define the property.
2. Construct proof obligations.
3. Derive logical conditions.
4. Evaluate supported obligations.
5. Produce proofs, counterexamples, or unresolved results.
6. Record proof assumptions.

### Output

- PROVEN.
- DISPROVEN.
- UNKNOWN.
- INCOMPLETE.
- UNSUPPORTED.

A failed proof attempt does not automatically prove that a property is false.

## 10. Fixed-Point Computation

### Purpose

Compute stable abstract or logical states in iterative program analyses.

### Mathematical concepts

- Lattices.
- Monotone functions.
- Least fixed points.
- Greatest fixed points.
- Worklist algorithms.
- Widening and narrowing.

### Input

- Abstract state space.
- Transfer functions.
- Initial state.
- Convergence configuration.

### Processing

1. Initialize the state space.
2. Select pending nodes.
3. Apply transfer functions.
4. Merge updated information.
5. Detect convergence.
6. Apply widening if necessary.
7. Stop on convergence or configured resource limits.

### Output

- Fixed-point result.
- Iteration count.
- Convergence status.
- Precision metadata.

## 11. Algorithm Composition

The algorithms must operate through documented interfaces.

Candidate composition:

- Symbolic execution produces path constraints.
- Constraint solving evaluates path feasibility.
- Abstract interpretation summarizes possible behavior.
- Fixed-point computation propagates abstract states.
- Structural causal models represent mechanisms.
- Intervention analysis evaluates controlled changes.
- Counterfactual reasoning evaluates hypothetical outcomes.
- Formal verification evaluates specified properties.

The orchestrator must not assume that every algorithm can consume every other algorithm's output directly.

Explicit conversion and validation are required.

## 12. Result Classification

Every algorithm must distinguish:

- Proven result.
- Derived result.
- Observed result.
- Approximate result.
- Incomplete result.
- Unknown result.
- Unsupported result.
- Timed-out result.

The classification must be preserved through subsequent pipeline stages.

## 13. Resource Management

Initial target hardware:

- Windows 11.
- Python 3.13.
- Intel Core i5-8365U.
- Intel UHD Graphics 620.
- 8 GB RAM.

Each algorithm must support configurable:

- Execution time limits.
- Memory limits.
- Iteration limits.
- Graph size limits.
- Path exploration limits.
- Solver limits.
- Analysis depth.

Benchmarks must measure actual performance on the target hardware.

## 14. Dependency Evaluation

Potential infrastructure categories:

- Symbolic mathematics.
- SMT solving.
- Graph processing.
- Formal verification.
- Parsing and language semantics.

Each proposed dependency requires:

- Technical justification.
- Security review.
- License review.
- Maintenance assessment.
- Resource benchmark.
- Dependency approval.

The use of an infrastructure solver or parser does not mean using an externally trained AI model.

## 15. Testing Requirements

Each algorithm must have:

1. Unit tests.
2. Mathematical correctness tests.
3. Semantic consistency tests.
4. Edge-case tests.
5. Negative tests.
6. Timeout tests.
7. Resource usage tests.
8. Reproducibility tests.
9. Integration tests.
10. Independent verification tests.

Expected results must be documented for each test.

## 16. Acceptance Criteria

The algorithm foundation is not accepted until:

- Every selected algorithm has a formal specification.
- Input and output contracts are implemented.
- Assumptions are documented.
- Correctness tests pass.
- Failure and uncertainty states work.
- Resource limits are enforced.
- Results are traceable.
- Cross-algorithm integration is validated.
- Performance is measured on target hardware.

## 17. Governance

This document defines candidate algorithms, not an unconditional mandate to implement every technique.

Algorithms must be prioritized according to correctness, measurable benefit, complexity, and hardware feasibility.

The Project Director retains final authority over algorithm selection, dependencies, and major architecture changes.

Implementation must follow NSDP and approved task specifications.
