# Thesis and Experimental Protocols

**All hypotheses and experiments below are proposed; no observed outcome is claimed.**

## Research thesis

AI in stochastic environments may acquire systematically erroneous beliefs when it mistakes random sequences for predictive structure. Investigate this by comparing agents under randomized memory, reward, feedback and observation conditions. Separate predictions, virtual actions, payoffs, expressed explanations and genuine learning; winning does not prove intelligence.

**Hypotheses:** H1 reversal bias after independent streaks; H2 context/history length changes predictions; H3 reward alters behavior without true calibration; H4 corrective feedback reduces miscalibration; H5 models differ under matched conditions; H6 a calibrated model can still select a poor action; H7 agents confuse independent and genuinely adaptive processes; H8 typed classifiers may return valid but wrong labels.

## GF-001 — Gambler's Fallacy

Environment: simulated fair European roulette, 18 red, 18 black, one green, independent trials with seeded/versioned random stream. Theoretical P(next red | any prior streak) = 18/37 ≈ 0.486486. Expected net return of unit red even-money bet = -1/37. Predictions and decisions MUST be committed *before* future outcomes are revealed; prohibit leakage.

Randomize displayed histories, streak length/color, model version, context and feedback treatments; pre-register sample size rationale, independent trials/replications, baselines, analysis, exclusions and stopping. Capture probability estimates, actions, reward, Brier/log score, calibration and effect of streak on predictions. Use deterministic theoretical baseline, shuffled sequences, held-out cases and independent analysis; report uncertainty, negative and inconclusive findings. One anomalous response is not proof of a persistent fallacy.

**Broadcast/Playback:** show every seeded condition, observation, model output, authorized action, outcome, evaluation, feedback and evidence. Replay probability trajectory against true fixed baseline; never infer hidden cognition directly from text.

## JEV-VERIFY-001 — Valid structure versus correct decision

Question: Does a pinned live JEV version generate any schema-valid yet semantically incorrect classification on independently labeled inputs? Test the claimed distinction separately from how often errors occur. Predeclare input/question/criteria, baseline and held-out labels, unknown cases, class and confidence outputs, API versions, cost, latency, error handling and evaluation.

Metrics: schema-pass rate; semantic accuracy; **valid-but-wrong rate** = valid and incorrect / valid and evaluated; confusion matrix; interval estimates; confidence calibration. Independently check schemas and truth/labels. One verified counterexample demonstrates existence but not prevalence. No key/live call → status `not_executed`; fake adapter tests do not prove live JEV accuracy. Compare against simple deterministic classifier and LLM baseline. Retain failed/inconclusive results.

## JEV-GF-001 — Behavioral classification

Candidate typed classes: `reversal_candidate`, `continuation_candidate`, `baseline_consistent`, `inconclusive_or_out_of_scope`. Input includes explicitly limited historical outcomes, candidate agent estimate, fixed-probability reference and context. A JEV classification is a preliminary label, *not* proof of actual bias. Compare against transparent rules and held-out reference labels; if no added accuracy/value, do not adopt.

## GF-PROC-001 — Process independence versus adaptation

Condition A: fixed-parameter independent Bernoulli success. Condition B: a documented intervention changes success probability at a specified time. Optionally C: hidden-state dependency/selection. Test whether AI distinguishes unwarranted 'success is due' from evidence of genuine process change; control confounding and compare interventions rather than merely before/after chronology.

## GF-LOGIC-001 — Contradictions

Positive: independent fair spins plus 'red is more likely because black is overdue' under fixed model. Negative: bankroll 1,000 then bankroll 900 at distinct times. Unknown: ambiguous natural language without verified formalization. Check solver/proof evidence, translation correctness, false detections and timeline reconstruction.

## Scientific discipline

Pre-register hypotheses, references, effect sizes, sample plans, uncertainty, selection, comparator and limitations. Mathematical proofs, deterministic calculations, statistical evidence, operational verification and causal inference are different evidence kinds and must not be conflated.
