# task.md — Actionable Task Tracker

**Project:** KD-Edge-TinyML (see `prd.md` §1)

**Document role:** `task.md` converts requirements (`prd.md`), design (`architecture.md`), constraints (`rules.md`), and roadmap (`phases.md`) into concrete, verifiable work items. It is the actionable tracker; update it whenever a status changes (`rules.md` §E5). Completed tasks require checked acceptance criteria and recorded evidence (`rules.md` §G).

---

## 1. Current Project Status

| Field | Value |
|---|---|
| Project | KD-Edge-TinyML — documentation foundation established, no implementation |
| Code written | None |
| Data acquired | None |
| Models trained | None |
| Measurements taken | None |
| Documentation | 7/7 files created and cross-checked (T-004 `COMPLETED`) |
| Open decisions | U-01…U-12 (`memory.md` §8) |
| Blockers | None |
| Overall state | PH-0 complete; PH-1 (novelty) is the critical path |

## 2. Current Phase

**PH-0 — Source inspection and project setup** (`COMPLETED`, 2026-10-10). Current phase: **PH-1 — Literature verification and novelty assessment** (`NOT_STARTED`).

## 3. Priority Definitions

| Priority | Meaning |
|---|---|
| `CRITICAL` | Blocks other work or invalidates the research framing if wrong; do first |
| `HIGH` | Required for the phase exit criteria; schedule within the phase |
| `MEDIUM` | Valuable, deferrable within the phase without breaking exit criteria |
| `LOW` | Optional strengthening; drop first under time pressure |

## 4. Task Status Definitions

| Status | Meaning |
|---|---|
| `NOT_STARTED` | No work performed |
| `IN_PROGRESS` | Work started, acceptance criteria not yet met |
| `BLOCKED` | Cannot proceed; blocker recorded in the task's Notes and in `memory.md` §17 |
| `COMPLETED` | Acceptance criteria checked and evidence recorded (`rules.md` §G1) |

## 5. Task Dependencies

- `T-001…T-003` → `T-004` → PH-0 exit.
- **PH-1 gating:** `T-010…T-016` must complete before `T-030` (framing may change → wasteful implementation otherwise).
- **PH-2 gating:** `T-022` (dataset) and `T-023` (task) gate all modelling tasks.
- `T-030` (skeleton) gates `T-031…T-035`, which gate all of PH-4/PH-5.
- `T-040…T-046` (PH-4) and `T-050…T-055` (PH-5) gate `T-060…T-066` (PH-6).
- `T-060…T-066` and `T-070…T-073` gate `T-080…T-084`, which gate `T-090…T-095`.
- Cross-cutting: `T-012` (compute feasibility) gates the size of the PH-4/PH-5 matrix.

## 6. Task Acceptance Criteria (policy)

Every task below states its own acceptance criteria. A task is complete only when: (a) its output artifact exists, (b) the stated verification was actually run, (c) the evidence path/ID is recorded in this file, and (d) `memory.md` was updated if the task produced a decision, result, or lesson.

## 7. Active Tasks

**None.** All PH-0 tasks are complete (see §9).

Next tasks to start (PH-1): T-010, T-012, T-013 — see §11.

## 8. Blocked Tasks

None. U-01…U-12 are open decisions with planned resolution tasks, not blockers.

## 9. Completed Tasks

| ID | Title | Completed | Evidence |
|---|---|---|---|
| T-001 | Inspect and validate the source report | 2026-10-10 | `memory.md` §3 (path, size, SHA256); report read in full |
| T-002 | Inspect the workspace and existing repository | 2026-10-10 | `memory.md` §18 (paths, empty project folder) |
| T-003 | Create the seven documentation files | 2026-10-10 | `prd.md`, `architecture.md`, `rules.md`, `phases.md`, `memory.md`, `goal.md`, `task.md` |
| T-005 | Create the initial decision log and unresolved-decision register | 2026-10-10 | `memory.md` §6 (D-001…D-005), §8 (U-01…U-12) |
| T-004 | Cross-check documentation consistency and record the result | 2026-10-10 | `memory.md` §21 cross-check entry: 7/7 files present; 7 gaps, 6 RQs, 9 goals, 10 phases, 60 tasks, 14 experiments, 16 metrics, 12 components, 12 open decisions; 4 defects found and repaired (PH-7 bold marker, U-05…U-08/U-12 task-owner mapping, task count). Balanced bold markers; code fences even; no proposed experiment marked completed. |

---

## 10. Backlog — Full Task Specifications

### PH-0 — Source inspection and project setup

#### T-001 — Inspect and validate the source report

- **Desc/Why:** Read the primary Word document in full; extract gaps, proposed direction, RQs, and checklists; record provenance so later claims are traceable.
- **Maps:** G-001 · PH-0 · no RQ (foundation) · supports all requirements.
- **Priority/Status:** `CRITICAL` / `COMPLETED` (2026-10-10).
- **Deps:** — · **Output:** provenance record + extracted direction reflected in the seven files.
- **Acceptance:** document read beyond the introduction; gaps and direction represented without invention.
- **Verify:** spot-check extracted content against the source text; hash recorded.
- **Evidence:** `memory.md` §3 (SHA256 `b2ec98…ce87`), §21.

#### T-002 — Inspect the workspace and existing repository

- **Desc/Why:** Locate the source document, existing docs/code/data; choose the documentation home without overwriting unrelated work.
- **Maps:** PH-0 · G-001. **Priority/Status:** `CRITICAL` / `COMPLETED`.
- **Deps:** — · **Output:** workspace map + chosen project root.
- **Acceptance:** no unrelated files modified; documentation home justified.
- **Verify:** folder listing before/after shows only the seven new files.
- **Evidence:** `memory.md` §18.

#### T-003 — Create the seven documentation files

- **Desc/Why:** Author `prd.md`, `architecture.md`, `rules.md`, `phases.md`, `memory.md`, `goal.md`, `task.md` as one coordinated system with stable IDs.
- **Maps:** G-001, G-002…G-009 (framing) · PH-0. **Priority/Status:** `CRITICAL` / `COMPLETED`.
- **Deps:** T-001, T-002 · **Output:** seven substantive Markdown files.
- **Acceptance:** each file populated; status labels truthful; no fabricated facts.
- **Verify:** existence + content inspection (T-004).
- **Evidence:** the seven files in `Knowledge Distillation/`.

#### T-004 — Cross-check documentation consistency and record the result

- **Desc/Why:** Verify 7/7 files, all gaps/RQs, consistent IDs, no proposed work marked completed, no fake citations, logical dependencies.
- **Maps:** PH-0 · NFR-007. **Priority/Status:** `CRITICAL` / `COMPLETED` (2026-10-10).
- **Deps:** T-003 · **Output:** cross-check record in `memory.md` §21.
- **Acceptance:** checklist in `phases.md` fully executed; defects repaired in the same session.
- **Verify:** ID grep across the seven files; defect list closed.
- **Evidence:** `memory.md` §21 entry.

#### T-005 — Create the initial decision log and unresolved-decision register

- **Desc/Why:** Record what is genuinely decided (D-001…D-005) and what remains open (U-01…U-12) so future sessions do not silently re-decide.
- **Maps:** PH-0 · `rules.md` §A3. **Priority/Status:** `HIGH` / `COMPLETED`.
- **Deps:** T-001, T-003 · **Output:** `memory.md` §6/§7/§8.
- **Acceptance:** every open design choice has an ID and a resolution task.
- **Verify:** U-xx count matches `architecture.md` §22.
- **Evidence:** `memory.md` §6, §8.

### PH-1 — Literature verification and novelty assessment

#### T-010 — Verify the 54-record literature map

- **Desc/Why:** Check the SRC-01 records exist, are relevant, and that citation counts are current; annotate errors. The report's counts are service-reported and may be stale.
- **Maps:** G-002 · PH-1 · RQ1–RQ6 (framing). **Priority/Status:** `CRITICAL` / `NOT_STARTED`.
- **Deps:** T-003 · **Output:** annotated bibliography (verified/unverifiable/irrelevant).
- **Acceptance:** all 54 records dispositioned; duplicates identified.
- **Verify:** each record opened at its source; discrepancies noted.
- **Evidence:** `memory.md` §9 entries + bibliography artifact path `TO_VERIFY`.

#### T-011 — Deep-read the priority papers

- **Desc/Why:** Read the report's 10 priority papers; extract method, teacher/student, quantization regime, hardware, datasets, metrics, reported numbers, and limitations.
- **Maps:** G-002 · PH-1. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-010 · **Output:** structured paper notes (one record per paper).
- **Acceptance:** each note contains all extraction fields; no numbers reproduced without source.
- **Verify:** cross-check 2 notes against the papers.
- **Evidence:** notes artifact path `TO_VERIFY`; summary in `memory.md` §9.

#### T-012 — Assess compute feasibility for teachers (U-10, U-01 preliminary)

- **Desc/Why:** Determine what compute can train/finetune/evaluate 2–4 large time-series models plus conventional baselines; this bounds the whole experiment matrix.
- **Maps:** G-002, G-003, G-T5 · PH-1 · RK-6. **Priority/Status:** `CRITICAL` / `NOT_STARTED`.
- **Deps:** T-003 · **Output:** compute assessment note with matrix reduction options.
- **Acceptance:** each candidate teacher has an explicit feasibility verdict.
- **Verify:** at least one teacher finetune smoke-run completes, or local reasoning is documented if not yet permitted.
- **Evidence:** assessment note path `TO_VERIFY`; decisions D-0xx.
- **Notes:** must precede T-031; may reduce teacher count — a scope change requiring a `memory.md` record.

#### T-013 — Target search: uncertainty/reliability-gated KD for time series

- **Desc/Why:** Find whether uncertainty-gated or reliability-weighted distillation under domain shift has been published for time-series/forecasting; this is the candidate novelty.
- **Maps:** G-002, G-004, G-007 · PH-1 · RQ5. **Priority/Status:** `CRITICAL` / `NOT_STARTED`.
- **Deps:** T-010 · **Output:** competitor list + gap verdict.
- **Acceptance:** ≥3 closest works identified with explicit differences, or a documented negative result.
- **Verify:** search queries/dates recorded; results linkable.
- **Evidence:** `memory.md` §9.

#### T-014 — Target search: KD × quantization on MCU/TinyML hardware

- **Desc/Why:** Establish the state of the art for joint KD+quantization deployed on microcontrollers, including agricultural applications. **Literature only** — this project itself runs no MCU experiments (`D-006`); the search matters because it bounds what is already claimed and what is still open.
- **Maps:** G-002, G-005, G-006 · PH-1 · RQ3, RQ4. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-010 · **Output:** annotated competitor set + which accuracy/footprint regimes are already covered.
- **Acceptance:** at least 5 relevant works with hardware and quantization details extracted.
- **Verify:** hardware/runtime claims traced to the papers.
- **Evidence:** `memory.md` §9.

#### T-015 — Write the novelty positioning memo

- **Desc/Why:** Produce the point-by-point comparison required by `prd.md` §28 and decide whether the candidate contribution stands or must be re-scoped.
- **Maps:** G-002, G-009 · PH-1 · `rules.md` §B2. **Priority/Status:** `CRITICAL` / `NOT_STARTED`.
- **Deps:** T-011, T-013, T-014 · **Output:** novelty memo + recommendation (proceed / re-scope to P-006 option).
- **Acceptance:** no unsupported novelty claim; every claim linked to a source.
- **Verify:** second reviewer pass (human or fresh agent) against the memo.
- **Evidence:** memo path `TO_VERIFY`; `memory.md` §6/§7 decision record.

#### T-016 — Refine RQs, hypotheses, and metrics if needed

- **Desc/Why:** Apply PH-1 findings: sharpen wording, adjust hypotheses, or change domain/method if novelty fails.
- **Maps:** G-002 · PH-1 · all RQs. **Priority/Status:** `MEDIUM` (conditional) / `NOT_STARTED`.
- **Deps:** T-015 · **Output:** updated `prd.md` §7/§12 if warranted.
- **Acceptance:** every change justified by a PH-1 finding and recorded in `memory.md`.
- **Verify:** re-run the ID consistency grep after editing.
- **Evidence:** `memory.md` §21 diff entry.

### PH-2 — Dataset and task definition

#### T-020 — Define dataset selection criteria

- **Desc/Why:** Turn DST-R1…DST-R5 into concrete, checkable criteria (variables, sampling rate, sites/seasons, license, gaps) before browsing datasets.
- **Maps:** G-003 · PH-2 · FR-001, FR-002, FR-004. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-003 · **Output:** criteria checklist.
- **Acceptance:** each criterion is objectively checkable.
- **Verify:** apply the checklist to one candidate dataset as a dry run.
- **Evidence:** criteria in `prd.md` §16 or a data-criteria artifact.

#### T-021 — Shortlist datasets, verify licenses, select DST-01

- **Desc/Why:** Choose the dataset that actually supports domain shift (multi-site/season) and a defensible task; record license and provenance.
- **Maps:** G-003 · PH-2 · FR-001, FR-005, RQ2. **Priority/Status:** `CRITICAL` / `NOT_STARTED`.
- **Deps:** T-020 · **Output:** DST-01 record + checksum + license.
- **Acceptance:** DST-R1…R5 all satisfied or deviations explicitly justified.
- **Verify:** download/access succeeds; checksum reproducible.
- **Evidence:** `memory.md` §10; manifest path.

#### T-022 — Define the prediction task (U-04)

- **Desc/Why:** Fix target variable(s), lookback, horizon, and whether an auxiliary alert/classification head is needed (affects MET-04).
- **Maps:** G-003, G-004 · PH-2 · FR-002, RQ1. **Priority/Status:** `CRITICAL` / `NOT_STARTED`.
- **Deps:** T-021 · **Output:** task definition section.
- **Acceptance:** horizon/lookback justified against the runtime latency budget and student capacity.
- **Verify:** a trivial persistence baseline can be computed on the task.
- **Evidence:** task definition artifact; `memory.md` decision record.

#### T-023 — Finalize the evaluation protocol and metrics (U-11 partial)

- **Desc/Why:** Lock MET-03/MET-06 choices, aggregation, and reporting; a single metric implementation must serve all models (FR-011).
- **Maps:** G-003 · PH-2 · FR-011, MET-01…MET-06. **Priority/Status:** `CRITICAL` / `NOT_STARTED`.
- **Deps:** T-022 · **Output:** protocol section + metric definitions.
- **Acceptance:** every reported metric has a formula and unit; no ambiguous metric.
- **Verify:** two independent implementations agree on a toy example.
- **Evidence:** protocol artifact; `prd.md` §12 updates if any.

#### T-024 — Define the domain-shift construction

- **Desc/Why:** Specify exactly which sites/seasons/sensors constitute source vs target domains; decide natural vs synthetic shift; label synthetic everywhere.
- **Maps:** G-004, G-007 · PH-2 · FR-004, FR-023–FR-025, RQ2, RQ5. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-021 · **Output:** domain map + split rules.
- **Acceptance:** every window is assigned to exactly one domain; chronology respected.
- **Verify:** assignment deterministic; no overlap.
- **Evidence:** config path; `memory.md` §10.

#### T-025 — Implement the data pipeline with leakage checks

- **Desc/Why:** Ingestion, validation, preprocessing, deterministic splits, manifest, and an abort-on-leakage check (FR-002, FR-003, FR-006, REP-003).
- **Maps:** G-003 · PH-2 · FR-001–FR-006. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-021, T-024 · **Output:** `src/data/` module + tests.
- **Acceptance:** split hashes identical on re-run; injected leakage aborts.
- **Verify:** negative test suite passes.
- **Evidence:** test report path; manifest hashes.

#### T-026 — Document data quality and limitations

- **Desc/Why:** Record gaps, sensor noise, coverage, and what the dataset cannot answer (protects against overclaiming).
- **Maps:** G-I5 · PH-2 · RQ2. **Priority/Status:** `MEDIUM` / `NOT_STARTED`.
- **Deps:** T-025 · **Output:** data-limitations section.
- **Acceptance:** limitations referenced later in PH-9.
- **Verify:** PH-9 threats-to-validity cites this section.
- **Evidence:** `memory.md` §15.

### PH-3 — Baseline implementation

#### T-030 — Build the repository skeleton, config system, and run registry

- **Desc/Why:** Implement the C-01/C-08 spine (config → run ID → artifacts) so every later result is traceable.
- **Maps:** G-003, G-T1, G-T2, G-T3 · PH-3 · FR-NFR: NFR-001, NFR-002, NFR-004, REP-001, REP-002. **Priority/Status:** `CRITICAL` / `NOT_STARTED`.
- **Deps:** T-025 · **Output:** repo layout per `architecture.md` §21; pinned environment; one end-to-end dummy run.
- **Acceptance:** a dummy experiment runs from config and emits a complete manifest.
- **Verify:** re-run yields the same manifest (except timestamps).
- **Evidence:** repo commit hash; run registry entry.

#### T-031 — Select and train teacher models (U-01)

- **Desc/Why:** Train/finetune 2–4 time-series foundation/large teachers plus a conventional strong baseline on the source domain.
- **Maps:** G-003, G-004 · PH-3 · FR-007, FR-010. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-012, T-030 · **Output:** teacher checkpoints + teacher metrics.
- **Acceptance:** teachers evaluated on in-domain test; uncertainty availability recorded per teacher.
- **Verify:** metrics recomputed from stored predictions.
- **Evidence:** run IDs; `memory.md` §11.

#### T-032 — Build the student model zoo (U-02)

- **Desc/Why:** Implement ≥2 architecture families × ≥3 capacities with footprint reporting.
- **Maps:** G-003 · PH-3 · FR-008, FR-009, NFR-003. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-030 · **Output:** `src/students/` + registry entries.
- **Acceptance:** ≥6 configurations with measured param counts; adapter addition needs no core edits.
- **Verify:** dummy-adapter extension test passes.
- **Evidence:** registry table; `memory.md` §11.

#### T-033 — Establish student no-KD baselines (EXP-002)

- **Desc/Why:** Mandatory comparison set before any distillation claim (`rules.md` §C1).
- **Maps:** G-003 · PH-3 · FR-016, EXP-002, RQ1. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-032 · **Output:** baseline metrics + footprints for every student configuration.
- **Acceptance:** all configurations trained under identical budgets/splits.
- **Verify:** metrics recomputed from stored predictions.
- **Evidence:** run IDs; comparison table.

#### T-034 — Evaluate teachers in-domain and on target domains (EXP-001)

- **Desc/Why:** Produce the reference column for every later comparison and quantify teacher degradation under shift.
- **Maps:** G-003 · PH-3 · EXP-001, FR-011, RQ1, RQ2. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-031, T-024 · **Output:** per-domain teacher metrics.
- **Acceptance:** per-domain reporting complete for every teacher.
- **Verify:** spot-check one teacher/domain pair by hand.
- **Evidence:** run IDs; results table.

#### T-035 — Prove baseline reproducibility (preliminary REP-004)

- **Desc/Why:** Re-run one baseline and compare; catches nondeterminism before it contaminates a whole phase.
- **Maps:** G-T2, G-T3, G-008 · PH-3 · REP-002–REP-004. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-030, T-033 · **Output:** reproduction delta record + tolerance decision.
- **Acceptance:** deltas within the stated tolerance, or the cause is identified and recorded.
- **Verify:** independent re-execution from the stored config.
- **Evidence:** delta table; `memory.md` §13.

### PH-4 — Knowledge-distillation experiments

#### T-040 — Implement the KD engine (KD-1…KD-3)

- **Desc/Why:** Logit/forecast, feature, and temporal-relation distillation with configurable λ/T (FR-012, FR-014).
- **Maps:** G-004 · PH-4 · FR-012, FR-014. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-033 · **Output:** `src/kd/` + unit tests per loss.
- **Acceptance:** each loss is unit-tested; KD-off reproduces T-033 exactly.
- **Verify:** KD-0 equivalence test.
- **Evidence:** test report; commit hash.

#### T-041 — Implement teacher uncertainty extraction (U-05)

- **Desc/Why:** Expose a per-window uncertainty signal for each teacher used in gating (FR-010), deployable-time computable or validation-fit.
- **Maps:** G-004, G-007 · PH-4 · FR-010, RQ5. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-031 · **Output:** `src/uncertainty/` + per-teacher signal records.
- **Acceptance:** every gating-eligible teacher has a signal; ineligible teachers documented as excluded.
- **Verify:** signal present for a sample batch; shape/range checks pass.
- **Evidence:** `memory.md` §11/§12.

#### T-042 — Implement uncertainty/reliability gating (KD-4, U-06)

- **Desc/Why:** Implement `g(t)` weighting such that KD-4 reduces exactly to ungated KD when `g ≡ 1` (FR-013).
- **Maps:** G-004 · PH-4 · FR-013, RQ5. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-040, T-041 · **Output:** `src/kd/gating.py` + ablation switch.
- **Acceptance:** gating-off run is bit-identical to ungated KD under the same seed.
- **Verify:** equality test between the two loss paths.
- **Evidence:** test report; `memory.md` §12.

#### T-043 — Run EXP-003: distillation-target comparison (in-domain)

- **Desc/Why:** Compare none/logit/feature/temporal targets under identical budgets.
- **Maps:** G-004 · PH-4 · EXP-003, RQ1, RQ2. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-040 · **Output:** results table + run IDs.
- **Acceptance:** all strategies share cached teacher signals, splits, and budgets.
- **Verify:** config diff shows only the intended factor differs.
- **Evidence:** run IDs; `memory.md` §13.

#### T-044 — Run EXP-005: distillation under domain shift

- **Desc/Why:** Evaluate every strategy on held-out site/season domains.
- **Maps:** G-004, G-007 · PH-4 · EXP-005, RQ2. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-043, T-024 · **Output:** per-domain comparison table.
- **Acceptance:** in-domain and shifted-domain results reported separately (FR-023).
- **Verify:** worst-domain error computed independently.
- **Evidence:** run IDs; `memory.md` §13.

#### T-045 — Run EXP-006: gated vs ungated distillation + ablations

- **Desc/Why:** Test the candidate contribution and isolate the gate (H-RQ5a/H-RQ5b).
- **Maps:** G-004, G-007 · PH-4 · EXP-006, FR-013, RQ5. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-042, T-044 · **Output:** ablation dossier (gate on/off, λ sweep on validation, threshold sweep).
- **Acceptance:** gating-only difference isolated; non-inferiority margin applied as pre-declared.
- **Verify:** paired per-window comparison on the failure subset.
- **Evidence:** run IDs; `memory.md` §13/§14.

#### T-046 — Record distillation failures and lessons

- **Desc/Why:** Failed configurations (divergence, no improvement, toolchain limits) are results and must persist (FR-017).
- **Maps:** G-I4 · PH-4 · FR-017. **Priority/Status:** `MEDIUM` / `NOT_STARTED`.
- **Deps:** T-043, T-044, T-045 · **Output:** failure records.
- **Acceptance:** every failed configuration appears with status and reason.
- **Verify:** count of runs vs count of records matches.
- **Evidence:** `memory.md` §14.

### PH-5 — Quantization experiments

#### T-050 — Implement the quantization pipeline with correctness checks

- **Desc/Why:** FP32/FP16/INT8-PTQ/INT8-QAT (+mixed if supported) and the output-deviation check (FR-018–FR-021).
- **Maps:** G-005 · PH-5 · FR-018–FR-022. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-033 · **Output:** `src/quant/` + settings records.
- **Acceptance:** each regime runnable and logged; calibration restricted to train.
- **Verify:** calibration-split assertion test passes.
- **Evidence:** commit hash; settings records.

#### T-051 — Run EXP-007: PTQ sweep and mixed-precision feasibility (U-09)

- **Desc/Why:** Map FP32→FP16→INT8-PTQ on selected students; determine whether INT4/mixed is supported.
- **Maps:** G-005 · PH-5 · EXP-007, FR-018, RQ3. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-050 · **Output:** delta table vs FP32 + support verdict.
- **Acceptance:** unsupported regimes reported explicitly, not skipped.
- **Verify:** recompute deltas from stored predictions.
- **Evidence:** run IDs; `memory.md` §13.

#### T-052 — Run EXP-008: QAT vs PTQ at matched bit width

- **Desc/Why:** Separate the value of quantization-aware training from post-training quantization (H-RQ3a).
- **Maps:** G-005 · PH-5 · EXP-008, RQ3. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-051 · **Output:** comparison table at identical bit width/protocol.
- **Acceptance:** bit width and evaluation protocol held constant; QAT settings recorded (FR-022).
- **Verify:** config diff shows only the regime differs.
- **Evidence:** run IDs; `memory.md` §13.

#### T-053 — Run EXP-009: KD × quantization interaction factorial

- **Desc/Why:** Test whether distilling before quantizing shifts the frontier (H-RQ3b/H-RQ3c).
- **Maps:** G-005 · PH-5 · EXP-009, RQ3. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-052, T-043 · **Output:** factorial results table.
- **Acceptance:** KD on/off × regime crossed with ≥2 capacities.
- **Verify:** interaction verified against stored per-run metrics.
- **Evidence:** run IDs; `memory.md` §13.

#### T-054 — Produce the toolchain-constraint report

- **Desc/Why:** Record which ops, bit widths, and schemes the chosen stack supports — this bounds every deployment claim.
- **Maps:** G-005, G-006 · PH-5 · FR-018, FR-026. **Priority/Status:** `MEDIUM` / `NOT_STARTED`.
- **Deps:** T-050 · **Output:** constraint matrix.
- **Acceptance:** every unsupported capability listed with the failing op/tool.
- **Verify:** PH-6 export tasks cite this report.
- **Evidence:** report path; `memory.md` §15.

#### T-055 — Record quantization outcomes and update memory

- **Desc/Why:** Consolidate deltas, failures, and settings into the persistent record (RQ3 evidence).
- **Maps:** G-005, G-T3 · PH-5 · RQ3. **Priority/Status:** `MEDIUM` / `NOT_STARTED`.
- **Deps:** T-051, T-052, T-053 · **Output:** `memory.md` §12/§13/§14 updates.
- **Acceptance:** RQ3 row in the results summary points to run IDs.
- **Verify:** traceability spot-check.
- **Evidence:** `memory.md` §21 entry.

### PH-6 — Software resource and efficiency evaluation

#### T-060 — Finalize target runtime and environment (U-07)

- **Desc/Why:** Decide the target software runtime and environment based on student-op support, availability, and measurability.
- **Maps:** G-006 · PH-6 · FR-026, FR-031, RK-4. **Priority/Status:** `CRITICAL` / `NOT_STARTED`.
- **Deps:** T-054 · **Output:** runtime/environment decision record.
- **Acceptance:** target runtime installed and reproducing a trivial benchmark (or fallback declared per RK-4).
- **Verify:** toolchain builds and runs a trivial model in the target runtime.
- **Evidence:** `memory.md` §6 decision; `architecture.md` §22 U-07 closed.

#### T-061 — Implement the export/deployment path (C-09)

- **Desc/Why:** Convert supported students to target-runtime artifacts, hash them, and record conversion settings (FR-026).
- **Maps:** G-006 · PH-6 · FR-026, FR-031. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-060 · **Output:** `src/deploy/` + deployment manifests.
- **Acceptance:** at least one student loads and runs in the target runtime.
- **Verify:** runtime run log exists (FR-031).
- **Evidence:** binary hashes; run log path.

#### T-062 — Implement the software benchmark harness (C-10) with methodology record

- **Desc/Why:** Measure latency and peak process memory with warm-up/repetitions; document methodology before reporting (FR-027, FR-028).
- **Maps:** G-006 · PH-6 · FR-027, FR-028, `rules.md` §D. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-061 · **Output:** harness + methodology record + raw per-repetition logs.
- **Acceptance:** units, repetitions, warm-up, and environment versions recorded; process memory and artifact size reported separately.
- **Verify:** repeat measurement twice; dispersion reported.
- **Evidence:** raw logs; methodology doc.

#### T-063 — Compute theoretical metrics for all candidates (EXP-004)

- **Desc/Why:** Pair every measured model with params/MACs so RQ4 can be tested.
- **Maps:** G-006 · PH-6 · EXP-004, FR-029, MET-07, MET-11. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-032, T-050 · **Output:** theoretical-metric table.
- **Acceptance:** every measured model has a theoretical counterpart row.
- **Verify:** parameter count cross-checked against the export tool's report.
- **Evidence:** registry table.

#### T-064 — Deploy candidates and collect measurements (EXP-010, EXP-011 measurement part)

- **Desc/Why:** Produce the measured axis of the Pareto frontier.
- **Maps:** G-006 · PH-6 · EXP-010, EXP-011, FR-027–FR-029, RQ4, RQ6. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-062, T-063 · **Output:** measurement dataset (per model, per environment).
- **Acceptance:** deployment failures recorded as results, not discarded.
- **Verify:** correlation analysis feasible from the data (both axes present).
- **Evidence:** `memory.md` §13.

#### T-065 — Energy measurement or explicit unavailability statement (U-08)

- **Desc/Why:** Either estimate energy/inference with a documented method or state clearly that it is unavailable (FR-030).
- **Maps:** G-006 · PH-6 · FR-030, FR-035, GAP-7. **Priority/Status:** `MEDIUM` / `NOT_STARTED`.
- **Deps:** T-062 · **Output:** MET-14 data **or** an unavailability statement.
- **Acceptance:** no estimated value presented as measured; any estimate carries methodology.
- **Verify:** report text checked against `rules.md` §D7.
- **Evidence:** `memory.md` §15.

#### T-066 — Optional: second software environment evaluation (U-12)

- **Desc/Why:** Add a second software environment to test whether theory-vs-measured findings generalize (strengthens RQ4).
- **Maps:** G-006 · PH-6 · RQ4. **Priority/Status:** `LOW` / `NOT_STARTED`.
- **Deps:** T-062 · **Output:** measurement data for the second environment, if available.
- **Acceptance:** same methodology as T-062.
- **Verify:** comparable logs.
- **Evidence:** `memory.md` §13.
- **Notes:** first task to cut under time pressure; its absence is recorded as a limitation.

### PH-7 — Robustness and statistical analysis

#### T-070 — Multi-seed runs for critical configurations (EXP-012)

- **Desc/Why:** Quantify seed/dispersion effects rather than reporting single-run numbers.
- **Maps:** G-007 · PH-7 · EXP-012, FR-032, MET-16. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-044, T-045, T-052 · **Output:** seed sets for critical comparisons.
- **Acceptance:** ≥2 seeds (target 3–5); all seeds reported; dropped seeds justified.
- **Verify:** dispersion metrics computed by C-11.
- **Evidence:** run registry; `memory.md` §13.

#### T-071 — Error-distribution, worst-domain, calibration, and failure analysis

- **Desc/Why:** Move beyond mean accuracy (GAP-5): percentiles, worst-group error, calibration, and worst-case inspection.
- **Maps:** G-007 · PH-7 · FR-024, FR-033, MET-05, MET-06. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-070 · **Output:** robustness report + failure dossier (worst-N windows with context).
- **Acceptance:** worst-domain and percentile statistics present for every compared method.
- **Verify:** recompute one percentile by hand.
- **Evidence:** analysis report path.

#### T-072 — Statistical analysis (EXP-014)

- **Desc/Why:** Apply pre-declared paired tests and effect sizes; report CIs rather than point estimates alone.
- **Maps:** G-007, G-008 · PH-7 · EXP-014, FR-034, U-11. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-070 · **Output:** statistics section with test names, assumptions, and results.
- **Acceptance:** tests named before results were inspected; assumptions checked.
- **Verify:** independent recomputation of one test.
- **Evidence:** `memory.md` §12 decision on U-11.

#### T-073 — Record robustness limitations and update memory

- **Desc/Why:** Capture what could not be tested (seed count, single software environment, energy not measured, synthetic shift) for PH-9.
- **Maps:** G-I5 · PH-7 · RQ5. **Priority/Status:** `MEDIUM` / `NOT_STARTED`.
- **Deps:** T-071, T-072 · **Output:** limitations list.
- **Acceptance:** each limitation maps to a PH-9 threats-to-validity item.
- **Verify:** PH-9 checklist cites them.
- **Evidence:** `memory.md` §15.

### PH-8 — Reproducibility and model selection

#### T-080 — Artifact completeness audit

- **Desc/Why:** Verify every run has config, hashes, metrics, and artifacts before drawing conclusions.
- **Maps:** G-008, G-T3 · PH-8 · REP-006, NFR-004. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-064, T-070 · **Output:** audit report with gaps and repairs.
- **Acceptance:** 100% of reported runs have non-empty manifests.
- **Verify:** automated manifest-field check.
- **Evidence:** audit report path.

#### T-081 — Consolidate configs and build the comparison framework

- **Desc/Why:** Produce the unified comparison tables/frontiers from the registry only (no hand-typed numbers).
- **Maps:** G-008 · PH-8 · NFR-002, `architecture.md` §16. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-080 · **Output:** `src/analysis/` pipeline + generated tables.
- **Acceptance:** regenerating from the registry reproduces the tables exactly.
- **Verify:** delete and regenerate outputs; compare hashes.
- **Evidence:** generated artifacts.

#### T-082 — Reproduction re-run checks (EXP-013, REP-004)

- **Desc/Why:** Re-execute critical configurations to test whether the framework is genuinely reproducible.
- **Maps:** G-008 · PH-8 · EXP-013, REP-004, RQ6. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-081 · **Output:** reproduction delta table.
- **Acceptance:** deltas within the stated tolerance, or causes documented.
- **Verify:** comparison performed by the analysis pipeline, not by hand.
- **Evidence:** delta table; `memory.md` §13.

#### T-083 — Build the Pareto frontier and budget-indexed selection (U-05 budget classes)

- **Desc/Why:** Deliver the project's central artifact: frontier, knee points, and the preferred configuration per budget class.
- **Maps:** G-008 · PH-8 · EXP-011, EXP-014, RQ6. **Priority/Status:** `CRITICAL` / `NOT_STARTED`.
- **Deps:** T-081, T-082 · **Output:** frontier plots/tables + selection rationale per budget.
- **Acceptance:** every frontier point traces to a run ID; confidence bands shown; selection justified by measured evidence.
- **Verify:** spot-check one knee point's provenance.
- **Evidence:** frontier artifacts; `memory.md` §13.

#### T-084 — Assemble the reproducibility release package (REP-007)

- **Desc/Why:** Make third-party reproduction possible: code, configs, split definitions, benchmark scripts, instructions.
- **Maps:** G-008, G-009 · PH-8 · REP-001–REP-007. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-082, T-083 · **Output:** package + README + completeness checklist.
- **Acceptance:** a clean-environment dry run of one experiment succeeds.
- **Verify:** dry run executed in a fresh environment.
- **Evidence:** package checklist; `memory.md` §19.

### PH-9 — Final analysis and research-paper preparation

#### T-090 — Consolidate findings and map them to RQ1–RQ6

- **Desc/Why:** Produce the authoritative result→RQ mapping; anything unmapped is either a new finding or not a finding.
- **Maps:** G-009 · PH-9 · `rules.md` §B6. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-083 · **Output:** findings map with evidence links.
- **Acceptance:** each RQ answered, partially answered, or explicitly unanswered with reason.
- **Verify:** every claim links to a run ID or citation.
- **Evidence:** findings map path.

#### T-091 — Generate figures and tables from real experimental data

- **Desc/Why:** Every figure/table must come from the registry; no hand-entered numbers.
- **Maps:** G-009 · PH-9 · NFR-004. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-083, T-090 · **Output:** figure/table sources + rendered outputs.
- **Acceptance:** regeneration script reproduces every figure.
- **Verify:** regenerate and compare.
- **Evidence:** generation scripts + artifacts.

#### T-092 — Draft methods, results, discussion, and related work

- **Desc/Why:** Write the manuscript sections from the evidence, following the report's proposed paper structure.
- **Maps:** G-009 · PH-9 · `prd.md` §28. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-090, T-091 · **Output:** draft sections.
- **Acceptance:** no unsupported claim; every reported number traceable.
- **Verify:** claim-by-claim audit against `memory.md` §13.
- **Evidence:** draft path.

#### T-093 — Write the limitations and threats-to-validity section

- **Desc/Why:** Make the boundaries of the evidence explicit (dataset scope, single software environment, energy estimated rather than measured, seed count).
- **Maps:** G-I5 · PH-9 · RQ2, RQ4, RQ5. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-073, T-092 · **Output:** limitations section.
- **Acceptance:** every known limitation from `memory.md` §15 addressed.
- **Verify:** cross-check against §15.
- **Evidence:** draft section.

#### T-094 — Validate the novelty statement (`prd.md` §28)

- **Desc/Why:** Confirm all six conditions for a novelty claim before any such claim is written.
- **Maps:** G-002, G-009 · PH-9 · `rules.md` §B2, §B9. **Priority/Status:** `CRITICAL` / `NOT_STARTED`.
- **Deps:** T-015, T-092 · **Output:** validated contribution statement or a documented decision to present the work as a benchmark/decision-framework contribution.
- **Acceptance:** if conditions fail, the claim is removed or re-scoped — no exceptions.
- **Verify:** point-by-point check against §28's six conditions.
- **Evidence:** `memory.md` §6 decision record.

#### T-095 — Pass the IEEE submission checklist and confirm venue fit

- **Desc/Why:** Apply the report's checklist (splits, CIs, environment/version disclosure, no parameter-as-energy, failure cases, artifacts) and verify the target venue's current scope/template/page limits at submission time.
- **Maps:** G-009 · PH-9 · `prd.md` §28. **Priority/Status:** `HIGH` / `NOT_STARTED`.
- **Deps:** T-092, T-093, T-094 · **Output:** checklist with per-item status + venue-fit note.
- **Acceptance:** every checklist item satisfied or explicitly waived with reason.
- **Verify:** checklist reviewed by a second pass.
- **Evidence:** checklist path; `memory.md` §21.

---

## 11. Next Actions

1. **T-010** then **T-013** — verify the literature map and search the candidate novelty (critical path: novelty decides the framing).
2. **T-012** — settle compute feasibility early; it bounds the whole matrix.
3. **T-020/T-021** — begin dataset scouting in parallel, since dataset access is an early external dependency and can force a domain change.

PH-0 is closed; T-004 is complete. No task is currently `IN_PROGRESS`.

## 12. Definition of Done

A task is **Done** when all of the following hold:

1. The expected output exists at a recorded path or run ID.
2. The stated acceptance criteria are checked off individually (not in aggregate).
3. The stated verification method was executed, and its result is recorded.
4. Evidence is linked in this file (path, run ID, or document section).
5. `memory.md` was updated if the task produced a decision, result, or lesson.
6. No rule in `rules.md` is violated by the way the task was performed.

A phase is **Done** only when all its tasks are Done **or** an explicit, justified exception is approved and recorded in `memory.md` (`rules.md` §G2).
