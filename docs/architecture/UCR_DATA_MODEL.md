# UCR_DATA_MODEL.md
# Neptune Spear — UCR Data Model Specification

**Status:** Proposed — Technical Specification  
**Version:** 0.1  
**Parent:** UCR_ARCHITECTURE.md  
**Consumers:** Argus, Ababil, Thoth, Shared Core

## 1. Purpose

This document defines the initial internal data model for Universal Code Representation (UCR).

The data model establishes a common contract for representing source code, semantic information, program relationships, program states, mathematical expressions, constraints, and evidence.

All three Neptune Spear systems must consume compatible UCR structures.

## 2. Design Principles

1. Every entity has a unique identifier.
2. Every source-derived entity retains source provenance.
3. Every relationship has an explicit type.
4. Unknown information must remain explicitly unknown.
5. Inferred information must be distinguished from directly observed information.
6. Transformations must be traceable and reproducible.
7. Schema versions must be explicit.
8. Numerical identifiers must not be confused with semantic values.
9. A numerical representation alone does not establish causality.
10. No pretrained AI model or neural-network representation is required.

## 3. UCR Document

The root object is `UCRDocument`.

Required fields:

- `ucr_id`: unique document identifier.
- `schema_version`: UCR schema version.
- `source_files`: source file references.
- `language_metadata`: language and adapter information.
- `syntax_nodes`: syntax entities.
- `symbols`: semantic symbols.
- `types`: type descriptors.
- `operations`: program operations.
- `relations`: explicit relationships.
- `control_flow`: control flow structures.
- `data_dependencies`: data dependency structures.
- `program_states`: program state descriptions.
- `state_transitions`: state transition descriptions.
- `mathematical_expressions`: mathematical structures.
- `constraints`: logical and mathematical constraints.
- `uncertainties`: unresolved or incomplete information.
- `transformations`: transformation history.

Collections may be stored separately and referenced by identifier to support large programs and incremental processing.

## 4. Common Entity Fields

Every UCR entity should contain:

- `entity_id`
- `entity_type`
- `schema_version`
- `source_references`
- `origin`
- `resolution_status`
- `metadata`

Allowed origins:

- `SOURCE_DERIVED`
- `STATICALLY_INFERRED`
- `DYNAMICALLY_OBSERVED`
- `MATHEMATICALLY_DERIVED`
- `HUMAN_PROVIDED`

Resolution statuses:

- `RESOLVED`
- `PARTIALLY_RESOLVED`
- `UNRESOLVED`
- `UNKNOWN`
- `UNSUPPORTED`

## 5. SourceReference

Represents the origin of an entity in source code.

Fields:

- `source_id`
- `file_path`
- `start_line`
- `start_column`
- `end_line`
- `end_column`
- `source_language`
- `content_hash`

Source references must remain valid across serialization and analysis sessions, subject to source version verification.

## 6. SyntaxNode

Represents a syntax element.

Fields:

- `node_id`
- `node_kind`
- `parent_id`
- `child_ids`
- `operator`
- `literal_value`
- `identifier_name`
- `source_reference`
- `attributes`

The model must support language-specific syntax details without forcing unsupported constructs into inaccurate universal categories.

## 7. SemanticSymbol

Represents a declared or referenced program symbol.

Fields:

- `symbol_id`
- `symbol_name`
- `symbol_kind`
- `scope_id`
- `type_id`
- `declaration_node_id`
- `reference_node_ids`
- `resolution_status`

Symbol kinds include:

- `VARIABLE`
- `FUNCTION`
- `CLASS`
- `MODULE`
- `PARAMETER`
- `FIELD`
- `CONSTANT`
- `UNKNOWN`

## 8. TypeDescriptor

Represents a program type.

Fields:

- `type_id`
- `type_kind`
- `type_name`
- `generic_arguments`
- `element_type_id`
- `parent_type_ids`
- `type_properties`
- `resolution_status`

The model must support primitive, composite, generic, union, optional, dynamic, and unresolved types.

## 9. ProgramOperation

Represents a semantically meaningful operation.

Fields:

- `operation_id`
- `operation_kind`
- `input_entity_ids`
- `output_entity_ids`
- `operator_semantics`
- `side_effects`
- `source_reference`
- `execution_context`

Operation kinds may include:

- `ASSIGNMENT`
- `ARITHMETIC`
- `COMPARISON`
- `FUNCTION_CALL`
- `MEMORY_ACCESS`
- `OBJECT_CREATION`
- `TYPE_CONVERSION`
- `INPUT`
- `OUTPUT`
- `CONTROL_OPERATION`
- `UNKNOWN_OPERATION`

## 10. Relation

Represents an explicit relationship between entities.

Fields:

- `relation_id`
- `relation_kind`
- `source_entity_id`
- `target_entity_id`
- `conditions`
- `derivation_method`
- `origin`
- `evidence_ids`
- `resolution_status`

Examples of relation kinds:

- `PARENT_OF`
- `REFERENCES`
- `DEFINES`
- `USES`
- `DEPENDS_ON`
- `CALLS`
- `FLOWS_TO`
- `CONTROLS`
- `TRANSFORMS`
- `MAY_ALIAS`
- `MUST_ALIAS`

A relation must not be labeled causal merely because two entities are connected.

## 11. ControlFlowNode

Fields:

- `control_node_id`
- `syntax_node_id`
- `successor_ids`
- `predecessor_ids`
- `branch_condition`
- `exceptional_edges`
- `loop_metadata`

Control flow must distinguish normal execution, conditional branches, loop edges, and exceptional execution.

## 12. DataDependency

Fields:

- `dependency_id`
- `source_entity_id`
- `target_entity_id`
- `dependency_kind`
- `path_conditions`
- `derivation_method`
- `evidence_ids`
- `resolution_status`

Dependency kinds include:

- `DATA_FLOW`
- `DEF_USE`
- `CONTROL_DEPENDENCY`
- `MEMORY_DEPENDENCY`
- `INTERPROCEDURAL_DEPENDENCY`

## 13. ProgramState

Represents a program state or abstract state.

Fields:

- `state_id`
- `state_kind`
- `variable_bindings`
- `memory_bindings`
- `object_bindings`
- `environment`
- `path_conditions`
- `state_precision`
- `origin`

The system must distinguish concrete observed states from abstractly inferred states.

## 14. StateTransition

Fields:

- `transition_id`
- `source_state_id`
- `target_state_id`
- `trigger_operation_id`
- `transition_condition`
- `effects`
- `transition_kind`
- `evidence_ids`

A transition may be possible, observed, or proven under documented assumptions.

## 15. MathematicalExpression

Represents a symbolic or numerical mathematical expression.

Fields:

- `expression_id`
- `expression_kind`
- `operator`
- `operand_ids`
- `constant_value`
- `variable_references`
- `domain`
- `source_entity_ids`
- `derivation_method`

Expressions must preserve types, domains, units where applicable, and evaluation assumptions.

## 16. Constraint

Represents a logical or mathematical restriction.

Fields:

- `constraint_id`
- `constraint_kind`
- `expression_id`
- `operator`
- `right_hand_expression_id`
- `assumptions`
- `satisfiability_status`
- `evidence_ids`

Constraint status:

- `SATISFIABLE`
- `UNSATISFIABLE`
- `UNKNOWN`
- `NOT_EVALUATED`

## 17. UncertaintyRecord

Fields:

- `uncertainty_id`
- `subject_entity_id`
- `uncertainty_kind`
- `description`
- `missing_information`
- `impact`
- `recommended_resolution`

Uncertainty must be preserved through subsequent processing stages.

## 18. TransformationRecord

Fields:

- `transformation_id`
- `input_entity_ids`
- `output_entity_ids`
- `transformation_kind`
- `algorithm_identifier`
- `algorithm_version`
- `assumptions`
- `validation_result`
- `timestamp`

This enables auditing and reproducibility of transformations.

## 19. Numerical Representation Contract

Numerical representations must be typed and explicitly mapped to their semantic entities.

The implementation must not rely on arbitrary numeric codes that lose meaning.

Requirements:

- Stable mapping between numerical elements and UCR entities.
- Explicit distinction between identifiers and actual numeric values.
- Preservation of operator semantics.
- Preservation of type and domain information.
- Traceability to source code.
- Validation against the original representation.
- No assumption that numeric proximity means semantic similarity.

## 20. Causal Extension Compatibility

UCR v0.1 is a program representation model, not a complete causal model.

Future causal extensions may introduce:

- CausalVariable.
- CausalMechanism.
- CausalEdge.
- Intervention.
- CounterfactualQuery.
- CausalAssumption.
- CausalEvidence.
- CausalConclusion.

These structures must reference UCR entities and preserve the distinction between dependency, correlation, and causation.

## 21. Serialization and Versioning

The initial implementation may use JSON-compatible serialization.

Requirements:

- Explicit schema version.
- Deterministic serialization.
- Stable identifiers within a document.
- Referential integrity.
- Validation before loading.
- Clear migration rules between schema versions.

Storage format and database selection require separate approval.

## 22. Testing Requirements

Tests must cover:

1. Entity creation and identifier uniqueness.
2. Referential integrity.
3. Source traceability.
4. Type consistency.
5. Relationship validation.
6. State transition consistency.
7. Constraint representation.
8. Unknown and unresolved values.
9. Serialization and deserialization.
10. Numerical mapping integrity.
11. Schema version compatibility.
12. Incremental updates.

## 23. Acceptance Criteria

UCR Data Model v0.1 is accepted when:

- Every required entity has a defined schema.
- Cross-entity references are valid.
- Source provenance is retained.
- Unknown information is explicit.
- Serialization is deterministic.
- Numerical mappings are traceable.
- Validation tests pass.
- Argus, Ababil, and Thoth can consume the same data contract.

## 24. Governance

This document is a proposed technical specification.

Changes to entity identity, semantic meaning, relation types, numerical representation, and causal compatibility require architecture review.

Implementation must follow NSDP and the approved task assignment process.
