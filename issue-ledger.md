# Agent PM Issue Ledger

## Review 2026-06-05

ReviewSpec:
- project_type: skill
- mode: discovery -> verification
- severity_threshold: P1
- max_findings: 8

| issue_id | severity | status | summary | fixed_files | verification |
|----------|----------|--------|---------|-------------|--------------|
| APM-WORKFLOW-001 | P1 | fixed | S7 formal artifact writes did not require scanning existing version directories before choosing or writing a version. | `SKILL.md` | S7 now requires scanning `pm-output/iterations/` and `pm-memory/OUTPUTS.md`, blocks same-version writes unless the user explicitly chooses to revise or overwrite, and handles state conflicts before writing. |
| APM-WORKFLOW-002 | P1 | fixed | S7 artifact generation did not explicitly require S8 consistency review before declaring completion. | `SKILL.md` | S7 now has a completion gate requiring scoped S8 consistency review, summary/state updates, and conflict handling before declaring formal output complete. |
| APM-OUTPUT-001 | P2 | fixed | `PRODUCT-DECISION-PACK.md` template lacked a version field even though it is the default persisted artifact. | `references/artifact-templates.md` | Product decision pack template now includes `## 2. 版本`, and later numbered sections were renumbered. |
| APM-OUTPUT-002 | P1 | fixed | Formal output strategy scattered core product understanding across multiple AI-facing files, while `PRD.md` lacked required flow diagrams, page maps, prototype layouts, environment context, and selection assumptions. | `SKILL.md`, `README.md`, `references/artifact-templates.md`, `references/prototype-ui-forge-bridge.md` | S7 now defaults to a complete human-readable `PRD.md`, uses Chinese names for optional user-facing files, limits default output to PRD plus optional `AI开发交接.md`, and adds a PRD completeness gate requiring Mermaid flows, page maps, text wireframes, interaction rules, acceptance, and risks. |
| APM-OUTPUT-003 | P1 | fixed | PRD-first consolidation still lacked module-level real product iteration granularity for complex features, such as multi-entry flows,主客态, H5-App jumps, authorization, copy assets, state machines, and acceptance cases. | `SKILL.md`, `README.md`, `references/artifact-templates.md` | Formal output now uses a layered `PRD.md` + `modules/` structure. Complex modules must generate dedicated module detail files with existing-vs-new changes, entrance matrix, role chain, wireframes, detailed interactions, business object state machines, jump/backflow rules, copy assets, data/API fields, risk controls, metrics, and Given/When/Then acceptance cases. |
| APM-OUTPUT-004 | P1 | fixed | The formal output set still included redundant standalone artifacts that should be absorbed into PRD and module detail files, including product decision pack, interaction spec, prototype brief, standalone acceptance criteria, AI-named handoff, and design output. | `SKILL.md`, `README.md`, `references/artifact-templates.md`, `references/product-visual-interaction-interrogation.md` | Formal output is now limited to `PRD.md`, `modules/`, optional `开发交接.md`, and supporting version-management files. Product decisions, interaction rules, prototype layouts, and acceptance criteria are embedded in PRD/modules. PM Assistant explicitly does not generate design-output or standalone prototype/UI handoff files. |
| APM-WORKFLOW-003 | P1 | fixed | The workflow did not explicitly identify product/system/technical/compliance/release environments before writing PRD, and module details lacked a mandatory interrogation mechanism for environment inheritance and true implementation granularity. | `SKILL.md`, `README.md`, `references/artifact-templates.md` | Added S1.5 environment identification and S5.6 module detail interrogation. PRD now carries global environment and modules carry environment inheritance/override tables, with required module interrogation covering positioning, environment, existing logic, entrances, roles, state machines, wireframes, jumps, copy, data/API, metrics, and acceptance cases. |
| APM-WORKFLOW-004 | P1 | fixed | S7 formal output trigger still allowed writing after only S2-S6 closure, so the newly added S1.5 environment stage and conditional S5.6 module interrogation could be skipped before generating PRD/modules. | `SKILL.md` | S7 now requires S1-S6 closure plus S1.5 completion, and requires S5.6 completion whenever modules are needed. S6 default saving flow and S7 write gate now enforce the same prerequisite. |

## Candidate Rules

- No formal rule promoted in this round. The observed pattern is local to this project so far: versioned artifact workflows need a write-time collision check that does not rely only on checkpoint state.

## Enhancements 2026-06-05

| enhancement_id | summary | files |
|----------------|---------|-------|
| APM-ENHANCE-001 | Added product dimension, visual interaction, and button-level interrogation so product decisions must map to page structure, component states, and core button behavior before interaction/prototype/handoff artifacts. | `SKILL.md`, `README.md`, `references/artifact-templates.md`, `references/prototype-ui-forge-bridge.md`, `references/product-visual-interaction-interrogation.md` |
| APM-ENHANCE-002 | Added Level 2 `ui-forge` bridge adapter via a fixed `UI-FORGE-HANDOFF.md` artifact and direct invocation phrase, without embedding `ui-forge` design execution into PM Assistant. | `SKILL.md`, `README.md`, `references/artifact-templates.md`, `references/prototype-ui-forge-bridge.md` |
| APM-ENHANCE-003 | Changed formal artifact strategy to PRD-first consolidation: `PRD.md` remains the stable entry file, optional user-facing files use Chinese names, and `AI开发交接.md` is only generated when implementation handoff is needed. | `SKILL.md`, `README.md`, `references/artifact-templates.md`, `references/prototype-ui-forge-bridge.md` |
| APM-ENHANCE-004 | Added module grouping as a first-class artifact layer so main PRD carries global context while `modules/` carries true online product-iteration details. | `SKILL.md`, `README.md`, `references/artifact-templates.md` |
| APM-ENHANCE-005 | Removed redundant standalone product artifacts and renamed implementation handoff to `开发交接.md`; PM Assistant now treats visual/prototype output as out of scope. | `SKILL.md`, `README.md`, `references/artifact-templates.md`, `references/product-visual-interaction-interrogation.md` |
| APM-ENHANCE-006 | Added environment layering and module interrogation flow: `S1.5` identifies global constraints, while `S5.6` forces module-level detail closure before writing `modules/*.md`. | `SKILL.md`, `README.md`, `references/artifact-templates.md` |
| APM-ENHANCE-007 | Split long stage and output rules out of `SKILL.md` into focused reference files without changing gates or behavior. | `SKILL.md`, `README.md`, `references/environment-interrogation.md`, `references/module-detail-interrogation.md`, `references/formal-output-rules.md` |
| APM-ENHANCE-008 | Moved checkpoint and version memory rules into a focused reference file while keeping memory boundaries and update gates visible in `SKILL.md`. | `SKILL.md`, `README.md`, `references/memory-rules.md` |
