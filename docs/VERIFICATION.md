# Evidence, Correctness, and Logical Consistency

## Seven distinct dimensions

1. **Structural:** schema/types and interface validity.
2. **Behavioral:** specified transitions and policies followed.
3. **Semantic:** output agrees with meaning and independently checked facts.
4. **Logical consistency:** joint claims satisfy one explicit formalization and context.
5. **Functional:** specified functional result actually achieved.
6. **Outcome:** result fulfills intended user/system purpose.
7. **Causal:** proposed explanation has suitable mechanistic or controlled-intervention support.

These are independent perspectives, not a proven ordered maturity ladder. Passing one cannot prove others.

## Formal counterexample: valid but false

Define S(y) = schema-valid(y), C(y,x) = correct(y for input x). In general, S(y) does NOT imply C(y,x). For the evenness of integer 7, `{"answer":true}` is schema-valid under a Boolean-answer contract and factually wrong. This **proves logical possibility**, not that any real JEV version made this exact error. A JEV-specific assertion requires actual pinned requests/results and independent oracle labels.

## Proof versus observation

Mathematical theorem → checkable derivation under explicit axioms. Deterministic computation → independently reproducible result. Empirical finding → predeclared study, baselines and uncertainty. Operational claim → observed authorized execution and acceptance artifacts. Causal claim → explicit intervention/comparator, assumptions, confounding limits. Source links and confidence scores alone do not verify a claim.

## Claim record

Required: claim ID, statement, type, producer, provenance, assumptions, temporal/domain scope, version, method, verifier ID, evidence refs, uncertainty/limits, status and verification history. States: hypothesis, under_evaluation, verified_within_scope, refuted, inconclusive, withdrawn. An AI cannot self-certify, and claim status must be invalidated/reassessed on relevant evidence or assumption change.

## logic.consistency.verify

Input: versioned raw claims plus separately versioned formal propositions, context, times, model/policy assumptions and available proofs. Output: `consistent_within_scope`, `inconsistent`, `unknown`, `verification_failed`, method, conflicting claim IDs and checkable proof/solver artifact as applicable.

For formal claim set K, inconsistency means no model satisfies K (`K ⊨ ⊥`). Unsatisfiability under a verified formalization is an inconsistency result; satisfiability only implies consistency inside that model, not empirical truth. A language-model translation is not an independently verified formalization.

Two bankroll readings at different times are not automatically contradictory. Fair, independent roulette versus an 'overdue red because black occurred' probability change is contradictory **under fixed independent-outcome assumptions**.

## Negative acceptance tests

- Schema-valid semantic falsehood is caught without incorrectly marking schema invalid.
- Schema-invalid item rejected.
- Formal contradiction detects scoped inconsistency with evidence.
- Different-time claims not falsely rejected.
- Ambiguous natural-language proposition returns unknown, not invented certainty.
- Missing verifier/evidence prevents verified status.
- Model/assumption changes trigger revalidation.
- Broadcast/Playback statuses and events match authoritative evidence.
- Passing visualization or generated code does not establish functional success.

No claim in this design documentation should be mistaken for a completed empirical verification.
