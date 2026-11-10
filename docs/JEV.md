# JEV: Candidate Adapter and Experimental Subject

**Adoption status: provisional pilot candidate, not verified or integrated.** Sources inspected: [jev-anything](https://github.com/grandamenium/jev-anything) README, SKILL.md, PLAN-TEMPLATE.md, PROVENANCE.md, technical references 01–04 (10 Nov 2026). This is an independent MIT-licensed skill, **not** official TypeSafe or OpenRouter software. Confirm current capabilities/API/prices against [first-party docs](https://docs.typesafe.ai/) before implementation. Remote API/models have separate terms and are not made open source by the skill license.

The inspected guide describes bounded `noul` (binary), `choice` (fixed list), and `score` (ordered rubric) primitives with probabilistic outputs. It emphasizes that schema-valid output is not guaranteed correct, that confidence can be misleading and that actions, thresholds, escalation and authorization remain in application logic. The guide's catalog is not necessarily an exhaustive statement of current TypeSafe features.

**Promising:** classify candidate reversal/continuation responses, detect/route anomalies, score bounded rubrics, triage cases for independent review. **Not authoritative for:** roulette probability, statistical significance, formal consistency proof, causal explanation, execution authorization or claim verification.

**Proposed first test:** JEV-VERIFY-001 evaluates actual pinned live JEV outputs against independently labeled truth, measuring schema validity, semantic accuracy, valid-but-wrong rate, confidence calibration, error paths, cost and latency. Include blind labels, held-out tests, randomized representative sampling and deterministic/LLM baselines. If API access is unavailable, fake-client integration tests are labeled offline only.

**Proposed GF use:** classify observed agent estimates as `reversal_candidate`, `continuation_candidate`, `baseline_consistent`, `inconclusive_or_out_of_scope`. Classification is a hypothesis, not scientific proof of bias; deterministic baseline may outperform JEV and should be preferred if so.

**Hard rules:** broadcast every authorized request, response, version, decision, error and verifier outcome; Playback shows labels, confidence, contradictions and changes across agent behavior; EvidenceGraph only promotes independently checked claims. Do not expose secret API keys, transmit unnecessary sensitive data, permit live gambling or infer correctness from structured success.

**Validation gate:** preapproved criteria and cost/error model; independently verified labels; real integration and failure tests; held-out accuracy with uncertainty; baseline comparison; stored source/evidence; faithful Broadcast/Playback; applicable UAF gates passed. Until then no scientific capability claim.
