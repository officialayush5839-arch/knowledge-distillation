# memory.md — Persistent Project Memory and Decision Log

**Project:** KD-Edge-TinyML (see `prd.md` §1)

**Document role:** `memory.md` preserves decisions, evidence, progress, and lessons so a future session (human or AI agent) can continue without re-discovering context. It must be updated in the same session as any significant decision (`rules.md` §E4). Unestablished facts use explicit placeholders marked `TO_VERIFY`. No fabricated results are permitted here.

---

## 1. Project Identity

| Field | Value |
|---|---|
| Project | Uncertainty-Gated Distillation and Mixed-Precision Quantization of Time-Series Foundation Models for Resource-Constrained Agricultural Forecasting (`PROPOSED` title; software-only scope, `D-006`) |
| Short name | KD-Edge-TinyML (label retained for ID stability; not a hardware claim — `D-006`) |
| Project folder | `C:\Users\ARYAN - AYUSH\OneDrive\Desktop\Knowledge Distillation\` |
| Documentation files | `prd.md`, `architecture.md`, `rules.md`, `phases.md`, `memory.md`, `goal.md`, `task.md` |
| Repo structure | Not created yet; proposed layout in `architecture.md` §21 |
| Current phase | PH-1 (literature verification and novelty assessment) — `NOT_STARTED`; PH-0 `COMPLETED` 2026-10-10 |
| Data/experiments | None. No code, data, models, or measurements exist. |

## 2. Research Summary

Study how much useful knowledge a large time-series teacher model can transfer into a compact, quantized student that meets explicit software resource budgets, and whether uncertainty/reliability-gated distillation improves behaviour when teacher and deployment domains differ. Central scientific output: a **software-measured, domain-shift-aware Pareto frontier** with knee points and confidence bands, plus a budget-indexed selection procedure. Source direction: `IEEE_Knowledge_Distillation_Edge_Literature_Gap_Report (1).docx` §"Recommended project direction".

## 3. Primary Source Documents

| ID | Document | Location | Notes |
|---|---|---|---|
| SRC-01 | `IEEE_Knowledge_Distillation_Edge_Literature_Gap_Report (1).docx` | `C:\Users\ARYAN - AYUSH\Downloads\IEEE_Knowledge_Distillation_Edge_Literature_Gap_Report (1).docx` | Read in full 2026-10-10; 47,651 bytes; SHA256 `b2ec98f3db088113e2d9793609ac433fda026db16dd57db3d71deb308f49ce87`; search date 30 Sep 2026; 54 records |
| SRC-01-EXT | Same report, extracted plain text | Not retained | Extraction was performed via `word/document.xml`; a temporary text extract was created and removed. Re-extract on demand if needed. |
| SRC-02 | `Software_Only_Foundation_Model_Distillation_Project_Master_Guide.docx` | `C:\Users\ARYAN - AYUSH\Downloads\` | Read in full 2026-10-10 (367-line plain-text extract). Its software-only framing was accepted by the researcher as the project scope (`D-006`); retained as a **supporting source only** — the seven-file structure and ID scheme stay authoritative (`D-007`) |
| SRC-03 | `Research paper for distillation work.docx` | `C:\Users\ARYAN - AYUSH\Downloads\` | Exists in workspace; **not read**; relevance `TO_VERIFY` |

## 4. Current Research Questions

RQ1 (knowledge retention under resource constraints), RQ2 (distillation under domain shift), RQ3 (distillation × quantization interaction), RQ4 (resource-realistic efficiency, software-measured), RQ5 (reliability-aware distillation), RQ6 (reproducible model selection). Full definitions, hypotheses, IVs/DVs, baselines, metrics, and evidence requirements are in `prd.md` §7. All hypotheses are `PROPOSED`; none tested.

## 5. Research-Gap Summary

GAP-1 foundation-model→resource-constrained translation (Core; addressed at software level per `D-006`), GAP-2 domain shift during distillation (Core), GAP-3 KD × quantization interaction (Core), GAP-4 resource-realistic Pareto curves (Core; software-measured), GAP-5 robustness beyond mean accuracy (Core), GAP-6 reproducible decision framework (Core), GAP-7 sustainability (Optional). Scope assignment and evidence status: `prd.md` §8. Whether each gap is still open: **`TO_VERIFY` in PH-1**.

## 6. Confirmed Decisions

| ID | Decision | Status | Reason | Evidence | Alternatives considered | Date | Files affected |
|---|---|---|---|---|---|---|---|
| D-001 | Use `IEEE_Knowledge_Distillation_Edge_Literature_Gap_Report (1).docx` as the primary research authority | `DECIDED` | Required by the task specification; document present and readable | SRC-01 hash recorded (§3) | Other distillation docs in Downloads (SRC-02, SRC-03) — deferred, not authoritative | 2026-10-10 | all seven files |
| D-002 | Build the documentation system as the seven specified files in `OneDrive/Desktop/Knowledge Distillation/` | `DECIDED` | That folder was empty and created for this project; Desktop root contains unrelated projects | Directory listing 2026-10-10 | Desktop root; a new `docs/research/` subfolder | 2026-10-10 | all seven files |
| D-003 | Use the report's working title as provisional project title | `DECIDED` (provisional; title wording revised by D-006) | Directly supported by SRC-01 §"Recommended project direction" | SRC-01 | Generic titles rejected | 2026-10-10 | `prd.md` §1 |
| D-004 | Keep every model, dataset, framework, runtime, and environment choice open until its selection criteria are met | `DECIDED` | `TO_VERIFY` discipline required by the task specification; prevents unfounded design lock-in | `rules.md` §A | Premature selection of ESP32-S3/TFLite Micro as final | 2026-10-10 | `architecture.md` §22, `prd.md` §27 |
| D-005 | Adopt the ID scheme (FR/NFR/REP/EXP/MET/C/GAP/RQ/G/PH/T/D/U) | `DECIDED` | Cross-file traceability requirement | `prd.md` §15 | Ad-hoc naming rejected | 2026-10-10 | all seven files |
| D-006 | **Software-only experimental scope:** no physical IoT/edge hardware (no ESP32/Arduino, Raspberry Pi/Jetson, sensors, or power meters). Latency and memory are measured by executing artifacts in a target software runtime; energy is reported only as a labelled estimate | `DECIDED` | Explicit researcher choice, resolving a direct conflict between SRC-01 (which proposes hardware-measured edge experiments) and SRC-02 (which mandates a software-only setup). Software-only keeps every claim and word of the write-up aligned with the setting and removes hardware-dependency risk (RK-4/RK-5) | Researcher decision 2026-10-10, recorded in this session; SRC-02 scope statement | Keep SRC-01's hardware-measured direction; hybrid (benchmark hardware, no power measurement) | 2026-10-10 | all seven files |
| D-007 | Treat SRC-02 as a **supporting source only**; the seven-file documentation system, ID scheme, and traceability rules remain authoritative | `DECIDED` | SRC-02 is a complete alternative specification for the same project; adopting it wholesale would invalidate the existing ID/decision structure. Its software-only scope was adopted (D-006); its remaining content is advisory | Researcher decision 2026-10-10 | Replace the seven files with SRC-02's structure; ignore SRC-02 entirely | 2026-10-10 | all seven files |

## 7. Proposed Decisions (not approved)

| ID | Proposal | Rationale | Blocked/confirmed by |
|---|---|---|---|
| P-001 | Agricultural time-series forecasting as the final domain | Reported as the most defensible direction | PH-2 dataset feasibility (`TO_VERIFY`) |
| P-002 | Uncertainty/reliability-gated KD as the methodological novelty | Report's recommended direction | PH-1 novelty check (`TO_VERIFY`) |
| P-003 | Primary target software runtime plus optional second software environment (no hardware required) | Software-only scope (`D-006`); supersedes SRC-01's suggested hardware | U-07, U-12 |
| P-004 | FP32→FP16→INT8 PTQ→INT8 QAT→mixed precision ladder | Report's suggested compression matrix | U-09 toolchain support |
| P-005 | Budget classes 32/64/128/256 KB RAM for model selection | Report's suggested budgets | PH-2 calibration to the chosen runtime |
| P-006 | Re-scope options if novelty fails: (a) benchmark/decision-framework framing, (b) resource-aware mixed precision, (c) uncertainty-gated transfer only | Report's sanctioned alternatives | PH-1 outcome |

## 8. Unresolved Questions (U-xx)

| ID | Question | Owner task | Resolution needed by |
|---|---|---|---|
| U-01 | Which teachers (2–4 foundation/large + 1 conventional)? | T-013, T-031 | PH-3 |
| U-02 | Which student families/capacities? | T-032 | PH-3 |
| U-03 | Which dataset is DST-01? | T-021 | PH-2 |
| U-04 | Final prediction task (target, lookback, horizon) | T-022 | PH-2 |
| U-05 | Uncertainty estimation method per teacher | T-041 | PH-4 |
| U-06 | Gating function form + λ selection rule | T-042 | PH-4 |
| U-07 | Target software runtime + environment (OS/library stack, CPU or GPU) | T-060 | PH-6 |
| U-08 | Energy estimation method (no power instrumentation in scope) or unavailability statement | T-065 | PH-6 |
| U-09 | Mixed INT8/INT4 feasibility | T-051 | PH-5 |
| U-10 | Compute budget/location for training | T-012 | PH-3 |
| U-11 | Calibration metric + statistical test set | T-072 | PH-7 |
| U-12 | Include a second software environment? | T-066 | PH-6 |

## 9. Verified Literature Findings

**None yet.** The 54 records in SRC-01 are service-returned search results (Consensus, 30 Sep 2026), *not* independently verified findings. Citation counts must be rechecked before submission. Verification is the purpose of PH-1 (T-010…T-016). Do not cite any of these records as verified until they appear here with a verification date and a source link.

## 10. Dataset Decisions

**None.** DST-01 unselected (U-03). Requirements: `prd.md` §16 (DST-R1…DST-R5).

## 11. Model Decisions

**None.** Teachers (U-01) and students (U-02) unselected. Candidate families are listed in `architecture.md` §6/§7 as `PROPOSED` only.

## 12. Experimental Configurations

**None recorded.** Expected locations once created: `configs/experiments/<EXP-id>.yaml` (per `architecture.md` §21) and the run registry (C-08).

## 13. Results Summary

**No results exist.** This project has produced no measurements, metrics, or figures. Any number appearing later must trace to a run ID in the registry (`rules.md` §B).

## 14. Failed Experiments and Lessons Learned

| ID | What failed | Lesson | Status |
|---|---|---|---|
| L-001 | A single first attempt to extract the DOCX text with `python` failed because the Windows Store alias shadows `python`; `py` works | On this machine use `py` for Python scripts in Git Bash | `COMPLETED` |
| L-002 | Recursive `find` over the whole user profile timed out (60 s) | Scope filesystem searches to known directories (Downloads/Documents/Desktop) | `COMPLETED` |

| L-003 | Second audit pass found U-02/U-03/U-04 owner-task mappings drifted between `memory.md` §8, `architecture.md` §22, and `task.md` (an off-by-one from an earlier repair), plus two imprecise traceability task cells in `prd.md` §15 | Never verify ID mappings by eye — run a set-compare (`comm`) of defined vs referenced IDs; fix all files in one pass | `COMPLETED` |

No experiments have been run; no other lessons exist.

## 15. Known Limitations

1. 54-record literature map is unverified and dated (30 Sep 2026) — literature churn expected.
2. Novelty of uncertainty-gated KD for time-series domain shift is unknown; the report explicitly warns prior work may already cover it.
3. No dataset, compute, or energy estimator has been confirmed available (physical hardware is out of scope by `D-006`).
4. This documentation set was authored from the report alone; no experimental evidence exists.
5. The source report itself is a planning dossier, not peer-reviewed evidence.
6. **Scope is software-only (`D-006`).** No MCU/edge-hardware measurement exists, so RQ4/RQ6 rest on software-measured latency and process memory plus labelled energy estimates. This is a deliberate, recorded limitation — it must be stated in any draft (`rules.md` §B8) and never softened into a hardware claim.

## 16. Current Phase

**PH-0 — Source inspection and project setup**: `COMPLETED` (2026-10-10). Seven files created, source read and hashed, cross-check executed with 4 defects found and repaired; PH-0 exit criteria met. A later scope revision (`D-006`/`D-007`) was propagated across all seven files in the same session, with the cross-check re-run afterwards. **PH-1 — Literature verification and novelty assessment**: `NOT_STARTED` (next; start with T-010, T-012, T-013).

## 17. Current Blockers

None. Items U-01…U-12 are open decisions, deliberately deferred, not blockers. Watch items: no confirmed target runtime/benchmark environment (RK-4) and no confirmed dataset (RK-2) — both first matter in PH-2/PH-6.

## 18. Important Repository Paths

| Path | Purpose | Status |
|---|---|---|
| `C:\Users\ARYAN - AYUSH\OneDrive\Desktop\Knowledge Distillation\` | Project root (documentation home) | Exists |
| `.../Knowledge Distillation/{prd,architecture,rules,phases,memory,goal,task}.md` | The seven authoritative files | Created 2026-10-10 |
| `C:\Users\ARYAN - AYUSH\Downloads\IEEE_Knowledge_Distillation_Edge_Literature_Gap_Report (1).docx` | Primary source document | Exists (hash in §3) |
| `kd-edge-tinyml/` (proposed) | Future code repository root | Not created (`TO_VERIFY` location) |

## 19. Key Artifact Locations

**None yet.** Planned: `artifacts/runs/<run_id>/…` and `results/` per `architecture.md` §21. No checkpoints, binaries, logs, or measurement files exist.

## 20. Next Recommended Actions

1. Start **T-010** (verify the literature map) and **T-011** (deep-read the priority papers) — PH-1 is the critical path because novelty determines whether the framing survives.
2. Start **T-013** (search for uncertainty/reliability-gated KD) early: it decides whether the candidate contribution stands or must be re-scoped.
3. In parallel, start **T-020/T-021** dataset scouting, since dataset access is an early external dependency and can invalidate the domain choice.
4. Resolve **U-10** (compute) via **T-012** early: teacher training feasibility gates the whole experiment matrix.

## 21. Change History

| Date | Change | By | Files |
|---|---|---|---|
| 2026-10-10 | Initial documentation system created from SRC-01: seven files, ID scheme, gaps/RQs/goals/phases/tasks populated in `NOT_STARTED`/`PROPOSED` state | AI agent (Buffy/Freebuff) | all seven |
| 2026-10-10 | Source document located, read in full, SHA256 recorded; temp text extract removed | AI agent | `memory.md`, `phases.md` |
| 2026-10-10 | Added the two Mermaid diagrams required by the specification that were missing: experiment execution flow (`architecture.md` §14) and evaluation/reporting flow (`§16`); diagram count now 6 (4 required types covered + quantization and software-benchmarking pipelines). | AI agent | `architecture.md` |
| 2026-10-10 | Third pass: renamed workflow steps in `architecture.md` §6/§7 from `T-1…T-5` / `S-1…S-5` to `TS-1…TS-5` / `SS-1…SS-5` to remove visual confusion with task IDs (`T-xxx`); internal reference `S-2`→`SS-2` updated. No semantic change. | AI agent | `architecture.md` |
| 2026-10-10 | Second verification pass (full content audit): 5 residual defects found and repaired — U-02/U-03/U-04 owner-task mappings in `memory.md` §8 and `architecture.md` §22 (now T-032 / T-021 / T-022, matching `task.md`), and GAP-1 + GAP-7 task cells in `prd.md` §15 (now T-031/T-032/T-033/T-061/T-064 and T-065). Verified: 60 defined tasks = 60 referenced, zero phantom references, zero orphan tasks, bold markers balanced. | AI agent | `prd.md`, `architecture.md`, `memory.md` |
| 2026-10-10 | **Scope revision (`D-006`/`D-007`)**: researcher chose the software-only experimental scope, resolving a conflict between SRC-01 (hardware-measured) and SRC-02 (software-only). SRC-01's implied 'Hardware-Aware … TinyML … Edge' framing was removed from titles, scope, requirements (FR-026–FR-031), metrics (MET-09/10/14), architecture (C-09/C-10, §13), rules §D, phases PH-6, goals G-001/G-006 and tasks T-060–T-066. No hardware measurement is performed anywhere; energy is estimate-only. | AI agent (Buffy/Freebuff), on researcher decision | all seven |
| 2026-10-10 | PH-0 cross-check executed: 7/7 files present; 7 gaps, 6 RQs, 9 goals, 10 phases, 60 tasks, 14 experiments present; ID set consistent (FR-001–FR-035, NFR-001–NFR-010, REP-001–REP-007, EXP-001–EXP-014, MET-01–MET-16, C-01–C-12, G-001–G-009, PH-0–PH-9, T-001–T-095 in ten phase blocks (60 tasks), D-001–D-005, U-01–U-12). One formatting defect found and repaired in `phases.md` (unclosed bold marker in PH-7). No fabricated results present. PH-0 exit criteria met. | AI agent | all seven |

---

### How to use this file in a new session

1. Read `rules.md` (constraints), then this file (§16–§20), then `task.md` (what to do next).
2. Do not repeat completed tasks; do not contradict `DECIDED` records without a new decision record.
3. After any significant action, append to §21 and update the affected sections, `task.md` status, and — if a phase changed — `phases.md`.
