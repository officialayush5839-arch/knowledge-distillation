# rules.md — Mandatory Rules Governing All Project Work

**Project:** KD-Edge-TinyML (see `prd.md` §1)

**Document role:** `rules.md` defines binding constraints for **every** future session — human or AI agent — working on this project. Any deliverable produced under violation of these rules is invalid until corrected. Conflicts between files are resolved by the precedence order in §A.

---

## A. Source-of-Truth Rules

1. **Primary research reference:** the source Word document
   `IEEE_Knowledge_Distillation_Edge_Literature_Gap_Report (1).docx`
   (search date 30 Sep 2026; SHA256 `b2ec98f3db088113e2d9793609ac433fda026db16dd57db3d71deb308f49ce87`).
   It is the authority for research background, gaps, and proposed direction until project decisions supersede it.

2. **Operational documentation system:** the seven Markdown files `prd.md`, `architecture.md`, `rules.md`, `phases.md`, `memory.md`, `goal.md`, `task.md`. They form one system; no competing copies of an authoritative file may exist.
3. **Precedence on conflict:** `rules.md` > `prd.md` (requirements) > `architecture.md` (design) > `phases.md` (order of work) > `task.md` (work items) > `goal.md`/`memory.md` (recorded state). A conflict must be **resolved explicitly** by editing the affected files and recording the resolution in `memory.md` — never silently.
4. **Traceability:** every research claim in any file must be traceable to (a) the source document, (b) verified literature, or (c) an experiment artifact. Otherwise it carries a status label (`ASSUMPTION`/`PROPOSED`/`TO_VERIFY`).
5. **Never invent** missing requirements, results, citations, measurements, or decisions.
6. **Never silently change the research direction.** A direction change requires: rationale, affected-file list, and a `memory.md` decision record.

## B. Research-Integrity Rules

1. Never fabricate citations, datasets, results, or measurements. (Citation counts in the source report are service-reported as of 30 Sep 2026 and must be rechecked before submission.)
2. Never claim novelty without a documented literature investigation satisfying `prd.md` §28.
3. Never report a proposed experiment as completed. Status labels (`PROPOSED`/`COMPLETED`/…) are mandatory and must be truthful.
4. Never select only favorable seeds, students, or configurations. All valid runs are registered; any exclusion needs a recorded reason.
5. Never hide failed experiments; store and reference them (FR-017).
6. Distinguish correlation from causation in every interpretation and in paper drafts.
7. Document negative and inconclusive findings; they are results.
8. Explain limitations honestly, including threats to validity (dataset scope, single environment, no energy instrumentation, software-only scope `D-006`, etc.).
9. Do not claim IEEE acceptance, publication, or superior performance as guaranteed outcomes (`prd.md` §2, §28).

## C. Experimental Rules

1. **Define baselines before evaluating the proposed method** (no-KD student, conventional teacher, ungated KD). Enforced by phase/task dependencies (`phases.md` PH-3 → PH-4).
2. Keep train/validation/test separated; respect chronology and site/season boundaries; never use test data for model, hyperparameter, λ, temperature, gate, or calibration selection.
3. Prevent data leakage; run automated leakage checks and abort on failure (FR-006).
4. Record dataset versions, checksums, and all preprocessing steps (FR-003, FR-005).
5. Fix and record random seeds; report all seeds run; document any dropped seed.
6. Record dependencies, environment, and code version per run (REP-002).
7. Make comparisons fair: identical splits, budgets, and metric code across compared methods (FR-011).
8. Record all model and quantization settings (FR-014, FR-021, FR-022).
9. Evaluate robustness where the RQ requires it (FR-032–FR-034).
10. **Separate simulated/estimated performance from measurements taken in the target runtime** everywhere (NFR-008).
11. Hyperparameter sweeps are performed on validation only and are reported, not cherry-picked.

## D. Software-Measurement Rules

1. Do not describe theoretical estimates (FLOPs, params) as measured latency, memory, or energy.
2. Under `D-006` there are no hardware measurements in this project: latency comes from executing an artifact in the target runtime, and energy is always an estimate.
3. Record the environment for every measurement: OS and version, CPU/GPU, library/runtime versions, thread/affinity settings, and any power or thermal configuration.
4. Record the measurement methodology: warm-up iterations, repetition count, input shape, batching (batch=1 for single-sample deployment latency), units.
5. Report units explicitly (ms, bytes/KB, mJ).
6. Distinguish peak process memory, serialized artifact size on disk, and total host memory; never conflate them (FR-028).
7. Store raw per-repetition measurement values, not only aggregates.
8. Energy is always an estimate in this project (`D-006` — no power instrumentation is in scope): never present an estimate as a measurement, and always state the estimation method (FR-030).
9. Never claim runtime/edge compatibility without a recorded run of that artifact in that runtime (FR-031).
10. Any carbon/energy estimate must state methodology, assumptions, and data sources (FR-035).

## E. Documentation Rules

1. All documentation is Markdown, in professional technical English, in these seven files.
2. Keep terminology identical across files (one name per method, component, metric, dataset).
3. Assign and use stable IDs: requirements `FR/NFR/REP/EXP`, metrics `MET-xx`, components `C-xx`, gaps `GAP-x`, RQs `RQx`, goals `G-xxx`, phases `PH-x`, tasks `T-xxx`, decisions `D-xxx`, unresolved decisions `U-xx`.
4. **Update `memory.md`** after every significant decision or milestone (new decision record + change history entry).
5. **Update `task.md`** when any task status changes (same session as the change).
6. **Update `phases.md`** when a phase completes or is re-planned.
7. **Update `goal.md`** when a goal is achieved, blocked, or legitimately revised.
8. Record reasons for every significant scope change, including matrix reductions.
9. Reference IDs instead of copying sections between files; each file keeps one purpose.
10. When a decision changes, sweep all seven files for consistency in the same session.

## F. Agent-Execution Rules

1. Inspect the current workspace before creating or editing files; preserve useful existing work; do not overwrite unrelated files.
2. Do not begin large-scale implementation before the documentation is internally consistent (PH-0 exit criteria met).
3. Do not mark a task complete merely because files were generated; completion requires checked acceptance criteria and recorded evidence (§G).
4. Validate every generated/edited file (existence, completeness, ID consistency).
5. Read `memory.md` and `task.md` **first** in any new session; do not redo completed work; do not contradict recorded decisions without a decision record.
6. When blocked, state the missing information, its owner/consumer, and propose one bounded next step (see `task.md` §Next Actions).
7. Do not run destructive commands (deletions, resets, force-pushes) without explicit user authorization.
8. Do not download large datasets, train models, or install heavy dependencies until the relevant phase is active and its entry criteria are met.

## G. Completion Rules

1. A **task** (`T-xxx`) is `COMPLETED` only when: its acceptance criteria have been checked, its evidence (artifact path, run ID, or document section) is recorded in `task.md`, and any dependent files were updated.
2. A **phase** (`PH-x`) is `COMPLETED` only when its exit criteria in `phases.md` are satisfied, or an explicit, justified exception has been approved and recorded in `memory.md`.
3. An **experiment** (`EXP-xxx`) is `COMPLETED` only when runs are registered, metrics are computed by C-11, and the results (including failures) are visible in the registry.
4. A **goal** (`G-xxx`) is marked achieved only when its success criteria in `goal.md` are demonstrably met with evidence.
5. Documentation-only milestones (e.g., PH-0) are completed by the cross-check procedure, not by file existence alone.
