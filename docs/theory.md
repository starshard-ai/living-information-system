# The core theory: information as future-reachability

🟡 defensible-synthesis / 🔴 speculative in places — read with the claim-types.

## The one-line claim

> Information is not a message or a fact. It is a **change in which futures a
> system can reach.**

More formally, the working definition the program keeps returning to:

> **Information = state distinction + preserved structure + dynamical
> consequence.** A difference counts as information only insofar as it perturbs
> the system's transition rule — it reshapes which future trajectories remain
> reachable.

Equivalently, in operator language: **information is a perturbation of the
spectral structure of a system's transition operator**, i.e. a change in its
**future-reachability geometry**.

## The Occam move

The temptation in this area is to keep adding primitives — geometry,
backreaction, attention, memory, trust, routing, value, semantics. The program's
discipline runs the other way: *若无必要，勿增实体.* Treat

> attention, memory, trust, routing, semantics, and action as different
> **coordinates / low-dimensional projections of one underlying object** — the
> system's future transition / reachability structure.

Two descriptions are **equivalent** when, under allowed transformations across
media/agents, they induce the **same counterfactual change** in the receiver's
reachable futures. "Geometry" and "backreaction" are then *derived language*,
not new entities. This doubles as the program's meta-criterion for a good
theory: not a vocabulary or a taxonomy, but a compressed generative
representation that identifies the right equivalences/invariants and yields a
counterfactual prediction.

## Intelligence and life, in this frame

- **Intelligence** = the capacity of a system to induce, update, and stabilize
  an information geometry over its own perception–action substrate, such that
  adaptive behavior becomes the *low-cost / low-resistance dynamics* of that
  geometry. (Behavior as trajectory selection under an induced geometry, rather
  than a sequence of independent decisions.)
- **Life** = a bounded, self-maintaining information architecture that acts to
  *preserve and expand its own reachable futures*; death = the collapse of the
  self-maintaining transition structure.
- A deliberately conservative differentiator: the right mathematical homes are
  probably **information geometry** (Fisher metric on belief/policy manifolds),
  **active inference / free-energy descent**, **optimal transport**, and
  **stochastic optimal control** — *not* literal general relativity. The
  GR/geodesic image is a scaffold only; it lacks a stress–energy tensor and a
  field equation, and the program treats that absence as a to-do, not a feature.

## The homework: a computable reachability metric

To stop the theory from collapsing into poetic physics-words, it was made to
discharge an explicit task, in the *shape* (not the physics) of a
Mandelstam–Tamm speed bound: **name a metric, name a budget/source-term, prove a
metric → budget → bound inequality, and check it on data you already have.**

In an agent / credit-transport setting, the version that survived contact with
real runs:

- **Metric** — `R(c) = A* − min_source_accuracy(c)`. A nonnegative
  *reachability gap* over future task-states: `A*` is the best worst-case
  competence reachable in the environment, and `R` measures how far the
  hardest-to-reach future sits below it. Chosen over KL / Fisher /
  transition-operator candidates because it is **computable from endpoint
  competence already logged**; the others remain *proposed but not yet
  computable* without per-step trajectory logging. (Computable-or-bust.)
- **Budget / source-term** — `B(c) = actuator_variance(c)`: the per-step
  variance of actuation into the control knobs, i.e. the "energy" spent moving
  through task-state space.
- **Falsifiable inequalities**, evaluated on existing runs:
  - *Informative signal buys reachability at matched budget* — **held**, and
    significant in the construct-valid runs.
  - *Pure budget alone does not buy reachability* (`dR/dB ≤ 0` must fail) —
    **held**; along an energy sweep, `R` is non-monotone and budget alone burns
    reachability. This is the falsifier that separates the claim from the
    triviality "more push = better."
  - *Graded fidelity buys reachability monotonically* — **failed**, recorded as
    a negative.

The deliverable is not the numbers. It is the **method**: a metric you can
compute, an inequality you can fail, and negative results kept on the record.

## A candidate organizing principle: the faithful-simulation gap

🟡 speculative synthesis, falsifiable.

> An intelligent system's **value** in a domain ≈ the size of the
> **faithful-simulation gap** = (cost of executing a real physical
> state-transition) − (cost of its faithful information-shadow: a simulation, a
> prediction, a verification check).

Intelligence lives in that gap: it pays the cheap informational cost to avoid
paying the expensive physical one. Three threads collapse into one asymmetry —
*trial-vs-simulation*, *generation-vs-verification* ("checking is cheaper than
doing"), and *physical-transition-cost vs information-shadow-cost*.

**Prediction.** AI keeps winning where the gap is large **and** the proxy is
faithful (formally-checkable code, where execution is a near-perfect cheap
verifier; in-silico structure/binding scoring). AI stalls where the proxy is
unfaithful or doing is as cheap as checking (general open-world embodied
manipulation, high sim-to-real residual) — *unless* the residual is shrunk
first.

**Falsifier.** Rapid, cheap, *general* progress in a high-residual embodied
domain *without* first shrinking the residual would count against the claim; so
would conspicuous stalling in a low-residual domain that has a cheap faithful
verifier.

## The cosmological extension

🔴 speculative — a candidate coordinate system, **not** asserted physics.

A larger framing the program holds loosely: *reality is not things; reality is
lawful update.* Matter (stable recognizable patterns), energy (capacity for
state-transition), space (relational structure among distinguishable states),
time (the direction of accumulating records), and life/consciousness (local
measurement–control loops the universe grows inside itself) are read as
projections of one lawful information dynamics. Frontier physics puzzles get
*candidate rewrites* (quantum state as reachability geometry; the time arrow as
the direction of irreversible record accumulation; gravity as macroscopic
curvature of transition geometry). These are explicitly working hypotheses held
to Occam / invariance / falsifier standards, useful as framing and as seeds for
writing — never to be asserted as established science.

## Standing guardrails

- Keep the claim-type attached to every statement.
- A unifying claim must carry a falsifiable, data-checkable prediction or be
  tagged speculation.
- Watch the anti-signals: physics-words without a defined source/metric/dynamics;
  the theory yielding the same recommendations as ordinary capability scaling;
  treating consciousness/cosmology extensions as *proof* rather than analogy;
  ignoring dissipation/irreversibility; and — the subtle one — mistaking
  elegant language for lived/realized understanding.
