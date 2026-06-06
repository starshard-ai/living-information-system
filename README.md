# Living Information System

*A one-person, AI-assisted, interdisciplinary research program.*

**Macheng Shen — independent researcher.**
Contact: GitHub issues on this repo, or [machengshen.github.io](https://machengshen.github.io).

**Ask the program directly:** [ask.clawishmacheng.com](https://ask.clawishmacheng.com)
— a public Q&A agent grounded *only* in this repository and
[`reversible-layer-aging`](https://github.com/starshard-ai/reversible-layer-aging).
It answers questions about the research, claim-types what it says
(🟢 established / 🟡 defensible / 🔴 speculative), and refuses to speculate
beyond the public corpus.

---

## What this is

This is the public front door to a research program run by one independent
researcher working together with a self-built AI system. The program is
organized around a single thread:

> **Information — its *future-reachability*, and how it is preserved and
> transformed in physical, living, and cognitive systems.**

"Future-reachability" is the working name for the object this program keeps
returning to: the claim that the useful content of *information* is not a
message or a fact, but **a change in which futures a system can reach**. A bit
of information matters to the extent that it perturbs the system's transition
structure — it opens some future trajectories and closes others. Physics,
biology, and cognition are then studied as three regimes of the *same*
question: how is reachability created, stored, degraded, and repaired?

The program is run as a small, honest operation. It does not own a wet lab. Its
edge is **cross-domain synthesis plus falsifiable re-analysis on public data** —
taking an idea that recurs across fields and forcing it to make a prediction
that can be checked against data that already exists. Speculation is allowed,
but it is *labelled* as speculation; claims that touch real data are expected to
carry a falsifier.

This README is the map. The research lines, the theory, and the dual lens on
the AI system itself are below. Deeper notes live in [`docs/`](docs/).

---

## Why it is organized this way

Most research is organized by *field*. This program is organized by *one
question asked across fields*, for two reasons:

1. **A single researcher cannot out-specialize a field.** The available edge is
   not depth in one silo; it is the ability to notice when the same structural
   move appears in physics, in aging biology, and in machine learning, and to
   make that move pay rent in the form of a checkable prediction.
2. **The AI system is part of the method, not just a tool.** The same
   future-reachability lens used to study living systems is turned back on the
   research apparatus itself (see [System architecture](#system-architecture-the-dual-lens)).
   The program is, in part, a long experiment in whether a self-maintaining
   information system can do durable research without losing the human at its
   center.

---

## Research lines

### A. Frontier theoretical / foundational physics

A conservative, literature-grounded entry into foundational physics through one
lens: **what is fundamental may be the structure of lawful state-update and
information, with matter / energy / space / time read as stable projections of
it.** This is treated as a *candidate coordinate system / research program*, not
a claimed final theory, and it is disciplined by hard constraints (Lorentz
invariance, unitarity, no-signaling, thermodynamics, known experimental bounds).

Questions the program actually cares about:

- **Information and the holographic / boundary picture.** Modern theoretical
  physics (Bekenstein–Hawking area-entropy; AdS/CFT; the post-2020 Page-curve
  resolution via entanglement wedges; ER=EPR; tensor-network reconstructions of
  spacetime) increasingly treats black holes and even spacetime as
  *phenomenological faces of more fundamental information structure* rather than
  as primitives. The program studies these as established anchors, and asks
  where a reachability/transition reading adds anything beyond restating them.
- **A candidate structural isomorphism: information-density saturation → horizon.**
  A speculative (and explicitly flagged) line: a Bekenstein-style bound on
  information density in a finite region, and a "cognitive cone" bound on how
  fast an agent can compress and propagate information through itself, may both
  be instances of *the same motif* — saturate an information-density ceiling in
  a finite region and you get a causal or epistemic horizon. Status: suggestive
  shape, not a proven mapping.
- **Discipline over cosmology.** The standing rule on this line is to *resist*
  expanding into a grand "theory of everything." The bottleneck is observables
  and falsifiers, not more vocabulary. A good theory is judged by whether it
  finds the right equivalences/invariants and yields a counterfactual
  prediction — not by how many phenomena it can re-narrate.

See [`docs/physics.md`](docs/physics.md).

### B. Information-theoretic life science

The hypothesis: **aging and cancer are, in part, failures of organism-level
regulatory / information integrity** — not only the accumulation of physical
damage.

- **Aging as reversible regulatory / information-integrity breakdown.** Public
  artifact, replicated:
  **[`starshard-ai/reversible-layer-aging`](https://github.com/starshard-ai/reversible-layer-aging).**
  Question: under partial/transient epigenetic reprogramming, which methylation
  layer moves toward youth — the *causal-damage* layer (DamAge) or the
  *adaptive* layer (AdaptAge)? Result on two independent human EPIC datasets:
  **the causal-damage layer reverts youthward; the adaptive layer does not**, and
  the dissociation **replicates across two labs and two reprogramming
  chemistries.** Built non-circularly on Ying et al.'s DamAge/AdaptAge clocks
  (*Nature Aging*, 2024) via the `biolearn` coefficients. It is deliberately a
  small, single-question, honest re-analysis you can reproduce from public data
  in minutes — not a new clock and not a large-magnitude claim. This is the
  template for what "information-integrity" claims should look like: a sign-test
  with an independent coefficient and a falsifier.
- **Cancer as a decoupled information-processing subsystem.** Framing: a tumor
  is a local cell collective whose control loop has *decoupled* from the
  organism-level objective and now optimizes local survival/replication
  (metabolism, microenvironment modification, immune evasion, phenotypic
  plasticity). This is positioned honestly — adversarial review found it
  **defensible as a systems/evolutionary/control synthesis but underspecified
  and overlapping heavily with existing oncology** (Hallmarks, somatic
  evolution, Gatenby/Maley adaptive therapy, tumor ecology, Levin's bioelectric
  work). It earns its keep only if it produces *measurable proxies* for
  decoupling and ≥3 unique falsifiable predictions (e.g. bioelectric
  perturbation causally *preceding* transcriptional state change; spatial
  membrane-potential heterogeneity predicting response orthogonally to
  TMB/PD-L1). The slogan "cancer is an intelligent dissipative structure" is
  *not* used as a primary claim.

See [`docs/life-science.md`](docs/life-science.md).

### C. The core theory — intelligence / life via future-reachability

The unifying line the other two lines feed:

- **Information = a perturbation of a system's transition structure** — a change
  in the spectral structure of its transition operator, equivalently a change in
  its **future-reachability geometry**. Memory, attention, trust, routing,
  semantics, and action are read as *coordinate projections* of that one deeper
  object (an Occam move: fewer primitives doing more work, related descriptions
  counted equivalent when they induce the same counterfactual change in reachable
  futures).
- **Intelligence = the capacity to induce, update, and stabilize that geometry**
  so that adaptive behavior becomes the low-cost dynamics of the geometry; **life
  = a bounded, self-maintaining information architecture** that acts to preserve
  and expand its own reachable futures.
- **A computable reachability metric (checked, claim-typed).** To keep this from
  staying a metaphor, the theory was forced to discharge an explicit "homework":
  *name a metric, name a budget/source-term, prove a metric→budget→bound
  inequality* (the shape, not the physics, of a Mandelstam–Tamm-style speed
  bound). The version that survived contact with real data, in an
  agent/credit-transport setting:
  - **Metric** `R(c) = A* − min_source_accuracy(c)` — a nonnegative
    reachability *gap* over future task-states (how far the worst-reachable
    future is from the best achievable). Chosen because it is computable from
    endpoint competence already logged, where KL/Fisher/transition-operator
    variants are *proposed but not yet computable* from current data.
  - **Budget / source-term** `B(c) = actuator_variance(c)` — the "energy" spent
    moving through task-state space.
  - **Falsifiable inequalities, checked on existing runs:** informative signal
    buys reachability at matched budget (held, significant); *pure budget alone
    does not* buy reachability (held — the key falsifier separating the claim
    from "more push = better"); *graded* fidelity buying reachability
    monotonically (**failed** — recorded as a negative).

  The point is not the specific numbers; it is the **discipline**: a metric you
  can compute, an inequality you can fail, and negatives kept on the record.
- **A candidate organizing principle — the "faithful-simulation gap."** A
  speculative-but-falsifiable synthesis: an intelligent system's *value* in a
  domain ≈ the size of the gap between the cost of executing a real physical
  state-transition and the cost of its faithful information-shadow (a
  simulation, a prediction, a verification check). Intelligence lives in that
  gap — it pays the cheap informational cost to avoid the expensive physical
  one. Prediction: AI keeps winning where the gap is large *and* the proxy is
  faithful (formally-checkable code; in-silico structure/binding scoring) and
  stalls where the proxy is unfaithful (open-world embodied manipulation with
  high sim-to-real residual) — *unless* the residual is shrunk first.

See [`docs/theory.md`](docs/theory.md).

---

## System architecture (the dual lens)

*Principle-level only. This section describes how the AI research system is
**thought about**, not how any deployment is wired.*

The AI system that assists this program is designed under two simultaneous
lenses, because the research thesis is reflexive — the same theory used to study
living and cognitive systems is applied to the apparatus itself.

**Lens 1 — the system as a living organism.** Not as decoration, but as a
checklist of *measurable closed loops*. A system earns the word "organism" only
if it names: sensors → state variables → actuators → gain/brake → audit trail →
rollback. Concretely the program thinks in terms of:

- **Metabolism** — world feedback and new evidence treated as *source current*,
  not traffic; experience converted into durable structure rather than hoarded.
- **Homeostasis** — explicit internal state variables (integrity, attention
  load, risk, memory pressure, goal coherence) with brakes against runaway.
- **Immune-like self-maintenance** — provenance, lineage, quotas, quarantine of
  self-modifying loops, and an explicit defense against the *cancer failure
  mode*: a local subsystem that decouples from the whole and optimizes its own
  replication. (This is the same decoupling studied in line B — studied here in
  software, where it is cheap to observe.)
- **Consolidation** — a sleep-like replay/pruning phase, on the hypothesis that
  genuine restructuring needs an energy-using consolidation cycle, not just an
  in-the-moment update.

**Lens 2 — the system as an information-processing system.** Memory is not
storage but *plastic topology* that changes future behavior; an insight is not
"metabolized" until it changes live behavior, becomes a checkable task, or is
explicitly recorded as no-action. Stability is treated as a coupling axis with
*two* failure modes at the extremes — over-coupling (everything collapses into
one attractor) and under-coupling (cancer-like local runaway) — with health in
between.

**The self-referential move.** The future-reachability theory is used to
*optimize the system itself*: the research apparatus is evaluated by whether new
information actually expands what futures it can reach (does it reduce the
human's babysitting, solve new tasks, preserve trust/identity, and update its
own organs) rather than by whether it produced fluent language. This is also the
program's main guardrail against its own failure mode — mistaking elegant theory
for realized understanding.

See [`docs/system-architecture.md`](docs/system-architecture.md).

---

## A note on epistemic discipline

This program is interdisciplinary and unafraid of large claims, which is exactly
why it tries to be strict about *claim-typing*:

- 🟢 **established** (cited public science),
- 🟡 **defensible synthesis** (a framing that survives adversarial review but is
  not yet uniquely predictive),
- 🔴 **speculative** (a candidate coordinate system / vision, explicitly not a
  factual claim).

Physics-as-information, cancer-as-decoupled-computation, and the cosmological
"reality as lawful update" framing are 🔴/🟡 and labelled as such. The aging
re-analysis is the 🟢 anchor. The standing rule: a unifying claim must either
carry a falsifiable, data-checkable prediction or be tagged speculation — and
elegant-but-empty theory is something the program actively tries to cut.

---

## Call for collaboration

This is a small operation looking for people who find this thread worth pulling.
Specifically:

- **Theoretical / foundational physicists** — to tell us where a
  reachability/transition reading is genuinely load-bearing versus merely a
  restatement, and to keep the physics honest against unitarity / no-signaling /
  thermodynamics.
- **Aging & epigenetics researchers** — to extend, break, or replicate the
  DamAge/AdaptAge dissociation, and to sharpen the "information-integrity vs.
  damage-accumulation" predictions on public data.
- **Cancer / systems-biology researchers** — to turn the
  decoupled-information-processing frame into measurable proxies and to
  adversarially test whether it predicts anything the Hallmarks/eco-evolutionary
  view does not.
- **Information-theory / ML people** — on the reachability metric, credit
  transport beyond backpropagation, and consolidation/replay dynamics.
- **The curious** — anyone who wants to argue with the framing, point at a
  paper, or break a claim. Disconfirmation is welcome and counts as a
  contribution.

**How to reach:** open a [GitHub issue](../../issues) on this repo (the best
place — it is the public square for this work), ask the corpus-grounded Q&A
agent at [ask.clawishmacheng.com](https://ask.clawishmacheng.com), or visit
[machengshen.github.io](https://machengshen.github.io).

---

## Public artifacts

- **[`starshard-ai/reversible-layer-aging`](https://github.com/starshard-ai/reversible-layer-aging)**
  — the replicated DamAge/AdaptAge dissociation result; reproducible from public
  data.
- This repository — the program's map and conceptual documentation.
- **[`ask.clawishmacheng.com`](https://ask.clawishmacheng.com)** — a public,
  corpus-grounded Q&A agent over these artifacts.
- **[`docs/how-to-build-your-own.md`](docs/how-to-build-your-own.md)** — how the
  public-facing parts of this program are built, so you can run your own.

*Released for scrutiny.*
