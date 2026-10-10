# goal.md — Long-Term Project Objectives

**Project:** KD-Edge-TinyML (see `prd.md` §1)

**Document role:** `goal.md` defines intended outcomes and the conditions required to reach them. Goals are distinct from guaranteed outcomes: **publication, novelty, and superior performance are not guaranteed** (`prd.md` §28, `rules.md` §B9). Update this file when a goal is achieved, blocked, or legitimately revised (`rules.md` §E7).

Status values: `NOT_STARTED` | `IN_PROGRESS` | `BLOCKED` | `ACHIEVED` | `REVISED`. Thresholds that the source report does not establish are left as `TO_VERIFY` with a statement of how they will be determined — never invented.

---

## Primary Goal

**G-001 — Primary research goal** *(status: `IN_PROGRESS` — documentation foundation only; no experimental work yet)*

- **Description:** Develop and evaluate a reproducible research framework that investigates the transfer of useful foundation-model knowledge into compact, quantized deployment models (including resource-constrained deployment targets) under realistic software resource budgets and domain shift.
- **Why it matters:** It is the project's reason to exist; everything else is instrumental.
- **Related RQs:** RQ1–RQ6 (all).
- **Related requirements:** FR-001…FR-035, NFR-001…NFR-010, REP-001…REP-007.
- **Success criteria:** (1) framework runs registered experiments reproducibly; (2) ≥1 software-measured Pareto frontier exists with traceable points (`D-006`); (3) each core RQ has evidence or a documented limitation; (4) documentation remains consistent throughout.
- **Dependencies:** all phases PH-0…PH-9.
- **Evidence required:** the run registry + final analysis pack (PH-8/PH-9).
- **Scope lock:** the exact domain and method remain consistent with SRC-01 and approved decisions; any change requires a `memory.md` decision record.

---

## Research Goals

**G-002 — Literature and novelty validation** *(status: `NOT_STARTED`)*

- **Description:** Independently verify that the seven gaps and the candidate contribution remain open; re-scope if not.
- **Why it matters:** Novelty is the single largest project risk (report's "Important novelty warning").
- **RQs:** all (refinement). **Requirements:** PH-1 acceptance criteria in `phases.md`.
- **Success criteria:** documented search procedure; 54 records verified; priority papers read; point-by-point comparison with ≥3 closest works; no unsupported novelty claim remains.
- **Dependencies:** PH-0. **Evidence:** search log + novelty memo in `memory.md` §9.
- **Threshold note:** "closest works" list is drawn from SRC-01's priority list; it must be extended if searches surface closer work — no fixed numeric novelty threshold exists.

**G-003 — Reproducible baselines** *(status: `NOT_STARTED`)*

- **Description:** Establish teacher and student (no-KD) baselines that reproduce from stored configs.
- **Why it matters:** Every later claim is relative to these; unfair baselines invalidate results (`rules.md` §C1).
- **RQs:** RQ1, RQ2. **Requirements:** FR-007, FR-008, FR-011, REP-001, REP-002.
- **Success criteria:** baselines registered with configs/hashes/seeds; one re-run within stated tolerance (tolerance `TO_VERIFY`); limitations documented.
- **Dependencies:** PH-1, PH-2. **Evidence:** registry entries + baseline comparison table.

**G-004 — Distillation evaluation** *(status: `NOT_STARTED`)*

- **Description:** Compare distillation targets (none, logit/forecast, feature, temporal-relation, uncertainty-gated), in-domain and under domain shift.
- **Why it matters:** Directly answers RQ1, RQ2, and part of RQ5; hosts the candidate contribution.
- **RQs:** RQ1, RQ2, RQ5. **Requirements:** FR-012–FR-017, EXP-003, EXP-005, EXP-006.
- **Success criteria:** KD comparisons share identical teacher signals/splits/budgets; gating ablation isolates the gate; per-domain results reported; failures retained.
- **Dependencies:** PH-3. **Evidence:** EXP-003/005/006 run records + analysis tables.
- **Threshold note:** the "material improvement" margin for gating (H-RQ5a/H-RQ5b) is `TO_VERIFY` and will be fixed before PH-4 runs, then recorded as a decision.

**G-005 — Quantization evaluation** *(status: `NOT_STARTED`)*

- **Description:** Quantify FP16/INT8 PTQ/INT8 QAT (and mixed precision where supported) effects and their interaction with KD.
- **Why it matters:** Answers RQ3; determines whether the frontier's compression axis is usable in the target runtime.
- **RQs:** RQ3. **Requirements:** FR-018–FR-022, EXP-007–EXP-009, REP-005.
- **Success criteria:** FP32 reference for every comparison; PTQ-vs-QAT at matched bit width; settings recorded; unsupported regimes reported not skipped.
- **Dependencies:** PH-3. **Evidence:** delta tables vs reference + settings records.

**G-006 — Runtime-efficiency evaluation (software-measured)** *(status: `NOT_STARTED`)*

- **Description:** Measure latency and process memory in the target runtime (plus artifact size and an energy estimate if derivable) and test how well theoretical indicators predict them.
- **Why it matters:** RQ4 exists because proxies mislead; the frontier is only credible if measured.
- **RQs:** RQ4, RQ6. **Requirements:** FR-026–FR-031, EXP-004, EXP-010, EXP-011.
- **Success criteria:** methodology documented before reporting; measured vs estimated separated; correlation analysis (Spearman/Pearson) produced; no compatibility claim without a recorded run in that runtime.
- **Dependencies:** PH-4, PH-5. **Evidence:** raw measurement logs + correlation report.
- **Fallback (documented limitation):** without a target runtime or an energy estimator, RQ4 is partially answered from FLOPs/params and labelled estimates (`prd.md` §14 RK-4/RK-5). This is a legitimate outcome, not a hidden failure.

**G-007 — Robustness evaluation** *(status: `NOT_STARTED`)*

- **Description:** Evaluate variation, worst-domain behavior, error distributions, calibration, and failure cases across seeds.
- **Why it matters:** RQ5 and GAP-5 require going beyond mean accuracy.
- **RQs:** RQ2, RQ5. **Requirements:** FR-024, FR-032–FR-034, EXP-006, EXP-012.
- **Success criteria:** ≥2 seeds (target 3–5) for critical comparisons with all seeds reported; percentile/worst-domain statistics; failure dossier; pre-declared statistical tests.
- **Dependencies:** PH-4, PH-5. **Evidence:** seed set + analysis report.
- **Threshold note:** seed count is bounded by compute (U-10) and is recorded as a limitation if below target.

**G-008 — Reproducibility and model selection** *(status: `NOT_STARTED`)*

- **Description:** Consolidate runs into reproduccible comparisons and produce budget-indexed Pareto selection.
- **Why it matters:** This *is* the deliverable the report calls the most defensible gap (GAP-6).
- **RQs:** RQ6. **Requirements:** REP-001–REP-007, NFR-002, NFR-004, EXP-011, EXP-013, EXP-014.
- **Success criteria:** artifact audit passes; reproduction deltas within stated tolerance or documented; each budget class (32/64/128/256 KB-class, `TO_VERIFY` calibration) has a justified selected configuration.
- **Dependencies:** PH-6, PH-7. **Evidence:** frontier plots/tables + delta table + audit.

**G-009 — Research-paper preparation** *(status: `NOT_STARTED`)*

- **Description:** Consolidate findings into an evidence-traceable paper draft with explicit limitations, following the report's proposed structure.
- **Why it matters:** It is the publication vehicle; it is also where overclaiming does the most damage.
- **RQs:** all. **Requirements:** PH-9 criteria, `prd.md` §28, `rules.md` §B.
- **Success criteria:** every claim traced to an artifact or qualified; figures/tables generated from the registry; threats-to-validity section complete; reproducibility package ready; IEEE submission checklist passed.
- **Dependencies:** PH-8. **Evidence:** draft manuscript + figure sources + package.
- **Explicit non-guarantee:** acceptance, novelty, and superior performance are not goals that can be promised; the goal is a defensible, honest submission if the evidence supports one.

---

## Technical Goals

| ID | Technical goal | Success criterion | Status |
|---|---|---|---|
| G-T1 | Maintainable codebase with separated responsibilities | `NFR-001` module-boundary check passes; new adapter added without core changes | `NOT_STARTED` |
| G-T2 | Config-driven, reproducible experiments | Every run maps to one stored config (NFR-002); REP-001 dry run passes | `NOT_STARTED` |
| G-T3 | Systematic artifact/result recording | Traceability spot-check on 3 random results passes (NFR-004) | `NOT_STARTED` |
| G-T4 | Extensibility to new models/datasets | Dummy adapter test passes (NFR-003) | `NOT_STARTED` |
| G-T5 | Design realistic for available resources | Every phase's compute need fits available compute (U-10), or scope is reduced with a recorded decision | `NOT_STARTED` |

## Research-Integrity Goals

| ID | Integrity goal | Success criterion | Status |
|---|---|---|---|
| G-I1 | No unsupported novelty claims | `prd.md` §28 conditions all satisfied at submission time | `NOT_STARTED` |
| G-I2 | No data leakage | Automated leakage checks implemented and negative-tested; no test-based selection | `NOT_STARTED` |
| G-I3 | No fabricated metrics | Every reported number traces to a run ID | `NOT_STARTED` |
| G-I4 | Negative findings reported | Failure records present for every failed configuration | `NOT_STARTED` |
| G-I5 | Transparent limitations | Threats-to-validity section complete in PH-9 | `NOT_STARTED` |
| G-I6 | Estimates separated from measurements | `measurement_type` present on all reported values | `NOT_STARTED` |

---

## Goal Hierarchy and Mapping

| Goal | Depends on | Blocks | Primary phases | Primary tasks |
|---|---|---|---|---|
| G-001 | all | — | PH-0…PH-9 | all |
| G-002 | G-001 (docs) | G-003, G-004 framing | PH-1 | T-010…T-016 |
| G-003 | G-002, PH-2 | G-004, G-005 | PH-3 | T-030…T-035 |
| G-004 | G-003 | G-006, G-007 | PH-4 | T-040…T-046 |
| G-005 | G-003 | G-006, G-007 | PH-5 | T-050…T-055 |
| G-006 | G-004, G-005 | G-008 | PH-6 | T-060…T-066 |
| G-007 | G-004, G-005 | G-008 | PH-7 | T-070…T-073 |
| G-008 | G-006, G-007 | G-009 | PH-8 | T-080…T-084 |
| G-009 | G-008 | — | PH-9 | T-090…T-095 |

## Relationship to Requirements and RQs

- Goals ↔ requirements: see the traceability table in `prd.md` §15 (goal column).
- Every core requirement maps to at least one goal; if a requirement has no goal, either the goal set or the requirement is wrong — resolve before PH-1.
- Every RQ appears in at least one goal (RQ1→G-003/G-004, RQ2→G-004/G-007, RQ3→G-005, RQ4→G-006, RQ5→G-004/G-007, RQ6→G-006/G-008).
