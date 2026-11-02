# REASONING_EXECUTION_PIPELINE.md
# Neptune Spear — Reasoning Execution Pipeline

**Status:** Proposed — Technical Specification  
**Version:** 0.1  
**Parent:** AI_ARCHITECTURE.md  
**Dependencies:** UCR_ARCHITECTURE.md, UCR_DATA_MODEL.md, CAUSAL_ENGINE_ARCHITECTURE.md, CAUSAL_DATA_MODEL.md  
**Consumers:** Argus, Ababil, Thoth

## 1. Purpose

The Reasoning Execution Pipeline (REP) defines the execution sequence through which Neptune Spear transforms source-code input into mathematically justified, evidence-supported conclusions.

REP coordinates the shared UCR, Causal Reasoning Engine, mathematical solvers, evidence system, and output reconstruction components.

It must provide deterministic and reproducible execution wherever the underlying operations permit it.

REP must not depend on pretrained neural networks, LLMs, or similarity-based inference.

## 2. Execution Principles

1. Every stage must have explicit inputs and outputs.
2. Every transformation must preserve source provenance.
3. Every reasoning operation must be traceable.
4. Mathematical derivations must preserve programming-language semantics.
5. Dependency relationships must not automatically become causal claims.
6. Causal conclusions must identify assumptions and evidence.
7. Unknown information must not be silently replaced with guesses.
8. Expensive operations must have configurable resource limits.
9. Failed stages must produce explicit error states.
10. All three AI systems must use compatible pipeline contracts.

## 3. Pipeline Overview

The pipeline consists of ten primary stages:

1. Input Acquisition.
2. UCR Transformation.
3. Semantic Interpretation.
4. Causal Variable Extraction.
5. Causal Mechanism Construction.
6. Mathematical and Symbolic Reasoning.
7. Intervention and Counterfactual Evaluation.
8. Evidence Verification.
9. Conclusion Generation.
10. Output Reconstruction.

The pipeline may support conditional execution, incremental processing, and controlled re-evaluation.

Not every task requires every stage. Skipped stages must be recorded with a reason.

## 4. Stage 1 — Input Acquisition

### Purpose

Acquire source code and its relevant execution context.

### Inputs

- Source files.
- Project configuration.
- Language and version information.
- Dependency metadata.
- Optional execution environment description.
- Explicit analysis scope.

### Processing

- Validate input availability.
- Identify source languages.
- Calculate source content hashes.
- Identify relevant project boundaries.
- Record configuration.
- Establish analysis resource limits.

### Outputs

- InputManifest.
- SourceReference collection.
- EnvironmentDescriptor.
- AnalysisConfiguration.

Invalid or unavailable input must produce an explicit error.

## 5. Stage 2 — UCR Transformation

### Purpose

Convert source code into the common UCR representation.

### Processing

- Invoke the appropriate language adapter.
- Parse syntax.
- Construct syntax entities.
- Resolve symbols where possible.
- Extract type information.
- Construct program relations.
- Represent program states where supported.
- Generate traceable mathematical structures.

### Outputs

- UCRDocument.
- TransformationRecord collection.
- Parsing diagnostics.
- UncertaintyRecord collection.

Unsupported syntax must remain visible as unsupported or unresolved information.

## 6. Stage 3 — Semantic Interpretation

### Purpose

Establish the meaning and operational semantics of the represented program constructs.

### Processing

- Evaluate operator semantics.
- Validate type compatibility.
- Resolve function behavior where possible.
- Analyze control-flow conditions.
- Interpret data dependencies.
- Identify side effects.
- Record external dependencies.
- Identify unknown runtime behavior.

### Outputs

- SemanticModel.
- OperationSemantics.
- TypeConstraints.
- ProgramBehaviorDescription.
- SemanticUncertainty collection.

The engine must preserve language-specific details such as integer overflow, floating-point behavior, evaluation order, and exception semantics where relevant.

## 7. Stage 4 — Causal Variable Extraction

### Purpose

Identify candidate variables and conditions relevant to a causal analysis.

### Processing

- Identify program inputs.
- Identify program outputs.
- Identify intermediate values.
- Identify execution conditions.
- Identify relevant program states.
- Identify environmental influences.
- Establish variable domains.
- Map variables to UCR entities.

### Outputs

- CausalVariable collection.
- VariableDomain collection.
- VariableProvenance records.

A variable being identified does not establish a causal relationship.

## 8. Stage 5 — Causal Mechanism Construction

### Purpose

Construct explicit candidate mechanisms explaining program behavior.

### Processing

- Analyze relevant operations.
- Construct input-output relationships.
- Translate operations into symbolic expressions.
- Establish preconditions and postconditions.
- Represent conditional execution.
- Represent state transitions.
- Identify external influences.
- Record mechanism assumptions.

### Outputs

- CausalMechanism collection.
- StructuralEquation collection.
- CausalGraph candidate.
- Assumption collection.

Mechanisms must be derived from program semantics, documented specifications, or validated observations.

The engine must distinguish direct semantic derivation from experimentally supported mechanisms.

## 9. Stage 6 — Mathematical and Symbolic Reasoning

### Purpose

Evaluate candidate mechanisms using mathematical and logical operations.

### Processing

- Construct symbolic expressions.
- Apply valid expression transformations.
- Evaluate constraints.
- Analyze path conditions.
- Check type and domain compatibility.
- Evaluate state transitions.
- Solve supported mathematical conditions.
- Record contradictions and unresolved expressions.

### Outputs

- MathematicalDerivation collection.
- ConstraintResult collection.
- SymbolicEvaluation records.
- ReasoningTrace segments.

### Solver outcomes

- SATISFIABLE.
- UNSATISFIABLE.
- UNKNOWN.
- TIMEOUT.
- UNSUPPORTED.

An unknown or timed-out result must never be interpreted as proof.

## 10. Stage 7 — Intervention and Counterfactual Evaluation

### Purpose

Evaluate the consequences of controlled changes to a causal model.

### Processing

- Define the original scenario.
- Select intervention targets.
- Validate intervention preconditions.
- Apply the intervention to the model.
- Recalculate affected mechanisms.
- Evaluate downstream state changes.
- Construct counterfactual scenarios.
- Compare original and alternative results.

### Outputs

- InterventionResult collection.
- CounterfactualResult collection.
- AffectedVariable collection.
- ModelAssumption records.

Mathematical intervention must be distinguished from actual program execution.

Any actual execution experiment must be delegated to Ababil and must comply with its authorization and sandbox requirements.

## 11. Stage 8 — Evidence Verification

### Purpose

Evaluate whether the proposed explanation is supported by available evidence.

### Processing

- Verify source provenance.
- Check semantic derivations.
- Re-evaluate mathematical expressions.
- Validate constraints.
- Inspect experimental observations.
- Compare predictions with observed outcomes.
- Identify contradictory evidence.
- Identify missing evidence.
- Check assumption completeness.

### Outputs

- EvidenceAssessment.
- VerificationResult.
- ContradictionReport.
- EvidenceGapReport.

The system must not claim experimental validation when only static analysis has been performed.

## 12. Stage 9 — Conclusion Generation

### Purpose

Generate conclusions based on verified reasoning and available evidence.

### Processing

- Aggregate verified results.
- Evaluate supporting evidence.
- Evaluate contradicting evidence.
- Identify assumptions.
- Classify uncertainty.
- Determine conclusion status.
- Prepare an inspectable reasoning summary.

### Conclusion statuses

- SUPPORTED.
- PARTIALLY_SUPPORTED.
- REFUTED.
- INCONCLUSIVE.
- UNVERIFIABLE.

A conclusion must include its scope and limitations.

## 13. Stage 10 — Output Reconstruction

### Purpose

Transform internal results into outputs appropriate for each Neptune Spear system.

### Argus outputs

- Security findings.
- Causal hypotheses.
- Evidence-backed explanations.
- Test specifications.

### Ababil outputs

- Approved experiment specifications.
- Execution observations.
- Raw evidence.
- Experiment reports.

### Thoth outputs

- Independent audit findings.
- Verification results.
- Contradiction reports.
- False-positive and potential false-negative assessments.

### Shared output requirements

- Structured data.
- Source references.
- Reasoning trace references.
- Assumptions.
- Uncertainty.
- Execution metadata.

## 14. Pipeline Orchestration

The pipeline orchestrator must manage:

- Stage dependencies.
- Execution order.
- Conditional stages.
- Task identifiers.
- Resource allocation.
- Timeouts.
- Cancellation.
- Error handling.
- Retry policies.
- Incremental re-analysis.

Each stage must expose a documented interface.

A failed stage must not be treated as a successful empty result.

Retries must not silently change analysis assumptions or input scope.

## 15. Execution Modes

### Static Analysis Mode

Uses source code, UCR, semantics, symbolic reasoning, and static evidence.

### Mathematical Analysis Mode

Performs deeper symbolic evaluation, constraint solving, and supported causal model analysis.

### Experimental Validation Mode

Requests controlled experiments through Ababil.

### Independent Audit Mode

Allows Thoth to independently inspect models, assumptions, evidence, and conclusions.

Execution modes must remain subject to system-specific permissions.

## 16. Resource Management

The initial target environment is:

- Windows 11.
- Python 3.13.
- Intel Core i5-8365U.
- Intel UHD Graphics 620.
- 8 GB RAM.

The orchestrator must support:

- Memory limits.
- CPU time limits.
- Solver timeouts.
- Maximum graph sizes.
- Maximum analysis depth.
- Incremental computation.
- Cancellation.
- Resource usage reporting.

Resource exhaustion must produce an explicit incomplete or timed-out status.

## 17. Reproducibility

Every pipeline execution must record:

- Pipeline version.
- UCR schema version.
- Causal schema version.
- Language adapter versions.
- Algorithm versions.
- Input hashes.
- Configuration.
- Assumptions.
- Solver configuration.
- Execution environment.
- Stage results.

Deterministic operations must produce reproducible results for equivalent inputs and configurations.

Operations involving nondeterministic runtime behavior must record the relevant environmental conditions.

## 18. Testing Requirements

Tests must cover:

1. Successful end-to-end execution.
2. Invalid input.
3. Unsupported language constructs.
4. Semantic uncertainty.
5. Missing causal variables.
6. Incomplete mechanisms.
7. Invalid structural equations.
8. Solver timeout.
9. Contradictory evidence.
10. Failed intervention.
11. Counterfactual evaluation.
12. Pipeline cancellation.
13. Resource exhaustion.
14. Incremental re-analysis.
15. Reproducibility.
16. Output traceability.

## 19. Acceptance Criteria

REP is not considered complete until:

- All stages have defined contracts.
- Stage dependencies are validated.
- Source provenance is preserved end to end.
- Reasoning traces are inspectable.
- Uncertainty is handled explicitly.
- Solver failures are handled correctly.
- Experimental validation is distinguished from static derivation.
- Resource limits are enforced.
- All three systems can use the shared pipeline.
- End-to-end tests pass on the target environment.

## 20. Governance

This document defines the proposed execution architecture.

It does not authorize unrestricted implementation.

Specific algorithms, stage contracts, dependencies, and execution policies require technical review and approval through NSDP.

The Project Director retains final authority over major architecture decisions and releases.
