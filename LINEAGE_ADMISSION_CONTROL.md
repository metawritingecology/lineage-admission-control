# Lineage Admission Control for Multi-Agent Review

**Status: PUBLISHED CANDIDATE surface — not a confirmed component of any
system. Maturity: operator-derived, operationally exercised, externally
unvalidated. All rules are procedural today (see the rule register and
enforcement-maturity sections).**

Provenance of this text: it passed a three-round external adversarial
review gate (two REVISE rounds, then READY_TO_PUBLISH from a third,
previously unexposed reviewer lineage) on 2026-08-21, with every cited
source verified. Its claims of absence are bounded to the documented
search scope stated below.

## The problem this names

When several AI models review the same artifact, the value of their
agreement depends on their independence, and their independence is bounded
by their ancestry. Two review calls served by the same underlying model
through different products, interfaces, quota pools, or machines are one
opinion purchased twice. Evidence, with its scope stated: for
independently developed SOFTWARE VERSIONS, coincident failures exceed
independence-model predictions (Knight & Leveson 1986 — analogic, not
about models); for LLMs specifically, error correlation is measurably
higher for same-developer and same-base-architecture models (arXiv
2506.07962) and nominal nine-judge panels carry roughly two effective
votes (arXiv 2605.29800) — correlation evidence, which this document
converts into a conservative accounting rule, not a universal law. The
published LLM field measures and reweights (arXiv 2604.07650) or targets
verification by decision margin (arXiv 2608.06940); diversity advice
remains a soft preference. Nothing published enforces ancestry-keyed
admission control at panel time — a claim made within the documented
search scope below, not absolutely.

## What this document claims

A domain transfer, stated as such: admission-control shapes that exist
elsewhere (provenance-conditioned artifact acceptance in supply-chain
verification; threshold authorization that grants no credit to unknown
identities; the conservative treatment of undemonstrated independence in
functional-safety practice — no clause-level equivalence claimed) applied
to the REVIEWER PANEL of a multi-agent workflow, keyed on model ancestry.
The transfer's content is the rule set below operating together. Search
scope for the "unpublished" claim: English-language web, arXiv, and
framework documentation, surveyed 2026-08-21 at medium depth with
recorded queries; a claim of absence bounded by that scope.

**What this is relative to behavioral measurement — stated precisely.**
Behavioral-entanglement auditing (arXiv 2604.07650) estimates OBSERVED
dependence between models without needing their ancestry, and needs no
cooperation from providers. This document is not a competing estimator
and does not claim ancestry predicts dependence better than measurement.
It is a FAIL-SAFE CERTIFICATION POLICY for the complementary situation:
when evidence of independence is insufficient — ancestry unresolved,
behavior unmeasured, or both — the panel is not certified as independent.
An estimator answers "how dependent are these reviewers?"; this policy
answers "what may be certified when that question cannot yet be
answered?". The two compose: a behavioral estimate, where available, is
exactly the kind of evidence that can upgrade a pair from UNDEMONSTRATED.

## The mechanism

**Layer 0 — identity vs independence, kept separate.** A lineage IDENTITY
is the pair (base model, tuning chain); distillation binds to both teacher
and student chains. Distinct identities are NOT thereby independent:
INDEPENDENCE is a separate pairwise relation, and two identities sharing a
base, a teacher, or (where known) dominant training data are DEPENDENT.
A fine-tune therefore creates a new identity that is always dependent on
its base — which is why it never refreshes anything. A new base model
creates a candidate identity whose independence from existing lineages is
UNDEMONSTRATED until assessed — never assumed from novelty (same-developer
and shared-data correlation persists across bases). A provider-side update
to a served base model renders the served identity UNRESOLVED under rule 2
until re-resolved — the update case routes to the fail-closed branch,
never to silent continuity.

1. **Route identity.** A review route is (interface, lineage identity).
   Interface carries zero independence credit; one lineage reached through
   two interfaces is one reviewer.
2. **Fail-closed on unknown.** A route whose lineage identity cannot be
   resolved at dispatch contributes ZERO to the panel's independence
   count. If the resolved count cannot meet the review's declared floor,
   the review is not certified as independent. An unresolved-lineage
   reviewer MAY still be run for its usefulness, under a QUARANTINE rule:
   its findings are recorded as leads and may not influence a certified
   decision until independently reproduced by a counted reviewer.
   (Usefulness and countability separated; the laundering path — authority
   smuggled back through adoption — is closed by the reproduction
   requirement, not by trust.) Operators preferring strict exclusion lose
   nothing in the accounting.
3. **Non-composition.** Independence is pairwise and does not compose;
   the count of pairwise-independent resolved lineages is an UPPER BOUND
   on achieved independence, never its measure (shared data, architectural
   convergence, and benchmark optimization remain uncounted).
4. **Blind first-read depletion.** Within one review subject, each lineage
   that has read the material is SPENT for BLIND FIRST-READS of it — a
   statement about blindness eligibility, not about that lineage's
   independence from others, which is unchanged. Blind-first-read capacity
   is an inventory that saturates; saturation (execution capacity
   remaining, blind-first-read capacity exhausted) is a declared planning
   state. A fallback route through another interface to a spent or
   unknown lineage restores availability, never eligibility.

## Rule register

| Rule | State | Enforcement today |
|---|---|---|
| Layer 0 (identity & dependence definitions) | EXPERIMENTAL | procedural |
| 1 — interface zero credit | HEURISTIC | procedural |
| 2 — fail-closed + quarantine | HARD (mechanically checkable once a ledger exists) | procedural |
| 3 — non-composition upper bound | HARD (definitional) | procedural |
| 4 — blind first-read depletion | HEURISTIC | procedural |

States follow a four-value vocabulary (mechanically-checkable HARD /
operating-judgment HEURISTIC / owner-reserved OWNER / under-observation
EXPERIMENTAL); promotion between states requires evidence, not
familiarity. Extending or reclassifying rules is reserved to the
operating owner.

## Minimal implementation (conceded, welcomed)

These rules are SEMANTICS, not an apparatus. A signed allowlist of
resolved lineage identities plus an append-only per-subject usage ledger
implements every rule above; a reviewer proposed exactly that, and it is
accepted as the reference implementation shape rather than refuted. What
the semantics add over an unadorned allowlist is the layer-0 separation,
the zero-credit and quarantine rules, and the depletion state — properties
a list alone does not express but a list plus ledger can enforce.

## What this is NOT

Not a diversity heuristic; not a correlation estimator; not a claim that
resolved-and-distinct implies independent (layer 0); not a cost policy
(qualification precedes cost, and no price consideration relaxes the
rules); not an enforced system — see maturity.

## Relation to prior art (acknowledged, by name)

Empirical: Knight & Leveson 1986 (software N-versions, analogic); arXiv
2506.07962; Correlated Errors in LLMs (Kim et al., ICML 2025 — 350+
models; correlation tracks shared architecture and provider, AND remains
high among capable models across different architectures, which is
precisely why rule 3 treats the lineage-distinct count as only an upper
bound); Nine Judges, Two Effective Votes (arXiv 2605.29800).
Deliberate family diversity in panel design: PoLL (arXiv 2404.18796,
2024 — disjoint model families as jury composition; a design preference,
not an admission gate). Measurement/reweighting: arXiv 2604.07650.
Margin-keyed normative turn: arXiv 2608.06940. Claim-level graded
provenance with serve/review/quarantine routing in multi-agent systems:
the Isnad-Rijal framework (arXiv 2607.24117) — its serve/review/
quarantine routing uses a chain(narrator)-grade × content-assessment
decision matrix, with transmitter reliability graded per domain; this
document's quarantine gates REVIEWER ANCESTRY RESOLUTION. Shared
vocabulary, different admission key; acknowledged, not claimed. Transferred shapes:
SLSA-class provenance verification (enforcement is verifier policy, not
automatic — noted); TUF/in-toto threshold authorization (keys, not
ancestry); conservative undemonstrated-independence treatment in
functional-safety practice (stated generically; no clause citation
claimed). Soft-preference practice: the Jury Pattern and multi-model
review guidance (2026). Attestation substrate: AIBOM / SPDX 3.0 AI
Profile / CycloneDX ML-BOM.

## Enforcement maturity (self-disclosure)

Every rule is procedural today. Bypass paths: undisclosed aggregator
re-routing (upstream changes without notice — recheck on upstream change);
self-reported lineage without attestation; prose accounting. To become
enforced: a machine-checkable ledger consumed at dispatch;
attestation-backed identity claims; a dispatcher that refuses. None ships
here, and nothing in this document should be read as claiming otherwise.

## Possible relations (not asserted)

This surface emerged from one operating practice in parallel with other
candidate surfaces: lineage-aware-agent-governance, disclosure-order-review, falsifiability-first-protocol, claim-strength-profile, scoped-rejection. Common origin is the only relation asserted.
Composition, dependency, or a unified framework among any of them is
possible and deliberately NOT asserted; no confirmed relation exists, and
none should be inferred from co-ownership, shared vocabulary, or
structural resemblance. Read under a weakest-compatible-relation default:
navigation adjacency. If a composition is ever established it will be
stated explicitly; absence of that statement means it has not been.

## Public / internal boundary

This surface does not expose the operating system behind it: no
operational records, dispatch histories, route or account availability,
internal registries, or infrastructure topology appear here. The
non-inference runs both ways: absence from this surface does not imply
absence internally, and nothing published here is sufficient to
reconstruct the internal system.

## Fork / derivative boundary

Source provenance is not inherited authority, and attribution is not
endorsement. A derivative of this document may preserve provenance while
developing different operational logic; downstream decisions to formalize,
remove, automate, or replace any rule belong to the derivative system and
must not be attributed upstream.

## Review questions (refutation invited)

1. Name a public framework computing reviewer-panel independence from
   model ancestry with zero credit for unresolved identities. That defeats
   the transfer claim within any scope.
2. Does the quarantine rule actually close the adoption-laundering path,
   or does reproduction by a counted reviewer inherit the uncounted
   reviewer's framing (an anchoring channel)?
3. Is layer 0's dependence relation decidable in practice for closed
   models — and if it fails closed on most pairs, does the mechanism
   degrade into "one reviewer per developer"? Is that degradation wrong?
4. Should blind-first-read depletion (rule 4) carry a decay horizon tied
   to material change of the subject?
5. A simpler structure producing equivalent assurance is a successful
   challenge; the minimal-implementation section states our current best
   candidate — improve on it.

Negative findings are relevant findings.
