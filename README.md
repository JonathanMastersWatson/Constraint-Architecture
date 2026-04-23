# Constraint Architecture

This repository defines **Constraint Architecture**: the upstream
discipline that exists because execution has crossed a physical boundary.

As AI and agentic systems operate at machine speed, traditional
governance models fail. Review arrives too late. Escalation becomes
narrative. Authority exercised during execution no longer functions.

What survives is constraint.

This repo establishes the **language, primitives, and roles** required
to design systems that remain coherent when execution outruns human
intervention.

Governance is not achieved by observing behaviour.
It is achieved by constructing the boundaries within which
behaviour is possible.

---

## What Constraint Architecture Is

Constraint Architecture is the practice of defining **what is allowed
to execute before execution occurs**, and **what evidence is produced
after execution completes**, in systems where runtime human control
is physically impossible.

It is not about:

- models
- alignment techniques
- monitoring
- dashboards
- optimisation
- policy interpretation

It is about:

- execution admissibility
- pre-committed authority
- irreversibility
- evidence
- structural clarity under scale

---

## The Core Problem

For most of human history, authority functioned because execution was
slow enough for humans to intervene.

A supervisor could stop a machine.
A banker could pause a transfer.
A pharmacist could refuse to dispense medication.

As execution moves to milliseconds and microseconds, those intervention
points disappear.

Authority does not vanish — it **moves upstream**.

Constraint Architecture formalises that move.

---

## The Stack

Three layers. No overlap. No confusion.

| Layer | What it does | Repo |
|---|---|---|
| **Constraint Architecture** | Defines what is admissible — the boundaries within which execution is permitted | This repository |
| **512** | Enforces admissibility at the commit boundary — binary, deterministic, at machine speed | [github.com/JonathanMastersWatson/512](https://github.com/JonathanMastersWatson/512) |
| **CVS** | Witnesses execution and produces independently verifiable evidence | [github.com/JonathanMastersWatson/Evidence-Sidecar](https://github.com/JonathanMastersWatson/Evidence-Sidecar) |

Constraint Architecture defines the world.
512 enforces it.
CVS proves it.

---

## Canonical Primitives

### 512 — Execution Admissibility

A discovered constraint defining the minimum conditions under which
execution at machine speed can be considered legitimate.

512 is:

- binary — ALLOW or DENY
- deterministic — identical inputs produce identical outputs
- non-interpretive — no discretion, no scoring, no weighting
- enforced at the commit boundary — the point of irreversible state change

When the gate cannot complete evaluation, it produces no output.
Execution proceeds under the fail-open posture required by Invariant 6.
The witness layer records the ungoverned period as an evidence chain gap.
That gap record is a witness layer classification — not a gate output.

512 is not:

- a governance body
- a control system
- a monitoring tool
- a policy engine
- an AI model

512 was not invented. It was identified as a constraint that physics
and scale force into existence regardless of whether any specific
implementation exists.

### CVS — Cryptographic Verification Sidecar

An invented witness architecture that operates alongside systems
satisfying 512's properties to produce independently verifiable
evidence of execution.

CVS:

- observes without intervening
- produces immutable Evidence Objects
- enables audit, replay, and attribution after the fact
- is independently verifiable without operator cooperation

CVS is a witness, not a control mechanism.

---

## Roles

This repository defines **roles**, not organisations.

**Constraint Architect**
Defines execution boundaries and admissible state spaces upstream of
enforcement. Translates domain policy into binary-reducible constraint
definitions ready for compilation. Works at the boundary between human
authority and machine execution. The output of this role is a compiled
constraint set — not a policy document.

**512 Integration Specialist**
Helps systems satisfy 512's properties at the commit boundary.
Identifies execution paths, maps them to invariant requirements,
and verifies that all paths cross the boundary under gate control.

**CVS Specialist**
Designs, integrates, and interprets execution evidence planes.
Ensures witness independence, Evidence Object sufficiency, and
independent verifiability.

These roles represent a migration of expertise upstream — from
interpretation after the fact to definition before execution.

---

## What This Repo Is and Is Not

This repo **is**:

- canonical language for the upstream constraint discipline
- slow-moving and append-only
- upstream of products, implementations, and regulation
- a reference for professionals transitioning into constraint-based roles

This repo **is not**:

- a standards body
- a certification authority
- a consulting firm
- a product roadmap
- an implementation guide

It exists to prevent conceptual collapse as the discipline matures.

---

## Upstream Positioning

This repository operates strictly upstream of execution.

It defines:

- language and terminology
- the three-layer stack and its boundaries
- admissibility principles
- roles that exist before execution occurs

It does not provide:

- implementations
- tooling
- certification
- operational guidance

If you are building systems, start with the canonical primitives:

- 512: https://github.com/JonathanMastersWatson/512
- CVS: https://github.com/JonathanMastersWatson/Evidence-Sidecar

This repository defines the constraints those systems satisfy.
It does not tell you how to build them.

---

## Audience

This repository is for professionals whose work historically relied
on interpretation, judgment, and discretionary enforcement —
including compliance, audit, policy, legal, risk, and operations.

As execution-time constraint systems mature, these roles do not
disappear. They move upstream: designing constraint boundaries,
defining admissible state spaces, and shaping what automated systems
are permitted to do before they do it.

The interpretive class does not become obsolete.
It becomes the constraint definition layer.

---

## Repository Structure
```
CANON/              — canonical definitions and primitives
CONSTRAINT_TOOLS/   — tools and frameworks for constraint definition
ROLES/              — role definitions and competency models
WHITEPAPERS/        — research and analysis
GLOSSARY.md         — canonical terminology
README.md           — this document
```
