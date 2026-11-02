# CAUSAL_DATA_MODEL.md
# Neptune Spear — Causal Data Model Specification

**Status:** Proposed — Technical Specification  
**Version:** 0.1  
**Parent:** CAUSAL_ENGINE_ARCHITECTURE.md  
**Foundation:** UCR_DATA_MODEL.md  
**Consumers:** Argus, Ababil, Thoth, Shared Core

---

## 1. Purpose

This document defines the common data structures used by Neptune Spear's Causal Reasoning Engine.

The Causal Data Model provides a formal representation for causal variables, mechanisms, graphs, structural equations, interventions, counterfactual queries, assumptions, evidence, and conclusions.

All three AI systems must use compatible causal data contracts.

## 2. Design Principles

1. Every causal entity must have a unique identifier.
2. Every entity must preserve its UCR references.
3. Causal relationships must have explicit justifications.
4. Dependency must not automatically imply causation.
5. Correlation must not automatically imply causation.
6. Observations must be distinguished from interventions.
7. Mathematical derivations must be reproducible.
8. Assumptions must be explicit.
9. Unknown information must remain unknown.
10. Evidence must be independently inspectable.
11. No pretrained neural-network model is required.
12. The data model must support local execution and bounded computation.

## 3. CausalModel

The root entity representing a causal model.

Required fields:

- `causal_model_id`
- `schema_version`
- `ucr_document_id`
- `model_name`
- `model_description`
- `causal_variables`
- `causal_mechanisms`
- `causal_edges`
- `structural_equations`
- `assumptions`
- `evidence_references`
- `model_validation_status`
- `model_version`

A causal model must explicitly identify its scope and limitations.

## 4. CausalVariable

Represents a variable participating in a causal model.

Required fields:

- `causal_variable_id`
- `name`
- `variable_kind`
- `data_type`
- `value_domain`
- `current_value`
- `ucr_entity_references`
- `source_references`
- `origin`
- `observation_status`
- `uncertainty_reference_ids`

Variable kinds:

- `PROGRAM_INPUT`
- `PROGRAM_OUTPUT`
- `PROGRAM_STATE`
- `ENVIRONMENT`
- `EXECUTION_CONDITION`
- `MEMORY_STATE`
- `CONTROL_CONDITION`
- `EXTERNAL_INFLUENCE`
- `UNKNOWN`

Observation statuses:

- `OBSERVED`
- `DERIVED`
- `INFERRED`
- `UNOBSERVED`
- `UNKNOWN`

A variable's numerical identifier must never be confused with its actual mathematical value.

## 5. CausalMechanism

Represents an explicit mechanism describing how variables influence an effect.

Required fields:

- `mechanism_id`
- `mechanism_name`
- `input_variable_ids`
- `output_variable_ids`
- `mechanism_kind`
- `mechanism_definition`
- `preconditions`
- `postconditions`
- `ucr_operation_references`
- `source_references`
- `assumption_ids`
- `evidence_ids`
- `validation_status`

Mechanism kinds:

- `ASSIGNMENT`
- `ARITHMETIC_TRANSFORMATION`
- `CONDITIONAL_EXECUTION`
- `FUNCTION_EXECUTION`
- `STATE_TRANSITION`
- `MEMORY_OPERATION`
- `INPUT_TRANSFORMATION`
- `OUTPUT_GENERATION`
- `EXTERNAL_INTERACTION`
- `UNKNOWN_MECHANISM`

A mechanism must explain the operation connecting its inputs and outputs.

## 6. CausalEdge

Represents a directed relationship between causal variables or mechanisms.

Required fields:

- `causal_edge_id`
- `source_id`
- `target_id`
- `edge_kind`
- `conditions`
- `mechanism_id`
- `derivation_method`
- `assumption_ids`
- `evidence_ids`
- `causal_status`

Causal statuses:

- `PROPOSED`
- `SEMANTICALLY_DERIVED`
- `MATHEMATICALLY_DERIVED`
- `EXPERIMENTALLY_SUPPORTED`
- `REFUTED`
- `INCONCLUSIVE`

A proposed edge must not be treated as an established causal relationship.

## 7. StructuralEquation

Represents a mathematical mechanism.

Required fields:

- `equation_id`
- `dependent_variable_id`
- `independent_variable_ids`
- `expression`
- `operator_semantics`
- `value_domain`
- `type_constraints`
- `assumption_ids`
- `derivation_method`
- `source_references`
- `validation_status`

A structural equation may use a form such as:

`Y = f(X1, X2, ..., Xn, U)`

Where:

- `Y` is the dependent variable.
- `X1 ... Xn` are modeled parent variables.
- `U` represents external or unmodeled influences.
- `f` is the explicitly defined mechanism.

The equation must preserve the semantics of the original programming language.

## 8. CausalAssumption

Represents an assumption required by a causal model or derivation.

Required fields:

- `assumption_id`
- `description`
- `assumption_kind`
- `affected_entity_ids`
- `origin`
- `validation_status`
- `supporting_evidence_ids`
- `limitations`

Assumption kinds:

- `LANGUAGE_SEMANTICS`
- `EXECUTION_ENVIRONMENT`
- `INPUT_DOMAIN`
- `MEMORY_MODEL`
- `EXTERNAL_SYSTEM`
- `MODEL_COMPLETENESS`
- `CAUSAL_IDENTIFICATION`
- `OTHER`

Assumptions must be visible in reasoning traces and reports.

## 9. CausalIntervention

Represents a controlled change to a causal variable.

Required fields:

- `intervention_id`
- `target_variable_id`
- `intervention_operator`
- `intervention_value`
- `original_value`
- `intervention_conditions`
- `affected_mechanism_ids`
- `model_id`
- `assumption_ids`
- `execution_status`
- `result_references`

Intervention operators may include:

- `SET_VALUE`
- `SET_CONDITION`
- `REPLACE_EXPRESSION`
- `REMOVE_EFFECT`
- `OTHER`

An intervention must distinguish mathematical simulation from actual program execution.

## 10. CounterfactualQuery

Represents a hypothetical alternative scenario.

Required fields:

- `counterfactual_id`
- `model_id`
- `original_scenario`
- `hypothetical_changes`
- `target_variable_ids`
- `background_assumption_ids`
- `evaluation_method`
- `result_status`
- `result_references`

The model must preserve the original scenario and explicitly describe the hypothetical changes.

Counterfactual results are only as valid as the underlying causal model and assumptions.

## 11. CausalEvidence

Represents evidence supporting or challenging a causal claim.

Required fields:

- `evidence_id`
- `evidence_kind`
- `source_reference`
- `related_entity_ids`
- `observation`
- `evidence_origin`
- `collection_method`
- `validation_status`
- `limitations`

Evidence kinds:

- `SOURCE_CODE`
- `STATIC_ANALYSIS`
- `SEMANTIC_DERIVATION`
- `MATHEMATICAL_DERIVATION`
- `DYNAMIC_OBSERVATION`
- `CONTROLLED_EXPERIMENT`
- `FORMAL_PROOF`
- `HUMAN_PROVIDED`

Evidence must not be treated as proof beyond what its collection method establishes.

## 12. CausalConclusion

Represents the result of a causal analysis.

Required fields:

- `conclusion_id`
- `model_id`
- `claim`
- `related_variable_ids`
- `related_mechanism_ids`
- `supporting_evidence_ids`
- `contradicting_evidence_ids`
- `assumption_ids`
- `reasoning_trace_id`
- `conclusion_status`
- `limitations`

Conclusion statuses:

- `SUPPORTED`
- `PARTIALLY_SUPPORTED`
- `REFUTED`
- `INCONCLUSIVE`
- `UNVERIFIABLE`

A conclusion must identify the evidence and assumptions that justify it.

## 13. CausalReasoningTrace

Records the reasoning process that produced a conclusion.

Required fields:

- `reasoning_trace_id`
- `input_entity_ids`
- `causal_model_id`
- `applied_mechanism_ids`
- `equation_ids`
- `constraint_ids`
- `intervention_ids`
- `counterfactual_ids`
- `assumption_ids`
- `intermediate_results`
- `final_result_reference`
- `execution_metadata`

The trace must support independent review and reproducibility.

## 14. CausalModel Validation

The model must be checked for:

- Referential integrity.
- Variable domain consistency.
- Equation type consistency.
- Mechanism input-output consistency.
- Graph integrity.
- Assumption completeness.
- Evidence provenance.
- Structural equation validity.
- Contradictory mechanisms.
- Unsupported causal edges.

A model with unresolved contradictions must not be silently marked valid.

## 15. Numerical Representation

Numerical representation must preserve:

- Variable identity.
- Variable type.
- Domain information.
- Equation structure.
- Operator semantics.
- Mechanism relationships.
- Constraint relationships.
- Source provenance.

Numerical encoding must not imply that numerical distance represents causal or semantic similarity.

The mapping between numerical representations and causal entities must remain traceable.

## 16. Serialization and Versioning

The initial implementation may use JSON-compatible serialization.

Requirements:

- Explicit schema version.
- Deterministic serialization.
- Referential integrity.
- Validation before loading.
- Stable entity identifiers within a model.
- Documented migration rules.
- Reproducible mathematical expressions.

Storage technology requires separate approval.

## 17. Integration

### Argus

Creates causal variables, mechanisms, model candidates, and hypotheses from UCR.

### Ababil

Consumes approved causal hypotheses, constructs interventions, executes authorized experiments, and returns evidence.

### Thoth

Independently validates causal models, assumptions, equations, evidence, and conclusions.

All systems must use the same approved causal data contract.

## 18. Testing Requirements

Tests must cover:

1. Variable creation and domain validation.
2. Mechanism input-output consistency.
3. Causal graph integrity.
4. Structural equation evaluation.
5. Assumption tracking.
6. Intervention validation.
7. Counterfactual scenario handling.
8. Evidence provenance.
9. Conclusion status classification.
10. Reasoning trace reproducibility.
11. Serialization and deserialization.
12. Contradictory and incomplete models.
13. Unknown and unsupported values.

## 19. Acceptance Criteria

Causal Data Model v0.1 is accepted when:

- All entities have defined schemas.
- References between entities are valid.
- Assumptions are explicit.
- Evidence provenance is preserved.
- Equations retain their semantic meaning.
- Interventions and counterfactuals are distinguishable.
- Conclusions are traceable.
- Uncertainty is preserved.
- All three systems can consume the same contract.
- Validation tests pass.

## 20. Governance

This document is a proposed technical specification.

Changes to causal entity definitions, equation semantics, intervention rules, evidence classifications, and conclusion statuses require architecture review.

Implementation must follow NSDP and approved task assignments.

The Project Director retains final approval authority.
