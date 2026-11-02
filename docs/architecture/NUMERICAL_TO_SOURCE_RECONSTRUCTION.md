# NUMERICAL_TO_SOURCE_RECONSTRUCTION.md

## 1. Purpose

This document defines the architecture and requirements for reconstructing source code from the numerical and formal representations produced by Neptune Spear's Causal Reasoning Engine (CRE).

The primary objective is to ensure that information processed and transformed by the reasoning engine can be translated back into valid source code using the original programming language.

For example:

- Python source code must be reconstructed as Python.
- Java source code must be reconstructed as Java.
- Other supported programming languages must retain their original language identity.

This component is responsible for translating the final reasoning representation into source code, not merely generating unrelated code based on a textual description.

## 2. Position in the Architecture

The reconstruction component operates between the Causal Reasoning Engine, UCR, and the source-code output layer.

The intended pipeline is:

1. Original Source Code Acquisition
2. UCR Transformation
3. Numerical and Formal Representation
4. Causal Reasoning and Mathematical Processing
5. Final Reasoning Representation
6. Numerical-to-UCR Reconstruction
7. UCR-to-Source Reconstruction
8. Syntax and Semantic Validation
9. Source Code Output

The reconstruction process must preserve the relationship between the original source code, its UCR representation, and the final reasoning result.

## 3. Core Responsibilities

### 3.1 Numerical Representation Interpretation

The reconstruction component must interpret the final numerical and formal data produced by the Causal Reasoning Engine.

It must identify:

- Program structures.
- Variables and their identities.
- Data types.
- Operators and their semantics.
- Function definitions and calls.
- Control-flow structures.
- Expressions and statements.
- Relationships between program components.
- Changes introduced during reasoning.

Numerical identifiers must never be interpreted as meaningful program instructions without their associated formal definitions and metadata.

### 3.2 Numerical-to-UCR Reconstruction

The component must transform the final formal representation into a valid UCR structure.

The reconstructed UCR must preserve:

- Structural relationships.
- Symbol identities.
- Type information.
- Operator semantics.
- Control-flow relationships.
- Data dependencies.
- Source-language metadata.
- Source-location provenance where available.

The reconstructed UCR must also represent any intentional changes made during causal reasoning.

### 3.3 UCR-to-Source Translation

The component must translate reconstructed UCR structures into source code.

The translation process must:

- Identify the original programming language.
- Apply the correct language-specific syntax rules.
- Reconstruct expressions and statements.
- Reconstruct functions and program structures.
- Preserve variable and function identities.
- Generate valid language-specific syntax.
- Respect language-specific type and operator semantics.

The component must support language-specific translation adapters rather than assuming that every programming language shares identical syntax or semantics.

### 3.4 Original Language Preservation

The original programming language must be recorded before the source code enters the UCR transformation process.

The reconstruction component must use this information to select the correct output language.

For example:

| Original input | Required output |
|---|---|
| Python | Python |
| Java | Java |
| C++ | C++ |
| JavaScript | JavaScript |

Automatic conversion into another programming language is outside the default reconstruction process.

### 3.5 Source Information Preservation

The system must preserve source provenance throughout the entire processing pipeline.

Where available, this includes:

- Original variable names.
- Function names.
- Class names.
- Comments.
- Source locations.
- Formatting information.
- Original syntax metadata.
- Relationships between original and reconstructed instructions.

If some information cannot be recovered, the system must distinguish between reconstructed information and unavailable information.

It must not fabricate original comments, formatting, or identifiers.

## 4. Reconstruction Modes

The system must distinguish between three reconstruction modes.

### 4.1 Exact Reconstruction

Used when no meaningful program changes have been introduced.

The objective is to reconstruct code with equivalent program structure and behavior.

Exact textual reproduction is only guaranteed when sufficient original source information has been preserved.

### 4.2 Semantics-Preserving Reconstruction

Used when internal transformations have occurred but the intended program behavior must remain equivalent.

The reconstructed source code may have different formatting or syntax organization while preserving the required semantics.

### 4.3 Reasoning-Modified Reconstruction

Used when the Causal Reasoning Engine intentionally modifies program logic or structure.

The output must reflect the modifications represented in the final UCR.

The component must retain traceability between each modification and its originating reasoning result.

## 5. Source Language Adapters

Each supported programming language must have a dedicated reconstruction adapter.

A language adapter is responsible for:

- Language-specific syntax generation.
- Expression reconstruction.
- Statement reconstruction.
- Type compatibility checks.
- Operator mapping.
- Function and class reconstruction.
- Language-specific validation.

The architecture must not assume that a single generic syntax generator can correctly reconstruct every programming language.

## 6. Semantic Preservation and Correctness

The reconstructed source code must be evaluated against the final formal representation.

The system must distinguish:

1. Syntactic correctness: whether the generated code follows the target language grammar.
2. Structural correctness: whether the expected program structures are reconstructed.
3. Type correctness: whether type constraints are respected.
4. Semantic correctness: whether the generated code preserves the intended program behavior.
5. Transformation correctness: whether intentional reasoning changes are correctly reflected.

Semantic equivalence must be established only within explicitly defined assumptions, supported language semantics, and verification capabilities.

The system must never claim universal equivalence based solely on successful parsing.

## 7. Provenance and Traceability

Every reconstructed instruction should retain a traceable relationship to its corresponding UCR element and, where available, its original source location.

The system must support tracing:

- Original source instruction.
- Original UCR element.
- Final reasoning representation.
- Reconstructed UCR element.
- Generated source instruction.

This enables Argus and Thoth to inspect how a conclusion or transformation affected the final code.

## 8. Validation and Verification

Before reconstructed source code is accepted, it must pass the applicable validation stages.

Required validation includes:

- Output language identification.
- Syntax parsing.
- Structural consistency checks.
- Type validation where supported.
- UCR-to-source mapping validation.
- Semantic verification where feasible.
- Comparison against expected transformation results.

Generated code must not automatically be considered correct merely because it can be parsed.

Failed validation must produce an explicit error report and preserve the associated reasoning trace.

## 9. Error Handling

The component must handle:

- Missing source-language metadata.
- Incomplete UCR structures.
- Invalid numerical or formal representations.
- Missing symbol information.
- Unsupported syntax structures.
- Type inconsistencies.
- Unrecoverable source information.
- Failed semantic validation.

The system must not silently produce misleading or incomplete code.

When reconstruction cannot be completed reliably, it must report the limitation and identify the affected elements.

## 10. Integration with Neptune Spear

### Argus

Argus may use reconstruction to produce modified or normalized source code based on verified analysis results.

### Ababil

Ababil may use reconstructed code as an input for authorized testing, subject to explicit scope and sandbox restrictions.

### Thoth

Thoth must be able to audit the relationship between reasoning evidence, UCR transformations, and generated source code.

### Shared Core

Shared Core must provide the data contracts, provenance metadata, serialization, and error-reporting mechanisms required by reconstruction.

### Causal Reasoning Engine

The Causal Reasoning Engine provides the final formal representation and transformation information required by the reconstruction component.

## 11. Security and Execution Restrictions

Reconstruction must be separated from execution.

Generating source code must not automatically execute it.

Execution, when required, must follow the authorization, sandbox, and resource restrictions defined by Ababil's architecture.

Generated code must be treated as untrusted until it has passed the required validation and approval procedures.

## 12. Resource Constraints

The reconstruction component must be designed for local execution on the Neptune Spear target environment.

It must consider:

- Limited RAM.
- CPU availability.
- Large source files.
- Complex program structures.
- Reconstruction time.
- Incremental processing where feasible.

The component must not require cloud-based code generation or external AI inference.

## 13. Testing Requirements

Testing must cover:

- Exact reconstruction of supported source structures.
- Original programming language preservation.
- Variable and function identity preservation.
- Operator and expression reconstruction.
- Control-flow reconstruction.
- Reconstruction after mathematical transformations.
- Reconstruction after intentional reasoning modifications.
- Invalid representation handling.
- Semantic preservation checks.
- Provenance and traceability.

Testing must include both small isolated examples and larger multi-function programs.

## 14. Definition of Done

This component may be considered implemented only when:

1. It can interpret the final formal representation.
2. It can reconstruct a valid UCR structure.
3. It can identify and preserve the original programming language.
4. It can translate reconstructed UCR into source code.
5. It can preserve required symbol and structural information.
6. It can distinguish unchanged reconstruction from reasoning-modified reconstruction.
7. It can validate generated source code.
8. It can provide traceability to the original source and reasoning results.
9. Its behavior is supported by reproducible tests.
10. Its limitations are explicitly documented.

## 15. Governance

This document defines the architectural requirements for Numerical-to-Source Reconstruction.

Implementation details, language support expansion, and changes to reconstruction semantics must follow the Neptune Spear Development Protocol (NSDP).

Major architectural changes require approval from the Project Director.

Successful code generation alone does not constitute successful reconstruction. Correctness must be demonstrated through validation and testing.
