# AGIL Specialized UAF v1.7 Architecture

**Status:** proposed architecture; UAF-001 v1.7 itself is a proposed governance baseline, not yet formally approved or verified in this repository.

## UAF placement

AGIL specializes, without replacing, all 16 UAF perspectives: purpose/value; stakeholders; environment; domain; requirements; capabilities; system; behavior/process; information; communication; execution; intelligence/decision; control/feedback; verification/evidence; security/governance; lifecycle/economics. Cross-cutting AnnotationGraph and Causal/Traceability, plus Sections 26–28 Enterprise AI Universal Control Loop and Agents/Agency/Work, are reused.

The five sequential UAF foundation gates remain mandatory: **(1) UADC human-readable + executable versioned architecture contract → (2) shared stable identity → (3) typed cross-perspective graphs → (4) real authorized end-to-end execution → (5) independent verification/evidence/real Broadcast/historical Playback**. Parallel prototypes are not operationally verified.

## Seven-stage experimental loop

| Stage | AGIL responsibility | Authoritative record |
|---|---|---|
| Environment | independent, pinned seeded simulator and external context | environment/seed/version |
| Filter | permitted history/context, leakage prevention, privacy | policy/filter decision |
| Signal | candidate run/streak/anomaly | event-derived signal |
| Decision | agent forecast and virtual action under agency bounds | pre-outcome decision |
| Execution | actual authorized simulator and virtual ledger | invocation, outcome, state |
| Evaluate | math, calibration, bias, correctness and criteria | independent evaluation |
| Feedback | explicitly permitted policy/memory updates | versioned change and authority |

Broadcast and Playback cover **all seven stages** but neither grants authority or establishes proof. A UI-only demonstration cannot satisfy execution or verification gates.

## Agent and agency model

Experimental AI gambler (predicts/chooses virtual actions), deterministic reference agent (mathematics), behavioral observer (tentative pattern annotation), experiment controller (randomization and controls), independent verifier (separate acceptance evidence), research orchestrator (work, delegation, policy, event scheduling). An agent is not the same thing as a model; capability is not permission. No agent sees future outcomes, modifies reference evidence, verifies itself, or executes real-money bets.

WorkGraph anchors experiment work items. OrganizationGraph/AgencyGraph record roles, authority, autonomy, accountability and event-time policy/delegation. Model/agent IDs, versions, context snapshots, experiment/trial/run/outcome IDs, claims and evidence are shared across graph views.

## Graph architecture and source boundaries

UAF MetaGraph represents desired state; Enterprise Metagraph federates actual work and the seven loop views. EnvironmentGraph, FilterGraph, SignalGraph, DecisionGraph, ExecutionGraph, EvaluationGraph and FeedbackGraph are logical projections. EventGraph stores occurrences and ordering; CausalGraph stores mechanisms/hypotheses with method and limits; EvidenceGraph stores independent measurement, claim testing and provenance; AnnotationGraph anchors questions/discrepancies to exact versioned events. None invent evidence or other graphs' authoritative records.

Examples of typed relations: `DECISION_CONCERNS_WORK`, `DECISION_AUTHORIZED_BY_POLICY`, `EXECUTION_PRODUCES_OBSERVATION`, `EVIDENCE_SUPPORTS_CLAIM`, `ANNOTATION_TARGETS_ENTITY`, `FEEDBACK_REFERENCES_EVALUATION`. Edges require endpoint types, ownership, temporal rules and identity integrity.

## Broadcast and Playback contracts

Each consequential event: stable identity, type, source/run IDs, event/effective/observation/processing times as relevant, model/agent/policy versions, cause/trigger classification, payload reference, outcome/verification status and evidence, authorization and redaction. Broadcast must reflect actual source records, including failures and denied states.

Playback should visualize probability estimates versus true odds, memory/strategy updates, risk exposure, inter-agent decisions, JEV/LLM/rule disagreement, logical contradiction timelines, evidence status, and uncertainty. Explicit modes: history from events; pinned computational re-execution; labeled hypothetical counterfactual. Replay consistency requires tests, not decorative UI.

## Scientific tooling candidates

Python/SciPy for execution, GNU R/Octave/GSL for independent numerical cross-checks, SMT solvers for logical satisfiability, Codex for authorized engineering, GitHub primary source of truth and optional GitLab CI. JEV only as a bounded replaceable decision adapter. Availability, accuracy, licensing, cost and independent performance remain to be tested.
