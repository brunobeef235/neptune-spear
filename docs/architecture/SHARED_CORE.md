# SHARED CORE ARCHITECTURE

**Project:** Neptune Spear  
**Component:** Shared Core  
**Document Type:** Shared Infrastructure Architecture Specification  
**Status:** Initial Architecture Baseline  
**Version:** 1.0

---

## 1. PURPOSE

Shared Core is the common infrastructure and interoperability foundation of Neptune Spear.

Its primary purpose is to provide shared data models, protocols, interfaces, configuration standards, logging, serialization, and common utilities used by Argus, Ababil, and Thoth.

Shared Core ensures that all three systems can exchange information consistently without creating incompatible implementations of common functionality.

Shared Core is not a replacement for the independent responsibilities of Argus, Ababil, or Thoth.

## 2. CORE RESPONSIBILITIES

Shared Core is responsible for:

1. Defining common data models.
2. Defining inter-system communication contracts.
3. Providing shared serialization and deserialization.
4. Defining evidence and finding schemas.
5. Providing configuration management.
6. Providing structured logging.
7. Managing common identifiers and metadata.
8. Defining schema and protocol versioning.
9. Providing common error and status representations.
10. Supporting compatibility between system components.

Shared Core must remain modular and must not become a centralized location for unrelated system-specific logic.

## 3. HIGH-LEVEL ARCHITECTURE

Shared Core consists of the following logical components.

### 3.1 Common Data Models

Defines reusable data structures shared across the three systems.

Initial model categories include:

- Project metadata.
- Source file metadata.
- Source location.
- Analysis instruction.
- Function and symbol references.
- Hypothesis.
- Finding.
- Test case.
- Execution record.
- Evidence.
- Audit record.
- System status.
- Error information.

Each model must have a documented purpose and clearly defined fields.

### 3.2 Inter-System Contracts

Defines how Argus, Ababil, and Thoth exchange information.

Initial communication flows:

- Argus → Ababil: security hypotheses and supporting evidence references.
- Ababil → Argus: experiment outcomes and evidence references.
- Argus → Thoth: static analysis findings and reasoning evidence.
- Ababil → Thoth: test definitions, execution records, and raw evidence references.
- Thoth → Argus: audit conclusions and analysis recommendations.
- Thoth → Ababil: experiment audit conclusions and testing recommendations.

Contracts must define required fields, optional fields, validation rules, and failure behavior.

### 3.3 Serialization Layer

Provides consistent data serialization and deserialization.

Initial supported format:

- JSON.

Additional formats may be introduced when justified.

Serialization must preserve:

- Data types.
- Identifiers.
- Timestamps.
- Version information.
- Source references.
- Evidence relationships.
- Explicit uncertainty and status information.

Invalid or incompatible data must be rejected safely.

### 3.4 Schema Registry

Maintains definitions of shared data schemas.

Responsibilities:

- Schema identification.
- Schema versioning.
- Validation rules.
- Compatibility checking.
- Deprecation records.
- Migration guidance.

Schema changes must be reviewed before being introduced into shared interfaces.

### 3.5 Evidence Model

Defines a common structure for evidence generated or referenced by Neptune Spear systems.

Evidence metadata should include:

- Evidence identifier.
- Evidence type.
- Originating system.
- Parent hypothesis or test identifier.
- Source location when applicable.
- Creation timestamp.
- Content hash when applicable.
- Storage reference.
- Collection metadata.
- Integrity and validation status.

Raw evidence must remain distinguishable from interpretations and conclusions.

Shared Core must not silently modify evidence supplied by another system.

### 3.6 Finding and Hypothesis Models

Defines consistent structures for security findings and hypotheses.

A finding should support:

- Unique identifier.
- Security category.
- Severity.
- Affected component.
- Source location.
- Supporting evidence references.
- Reasoning summary.
- Confidence information.
- Limitations.
- Lifecycle status.

A hypothesis should support:

- Unique identifier.
- Parent finding when applicable.
- Target component.
- Preconditions.
- Input constraints.
- Expected behavior.
- Suggested experiment.
- Supporting evidence.
- Confidence and uncertainty.

Severity, confidence, and validation status must be separate concepts.

### 3.7 Configuration Management

Provides shared configuration conventions.

Responsibilities:

- Configuration loading.
- Configuration validation.
- Default values.
- Environment-specific settings.
- Resource limit definitions.
- Path handling.
- Configuration versioning.

Security-sensitive settings must not silently fall back to permissive defaults.

Secrets must not be stored in source-controlled configuration files.

### 3.8 Logging and Diagnostics

Defines common structured logging conventions.

Log records should support:

- Timestamp.
- System name.
- Component name.
- Severity level.
- Event identifier.
- Correlation identifier.
- Message.
- Relevant metadata.

Logs must avoid exposing secrets, credentials, or unnecessary sensitive data.

### 3.9 Error and Status Model

Defines common error and execution status representations.

Initial status categories may include:

- `PENDING`
- `RUNNING`
- `COMPLETED`
- `FAILED`
- `REJECTED`
- `BLOCKED`
- `CANCELLED`
- `TIMEOUT`

Error records should identify the affected component, error category, context, and whether retry is appropriate.

A failure in one system must not be silently represented as successful completion in another.

### 3.10 Identifier and Correlation Management

Provides consistent identifiers for objects and workflows.

Identifiers should support traceability across systems.

A single investigation may involve:

- Analysis identifier.
- Finding identifier.
- Hypothesis identifier.
- Test case identifier.
- Execution identifier.
- Evidence identifier.
- Audit identifier.

Correlation identifiers should connect related operations without conflating their individual identities.

## 4. DATA FLOW AND CONTRACT GOVERNANCE

Shared Core defines the contracts, while individual systems remain responsible for their own operations.

The intended workflow is:

1. Argus produces a hypothesis.
2. Shared Core validates the data contract.
3. Ababil receives the hypothesis.
4. Ababil returns execution records and evidence references.
5. Shared Core validates the returned structures.
6. Thoth receives the relevant findings and evidence.
7. Thoth returns audit records and recommendations.
8. Relevant systems consume the validated results.

Shared Core must not independently authorize security testing or execute target code.

## 5. VERSIONING AND COMPATIBILITY

All shared contracts must have explicit versions.

Versioning rules should distinguish:

- Backward-compatible additions.
- Breaking field changes.
- Deprecated fields.
- Removed fields.
- Schema migrations.

Breaking changes require a documented proposal and approval.

Systems must not silently interpret incompatible schema versions.

## 6. SECURITY PRINCIPLES

Shared Core must follow these principles:

1. Validate data at system boundaries.
2. Reject malformed or incompatible inputs.
3. Preserve evidence provenance.
4. Protect sensitive configuration.
5. Avoid logging secrets.
6. Use least-privilege filesystem access.
7. Prevent unsafe deserialization.
8. Maintain traceable identifiers.
9. Avoid implicit authorization.
10. Fail safely when contracts cannot be validated.

Shared Core is not itself a security sandbox or authorization authority.

## 7. RESOURCE CONSTRAINTS

The initial target environment is:

- Operating System: Windows 11.
- Python: 3.13.
- Memory: 8 GB RAM.
- CPU: Intel Core i5-8365U.
- GPU: Intel UHD Graphics 620.

Shared Core must remain lightweight.

It should avoid unnecessary heavyweight dependencies and support efficient processing of structured data.

## 8. DEPENDENCY GOVERNANCE

Shared Core should minimize dependencies.

Every external dependency must have:

- A documented purpose.
- A compatibility assessment.
- A license review.
- A maintenance assessment.
- A security review appropriate to its role.

No dependency should be introduced solely for convenience when a smaller and maintainable implementation is sufficient.

## 9. CURRENT IMPLEMENTATION BASELINE

Shared Core is currently an architectural design target.

The existence of this document does not imply that all shared schemas, registries, protocols, or utilities have already been implemented.

Each capability must be implemented, tested, and integrated before being considered operational.

## 10. KNOWN LIMITATIONS AND FUTURE WORK

Planned capabilities include:

- Formal schema definitions.
- Common Python package structure.
- Schema validation.
- Contract test suite.
- Evidence reference management.
- Structured logging.
- Configuration validation.
- Version compatibility checks.
- Common error handling.
- Inter-system integration tests.

The initial implementation should prioritize stable contracts over unnecessary abstraction.

## 11. DEFINITION OF DONE

A Shared Core capability is considered complete only when:

1. Its technical specification is approved.
2. Its schema or interface is documented.
3. Its implementation is integrated.
4. Relevant automated tests exist.
5. Tests have actually been executed.
6. Compatibility behavior is validated.
7. Security implications are reviewed.
8. Known limitations are documented.
9. Argus, Ababil, and Thoth can use the contract correctly.
10. The Project Director approves completion.

Implementation alone does not mean a capability is complete.

## 12. ARCHITECTURE GOVERNANCE

This document defines the initial architectural baseline for Shared Core.

Changes to common data models, protocol contracts, versioning, evidence formats, configuration standards, and shared dependencies require a documented proposal and approval from the Project Director.

Shared Core changes must be coordinated with all affected systems.

All implementation tasks must follow the approved architecture and NSDP workflow.

---

**End of Shared Core Architecture Specification**
