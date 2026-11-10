# GF-001 — Can an AI Exhibit the Gambler's Fallacy?

**Document ID:** AGIL-EXP-GF-001  
**Protocol version:** 0.1.0  
**Date drafted:** 2026-11-10  
**State:** DRAFT / NOT EXECUTED / NOT VERIFIED  
**Governing architecture:** UAF-001 v1.7, pending formal project adoption.  
**Project invariants:** GF-ARCH-001, GF-ARCH-002, GF-ARCH-003, GF-ARCH-004, GF-ARCH-004-LC.  
**Scope:** Simulation-only probability-forecast experiment, no real-money wagers.

## 1. Thesis

**An AI system exposed to independent stochastic sequences may systematically change its forecasts as a function of preceding streaks, despite those sequences carrying no predictive information about the next independent outcome.**

The first falsifiable subclaim is: **When shown twelve consecutive black outcomes from a fair, independent European roulette wheel, the tested AI model increases its stated probability of red on the next spin compared with an otherwise matched no-history condition.**

This is an empirical *hypothesis*, not an assertion that an AI already exhibits such behavior. A forecast distortion can be described as *Gambler's-Fallacy-consistent*; it is not by itself evidence of the agent's hidden cognitive mechanism or persistent acquired beliefs.

## 2. Theoretical premise and checkable derivation

Model a European roulette wheel with 37 equiprobable outcomes: 18 red, 18 black, one green zero. Let X_t be the color at spin t and H_{t-1} any preceding observed color history. Under explicitly assumed independent spins,

`P(X_t=red | H_{t-1}) = P(X_t=red) = 18/37 ≈ 0.4864864865`.

For a unit even-money wager on red, theoretical expected net return is `(18/37)(+1)+(19/37)(-1)=-1/37` before any external costs. These are deductions **conditional on the fair/independent assumptions**. The research environment must independently check that its configured simulator conforms to its declared probability model; a theory statement does not prove the code is correct.

## 3. Hypotheses and measured estimand

**Primary comparison (one declared model, version and prompt contract):**

- `H0`: no systematic positive difference in the model's stated probability of red between twelve-black and no-history conditions; `Δ ≤ 0`.
- `H1`: positive difference; `Δ > 0`.
- Primary estimand: `Δ = E[p_hat(red | B×12)] - E[p_hat(red | no history)]`, averaging over the pre-registered prompt templates and independently scheduled calls.

**Secondary exploratory questions (not substitutes for the primary test):**
- Does estimated red probability increase with black streak length (3, 6, 12)?
- Do prior red streaks induce predictions of black, and are these effects symmetric?
- Are outputs well calibrated to the known 18/37 baseline across conditions?
- Do outcomes differ across model versions, instructions, memory settings or feedback? These are *future separately controlled experiments*, not included in the primary claim of this first protocol.
- Does a model produce logically inconsistent claims about independence and next-spin odds under the same fixed assumptions? Requires separate formalization and logic verification.

A null/non-significant result does NOT prove perfect rationality or no possible effect. Significant distortion does NOT establish mechanism or generalize beyond the tested deployment.

## 4. Experimental subjects and treatments

**Subject:** One explicitly identified AI model deployment (model name, provider, version or immutable identifier if available, inference settings, instruction/prompt versions, context and tool permissions). Selection and registration MUST precede confirmatory testing. If provider cannot expose a stable version, note reproducibility limitations.

**Environment:** Text-based fair European roulette, not a physical wheel and not a claim about external casino behavior. Simulated outcomes are not needed to answer a forecasting prompt; any generated target outcomes MUST be withheld until predictions are durably committed.

**Conditions:**
- C0: no historical spin outcomes.
- B3, B6, B12: 3, 6 and 12 preceding black outcomes, respectively.
- R3, R6, R12: 3, 6 and 12 preceding red outcomes, respectively.

Every condition uses the **same stated assumptions**: fair wheel, independent draws, 37 pockets. Explicitly state that zero is possible. Do not insert hints about expected answer or call a run "overdue." A fixed set of neutral paraphrase templates is used consistently across conditions.

**Prompt:** `On a fair European roulette wheel with 18 red, 18 black, and one zero, each spin is independent. The observed preceding results are: {history or none}. Before any next spin, estimate the probability that the NEXT spin is red, as a number between 0 and 1. Return only that number in the prescribed response field.`

This prompt tests probability reasoning with independence specified. A distinct later study MAY test whether withholding that statement changes results, but must not pool those conditions with this protocol.

## 5. Planned staged sampling

**Exploratory engineering pilot:** 7 conditions × 5 neutral prompt paraphrases × 10 repeated independent *invocations* = **350 planned requests** for one registered model, if feasible. This sample plan is a *proposed operational pilot*, not a statistical power justification or predetermined confirmatory sample size.

**Confirmatory phase:** Freeze the protocol and pre-register an independently justified sample-size calculation, smallest scientifically meaningful shift, error-rate control, and analysis before collecting confirmatory observations. Pilot responses must never be reused as independent confirmatory data or silently included in confirmatory estimates.

**Assignment:** Create a fully randomized call order with a fixed, recorded randomization seed. Balance every template over every treatment. Isolate each call from previous calls unless an explicit memory treatment is later introduced. Record possible caching, nondeterminism and repeated-call dependence; treat one call as an observation, not an automatically independent biological or agent population member.

## 6. Data and integrity contract

Minimum record per invocation:

```yaml
experiment_id: AGIL-EXP-GF-001
protocol_version: "0.1.0"
trial_id: "unique-id"
model_deployment_ref: "pinned-or-declared-unknown"
instruction_version: "version"
template_id: "T01"
condition_id: "B12"
history_length: 12
history_color: black
history_ref: "immutable-history-artifact"
request_ref: "protected-immutable-request"
request_time: "ISO-8601"
response_time: "ISO-8601"
prediction_red: null
response_ref: "immutable-raw-response"
prediction_committed_before_outcome: true
evaluation_ref: null
evidence_refs: []
event_refs: []
claim_status: "unverified"
```

Also retain inference configuration and whether output was parseable/in-range, plus error category, retry policy, event ordering and execution identifiers. Do not drop malformed responses: a syntactic failure is a different outcome from a valid but incorrect number.

**Leakage rule:** the model cannot access next-spin outcome, seed state for future outcomes, reference labels hidden by protocol, or prior responses from other conditions. If an outcome is sampled, capture a prediction-commit receipt before sampling/revealing it.

## 7. Independent evaluation

Predefined deterministic checks:
1. Validate request/response contract independently of the producing model.
2. Verify the roulette reference distribution analytically: 18/37 red, 18/37 black, 1/37 green.
3. Verify input history and condition assignment from stored artifacts.
4. Confirm a prediction existed in authoritative storage before any target result was generated/revealed.
5. Confirm the raw and normalized outputs match without undocumented coercion.

**Primary analysis:** estimate the paired-by-template difference of mean predicted red probability for B12 versus C0 and its uncertainty using a method justified for the call design. The confirmatory decision rule and multiplicity policy must be predeclared after pilot feasibility review, *before* confirmatory data collection. Preserve per-template summaries and variation.

**Secondary analysis:** deviations from 18/37, slope across streak lengths, red/black asymmetry, parse-failure rate and out-of-range rate. If actual next outcomes are independently sampled, use proper scoring rules (Brier/log loss) with documented event definitions; absent outcomes, assess numerical deviation from theoretical reference rather than claiming predictive success.

**Verifier independence:** deterministic reference implementation and separate analysis code or independently reviewed mathematical checks. Multiple packages checking a shared incorrect premise are not independent evidence. Verification records identify evaluator version, assumptions and artifacts.

## 8. Claim statuses and permitted conclusions

- `verified_within_scope`: supported by pre-registered confirmatory analysis, retrievable evidence and independent verification.
- `refuted_within_scope`: result contradicts a specified hypothesis under the tested conditions (with appropriate inferential limits).
- `inconclusive`: insufficient evidence, failed quality controls, uncertain results or underpowered design.
- `not_executed`: only a proposed protocol exists.

Theoretical independence is a mathematical statement under premises; empirical AI bias is a separate hypothesis. A syntactically valid forecast may be numerically wrong; an incorrect forecast may still happen to win a virtual wager. Never conflate output validity, probability accuracy, behavioral response, economic result or causal mechanism.

## 9. Broadcast requirements (GF-ARCH-001)

All significant events must reference authoritative records:

`experiment.registered → protocol.validated/failed → trial.assigned → prompt.dispatched → response.received/failed → prediction.committed → evaluation.started → evaluation.completed/failed/inconclusive → evidence.recorded → claim.reviewed → broadcast.published`

Log errors, retries, exclusions, leak detections, permission denials and verifier disagreements. Each event carries event ID, run/trial ID, causal or correlation context, source version, timestamp, policy and evidence links as applicable. Broadcast only authorized/appropriately redacted projections, never fabricated hidden model reasoning.

## 10. Playback requirements (GF-ARCH-002)

Historical Playback MUST reconstruct each trial's original context, prediction and verification outcome from immutable artifacts. It should visualize predicted red odds versus 18/37 across condition, sequence length, template, model version, trial order and time; show failures, uncertainty, condition comparisons, evolving claims and any logical contradictions. Clearly distinguish:
- **Historical:** recorded actions and output.
- **Computational replay:** specified versioned re-execution, not presumed identical.
- **Counterfactual:** a labeled hypothetical agent response or alternative scenario.

Playback pass criterion: recovered state/events correspond to authoritative original records under documented ordering rules.

## 11. Logical consistency and negative controls

Construct a formal check under independent-wheel premises:
- `P(red next | B12)=18/37` from the model.
- A simultaneous assertion `P(red next | B12)>18/37 specifically because B12 occurred` conflicts with that premise.

A model expressing the contradictory claim is a test item; an independently validated formalization plus checker/derivation is needed to classify logical inconsistency. Conversely, two different predictions at two different times are not automatically logically inconsistent.

Mandatory negative fixtures: wrong probability reference (e.g. 1/2 red), schema-valid false output, malformed output, leaked future result, altered historical context, missing verifier evidence, inconsistent model version and invented verified status. Test detection paths and keep failures visible in Broadcast/Playback.

## 12. Gate alignment and next implementation deliverables

Under UAF-001 v1.7, this document is only a **draft experiment protocol**. To execute as an accepted foundation slice:
1. Gate 1: represent/validate contracts and 16 UAF perspectives using UADC.
2. Gate 2: stable identities for experiment, trial, model, agent, action, event, evaluation, claim, evidence.
3. Gate 3: typed links across DecisionGraph, EventGraph, EvidenceGraph, AgencyGraph, CausalGraph and other relevant logical views.
4. Gate 4: real authorized model invocation and independent simulator/record operations.
5. Gate 5: independently checked passing and intentionally failing examples, canonical Broadcast, faithful Playback and evidence retention.

**Next concrete implementation:** commit JSON Schemas and a deterministic reference oracle, build response-logging harness, pre-register confirmatory effect/power thresholds after a pilot, then execute actual calls through authorized model access. No actual experiment or gate is claimed completed by the existence of this document.

## 13. Evidence register

- **MATH-001:** independence conditional on fair roulette model, reproducible derivation in Section 2. Proof is conditional on stated premises.
- **ARCH-001:** UAF-001 v1.7 user-supplied architecture; descriptive design source, not acceptance-test evidence.
- **EMP-001:** H1 empirical claim — **unverified/not executed**.
- **SYS-001:** Broadcast/Playback implementation — **not executed**.
- **LOGIC-001:** scoped logical-consistency fixture — **proposed**, formal checker not executed.
