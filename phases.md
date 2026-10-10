# phases.md — Project Roadmap

**Project:** KD-Edge-TinyML (see `prd.md` §1)

**Document role:** `phases.md` defines the order of work, dependencies, milestones, deliverables, risks, and exit criteria. Phase completion is governed by `rules.md` §G. Status values: `NOT_STARTED` | `IN_PROGRESS` | `BLOCKED` | `COMPLETED`. No dates are invented; scheduling happens only after an actual plan is approved.

**Status legend:** all phases start `NOT_STARTED` except PH-0, which is `COMPLETED` (2026-10-10: source read, seven files created, cross-check executed).

---

## Phase Overview

| Phase | Objective | Status | Depends on |
|---|---|---|---|
| PH-0 | Source inspection and project setup | `COMPLETED` (2026-10-10) | — |
| PH-1 | Literature verification and novelty assessment | `NOT_STARTED` | PH-0 |
| PH-2 | Dataset and task definition | `NOT_STARTED` | PH-0 (parallel with PH-1 allowed) |
| PH-3 | Baseline implementation | `NOT_STARTED` | PH-1, PH-2 |
| PH-4 | Knowledge-distillation experiments | `NOT_STARTED` | PH-3 |
| PH-5 | Quantization experiments | `NOT_STARTED` | PH-3 (parallel with PH-4 allowed) |
| PH-6 | Software resource and efficiency evaluation | `NOT_STARTED` | PH-4, PH-5 |
| PH-7 | Robustness and statistical analysis | `NOT_STARTED` | PH-4, PH-5 |
| PH-8 | Reproducibility and model selection | `NOT_STARTED` | PH-6, PH-7 |
| PH-9 | Final analysis and research-paper preparation | `NOT_STARTED` | PH-8 |

---

## PH-0 — Source Inspection and Project Setup

- **Objective:** Establish the documentation foundation: read the primary source, understand the workspace, create the seven coordinated files, and record missing inputs and initial decisions.
- **Tasks:** T-001, T-002, T-003, T-004, T-005 (see `task.md`).
- **Dependencies:** none.
- **Deliverables:** the seven Markdown files; source-document provenance record (path, hash, extraction notes); initial decision log (`memory.md`); unresolved-decision list (U-01…U-12).
- **Acceptance criteria:**
  - [x] Source document located and read in full (SHA256 recorded, `memory.md` §3).
  - [x] Workspace inspected; empty project folder identified as documentation home.
  - [x] Research direction, seven gaps, six RQs represented in the seven files.
  - [x] Status labels applied; nothing proposed marked completed.
  - [x] Cross-check of all seven files for ID consistency executed and recorded (`memory.md` §21).
- **Exit criteria:** cross-check checklist (below) passes; missing information recorded; no fake citations/measurements; tasks align with phases; requirements align with goals; architecture aligns with RQs.
- **Potential blockers:** none identified. Missing inputs are recorded as U-01…U-12 rather than blockers.
- **Evidence required:** this file + `memory.md` §1/§3/§21 + `task.md` status rows.

## PH-1 — Literature Verification and Novelty Assessment

- **Objective:** Independently verify that the research gaps and the proposed contribution (uncertainty-gated KD × mixed-precision quantization × agricultural edge forecasting) remain open, and re-scope if they do not.
- **Tasks:** T-010…T-016.
- **Dependencies:** PH-0.
- **Deliverables:** documented search procedure (databases, queries, dates, inclusion criteria); verified/annotated literature map; closest-competitor analysis; novelty memo; refined RQs/hypotheses.
- **Acceptance criteria:**
  - [ ] All 54 source-report records checked for existence and relevance (errors annotated).
  - [ ] Priority papers (report's "read first" list) read and summarized with method/baseline/metric extraction.
  - [ ] Targeted searches for: uncertainty/reliability-gated KD in time-series; KD × quantization on MCUs; agricultural time-series forecasting on edge; multi-teacher foundation-model distillation.
  - [ ] Explicit point-by-point comparison against the 3 closest competitors.
- **Exit criteria:** literature evidence recorded in `memory.md` §9; novelty risks documented; RQs refined if needed; **no unsupported novelty claim remains**; if novelty is blocked, a re-scope proposal is recorded in `memory.md` §7.
- **Potential blockers:** paywalls; rapid 2026 literature churn (searches must be dated and refreshed before submission).
- **Evidence required:** search log + annotated bibliography + novelty memo.

## PH-2 — Dataset and Task Definition

- **Objective:** Select the agricultural time-series dataset (DST-01), define the prediction task and the domain-shift construction, and lock the evaluation protocol before any training.
- **Tasks:** T-020…T-026.
- **Dependencies:** PH-0 (can run in parallel with PH-1; novelty re-scope may still change the domain).
- **Deliverables:** dataset selection record (criteria, license, provenance, checksum); task definition (target variable, lookback, horizon); split and domain-assignment protocol; preprocessing spec; data-quality/limitations report.
- **Acceptance criteria:**
  - [ ] Candidate datasets evaluated against DST-R1…DST-R5 (`prd.md` §16).
  - [ ] License and access verified; recorded.
  - [ ] Chronological + site/season holdout splits specified; leakage check implemented and negative-tested.
  - [ ] Metrics finalized (MET-03/MET-06 choices resolved or explicitly deferred).
- **Exit criteria:** dataset and task justified in `memory.md` §10; evaluation protocol specified; splitting strategy documented; unresolved dataset risks recorded.
- **Potential blockers:** no dataset with real multi-site/season variation (→ RQ2/RQ5 limitation recorded; synthetic shift only, labeled).
- **Evidence required:** dataset manifest + split config + protocol document section.

## PH-3 — Baseline Implementation

- **Objective:** Build the reproducible experimental skeleton and establish all baselines required before any KD/quantization claim.
- **Tasks:** T-030…T-035.
- **Dependencies:** PH-1, PH-2.
- **Deliverables:** repository skeleton with pinned environment; experiment orchestrator (C-01) and registry (C-08); teacher baselines (conventional + ≥1 foundation model) evaluated; student no-KD baselines across families/capacities; reproducibility proof (one re-run matched within tolerance).
- **Acceptance criteria:**
  - [ ] FR-007, FR-008 baselines exist with recorded metrics and footprint.
  - [ ] Teacher uncertainty availability resolved (U-05) or teacher excluded with reason.
  - [ ] One baseline re-run reproduces within stated tolerance (REP-004 preliminary).
- **Exit criteria:** baseline runs reproducible from stored configs; artifacts and evaluation records exist; baseline limitations documented.
- **Potential blockers:** compute for teacher training (U-10); export/toolchain issues surfacing late.
- **Evidence required:** run registry entries + baseline comparison table.

## PH-4 — Knowledge-Distillation Experiments

- **Objective:** Compare distillation strategies in-domain and under domain shift; test uncertainty/reliability gating with ablations.
- **Tasks:** T-040…T-046.
- **Dependencies:** PH-3.
- **Deliverables:** KD engine (KD-0…KD-3); uncertainty module and gating (KD-4, if retained); EXP-003, EXP-005, EXP-006 results; ablation dossier including failures.
- **Acceptance criteria:**
  - [ ] KD comparisons share identical cached teacher signals, splits, and budgets.
  - [ ] Gating ablation isolates the gate (g ≡ 1 vs learned/configured g).
  - [ ] In-domain and shifted-domain results reported separately (FR-023).
- **Exit criteria:** distillation comparisons reproducible; RQ1, RQ2 and relevant parts of RQ5 have sufficient evidence **or explicit documented limitations**.
- **Potential blockers:** no usable teacher uncertainty signal (RK-3); PH-1 finding that KD-4 is already published (→ re-scope per `memory.md` §7).
- **Evidence required:** EXP-003/005/006 run records + analysis tables.

## PH-5 — Quantization Experiments

- **Objective:** Quantify PTQ/QAT effects on the accuracy–footprint frontier and their interaction with KD.
- **Tasks:** T-050…T-055.
- **Dependencies:** PH-3 (parallel with PH-4 allowed; EXP-009 needs both).
- **Deliverables:** quantization pipeline with correctness checks; EXP-007, EXP-008, EXP-009 results; toolchain constraint report (bit widths, per-channel support, unsupported ops).
- **Acceptance criteria:**
  - [ ] FP32 reference established for every quantized comparison.
  - [ ] PTQ vs QAT compared at matched bit width and protocol.
  - [ ] Quantization settings recorded per run (REP-005).
- **Exit criteria:** quantization experiments documented; RQ3 has sufficient evidence or explicit limitations (including any unsupported regimes).
- **Potential blockers:** QAT compute cost; missing INT4 support (U-09).
- **Evidence required:** quantized-vs-reference delta tables + settings records.

## PH-6 — Software Resource and Efficiency Evaluation

- **Objective:** Measure deployment costs in the target software runtime and compare them against theoretical indicators.
- **Tasks:** T-060…T-066.
- **Dependencies:** PH-4, PH-5 (needs the candidate model set).
- **Deliverables:** target runtime + environment decision (U-07/U-12); export path (C-09); benchmark harness with documented methodology (C-10); EXP-004, EXP-010, EXP-011 measurement data; energy estimate with stated method, or an explicit unavailability statement.
- **Acceptance criteria:**
  - [ ] Measurement methodology documented before any number is reported (`rules.md` §D).
  - [ ] Measured vs estimated separated in the registry (NFR-008).
  - [ ] Theory-vs-measured correlation analysis produced (RQ4).
- **Exit criteria:** measurement methods documented; measurements in the target runtime separated from estimates; RQ4 and relevant parts of RQ6 have evidence or documented limitations.
- **Potential blockers:** no target runtime/benchmark environment (RK-4); no energy estimator (RK-5); export incompatibility (RK-7).
- **Evidence required:** raw measurement logs + environment/runtime records + correlation report.

## PH-7 — Robustness and Statistical Analysis

- **Objective:** Move beyond mean accuracy: multi-seed variation, error distributions, worst-domain behavior, calibration, failure analysis, and justified statistics.
- **Tasks:** T-070…T-073.
- **Dependencies:** PH-4, PH-5.
- **Deliverables:** multi-seed run set (target 3–5 seeds for critical comparisons; minimum 2, `TO_VERIFY`); failure-case dossier; statistical analysis report with pre-declared tests and effect sizes.
- **Acceptance criteria:**
  - [ ] All seeds reported; none dropped without recorded reason.
  - [ ] Worst-domain and percentile error statistics present (FR-024).
  - [ ] Statistical methods named before results were seen (FR-034).
- **Exit criteria:** robustness evidence documented; statistical methods justified; negative/inconclusive results retained.
- **Potential blockers:** compute for repeated seeds (U-10).
- **Evidence required:** run registry seed sets + analysis report.

## PH-8 — Reproducibility and Model Selection

- **Objective:** Consolidate the framework into reproducible comparisons and produce budget-indexed Pareto selection.
- **Tasks:** T-080…T-084.
- **Dependencies:** PH-6, PH-7.
- **Deliverables:** artifact-completeness audit; reproduction re-run results (REP-004); Pareto frontiers with knee points and confidence bands (EXP-011, EXP-014); documented selection rationale per budget (32/64/128/256 KB-class).
- **Acceptance criteria:**
  - [ ] Every frontier point traces to a run ID with config and artifacts (NFR-004).
  - [ ] Reproduction deltas within stated tolerance, or failures documented.
  - [ ] Selected configuration per budget justified against measured evidence.
- **Exit criteria:** comparisons traceable; reproduction checks documented; RQ6 has evidence or explicit limitations.
- **Potential blockers:** incomplete artifacts discovered in audit (→ repair loop); tolerance too tight for available compute (→ adjust with recorded justification).
- **Evidence required:** frontier plots/tables + reproduction delta table + audit report.

## PH-9 — Final Analysis and Research-Paper Preparation

- **Objective:** Consolidate findings into an evidence-traceable paper draft with honest limitations.
- **Tasks:** T-090…T-095.
- **Dependencies:** PH-8.
- **Deliverables:** results consolidation mapped to RQ1–RQ6; comparison to related work; threats-to-validity section; figures/tables generated from registry data; methods/results/discussion drafts; reproducibility statement and artifact package (REP-007); venue-fit check.
- **Acceptance criteria:**
  - [ ] Every claim links to an artifact or is qualified.
  - [ ] Novelty statement satisfies `prd.md` §28.
  - [ ] Figures/tables contain no hand-typed numbers.
  - [ ] IEEE submission checklist from the source report passed (incl. template/scope/page-limit check at submission time).
- **Exit criteria:** every research claim supported or appropriately qualified; results traceable; limitations explicit; paper draft ready for internal review — subject to the actual strength of the evidence; **publication is not guaranteed**.
- **Potential blockers:** weak evidence for the gating contribution → pivot to benchmark/decision-framework framing (report's sanctioned alternatives).
- **Evidence required:** draft manuscript + figure sources + reproducibility package.

---

## Cross-Check Checklist (PH-0 exit)

Executed after all seven files are written; results recorded in `memory.md` §21.

- [ ] All seven files exist with substantive content.
- [ ] All 7 gaps, 6 RQs represented; traceability table complete.
- [ ] No proposed work labeled `COMPLETED`; no fabricated citations/measurements.
- [ ] ID scheme consistent (FR/NFR/REP/EXP/MET/C/GAP/RQ/G/PH/T/D/U).
- [ ] Tasks ↔ phases ↔ goals ↔ requirements align (spot-checked via ID grep).
- [ ] Unresolved decisions U-01…U-12 visible in `architecture.md` §22 and `memory.md` §8.
