\# ARGUS ARCHITECTURE



\*\*Project:\*\* Neptune Spear  

\*\*System:\*\* Argus  

\*\*Document Type:\*\* System Architecture Specification  

\*\*Status:\*\* Initial Architecture Baseline  

\*\*Version:\*\* 1.0



\---



\## 1. PURPOSE



Argus is the static code analysis and program understanding engine of Neptune Spear.



Its primary purpose is to analyze source code, reconstruct its structure and behavior, identify potentially dangerous execution paths, and generate evidence-based security hypotheses.



Argus must go beyond simple pattern matching. It should progressively understand program structure, data flow, control flow, dependencies, and semantic relationships.



Argus does not execute target code as part of its normal static analysis pipeline.



\## 2. CORE RESPONSIBILITIES



Argus is responsible for:



1\. Source code ingestion and normalization.

2\. Multi-language parsing through language adapters.

3\. Intermediate Representation (IR) generation.

4\. Symbol and scope analysis.

5\. Control Flow Graph (CFG) construction.

6\. Call Graph construction.

7\. Data-flow and dependency analysis.

8\. Taint analysis and security-oriented reasoning.

9\. Mathematical and logical hypothesis generation.

10\. Evidence collection and reporting.

11\. Generating bounded analysis hypotheses for Ababil.



Argus must clearly distinguish confirmed facts, inferred relationships, and uncertain hypotheses.



\## 3. HIGH-LEVEL ARCHITECTURE



Argus consists of the following logical components:



\### 3.1 Source Ingestion Layer



Responsibilities:



\- Read source files from explicitly supplied project directories.

\- Identify supported programming languages.

\- Handle file encodings and source locations.

\- Respect exclusions and analysis scope.

\- Record source hashes and file metadata.



\### 3.2 Language Adapter Layer



Each supported language must have an adapter responsible for translating language-specific syntax into the shared representation.



Initial priority:



\- Python

\- JavaScript

\- TypeScript

\- C

\- C++



Additional languages may be added through independent adapters.



Language adapters must not introduce language-specific assumptions into the shared analysis core.



\### 3.3 Intermediate Representation (IR)



IR is the normalized representation used by Argus.



It should preserve:



\- Instructions and expressions.

\- Variables and symbols.

\- Functions and methods.

\- Types where available.

\- Source locations.

\- Control-flow relationships.

\- Data dependencies.

\- Call relationships.

\- Language-specific metadata when necessary.



IR must be extensible and versioned.



\### 3.4 Program Structure Engine



This component reconstructs the structure of the analyzed program.



It includes:



\- Symbol tables.

\- Scope resolution.

\- Function and class indexing.

\- Control Flow Graphs.

\- Call Graphs.

\- Module and import relationships.



The engine must explicitly represent unresolved or ambiguous relationships rather than inventing certainty.



\### 3.5 Semantic Analysis Engine



This component reasons about program behavior.



Planned capabilities:



\- Reaching definitions.

\- Use-definition chains.

\- Data dependency analysis.

\- Alias and memory modeling.

\- Interprocedural data flow.

\- Function summaries.

\- Type and value propagation.

\- Path-sensitive reasoning.



These capabilities must be implemented incrementally and validated independently.



\### 3.6 Security Analysis Engine



This component identifies potentially dangerous code behavior.



Analysis categories include:



\- Source and sink identification.

\- Taint propagation.

\- Input validation analysis.

\- Sanitization analysis.

\- Authentication and authorization logic.

\- Injection-related behavior.

\- Unsafe deserialization.

\- Command execution.

\- File and path manipulation.

\- Sensitive data exposure.

\- Insecure cryptographic usage.



Findings must include evidence, source locations, reasoning, confidence, and limitations.



A pattern match alone must not automatically be presented as a confirmed vulnerability.



\### 3.7 Mathematical and Logical Reasoning Engine



Argus should progressively use formal and mathematical reasoning to analyze program behavior.



Potential techniques:



\- Constraint generation.

\- Symbolic expressions.

\- Boolean logic.

\- Path condition analysis.

\- Abstract interpretation.

\- Invariant inference.

\- Dependency equations.

\- Reachability reasoning.



Mathematical reasoning must remain explainable and tied to source evidence.



\### 3.8 Hypothesis and Experiment Interface



Argus may produce structured hypotheses for Ababil.



Each hypothesis should contain:



\- Unique identifier.

\- Target function or code location.

\- Security category.

\- Supporting evidence.

\- Preconditions.

\- Input constraints.

\- Expected behavior.

\- Confidence level.

\- Uncertainty and known limitations.

\- Suggested bounded test strategy.



Argus must not directly authorize arbitrary execution.



Ababil independently validates scope and execution permission.



\### 3.9 Evidence and Reporting Engine



Every important conclusion should be traceable to evidence.



Reports should distinguish:



\- Observed source facts.

\- Derived program relationships.

\- Analysis assumptions.

\- Security hypotheses.

\- Experiment results supplied by Ababil.

\- Independent audit conclusions supplied by Thoth.



Supported output formats should include JSON and human-readable Markdown.



\## 4. ANALYSIS PIPELINE



The intended analysis pipeline is:



1\. Project ingestion.

2\. File identification.

3\. Language detection.

4\. Parsing.

5\. IR generation.

6\. Symbol and scope resolution.

7\. CFG construction.

8\. Call Graph construction.

9\. Data-flow analysis.

10\. Semantic and security reasoning.

11\. Hypothesis generation.

12\. Evidence validation.

13\. Report generation.



The pipeline must support partial analysis when some files or language features cannot be fully understood.



Unsupported constructs must be reported explicitly.



\## 5. INTERACTION WITH OTHER SYSTEMS



\### 5.1 Shared Core



Argus uses Shared Core for:



\- Common data models.

\- IR contracts.

\- Evidence schemas.

\- Finding schemas.

\- Configuration.

\- Logging.

\- Serialization.

\- Inter-system communication.



Argus must not create incompatible duplicate versions of shared data models.



\### 5.2 Ababil



Argus provides structured analysis hypotheses to Ababil.



Ababil is responsible for:



\- Validating the authorized target scope.

\- Checking execution constraints.

\- Generating bounded test cases.

\- Running tests in an isolated environment.

\- Returning raw execution evidence.



Argus must not bypass Ababil's execution controls.



\### 5.3 Thoth



Thoth independently evaluates Argus findings and Ababil evidence.



Thoth may identify:



\- Unsupported conclusions.

\- False positives.

\- Missed vulnerabilities.

\- Incomplete reasoning.

\- Contradictory evidence.

\- Weak assumptions.



Argus must support traceable evidence so that Thoth can audit its conclusions.



\## 6. DESIGN PRINCIPLES



Argus must follow these principles:



1\. Local-first operation.

2\. No mandatory cloud inference.

3\. No mandatory large pretrained model.

4\. Modular and extensible architecture.

5\. Evidence-based conclusions.

6\. Explicit uncertainty representation.

7\. Reproducible analysis.

8\. Resource-aware execution.

9\. Separation of parsing, analysis, and reporting.

10\. Compatibility with Shared Core contracts.



\## 7. RESOURCE CONSTRAINTS



The initial target environment is:



\- Operating System: Windows 11.

\- Python: 3.13.

\- Memory: 8 GB RAM.

\- CPU: Intel Core i5-8365U.

\- GPU: Intel UHD Graphics 620.



Argus must prioritize efficient algorithms and incremental analysis.



Large projects should be processed with bounded memory consumption.



Parallel processing must not be assumed to improve performance on the target hardware.



\## 8. CURRENT IMPLEMENTATION BASELINE



Historical prototypes have demonstrated early versions of:



\- Basic opcode registry.

\- Basic IR.

\- Python AST adapter.

\- Basic graph representation.

\- Name-based intraprocedural taint candidate detection.

\- Basic scope and symbol representation.

\- Initial CFG construction.

\- Initial syntactic call graph.

\- Basic function summaries.



These prototypes are not equivalent to a complete production-grade analysis engine.



Their source code and tests must be integrated into the current repository and independently verified before they are treated as current capabilities.



\## 9. KNOWN LIMITATIONS AND FUTURE WORK



Major capabilities still requiring implementation and validation include:



\- Complete control-flow handling.

\- Exception-aware CFG.

\- Reaching definitions.

\- Alias and memory analysis.

\- Interprocedural taint analysis.

\- Cross-module resolution.

\- Dynamic dispatch.

\- Type inference.

\- Path-sensitive analysis.

\- Constraint solving.

\- Advanced vulnerability reasoning.

\- Evidence quality evaluation.



These are roadmap objectives, not claims of existing functionality.



\## 10. DEFINITION OF DONE



A major Argus capability is considered complete only when:



1\. Its technical specification is approved.

2\. Its implementation is integrated.

3\. Relevant automated tests exist.

4\. Tests have actually been executed.

5\. Expected behavior is demonstrated.

6\. Known limitations are documented.

7\. Evidence and outputs are reproducible.

8\. Security boundaries are respected.

9\. Thoth can independently audit its outputs.

10\. The Project Director approves completion.



Implementation alone does not mean a capability is complete.



\## 11. ARCHITECTURE GOVERNANCE



This document defines the initial architectural baseline for Argus.



Major changes to:



\- IR contracts.

\- Analysis pipeline.

\- Security boundaries.

\- Inter-system interfaces.

\- Core dependencies.

\- Execution responsibilities.



require a documented proposal and approval from the Project Director.



Implementation tasks must follow the approved architecture and NSDP workflow.



\---



\*\*End of Argus Architecture Specification\*\*

