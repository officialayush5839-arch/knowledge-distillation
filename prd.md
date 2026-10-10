# prd.md — Product Requirements Document

**Project:** Uncertainty-Gated Distillation and Mixed-Precision Quantization of Time-Series Foundation Models for Resource-Constrained Agricultural Forecasting *(working title — `PROPOSED`, see D-003)*

**Document role:** `prd.md` defines *what* the research system must accomplish and *why*. It is one of seven coordinated files (see `rules.md` §A for the source-of-truth order).

| Field | Value |
|---|---|
| Version | 0.1 (initial documentation foundation) |
| Status | Documentation created; no experimental work performed |
| Primary source | `IEEE_Knowledge_Distillation_Edge_Literature_Gap_Report (1).docx` (search date 30 Sep 2026; SHA256 `b2ec98f3db088113e2d9793609ac433fda026db16dd57db3d71deb308f49ce87`) |
| Related files | `architecture.md`, `rules.md`, `phases.md`, `memory.md`, `goal.md`, `task.md` |

**Status labels used throughout:** `DECIDED` (approved), `COMPLETED` (performed and verified), `PROPOSED` (planned, not implemented), `ASSUMPTION` (working assumption, needs confirmation), `TO_VERIFY` (requires investigation before it may be relied on).

---

## 1. Project Title

**Working title (revised for the software-only scope, `D-006`):** *Uncertainty-Gated Distillation and Mixed-Precision Quantization of Time-Series Foundation Models for Resource-Constrained Agricultural Forecasting.*

Short name: **KD-Edge-TinyML** (retained for ID stability; it does not imply hardware measurement — `D-006`). Title is provisional (`PROPOSED`); final title depends on the verified contribution (see §28).

---

## 2. Executive Summary

Large time-series foundation models now forecast well, but they cannot meet the strict size, memory, and latency budgets of the constrained deployments used for agricultural sensing (soil moisture, temperature, humidity, weather, irrigation telemetry). This project builds a **reproducible research framework** that studies how much of a teacher model's useful knowledge can be transferred into a compact student model, then compressed by quantization, and still behave reliably under explicit software resource budgets in a reproducible benchmarking environment.

The intended scientific output is not "one best model" but a **software-measured, domain-shift-aware Pareto frontier** relating predictive quality to model size, peak process memory, latency, estimated energy (labelled as an estimate), and robustness under domain shift, plus — if the evidence supports it — an uncertainty-gated distillation method evaluated against that frontier.

The immediate deliverable of this document set is the documentation foundation itself (`PH-0`). **No experiments, literature verification, or novelty claims have been completed at this stage.**

---

## 3. Research Problem

Resource-constrained deployments require models that (a) fit in tight size/memory budgets (tens-to-hundreds of KB of parameters and serialized artifacts), (b) meet latency budgets in the target runtime, and (c) remain reliable when field conditions differ from the data a large teacher model was trained on. Knowledge distillation (KD) and quantization are the standard compression tools, but the source report indicates they are usually studied **separately, on conventional benchmarks, with one student, one hardware target, and limited deployment measurement** (report §"Most defensible research gap"; `TO_VERIFY` against current literature in `PH-1`).

The research problem is therefore:

> How can we systematically and reproducibly determine, under explicit edge-resource budgets and domain shift, which distillation target and quantization strategy yields a student model whose predictive behavior is *reliable* — not merely accurate on average — when measured in a reproducible software environment?

---

## 4. Background and Motivation

Extracted from the source report (all `TO_VERIFY` until independently confirmed in `PH-1`):

- KD and quantization are often evaluated separately or on conventional benchmarks.
- Foundation-model distillation for a specific agricultural/health edge task is frequently demonstrated with one student, one hardware target, and limited deployment measurements.
- Agricultural sensor distributions change by field, season, sensor, and weather regime: a teacher can be globally strong yet locally misaligned (Gap 2).
- Parameters and FLOPs are not substitutes for measured latency, memory, model size, and energy (Gap 4; measured here in software, `D-006`).
- Several 2025–2026 papers already combine KD with quantization, agricultural deployment, medical foundation models, or time-series foundation models; a naive combination is unlikely to be sufficient novelty (report §"Important novelty warning").
- IEEE acceptance cannot be guaranteed by any plan; it depends on novelty, rigor, reproducibility, writing, and reviewer fit (report §"Executive conclusion").

**Motivation:** the practical value is a decision framework: *given a resource budget (e.g., 32/64/128/256 KB) and a deployment domain, which compression configuration should be chosen, and on what measured evidence?*

---

## 5. Target Users and Stakeholders

| ID | Stakeholder | Need |
|---|---|---|
| STK-1 | Student researcher / project owner | A reproducible, phased path from question to evidence to paper draft |
| STK-2 | Future AI coding agents | Stable IDs, explicit decisions, unambiguous next actions (`memory.md`, `task.md`) |
| STK-3 | Paper reviewers / readers | Traceable claims, honest limitations, resource-grounded numbers |
| STK-4 | Resource-constrained deployment practitioners | Pareto data and deployment artifacts for their target runtime |
| STK-5 | Reproducing third parties | Released code, configs, hashes, benchmark scripts |

---

## 6. Research Objectives

| ID | Objective | Type |
|---|---|---|
| RO-1 | Quantify how much teacher knowledge a compact student retains under explicit memory/latency budgets (RQ1) | Testable |
| RO-2 | Determine which distillation targets best preserve performance under domain shift (RQ2) | Testable |
| RO-3 | Characterize the interaction of KD with PTQ and QAT (RQ3) | Testable |
| RO-4 | Measure how well FLOPs/parameter count predict measured software latency, memory, and energy estimates (RQ4) | Testable |
| RO-5 | Test whether uncertainty/reliability-aware gating reduces failures under teacher mismatch (RQ5) | Testable |
| RO-6 | Build a reproducible benchmarking framework that identifies Pareto-efficient students across budgets (RQ6) | Testable |
| RO-7 | Investigate all seven research-gap directions to the extent resources permit | Partly non-testable research objective (Gap 7 may be infeasible; see §11) |
| RO-8 | Produce a reproducible artifact package and, if evidence justifies it, a paper-ready evidence base | Partly non-testable research objective (publication not guaranteed) |

---

## 7. Research Questions (RQ1–RQ6)

Wording preserved from the master specification, aligned with the report's IEEE-style RQ list.

| ID | Research question |
|---|---|
| **RQ1** | How much useful knowledge from a foundation-model teacher can a compact student retain while satisfying realistic memory and inference-latency constraints? |
| **RQ2** | Which distillation targets or strategies best preserve student performance when the teacher's training domain and the student's target deployment domain differ? |
| **RQ3** | How do PTQ and QAT interact with knowledge distillation in terms of predictive error, model size, memory requirements, and deployment efficiency? |
| **RQ4** | How accurately do theoretical indicators such as FLOPs and parameter count predict measured software inference latency, process memory usage, and estimated energy in the target software environment? |
| **RQ5** | Can uncertainty-aware or reliability-aware distillation reduce predictive failures when teacher knowledge is unreliable or mismatched with the target domain? |
| **RQ6** | Can a reproducible benchmarking framework identify Pareto-efficient student models across different resource budgets? |

### 7.1 Detailed RQ specification

Each RQ lists: problem → gap link → hypothesis (`PROPOSED`, not a conclusion) → independent variables → dependent variables → baselines → datasets → experiments → metrics → statistical analysis → evidence needed → conditions for remaining unanswered.

---

#### RQ1 — Knowledge retention under edge constraints

- **Problem:** It is unknown how much accuracy a student gives up once it must fit a stated software resource budget.
- **Gaps:** GAP-1, GAP-4, GAP-6.
- **Hypotheses (`PROPOSED`):** H-RQ1a: a distilled student retains a measurable fraction of teacher performance at a fixed budget compared with a same-size non-distilled student (retention fraction reported, threshold `TO_VERIFY`). H-RQ1b: retention degrades monotonically as the size/memory budget tightens.
- **Independent variables:** student architecture family; student capacity; presence/absence and type of distillation; resource budget level.
- **Dependent variables:** MET-01/02/05 (error), MET-08/09/10 (serialized size, peak process memory, artifact size on disk), MET-12 (latency).
- **Baselines:** non-distilled student of equal capacity (mandatory, set *before* evaluating KD — `rules.md` §C); conventional teacher; direct-naive compression of the teacher (where deployable, else documented as infeasible).
- **Datasets:** selected agricultural time-series dataset (DST-01, `TO_VERIFY`), source-domain split.
- **Experiments:** EXP-001, EXP-002, EXP-003, EXP-011.
- **Metrics:** MET-01, MET-02, MET-07–MET-10, MET-12, MET-13, MET-16.
- **Statistical analysis:** repeated seeds where feasible (≥2, target 3–5 `TO_VERIFY`); bootstrap CIs on test error; report dispersion, not only means.
- **Evidence needed:** reproducible runs with configs/hashes; runtime measurements for the deployed subset.
- **May remain unanswered if:** no student fits the target runtime's budget, or training compute is insufficient to train teachers.

---

#### RQ2 — Distillation under domain shift

- **Problem:** Teacher trained on source domain (fields/seasons/sites A) may not transfer to target domain (held-out field/season B).
- **Gaps:** GAP-2, GAP-5.
- **Hypotheses (`PROPOSED`):** H-RQ2a: feature- or temporal-relation-based targets degrade less than logit/forecast-only matching under domain shift; H-RQ2b: all KD strategies lose performance under shift relative to in-domain, and the loss differs significantly across strategies.
- **Independent variables:** distillation target (none / logit-forecast / feature / temporal-relation / uncertainty-gated); domain relationship (in-domain vs held-out site/season); shift severity.
- **Dependent variables:** in-domain error; shifted-domain error (MET-05); worst-group error; error-distribution tails.
- **Baselines:** non-distilled student in both domains; teacher performance in both domains (upper reference, not deployable).
- **Datasets:** DST-01 with a documented domain-split protocol (site/season held out; chronology respected).
- **Experiments:** EXP-003, EXP-005, EXP-006.
- **Metrics:** MET-01, MET-02, MET-05, MET-16; calibration metrics (MET-06, choice `TO_VERIFY`).
- **Statistical analysis:** paired comparisons per held-out domain; effect sizes; CIs.
- **Evidence needed:** split protocol documented in configs; per-domain results table.
- **May remain unanswered if:** no multi-site/multi-season dataset with real domain variation can be obtained (→ record limitation; synthetic shift only, labeled as such).

---

#### RQ3 — Interaction between distillation and quantization

- **Problem:** KD and quantization may interfere or complement each other; their effects are rarely separated.
- **Gaps:** GAP-3.
- **Hypotheses (`PROPOSED`):** H-RQ3a: QAT recovers more predictive quality than PTQ at INT8 but costs more training compute; H-RQ3b: KD applied *before* quantization shifts the accuracy–footprint frontier relative to quantizing a non-distilled student; H-RQ3c: bit-width effects interact with student capacity (smaller students are more quantization-sensitive). Report cites QKD as evidence interference exists (`TO_VERIFY`).
- **Independent variables:** quantization regime (none / FP16 / INT8-PTQ / INT8-QAT / mixed INT8-INT4 where the target runtime supports it); distillation (none vs selected KD); student capacity.
- **Dependent variables:** predictive error change vs FP32 reference; model size; peak process memory; latency; export/run success in the target runtime.
- **Baselines:** FP32 reference of the same student; quantized teacher where applicable.
- **Datasets:** DST-01, primary split.
- **Experiments:** EXP-007, EXP-008, EXP-009.
- **Metrics:** MET-01, MET-02, MET-08, MET-09, MET-10, MET-12, MET-14 (if available).
- **Statistical analysis:** paired per-window comparisons quantized vs reference; report deltas with CIs.
- **Evidence needed:** exact quantization settings (bit width, per-channel/per-tensor, calibration set) recorded per run (REP-005).
- **May remain unanswered if:** toolchain does not support INT4 in the chosen runtime or QAT exceeds compute budget (→ document supported subset).

---

#### RQ4 — Resource-realistic efficiency (software-measured)

- **Problem:** FLOPs/params are commonly used as efficiency proxies without validation against measured software behaviour.
- **Gaps:** GAP-4, GAP-7.
- **Hypotheses (`PROPOSED`):** H-RQ4a: FLOPs/param count correlate with measured latency only moderately in the selected runtime (correlation value `TO_VERIFY`, not prespecified); H-RQ4b: rank ordering of models by FLOPs differs from rank ordering by measured latency for at least one model family.
- **Independent variables:** model family/capacity/precision; target software environment (OS, library/runtime versions, CPU or GPU).
- **Dependent variables:** measured latency (MET-12), throughput (MET-13), peak process memory (MET-09), serialized size (MET-10), energy estimate (MET-14, labelled estimate only); theoretical MET-11.
- **Baselines:** theoretical estimates (FLOPs/params) for every measured model.
- **Datasets:** inference traces of fixed shape/length (input shape documented).
- **Experiments:** EXP-004, EXP-010.
- **Metrics:** MET-07, MET-09–MET-14.
- **Statistical analysis:** Spearman rank correlation and Pearson correlation between estimates and measurements; report measurement variance over repetitions.
- **Evidence needed:** measurement methodology documented (warm-up, repetitions, units, clock/power settings) per `rules.md` §D.
- **May remain unanswered if:** no target runtime or energy estimator is available (→ only FLOPs/params, explicitly labeled; RQ4 partially answered).

---

#### RQ5 — Reliability-aware distillation

- **Problem:** When the teacher is wrong for the target field/season, blind matching transfers error.
- **Gaps:** GAP-2, GAP-5 (and GAP-7 partially).
- **Hypotheses (`PROPOSED`):** H-RQ5a: uncertainty-gated distillation (weighting the KD loss by teacher reliability) reduces worst-domain error and failure-tail severity versus ungated KD; H-RQ5b: gating does not materially degrade in-domain error (non-inferiority margin `TO_VERIFY`).
- **Independent variables:** gating strategy (none / teacher-uncertainty-weighted / reliability-gated); level of teacher–target mismatch; uncertainty estimation method.
- **Dependent variables:** worst-domain error (MET-05); tail error statistics (e.g., 95th-percentile absolute error); calibration (MET-06); failure count/severity.
- **Baselines:** ungated KD (same target, same λ); non-distilled student; oracle gate (upper reference, computed post-hoc).
- **Datasets:** DST-01 with source/target domain construction; per-window teacher reliability labels computed on held-out data.
- **Experiments:** EXP-005, EXP-006, EXP-012.
- **Metrics:** MET-01, MET-02, MET-05, MET-06, MET-16; tail-error percentiles.
- **Statistical analysis:** paired per-window tests on failure subsets; effect sizes; seed dispersion.
- **Evidence needed:** ablations isolating the gating term; literature check (PH-1) that the specific combination is not already published.
- **May remain unanswered if:** teachers expose no usable uncertainty signal (`TO_VERIFY` — depends on teacher selection), or PH-1 finds the contribution already published (→ re-scope).

---

#### RQ6 — Reproducible model selection

- **Problem:** Papers optimize one configuration; there is no reproducible sweep showing which strategy wins at a stated budget.
- **Gaps:** GAP-6, GAP-4, GAP-7.
- **Hypotheses (`PROPOSED`):** H-RQ6a: a fixed sweep protocol yields stable Pareto knee points that reproduce within a stated tolerance across re-runs (tolerance `TO_VERIFY`); H-RQ6b: the preferred configuration differs across budgets (32/64/128/256 KB-class).
- **Independent variables:** budget level; candidate configurations (family × capacity × KD × precision).
- **Dependent variables:** Pareto membership; knee-point configuration; reproduction delta on re-run.
- **Baselines:** single-configuration optimization as done in typical papers (comparison by construction of the framework).
- **Datasets:** DST-01 (full protocol).
- **Experiments:** EXP-011, EXP-013, EXP-014.
- **Metrics:** MET-01, MET-02, MET-05, MET-08–MET-14, MET-16.
- **Statistical analysis:** bootstrap confidence bands on the frontier; reproduction deltas.
- **Evidence needed:** complete run registry with configs, hashes, seeds; at least one independent re-run per critical configuration.
- **May remain unanswered if:** candidate space too small to produce a frontier, or artifact registry incomplete (→ REP-007 fails).

---

## 8. Research Gaps (GAP-1 … GAP-7)

Scope legend: **Core** = central to the proposed study; **Supporting** = measured as a by-product of core work; **Optional** = attempted only if time and compute allow.

| ID | Gap (from source report) | Scope | Primary RQs | Notes |
|---|---|---|---|---|
| GAP-1 | Foundation-model-to-MCU translation: can knowledge from large models realistically run on MCUs (architecture, ops, memory, inference compatibility)? | **Core** | RQ1, RQ4 | Controlled comparison of multiple teachers/student capacities under identical software resource budgets (`D-006`) |
| GAP-2 | Domain shift during distillation: does a student keep useful performance when deployment domain ≠ teacher training domain? | **Core** | RQ2, RQ5 | Agricultural sensor distributions vary by field/season/sensor/weather |
| GAP-3 | Joint KD × quantization: how do they interact; PTQ vs QAT separable experimentally? | **Core** | RQ3 | Report cites QKD that the two can interfere (`TO_VERIFY`) |
| GAP-4 | Resource-realistic Pareto curves: FLOPs/params ≠ measured latency/memory/size | **Core** | RQ4, RQ6 | Frontier with knee points and CIs is a central scientific output |
| GAP-5 | Robustness beyond mean accuracy: variation, failure behavior, uncertainty, worst-group error | **Core** | RQ2, RQ5 | Report: report worst-group/shifted-domain error, calibration, failure cases |
| GAP-6 | Reproducible decision framework: fair comparison of models/compression/budgets; selection traceable to evidence | **Core** | RQ6 | Budgets e.g. 32/64/128/256 KB RAM |
| GAP-7 | Sustainability as first-class objective: energy and carbon where feasible | **Optional** (energy: estimate-only, never a measurement — `D-006`) | RQ4, RQ6 | Never invent carbon figures; state methodology/assumptions/data sources |

**Important qualification:** whether these gaps remain open in the literature is `TO_VERIFY` and is the first job of `PH-1`. The source report itself warns that 2025–2026 papers already combine KD + quantization + agriculture/time-series.

---

## 9. Proposed Research Contribution

### 9.1 Candidate contribution (all `PROPOSED`; none verified)

1. A **systematic, software-measured, domain-shift-aware Pareto framework** jointly varying teacher choice, distillation objective, precision, and student capacity, evaluated in a reproducible software benchmarking environment with latency, peak process memory, artifact size, and energy estimate (report's "most defensible research gap"; software-only scope per `D-006`).
2. An **uncertainty/reliability-gated distillation** variant for time-series forecasting in which the distillation loss is weighted by teacher reliability, evaluated under controlled teacher–target domain mismatch (RQ5).
3. A **budget-indexed model-selection procedure**: given a stated size/memory/latency budget, the framework returns the Pareto-efficient candidate with traceable evidence (RQ6).

### 9.2 Competing approaches that must be checked in `PH-1` (from the report's priority list, `TO_VERIFY`)

- QKD: Quantization-aware Knowledge Distillation (KD × quantization interaction).
- *When to Trust, How to Distill* — multi-foundation-model guidance, robust scientific time-series forecasting (closest to uncertainty-aware distillation).
- *Distilling Privileged Knowledge From Transformers to Lightweight CNNs for On-Device Time Series Forecasting* (closest large-teacher → on-device time-series direction).
- *Optimising TinyML with quantization and distillation of transformer and mamba models…* (hardware-constrained KD+quantization precedent).
- *Deployable Deep Learning for Cross-Domain Plant Leaf Disease Detection via Ensemble Learning, KD, and Quantization* (closest agriculture benchmark).
- *Adaptive multi-teacher KD framework with foundation models for medical image analysis*.

### 9.3 Unresolved design choices

Tracked as U-01…U-12 in `memory.md` §8 and mirrored in `architecture.md` §22; each has a task in `task.md`.

### 9.4 Evidence required to justify the contribution

A defensible contribution needs (report §"What would count as a convincing contribution"): an explicitly defined method **or** novel benchmark/decision framework; nontrivial ablations; multiple teachers/students/precision levels; measured latency/memory in the target runtime (`D-006`: software-only, no hardware measurements); leakage-safe cross-domain/temporal validation; repeated-seed statistics; a public reproducibility package; explicit comparison to the closest 2025–2026 papers.

---

## 10. Scope

**In scope (main experimental study):**

- Agricultural time-series forecasting (soil moisture, temperature, humidity, weather, irrigation telemetry) as the application domain, per the source report (`ASSUMPTION`: final domain confirmed only if `PH-1`/dataset access support it).
- 2–4 time-series foundation/large teacher models + ≥1 conventional strong teacher (report's proposed matrix).
- ≥2 student architecture families (tiny CNN/TCN; compact Transformer/Mamba-style; deployment-oriented) × ≥3 capacities.
- KD variants: none, logit/forecast, feature, temporal-relation, uncertainty-gated.
- Precision: FP32, FP16, INT8 PTQ, INT8 QAT, mixed precision where the runtime supports it.
- Domain: in-domain + held-out field/site/season.
- Software environment: ≥1 reproducible target runtime (OS + pinned library stack + CPU or GPU, `PROPOSED`); a second environment optional (U-12).
- Metrics: task error + robustness under shift + params + serialized size + peak process memory + artifact size on disk + MACs/FLOPs + latency + throughput + energy estimate (labelled as an estimate) + estimated carbon (methodology stated).

**Out of scope (explicit exclusions):**

- Guaranteeing IEEE acceptance, novelty, or superior performance (impossible; see §28).
- Large-scale pretraining of foundation models (only use/fine-tune existing ones).
- Vision/audio/multimodal models and non-agricultural tasks (unless dataset access forces a documented re-scope).
- Fabricated numbers; energy or carbon figures presented as measurements rather than labelled estimates.
- Physical MCU/edge hardware in the experimental loop (`D-006`: software-only scope — no ESP32/Arduino, Raspberry Pi/Jetson, sensors, or power meters).
- Real-time closed-loop control/actuation (forecasting + measurement only).
- Personal or personally-identifiable data.

---

## 11. Requirements

Every requirement has a stable ID and a testable check, or is explicitly marked **[non-testable research objective]**.

### 11.1 Functional requirements — Data (FR-001…FR-006)

| ID | Requirement | Verification / acceptance |
|---|---|---|
| FR-001 | The system shall ingest at least one agricultural time-series dataset with documented provenance (source, license, sampling rate, variables, time range) | `DST-01` record in `memory.md` §10 contains all fields; license documented |
| FR-002 | The data pipeline shall produce train/validation/test splits that respect chronology and, where multi-site/season data exists, hold out complete sites/seasons as target domains | Split configuration file exists; automated leakage check passes (no timestamp overlap across splits) |
| FR-003 | The pipeline shall record all preprocessing steps (imputation, resampling, normalization, windowing) with parameters | Preprocessing config is versioned and attached to each run ID |
| FR-004 | The pipeline shall support a source-domain (teacher training) and ≥1 target-domain (deployment) split to enable domain-shift experiments (GAP-2) | Domain assignment is explicit in config; EXP-005 can be configured from it |
| FR-005 | Dataset versions and checksums shall be recorded | Manifest contains version + hash; verified on re-run |
| FR-006 | The system shall fail loudly (abort with message) on missing data, split overlap, or schema mismatch | Negative tests: injected corruption/overlap causes abort, not silent pass |

### 11.2 Functional requirements — Models (FR-007…FR-011)

| ID | Requirement | Verification |
|---|---|---|
| FR-007 | The system shall support ≥2 distinct teacher models (time-series foundation/large forecasting models) plus ≥1 conventional strong teacher baseline | Config lists teacher IDs; each produces predictions on the evaluation set |
| FR-008 | The system shall support ≥2 student architecture families with ≥3 capacities each (separating capacity from architecture, per report matrix) | Student registry enumerates ≥6 configurations with measured param counts |
| FR-009 | Model choice (teacher/student) shall remain open until selection criteria are met; selection criteria must be documented before selection | Selection-criteria doc exists before any model ID is marked `DECIDED` (U-01/U-02) |
| FR-010 | Any teacher used for uncertainty-gated distillation shall expose a per-window uncertainty signal (e.g., ensemble spread, quantile width, predictive variance) | Uncertainty signal available for every teacher used in EXP-006, or the teacher is excluded with documented reason |
| FR-011 | Teachers and students shall be evaluated with identical data pipelines and metrics | Same run config drives both; no separate metric code path |

### 11.3 Functional requirements — Distillation (FR-012…FR-017)

| ID | Requirement | Verification |
|---|---|---|
| FR-012 | The pipeline shall implement at minimum: no-KD baseline, logit/forecast distillation, and one feature- or temporal-relation-based distillation variant | Each variant selectable by config key; unit test per loss |
| FR-013 | The pipeline shall implement uncertainty/reliability-weighted gating of the distillation loss, with the gating function configurable and ablatable | EXP-006 can toggle gating on/off with identical seeds (gating-only ablation) |
| FR-014 | Distillation settings (temperature, loss weights, target type, gating parameters) shall be recorded per run | Run manifest contains all settings |
| FR-015 | KD baselines shall be defined before the proposed method is evaluated | `phases.md` PH-3 exit precedes PH-4; enforced by task dependencies |
| FR-016 | The system shall quantify student retention relative to the teacher and relative to a same-size non-distilled student | Reporting pipeline emits retention table for EXP-002 |
| FR-017 | Failed and negative distillation results shall be recorded, not discarded | `memory.md` §14 populated for every failed run |

### 11.4 Functional requirements — Quantization (FR-018…FR-022)

| ID | Requirement | Verification |
|---|---|---|
| FR-018 | The quantization pipeline shall support FP32 reference, FP16, INT8 PTQ, and INT8 QAT; mixed INT8/INT4 only where the toolchain/runtime supports it | Each regime is runnable and logged; unsupported regimes are explicitly reported, not silently skipped |
| FR-019 | Quantization experiments shall separate predictive change (vs FP32) from footprint change (serialized size / peak process memory / latency) | Report contains both columns per configuration |
| FR-020 | PTQ calibration data shall be drawn only from training data | Config field `calibration_split=train`; automated check |
| FR-021 | Every quantized model shall record bit width, scheme (per-tensor/per-channel), and calibration set size | Run manifest completeness check |
| FR-022 | QAT runs shall record epochs, learning-rate schedule, and initialization checkpoint | Run manifest completeness check |

### 11.5 Functional requirements — Domain-shift evaluation (FR-023…FR-025)

| ID | Requirement | Verification |
|---|---|---|
| FR-023 | The evaluation pipeline shall report metrics separately for in-domain and each held-out domain | Results table has one column/block per domain |
| FR-024 | The system shall produce worst-group/worst-domain error and error-distribution statistics (e.g., p50/p90/p95 absolute error) | Report includes these fields for EXP-005/EXP-012 |
| FR-025 | Any synthetic shift (constructed rather than naturally held out) shall be labeled as synthetic everywhere it appears | Label present in tables/figures; audit by spot check |

### 11.6 Functional requirements — Runtime evaluation (FR-026…FR-031)

| ID | Requirement | Verification |
|---|---|---|
| FR-026 | An export path shall convert supported student models to the target runtime's serialized artifact and record conversion settings and artifact size | Conversion log + artifact hash + size stored per model |
| FR-027 | Latency measurements shall be taken by executing the exported artifact in the target runtime (never inferred from FLOPs) with documented warm-up, repetitions, and units | Measurement methodology record exists (D-0xx); raw per-repetition values stored |
| FR-028 | Peak process memory and serialized artifact size on disk shall be measured and kept distinct from each other and from total host memory | Both values reported separately with method noted |
| FR-029 | Theoretical metrics (FLOPs/MACs/params) shall be computed for every model that is measured, to enable RQ4 correlation analysis | EXP-010 dataset contains paired theoretical/measured rows |
| FR-030 | Energy per inference shall be reported only as an estimate with a stated method (no power instrumentation is in scope, `D-006`); if no estimator is available, energy must be reported as unavailable | `measurement_type=estimated` on every energy value, or an explicit unavailability statement |
| FR-031 | Runtime/edge compatibility shall never be claimed without a recorded run of that artifact in that runtime | Every "deployed" claim links to a run log from the runtime |

### 11.7 Functional requirements — Robustness (FR-032…FR-034)

| ID | Requirement | Verification |
|---|---|---|
| FR-032 | Critical comparisons shall be repeated across ≥2 fixed seeds where feasible (target 3–5; `TO_VERIFY` budget), with all seeds reported | Seed list in run registry; no seed dropped without documented reason |
| FR-033 | The system shall analyze failure cases: worst-N windows with context, teacher vs student error, and domain attribution | Failure analysis artifact exists for EXP-012 |
| FR-034 | Statistical tests shall be named in advance and justified; effect sizes reported alongside p-values | Analysis plan recorded before results are seen |

### 11.8 Functional requirements — Sustainability (FR-035, optional)

| ID | Requirement | Verification |
|---|---|---|
| FR-035 | If energy data is available, the system may compute an energy/carbon estimate; every such figure must state methodology, assumptions, and data sources | Any carbon number in any document carries a methodology footnote; otherwise omitted |

### 11.9 Non-functional requirements (NFR-001…NFR-010)

| ID | Requirement | Verification |
|---|---|---|
| NFR-001 | The framework shall be modular: data / training / evaluation / deployment responsibilities separated (see `architecture.md`) | Module dependency check: no reverse imports from `data` to `eval` etc. |
| NFR-002 | All experiments shall be configurable (YAML/JSON config per run) with configs stored alongside results | Every run ID maps to exactly one stored config |
| NFR-003 | The system shall support adding a new model or dataset without rewriting core pipelines | Adding a dummy model requires only a registered adapter (demonstrated in a test) |
| NFR-004 | Every result must be traceable to run ID → config → code version → data version | Traceability spot-check on 3 random results |
| NFR-005 | Documented behavior on failure: clear error, no silent defaults that change results | Negative tests (FR-006) + error-handling review in `architecture.md` §20 |
| NFR-006 | Dependencies and environment shall be pinned (lockfile) | Lockfile present; clean-environment install succeeds |
| NFR-007 | Documentation shall remain internally consistent across the seven files (see `rules.md` §E) | Consistency checklist in `phases.md` PH-0 exit criteria |
| NFR-008 | Simulated/estimated performance shall be labeled distinctly from measured performance in all outputs | Report schema has a `measurement_type` field (measured/estimated/simulated) |
| NFR-009 | The system shall run within available compute: no step may assume unbounded GPU resources | Each phase lists compute needs; runs fit available compute (U-10) |
| NFR-010 | Code, configs, and results shall be organized for third-party reproduction | REP-001…REP-007 all pass |

### 11.10 Reproducibility requirements (REP-001…REP-007)

| ID | Requirement | Verification |
|---|---|---|
| REP-001 | A documented one-path entry (script/Makefile target) shall run any registered experiment end-to-end | Dry run of one experiment from a clean checkout |
| REP-002 | Random seeds, library/runtime versions, and environment versions recorded per run | Manifest fields non-empty (automated check) |
| REP-003 | Dataset split protocol shall be deterministic given the config | Same config → identical split hashes twice |
| REP-004 | Selected experiments shall be re-run at least once in PH-8 and compared within a stated tolerance (tolerance `TO_VERIFY`) | Reproduction delta table exists |
| REP-005 | Exact quantization settings shall be recorded (see FR-021) | Manifest check |
| REP-006 | Artifacts (checkpoints, exported binaries, raw measurement logs) shall be stored with hashes | Artifact index lists hashes; spot-verified |
| REP-007 | The release package shall include code, configs, split definitions, benchmark scripts, and instructions | Package completeness checklist passes |

### 11.11 Experiment requirements (EXP-001…EXP-014)

Experiments are requirements of the study: each must be runnable and documented. Defined here with full definitions in `architecture.md` §16 / `phases.md`.

| ID | Experiment | RQs | Phase | Status |
|---|---|---|---|---|
| EXP-001 | Teacher baseline evaluation (in-domain, all teachers + conventional baseline) | RQ1, RQ2 | PH-3 | `PROPOSED` |
| EXP-002 | Student no-KD baselines across families/capacities | RQ1 | PH-3 | `PROPOSED` |
| EXP-003 | Distillation-target comparison (logit/feature/temporal vs none) | RQ1, RQ2 | PH-4 | `PROPOSED` |
| EXP-004 | Theoretical-metric computation for all candidates (params/MACs) | RQ4 | PH-6 | `PROPOSED` |
| EXP-005 | Domain-shift evaluation of distilled students (held-out field/site/season) | RQ2 | PH-4 | `PROPOSED` |
| EXP-006 | Uncertainty/reliability-gated distillation vs ungated (with ablations) | RQ5, RQ2 | PH-4 | `PROPOSED` |
| EXP-007 | PTQ sweep (FP32/FP16/INT8) on selected students | RQ3 | PH-5 | `PROPOSED` |
| EXP-008 | QAT vs PTQ comparison at matched bit width | RQ3 | PH-5 | `PROPOSED` |
| EXP-009 | KD × quantization interaction factorial (KD on/off × regime) | RQ3 | PH-5 | `PROPOSED` |
| EXP-010 | Software-runtime measurement (latency / process memory / artifact size / energy estimate) vs theoretical | RQ4 | PH-6 | `PROPOSED` |
| EXP-011 | Multi-budget Pareto sweep (32/64/128/256 KB-class budgets) | RQ6, RQ1 | PH-8 | `PROPOSED` |
| EXP-012 | Robustness, error distributions, calibration, failure analysis (multi-seed) | RQ5, RQ2 | PH-7 | `PROPOSED` |
| EXP-013 | Reproduction re-run of selected critical configurations | RQ6 | PH-8 | `PROPOSED` |
| EXP-014 | Statistical comparison and frontier confidence bands | RQ3–RQ6 | PH-7/PH-8 | `PROPOSED` |

---

## 12. Evaluation Metrics

| ID | Metric | Type | Unit | Used for |
|---|---|---|---|---|
| MET-01 | RMSE (primary forecast error) | Predictive | task units | RQ1–RQ3, RQ5, RQ6 |
| MET-02 | MAE | Predictive | task units | RQ1–RQ3, RQ5, RQ6 |
| MET-03 | sMAPE or MASE (final choice `TO_VERIFY` vs report's "RMSE/MAE/F1 as appropriate") | Predictive | % / dimensionless | RQ1–RQ3 |
| MET-04 | F1 (only if an auxiliary classification/alert task is defined) | Predictive | dimensionless | RQ1, RQ5 |
| MET-05 | Worst-domain / shifted-domain error | Robustness | task units | RQ2, RQ5 |
| MET-06 | Calibration / uncertainty quality (metric choice `TO_VERIFY`, e.g., interval coverage, CRPS) | Robustness | varies | RQ5 |
| MET-07 | Parameter count | Theoretical | count | RQ1, RQ4 |
| MET-08 | Model storage size | Footprint | bytes/KB | RQ1, RQ3, RQ6 |
| MET-09 | Peak process memory during inference (measured in the target runtime) | Footprint | bytes/KB | RQ1, RQ3, RQ4, RQ6 |
| MET-10 | Serialized artifact size on disk | Footprint | bytes/KB | RQ1, RQ3, RQ6 |
| MET-11 | MACs/FLOPs | Theoretical | MFLOPs | RQ4 |
| MET-12 | Inference latency in the target runtime (median + spread) | Measured (software) | ms | RQ1, RQ4, RQ6 |
| MET-13 | Throughput | Measured | inferences/s | RQ4 |
| MET-14 | Energy per inference | Estimated (no power instrumentation in scope — `D-006`) | mJ | RQ4, Gap 7 |
| MET-15 | Estimated carbon (only with methodology) | Estimated | gCO2e | Gap 7 |
| MET-16 | Seed-to-seed dispersion / confidence interval width | Statistical | varies | all RQs |

Metric selection must be finalized per dataset in PH-2 (`TO_VERIFY`); this table is the authoritative ID list.

Under `D-006` (software-only scope) only MET-12/MET-13 are measured — and they are measured **in software**, inside the target runtime. MET-14/MET-15 are estimates and must always carry `measurement_type=estimated`; no hardware-measured figure may appear anywhere in this project.

---

## 13. Acceptance Criteria (project level)

| ID | Criterion | Check |
|---|---|---|
| AC-1 | All seven documentation files exist, are substantively populated, and are cross-consistent | PH-0 exit checklist |
| AC-2 | Every requirement ID maps to ≥1 goal, component, or task | Traceability table (§15) complete, no orphans |
| AC-3 | Literature review completed with recorded citations and novelty risks; no unsupported novelty claim remains | PH-1 exit |
| AC-4 | Dataset/task/protocol documented and leakage-checked | PH-2 exit |
| AC-5 | Baselines reproducible from stored configs | PH-3 exit |
| AC-6 | Each core RQ has either sufficient evidence or an explicitly documented limitation | PH-4…PH-8 exit criteria |
| AC-7 | Measured and estimated values separated everywhere; no fabricated numbers | Audit per `rules.md` §B/§D |
| AC-8 | Reproduction check passes within stated tolerance | REP-004 |
| AC-9 | Every research claim traceable to an artifact | PH-9 exit |

Non-testable research objectives: RO-7 (partially), RO-8 (publication is not guaranteed — see §28).

---

## 14. Risks and Dependencies

| ID | Risk/Dependency | Impact | Mitigation |
|---|---|---|---|
| RK-1 | Novelty already claimed by 2025–2026 papers | Contribution re-scope | PH-1 first; re-scope options in `memory.md` §7 |
| RK-2 | No suitable multi-site/multi-season agricultural dataset | RQ2/RQ5 weakened | Early dataset survey (PH-2); document synthetic-shift limits |
| RK-3 | Teachers expose no uncertainty signal | RQ5 blocked | FR-010; select teachers with quantiles/ensembles; else fall back to error-based reliability proxy (`TO_VERIFY`) |
| RK-4 | Target software runtime or benchmark environment unavailable | RQ4/RQ6 partially unanswered | Fall back to FLOPs/params only, clearly labelled as estimates (NFR-008) |
| RK-5 | No reliable energy estimator available | Gap 7 only partially answerable | FR-030 estimate-only statement; no invented numbers |
| RK-6 | Compute insufficient for 2–4 teachers × full matrix | Scope overload | Prioritize matrix; record reduction as explicit scope change (`rules.md` §E) |
| RK-7 | QAT/mixed-precision unsupported on target runtime | RQ3 partial | Document supported subset; FR-018 |
| RK-8 | Drift between the seven files after decisions change | Inconsistency | `rules.md` §E update rules + PH-0 consistency checklist |
| Dependency | Source Word documents, dataset access, compute, software runtimes/toolchains | — | Tracked as U-01…U-12 in `memory.md` |

---

## 15. Traceability Table

`Research Gap → Research Question → Requirement → Architecture Component → Experiment → Metric → Task → Goal`

Components are defined in `architecture.md` §3 (C-01…C-12); tasks in `task.md`; goals in `goal.md`.

| Gap | RQ | Requirement(s) | Component(s) | Experiment(s) | Metric(s) | Task(s) | Goal |
|---|---|---|---|---|---|---|---|
| GAP-1 | RQ1 | FR-007, FR-008, FR-016, FR-026–FR-028 | C-03 (teacher), C-04 (student), C-09 (export), C-10 (runtime-bench) | EXP-001, EXP-002, EXP-011 | MET-01, MET-07, MET-08, MET-09, MET-12 | T-031, T-032, T-033, T-061, T-064 | G-003, G-004, G-006 |
| GAP-2 | RQ2 | FR-002, FR-004, FR-023, FR-024 | C-02 (data), C-05 (KD), C-11 (eval) | EXP-003, EXP-005 | MET-01, MET-02, MET-05 | T-025, T-043 | G-004, G-007 |
| GAP-3 | RQ3 | FR-018–FR-022, REP-005 | C-06 (quant), C-11 (eval) | EXP-007, EXP-008, EXP-009 | MET-01, MET-08, MET-09, MET-12 | T-051, T-052, T-053 | G-005 |
| GAP-4 | RQ4 | FR-027–FR-029, NFR-008 | C-09 (export), C-10 (bench), C-11 (eval) | EXP-004, EXP-010 | MET-11, MET-12, MET-13, MET-14 | T-061, T-062, T-063 | G-006 |
| GAP-5 | RQ5 | FR-024, FR-032, FR-033, FR-034 | C-07 (uncertainty), C-11 (eval), C-12 (analysis) | EXP-006, EXP-012 | MET-05, MET-06, MET-16 | T-044, T-071, T-072 | G-007 |
| GAP-6 | RQ6 | REP-001–REP-007, NFR-002, NFR-004 | C-01 (orchestr.), C-08 (registry), C-11 (eval), C-12 (analysis) | EXP-011, EXP-013, EXP-014 | MET-01, MET-09, MET-12, MET-16 | T-081, T-082, T-083 | G-008 |
| GAP-7 | RQ4, RQ6 | FR-030, FR-035, NFR-008 | C-10 (bench), C-12 (analysis) | EXP-010 (energy part) | MET-14, MET-15 | T-065 | G-006 |

---

## 16. Dataset Requirements

| ID | Requirement | Verification |
|---|---|---|
| DST-R1 | Domain fit: soil-moisture/temperature/humidity/weather/irrigation-type multivariate time series (agriculture) | DST-01 record shows variables matching the task |
| DST-R2 | Access & license permitting research use and redistribution of derived code | License text recorded (FR-001) |
| DST-R3 | Enough temporal depth for chronological splits **and** natural domain variation (≥2 sites/seasons) to support GAP-2 | Domain availability documented |
| DST-R4 | Documented sampling rate, gaps, and sensor noise | Data-quality report |
| DST-R5 | Predictive task definable with a lookback/horizon that fits student capacity | Task definition in PH-2 |

**Dataset status:** no dataset has been selected (`TO_VERIFY`). Candidate categories to investigate in PH-2: published agricultural IoT field-trial datasets, open soil-moisture/agrometeorological station networks, and forecasting benchmarks used by the closest papers (§9.2). Dataset selection must record why it satisfies DST-R1–R5.

## 17. Model Requirements

- Teachers: time-series foundation/large forecasting models (2–4) + ≥1 conventional strong baseline (FR-007). Specific architectures `TO_VERIFY` (U-01).
- Students: tiny CNN/TCN, compact Transformer/Mamba-style, deployment-oriented architecture; ≥2 families × ≥3 capacities (FR-008). Specific architectures `TO_VERIFY` (U-02).
- All models: config-registered, exportable or explicitly documented as non-exportable (FR-026, NFR-003).

## 18. Distillation Requirements

Covered by FR-012–FR-017. Additionally: distillation target and loss must be identical across compared strategies except for the factor under study; λ and temperature swept on validation only, never on test (leakage rule `rules.md` §C).

## 19. Quantization Requirements

Covered by FR-018–FR-022. PTQ vs QAT comparison must hold bit width and evaluation protocol constant (FR-019).

## 20. Domain-Shift Evaluation Requirements

Covered by FR-002, FR-004, FR-023–FR-025; shift construction recorded before experiments run (PH-2 exit).

## 21. Runtime-Evaluation Requirements

Covered by FR-026–FR-031; measurement methodology record required before any latency/energy number is reported (`rules.md` §D).

## 22. Robustness Requirements

Covered by FR-032–FR-034.

## 23. Reproducibility Requirements

Covered by REP-001–REP-007.

## 24. Sustainability Requirements

Covered by FR-030, FR-035 (Optional scope; no invented figures).

## 25. Evaluation Metrics

See §12 (authoritative metric ID list).

## 26. Acceptance Criteria

See §13.

## 27. Assumptions and Unresolved Questions

| ID | Item | Label |
|---|---|---|
| A-1 | Agricultural time-series is the final application domain | `ASSUMPTION` (strongly suggested by report; confirm feasibility in PH-2) |
| A-2 | At least one reproducible software runtime/benchmark environment is available to the researcher | `ASSUMPTION` (U-07) |
| A-3 | Teachers can be trained/fine-tuned within available compute | `ASSUMPTION` (U-10) |
| U-01…U-12 | Unresolved decisions list | see `memory.md` §8 |

## 28. Conditions Required Before Claiming Research Novelty

A novelty claim may be written **only if all** hold:

1. `PH-1` literature search is documented (databases, queries, dates, inclusion criteria) and current to within the report's search date (`TO_VERIFY` refresh required).
2. The closest prior works (§9.2 + new findings) are explicitly compared, point by point.
3. The claim is specific (method component, benchmark property, or decision framework) — not "KD + quantization + agriculture".
4. Ablations show the claimed component contributes (report requirement).
5. The claim is labeled with evidence links to `memory.md` §9 (verified literature findings).
6. `rules.md` §B is satisfied (no fabricated or selective citations).

Until then, all contribution statements remain `PROPOSED` and must be phrased as "candidate contribution".
