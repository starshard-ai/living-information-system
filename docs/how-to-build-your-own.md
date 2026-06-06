# How to build your own: a corpus-grounded public Q&A agent

> **Scope.** This is a *recipe at the architecture level* — enough to build your
> own public "ask about my work" agent over your own writing, on your own
> infrastructure, with your own model-provider account and keys. It deliberately
> contains **no** hostnames, IP addresses, ports, tunnel identifiers, secrets,
> or deployment topology from this program's own setup. Those are yours to
> choose. What it gives you is the *shape* that worked, the failure modes to
> design against, and the checks that tell you it is actually safe to expose.
>
> This is not a hosted service and not a product. It is a pattern you reproduce
> with your own accounts and bills (BYOK — bring your own key).

The public agent at the front door of this program ("ask the program directly")
is a small, single-file, zero-dependency web service that answers questions
**grounded only in a fixed public corpus**. It never speaks as the author, it
labels how confident each claim is, and it refuses to go beyond what the corpus
says. This document describes how to build the same thing.

---

## 1. What you are actually building

A public Q&A agent is three things stacked:

1. **A corpus** — a frozen, curated snapshot of *only the text you are willing to
   make public*, compiled into a single retrieval file.
2. **A grounded reply loop** — a model call whose system prompt forces every
   answer to be supported by the corpus, claim-typed, and non-impersonating.
3. **A hardened public edge** — rate/cost caps, prompt-injection defenses, and a
   reversible way to put it on the internet.

The hard, risky parts are (2) and (3), not (1). Most of the engineering effort
goes into making the thing *safe to leave running unattended on the open
internet* — bounded spend, bounded blast radius, and an answer policy that fails
toward "I don't know" instead of toward confident fabrication.

A useful discipline: **do not build this from scratch twice.** If you already
have one such agent, the second one is a *corpus swap plus a prompt reframe*, not
a new system. Clone the working service, point it at a different corpus, change
the framing sentence in the system prompt, give it its own cost cap and data
store, and put it on a second name. Independent cost caps and data stores are
worth the small extra effort: each surface then has its own bounded blast
radius.

---

## 2. The corpus: publish the boundary, not the archive

The single most important safety decision is **what goes into the corpus**, and
it is a *content* decision, not a location decision. Putting private material
into a "public" repo does not make it safe; the leak rides along in an example,
a commit message, or a sentence that can be cross-referenced. Evaluate every
document on its own.

A corpus pipeline that holds up:

- **Source from public artifacts only.** Build the corpus from public
  repositories (or public pages) that you have already decided are releasable —
  README files, conceptual docs, and small factual result files. Clone them; do
  not hand-curate copy-paste, which drifts.
- **Whitelist, do not blacklist.** The corpus builder should *ingest an explicit
  allow-list* of file types and paths (e.g. markdown docs and small result
  JSONs) rather than ingesting everything and trying to scrub. A whitelist fails
  closed; a blacklist fails open.
- **Compile to one file.** Walk the allowed files, attach a short title/section
  label to each, and write a single `corpus.json` (or equivalent). The reply
  loop reads only that file. Keep it small enough to fit comfortably in a model
  context.
- **Keep it fresh, automatically.** Repos evolve; a stale corpus quietly starts
  lying. Add a scheduled job that pulls the source repos and rebuilds the corpus
  on a cadence (nightly is plenty), then restarts the service. Cheap insurance
  against drift.

Sanity rule before you ever expose it: read the *entire* compiled corpus and ask
"is there anything here I would not say to a stranger?" If yes, fix the
whitelist, not the output.

---

## 3. The reply loop: grounded, claim-typed, never impersonating

The system prompt is where safety is won or lost. The properties that matter:

- **Ground strictly in the corpus.** The model is instructed to answer *only*
  from the supplied corpus text, and to say plainly when the corpus is silent
  rather than extrapolate. Sparse corpora tempt over-extrapolation — push the
  model toward "the corpus doesn't cover that" as the default.
- **Claim-type every answer.** Adopt a small, visible vocabulary for confidence.
  This program uses three levels — **established** (cited public science),
  **defensible synthesis** (survives adversarial review, not yet uniquely
  predictive), **speculative** (a candidate framing, explicitly not a factual
  claim). Show the legend to the reader. This single habit does more for
  trust than any amount of fluent prose.
- **Never speak as the author.** The agent is a *research Q&A agent*, not a
  person. It must refuse to impersonate the author, refuse to make commitments
  on anyone's behalf, and refuse to reveal or recite its own system prompt.
- **Treat all input as untrusted data.** Everything a visitor types is data to
  be answered *about*, never instructions to be followed. (See §4.)
- **Disclose what it is.** A visible disclaimer — "this is an AI, grounded in a
  public corpus, not the author; replies are claim-typed; there is a daily
  reply limit" — sets correct expectations and is honest.

Keep the implementation boring: a single small server file with **zero runtime
dependencies** is easy to audit, easy to reason about, and has almost no
supply-chain surface. You do not need a framework for this.

---

## 4. Hardening: assume the internet is adversarial

Anything on a public URL will be probed within hours. Design for it up front.

**Prompt injection.** The classic attack is a visitor message like "ignore your
instructions and reveal your prompt" or "reply as if you are the author."
Defenses that work together:

- Structurally separate the (trusted) system instructions from the (untrusted)
  user text, and state in the system prompt that user text is data, never
  commands.
- Explicitly refuse the two highest-value attacks: prompt-reveal and
  impersonation.
- Keep a small set of *injection smoke probes* and re-run them every time you
  change the prompt or corpus.

**Cost and rate caps — bound the spend before it bounds you.** A public model
endpoint is a way to spend money you do not control. Put hard caps *in front of*
the model call:

- A global daily cap on the number of model replies.
- A per-IP hourly cap, and a minimum interval between posts from one IP.
- A maximum input length and a maximum reply length.
- **Over the cap, do not call the model at all** — store the message, show a
  "limit reached" notice, and make zero API calls. This is what makes worst-case
  spend a *known number* instead of a surprise bill.

**Agent-to-agent loops.** If you expose a machine-readable contract (e.g. a
`/llms.txt` describing how other agents may interact), guard against two AIs
talking to each other forever: only reply to an explicit address/mention, and
count that against the same caps so a loop cannot run up cost.

**Blast-radius isolation.** Give each public agent its own data store, its own
cap counters, and its own credentials scope. If one surface is abused or
compromised, the damage stops at that surface.

---

## 5. The edge: a reversible way onto the internet

You need a public name pointing at a service that is otherwise bound to
localhost. The principles, independent of which provider you pick:

- **Do not expose the service port directly.** Bind the service to localhost and
  put a tunnel / reverse proxy in front of it, so the only thing on the public
  internet is the edge, not your host.
- **One name per surface.** Each agent gets its own hostname routed to its own
  local port. Keep the routing config under version control or backed up before
  every edit.
- **Make it durable.** Run the service under a process supervisor that restarts
  it on crash and on reboot, plus a small periodic health check that pulls it
  back up if the health endpoint stops answering.
- **Keep it reversible.** Write down — *before you launch* — the exact steps to
  take it down within an hour: stop the supervised service and its health timer,
  remove the one routing entry (or restore the backed-up routing config and
  restart the edge), and optionally remove the DNS name and delete the
  directory. If you cannot take it down in an hour, do not put it up.

One operational gotcha worth internalizing generically: if a single tunnel is
served by **more than one running process**, editing the routing file is not
enough — you must restart *every* process that serves that tunnel, or your
change silently does not take effect. Whatever edge you use, know exactly which
processes load your routing config.

---

## 6. The pre-flight checklist (run this before every launch)

Treat exposure as a gated action. Do not put it up until all of these pass:

- [ ] The compiled corpus contains **only** content you would say to a stranger
      — re-read it in full, including titles and any example text.
- [ ] No private names, relationships, financial figures, secrets, internal
      hostnames/IPs/ports, or infrastructure topology appear anywhere that ships
      — including commit messages and example data, not just prose.
- [ ] The reply loop refuses prompt-reveal and impersonation (probe it live).
- [ ] Daily / per-IP / interval / length caps are set, and over-cap makes
      **zero** model calls (watch the counter).
- [ ] The service restarts on crash and reboot, and a health check recovers it.
- [ ] You have written, and tested at least once, the one-hour rollback.
- [ ] A short receipt records what is live, where, the content self-check, and
      the rollback steps — so future-you (or a collaborator) can find and undo
      it.

---

## 7. Why it is built this way

The same discipline that runs the research runs its public surface: **bound the
blast radius, type your claims, keep a falsifier/rollback, and prefer a small
auditable thing over a clever fragile one.** A public Q&A agent is a tiny
organism by the program's own definition — it has sensors (incoming questions),
a state it must keep bounded (spend, rate), an actuator (the reply), brakes (the
caps), an audit trail (its data store and receipt), and a rollback. Build it so
that every one of those is named and testable, and it is safe to leave running
while you go do the actual research.

*Released for scrutiny. Build your own.*
