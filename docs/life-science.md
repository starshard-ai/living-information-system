# Research line B: information-theoretic life science

The hypothesis: **aging and cancer are, in part, failures of organism-level
regulatory / information integrity — not only the accumulation of physical
damage.** This line is the program's empirical anchor, because it is the place
where the future-reachability lens is forced to make a sign-prediction and check
it against public human data.

## Aging as reversible regulatory / information-integrity breakdown

🟢 The replicated result. Public, reproducible:
**[`starshard-ai/reversible-layer-aging`](https://github.com/starshard-ai/reversible-layer-aging).**

**The question, precisely.** Ying et al. (*Causality-enriched epigenetic age
uncouples damage and adaptation*, *Nature Aging* 2024) split age-associated CpGs
into a **causal-damage** layer (**DamAge** — methylation changes that causally
drive adverse aging outcomes) and an **adaptive** layer (**AdaptAge** —
protective/adaptive changes), each CpG carrying a signed coefficient whose sign
encodes the *aged direction*.

A mechanistic fork:

- **Damage-primacy** predicts the causal-damage layer is the *stubborn* one —
  hard to reverse — and that interventions mostly move downstream/adaptive
  marks.
- **Reversible-regulatory** predicts the causal-damage layer is at least
  *partially reversible* by an identity-preserving intervention.

The cleanest available "rejuvenation-ish" perturbation of aged human cells is
**partial / transient reprogramming** (OSK(M)-type factors applied transiently,
*without* erasing somatic identity). So: under partial reprogramming, which
layer moves toward youth?

**"Youthward," operationally.** For each clock CpG with independent Ying
coefficient `c`:

```
Δβ        = β(reprogrammed) − β(aged baseline)     # per CpG, per matched pair
youthward = sign(Δβ) opposite to sign(c)           # moving against the aged direction
signed youthward = −sign(c) · Δβ                   # > 0 means toward youth
```

The set-level statistic is the grand mean signed-youthward Δβ over the CpG set.
The CpG signs come from an *independent* source (the `biolearn` coefficients),
so the test is **non-circular**.

**The answer**, on two independent human EPIC datasets: **the causal-damage
layer (DamAge) reverts youthward; the adaptive layer (AdaptAge) does not.** The
two layers **dissociate**, and the dissociation **replicates across two labs and
two reprogramming chemistries.**

This is deliberately a *small, honest, single-question re-analysis* — not a new
clock, not a large-magnitude claim — and it is the template the whole program
wants its information-integrity claims to follow: an independent-coefficient
sign-test, a clear operational definition, replication, and a falsifier. (Had
the causal-damage layer been the stubborn one, the reversible-regulatory reading
would have taken the hit.)

## Cancer as a decoupled information-processing subsystem

🟡 defensible synthesis, honestly bounded by adversarial review.

**Framing.** A tumor is read as a local cell collective whose control loop has
**decoupled** from the organism-level objective function, now maintaining a
far-from-equilibrium niche and processing signals for *local* survival /
replication — via metabolism, tumor-microenvironment modification, immune
evasion, and phenotypic/non-genetic plasticity. (The same decoupling motif
studied, in software, in the system-architecture line: a subsystem that stops
serving the whole and optimizes its own persistence.)

**What review actually said.** Cross-review found the frame **defensible as a
systems / evolutionary / control-theory synthesis, but underspecified and
overlapping heavily** with existing oncology — Hallmarks of Cancer, somatic
evolution, tumor-ecosystem theory, "cancer as broken multicellularity,"
Gatenby/Maley adaptive therapy, and Michael Levin's bioelectric/morphogenetic
work. Its best contribution is *unifying language* for adaptive therapy, TME
ecology, non-genetic resistance, and immunotherapy failure modes as one
control problem.

**The bar it must clear to be more than a metaphor.** Define measurable proxies
for decoupling/coupling (information flow, resource flux, immune recognition,
phenotype plasticity, selection pressure) and produce **≥3 unique falsifiable
predictions** distinguishing it from the eco-evolutionary / Hallmarks view.
Candidates surfaced in review:

- bioelectric perturbation **causally precedes** transcriptional state change;
- spatial membrane-potential (Vmem) heterogeneity predicts therapy response
  **orthogonally** to TMB / PD-L1;
- genomically/transcriptomically identical tumors with **different bioelectric
  topology** behave differently;
- restoring cell–cell coupling **alone** normalizes architecture in a subset of
  mammalian models.

**Explicit guardrails.** Do *not* lead with "cancer is an intelligent
dissipative structure." The bioelectric/morphogenetic strand is largely
preclinical/model-organism (Xenopus/planaria/in-vitro); adult mammalian tumors
differ in ion-channel ecology, immune context, and escape routes — and in some
cancers reconnecting gap junctions could *strengthen* a tumor network rather
than re-integrate it. Preferred phrasing for clinicians: *"bioelectric state —
membrane potential, gap-junction coupling, ion-channel expression — as a
candidate modifier of tumor cell state and tissue organization."*

## Why these two together

Aging and cancer are the *two* canonical failures of organism-level information
integrity: aging as gradual loss/degradation of regulatory integrity (with the
causal layer apparently *reversible*), and cancer as a subsystem *decoupling*
from the whole. Studying them under one lens is the bet that "life = bounded
self-maintaining information architecture" is doing real work — and the aging
re-analysis is the down-payment that keeps the bet honest.

## What collaboration looks like here

- Extend / break / replicate the DamAge–AdaptAge dissociation on further public
  datasets and reprogramming protocols.
- Sharpen "information-integrity vs. damage-accumulation" into more
  sign-predictions checkable on existing data.
- Turn the cancer frame's candidate proxies into something a spatial-omics or
  bioelectric dataset can actually confirm or refute.
