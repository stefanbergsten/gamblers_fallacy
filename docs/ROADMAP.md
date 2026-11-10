# Implementation and Governance Roadmap

**Status:** documentation-only; no actual experiments, statistical verification, CI gate, simulation engine, JEV API calls, Broadcast or Playback runtime have been run in this repository.

## Proposed architecture decisions

- **AGIL-ADR-001:** Specialize UAF-001 v1.7; formally approve normative scope before enforcement. Adopt GF-ARCH-001/002/003/004/004-LC as project implementation requirements.
- **AGIL-ADR-002:** GitHub primary source; GitLab optional supplemental tests. Codex and other agents bound by UAF governance and tool authority. Python/SciPy and GNU R/Octave/GSL are candidates, not presumed installed.
- **AGIL-ADR-003:** JEV optional replaceable typed classification adapter; it neither verifies itself nor controls real-money actions.

## Required UAF gates

| Gate | Work product | Acceptance |
|---|---|---|
| 1 UADC | Human and machine-readable contracts covering all 16 perspectives, required 18 definition properties, versions and test fixtures | valid accepted; invalid rejected |
| 2 Shared identity | agents/models, experiments, trials, work, predictions, decisions, runs, events, claims, evidence, policy versions | missing/duplicate/incompatible references rejected |
| 3 Typed graphs | source ownership, endpoint types, work/agency/control-loop/event/causal/evidence/annotation edges | invalid edges and false verification links rejected |
| 4 Real execution | actual independent seeded simulator and agent prediction/action, pre-outcome record and ledger | reproducible, authorized, inspectable output |
| 5 Independent verification + Broadcast + Playback | passing and intentionally wrong cases, durable evidence, real event publication and replay | false result caught, broadcasts authentic, reconstructed history matches |

Prototypes may be developed in parallel but must be labeled unverified and cannot be promoted while prerequisite gates fail.

## Vertical slice 1

Design GF-001 → pin RNG/theoretical baselines → pre-register metrics → run actual simulator → capture AI prediction before sample outcome → enforce virtual-only action → independently evaluate prediction and ledger → persist evidence → canonical event stream → authorized Broadcast → reconstructed Playback. Include explicitly failing output and missing-evidence negative cases.

## Vertical slice 2

Implement the logic inconsistency contract and formalization provenance. Test contradictory, different-time noncontradictory and ambiguous cases. Compare independent numerical implementations for stochastic calculations as appropriate.

## Vertical slice 3

Verify current JEV APIs, securely configure keys, implement bounded decision adapter with fallback/error behavior, run JEV-VERIFY-001 on blind held-out data, compare rule and LLM baselines. Do not claim observed JEV errors without real retained samples.

## Vertical slice 4

Investigate genuine process adaptation versus independent random failure (GF-PROC-001); record effective interventions and causal uncertainty. Only then evaluate whether a reusable Universal Outcome Verification and Process Intelligence specialization adds measurable value.

## Proposed future layout

`contracts/`, `domain/`, `experiments/`, `src/gamblers_fallacy/`, `tests/`, `studio/broadcast/`, `studio/playback/`, `governance/`. Avoid empty folders pretending verified infrastructure exists.

**Project definition of progress:** independently accepted, evidence-backed capability gates rather than commits, lines of code, dashboards or model invocations.
