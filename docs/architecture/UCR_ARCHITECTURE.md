# UCR_ARCHITECTURE.md
# Neptune Spear — Universal Code Representation

**Status:** Proposed — Architecture Specification  
**Version:** 0.1  
**Parent Architecture:** AI_ARCHITECTURE.md  
**Applies to:** Argus, Ababil, Thoth, Shared Core

---

## 1. Purpose

Universal Code Representation (UCR) is the common representation system used by all three Neptune Spear AI systems.

Its purpose is to translate source code from different programming languages into a common, structured, mathematically processable representation while preserving the meaning and behavior of the original program.

UCR is not merely a tokenizer or character-to-number converter.

It must preserve the relationships between syntax, semantics, types, operations, control flow, data dependencies, and program states.

## 2. Core Design

UCR uses a layered architecture.

The five primary layers are:

1. Syntax Representation.
2. Semantic and Type Representation.
3. Program Relations Representation.
4. State and Behavior Representation.
5. Mathematical and Numerical Representation.

A graph-based representation is used where appropriate within these layers.

All layers must retain references to their source locations and related representations.

## 3. Layer 1 — Syntax Representation

### Responsibilities

- Parse source code.
- Construct abstract syntax trees.
- Preserve source locations.
- Identify declarations, expressions, statements, and language constructs.
- Preserve syntactic distinctions that may affect program meaning.
- Record parser errors and incomplete constructs.

### Required data

- Node identifier.
- Node type.
- Parent and child relationships.
- Source file identifier.
- Start and end positions.
- Original language.
- Original source reference.
- Parsing status.

The original source must remain recoverable.

## 4. Layer 2 — Semantic and Type Representation

### Responsibilities

- Resolve symbols where possible.
- Identify variable declarations and references.
- Represent data types.
- Represent operators and their semantics.
- Identify function signatures and scopes.
- Track type conversions.
- Record unresolved or ambiguous semantic information.

### Required data

- Symbol identifiers.
- Type identifiers.
- Scope relationships.
- Function signatures.
- Operator semantics.
- Type conversion rules.
- Resolution status.
- Semantic assumptions.

The system must distinguish between known types, inferred types, unknown types, and ambiguous types.

## 5. Layer 3 — Program Relations Representation

### Responsibilities

Construct and maintain relationships including:

- Control Flow Graph (CFG).
- Data Dependency Graph.
- Call Graph.
- Def-Use Relationships.
- Dependency Graph.
- Exception Flow.
- Interprocedural Relationships.

Each relationship must have an explicit type and source of derivation.

The architecture must support relationships across functions and modules when sufficient information is available.

## 6. Layer 4 — State and Behavior Representation

### Responsibilities

Represent program state and its possible transitions.

Required concepts include:

- Variable states.
- Memory state.
- Object state.
- Input and output state.
- Function execution state.
- Branch conditions.
- Loop conditions.
- Exception states.
- Side effects.
- State transitions.

The representation must distinguish between actual observed states and statically inferred possible states.

Unknown state must not be silently treated as a known value.

## 7. Layer 5 — Mathematical and Numerical Representation

### Responsibilities

Transform the preceding representations into mathematical structures suitable for causal reasoning.

Candidate structures include:

- Integer and symbolic identifiers.
- Typed relational structures.
- Adjacency and incidence representations.
- Constraint systems.
- Symbolic expressions.
- State-transition relations.
- Mathematical dependency structures.
- Causal graph candidates.

### Critical requirements

Numerical encoding must preserve semantic distinctions.

Different program constructs must not become indistinguishable merely because their numerical encodings are similar.

The system must retain reversible references between numerical structures and their original UCR elements.

Numerical representation must not be interpreted as proof of causality by itself.

Causal relationships require additional semantic justification and evidence.

## 8. Cross-Layer Integrity

Every transformation between layers must:

1. Preserve source references.
2. Preserve relevant semantic information.
3. Record assumptions.
4. Record unresolved information.
5. Support validation.
6. Produce reproducible results.
7. Expose transformation errors.

UCR must support tracing a mathematical result back to the original source-code construct.

## 9. Language Adapter Architecture

Each programming language must have its own adapter.

An adapter is responsible for translating language-specific syntax and semantics into UCR.

The architecture must support future language adapters without requiring changes to the shared causal engine.

Initial language support should be selected through a separate implementation priority decision.

Potential languages include Python, JavaScript, Java, C, and C++.

Unsupported constructs must be explicitly reported rather than silently discarded.

## 10. Common Data Model

The Shared Core must define stable schemas for:

- UCRDocument.
- SyntaxNode.
- SemanticSymbol.
- TypeDescriptor.
- ProgramOperation.
- Relation.
- ControlFlowNode.
- DataDependency.
- ProgramState.
- StateTransition.
- MathematicalExpression.
- Constraint.
- SourceReference.
- TransformationRecord.
- UncertaintyRecord.

All identifiers must be stable within a UCR document and have documented identity and lifecycle rules.

Schemas must be versioned.

## 11. Consistency and Validation

UCR must provide validation mechanisms for:

- Structural consistency.
- Parent-child integrity.
- Symbol resolution.
- Type consistency.
- Graph integrity.
- Data dependency integrity.
- State transition consistency.
- Numerical encoding integrity.
- Source traceability.

The system must identify unsupported or incomplete semantic interpretations.

## 12. Reconstruction

UCR must support reconstruction of relevant source-level structures from its internal representations.

However, exact source reconstruction and semantic reconstruction are different requirements.

Exact reconstruction requires preserving original formatting, comments, whitespace, and source tokens.

Semantic reconstruction requires preserving the meaning of the program, even if formatting differs.

Both capabilities must be tested independently.

## 13. Integration with Neptune Spear

### Argus

Consumes UCR to analyze program structure, dependencies, semantics, and possible causal paths.

### Ababil

Consumes UCR and approved test specifications to construct controlled experiments and interpret execution evidence.

### Thoth

Consumes UCR and evidence to independently inspect semantic consistency, reasoning assumptions, and conclusions.

All three systems must use compatible UCR schemas.

## 14. Performance and Resource Constraints

Initial hardware target:

- Windows 11.
- Python 3.13.
- Intel Core i5-8365U.
- Intel UHD Graphics 620.
- 8 GB RAM.

The implementation must support:

- Incremental parsing.
- Lazy construction of expensive representations.
- Memory-bounded graph processing.
- Configurable analysis depth.
- Efficient serialization.
- Reproducible processing.

Performance must be benchmarked on the actual target hardware.

## 15. Testing Requirements

UCR must be tested using:

- Small isolated code samples.
- Multiple programming languages.
- Nested control structures.
- Function calls.
- Type conversions.
- Exceptions.
- Memory and object operations.
- Ambiguous or unresolved constructs.
- Cross-module dependencies.

Tests must verify that transformations preserve the relevant syntax and semantics.

Numerical encoding tests must verify that distinct semantic structures remain distinguishable and traceable.

## 16. Acceptance Criteria

UCR is not considered complete until:

1. The layered architecture is implemented.
2. At least one language adapter works end to end.
3. Source-to-UCR mapping is traceable.
4. Semantic information is preserved.
5. Graph relationships pass integrity checks.
6. Numerical representations preserve relevant distinctions.
7. Reconstruction tests pass.
8. Unknown and unsupported constructs are handled explicitly.
9. Memory usage is measured.
10. All three systems can consume the approved UCR contract.

## 17. Governance

This document specifies the proposed UCR architecture.

It does not authorize unrestricted implementation or unapproved dependency selection.

Implementation must follow NSDP.

Major schema changes, semantic model changes, and numerical representation changes require architecture review and Project Director approval.
