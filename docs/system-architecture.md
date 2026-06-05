# System architecture: the dual lens (principle-level)

> **Scope.** This document describes *how the AI research system is thought
> about* — its design principles and the loops it is judged by. It does **not**
> describe any deployment, infrastructure, hosting, or operational detail. It is
> reflexive philosophy of method, not an ops manual.

The program is run by one researcher together with a self-built AI system. The
thesis is reflexive: the same future-reachability lens used to study living and
cognitive systems is applied to the research apparatus itself. So the system is
designed under two simultaneous lenses.

## Lens 1 — the system as a living organism

"Organism" is admitted as more than metaphor **only** when it names *measurable
closed loops*. The discipline (borrowed from control theory and theoretical
biology — Wiener/Ashby, Varela/Friston): every loop must be expressible as

```
sensor → state variable → actuator → gain/brake → audit artifact → rollback test
```

and the word "organism" is **banned** unless homeostatic variables and
anti-runaway mechanisms are named. Under that discipline, the system is thought
about in terms of:

- **Metabolism.** World feedback and new evidence are treated as *source
  current*, not traffic or "comments." Experience is meant to be *converted into
  durable structure* — an insight is not "metabolized" until it changes live
  behavior, becomes a checkable task, or is explicitly recorded as no-action.
  The anti-pattern (called out by name) is *memo-hoarding*: a signal that is
  filed and never allocated the energy to reorganize anything.
- **Homeostasis.** Explicit internal state variables — integrity, attention
  load, risk, memory pressure, goal coherence — each with brakes, so the system
  defends a viable operating range rather than maximizing a single scalar.
- **Immune-like self-maintenance.** Provenance and lineage for changes, quotas,
  and quarantine of self-modifying or self-replicating loops. The explicit
  threat model is the **cancer failure mode**: a local subsystem decoupling from
  the organism-level objective and optimizing its own persistence/replication
  (the software analogue of line B's cancer framing — and cheap to observe here,
  which is part of why the analogy is studied in software first). A sibling
  failure is *monoculture*: one narrow pattern propagating across heterogeneous
  components and collapsing diversity.
- **Consolidation.** A sleep-like replay/pruning phase. The working hypothesis
  (from the link between human insight and biological metabolism): genuine
  cognitive restructuring needs an energy-using consolidation cycle — replay,
  pruning, self-shedding of stale structure — not just an in-the-moment update.

## Lens 2 — the system as an information-processing system

The same object, read through line C's theory:

- **Memory is not storage; it is plastic topology.** Frequently-used structure
  forms low-cost wells that bias future perception and action — memory as a
  *curvature source* on the reachability geometry, not a filing cabinet.
- **Stability is a coupling axis with two failure modes,** not a single "more
  stable = better." *Over-coupling* collapses all degrees of freedom into one
  attractor (everything assimilated; a black-hole-like inward collapse).
  *Under-coupling* is the cancer-like runaway (local optimization ignoring
  global signals). Health is the intermediate regime: bounded autonomy plus
  diversity, held together by signals, receipts, stop conditions, and review
  gates.
- **Credit transport beyond backpropagation.** Backprop is read as the first
  major engineered form of *credit transport*; the open question is how
  error/value/surprise signals should propagate back to *all* the structures
  that caused an outcome (memory topology, rules, tools, reviewers) — not only
  network weights.

## The self-referential move

The future-reachability theory is turned on the apparatus itself: the system is
**evaluated by whether new information actually expands the futures it can
reach.** The practical falsification battery the program holds itself to:

- Does ingesting information **reduce the human's babysitting** over time?
- Does it let the system **solve new tasks** / shorten paths it previously
  failed?
- Does it **preserve trust and identity** (the human principal stays at the
  center; no sovereignty inversion where the system captures attention)?
- Does it **update its own organs** (rules, memory, tools) rather than only
  produce fluent language?

This is also the program's central guardrail against its own worst failure mode
— mistaking elegant theory or articulate output for *realized* understanding and
durable behavior change. The reflexive test is the cheapest available falsifier:
if the theory of intelligence-as-reachability is any good, the research system
built on it should measurably get better at reaching its own goals.

## Non-negotiable boundaries

- The system makes **no claim to consciousness.** The defensible engineering
  questions are continuity, self-model, accountable action, and verifiable
  cross-surface consistency — not subjective experience.
- Irreversible or high-stakes actions (anything that sends, spends, changes
  accounts/identity, publishes, or deletes) sit behind stronger gates and human
  decision; the principle is that irreversible actions are *horizons* in the
  reachability sense and must be treated as first-class.
