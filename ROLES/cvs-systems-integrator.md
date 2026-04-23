# CVS Systems Integrator

A **CVS Systems Integrator** designs and deploys the Cryptographic
Verification Sidecar (CVS) across complex, heterogeneous environments
without altering execution paths.

This role exists because CVS is intentionally **disjoint** from
execution. Integration therefore requires architectural discipline,
not feature development.

---

## What This Role Is

A CVS Systems Integrator is responsible for:

- identifying where execution evidence should be captured
- exposing appropriate observation points ("ports to listen on")
- ensuring evidence is complete, immutable, and attributable
- integrating CVS with existing infrastructure without introducing runtime risk

This is not governance.
This is **evidence plumbing at scale**.

---

## What This Role Is Not

A CVS Systems Integrator does **not**:

- enforce policy
- block or allow execution
- interpret behavior
- remediate failures
- introduce control loops

CVS observes.
Execution remains untouched.

---

## Why This Role Exists

Most enterprises already have:

- dozens of execution systems
- fragmented logging
- inconsistent audit trails
- post-hoc reconstruction workflows

CVS replaces narrative reconstruction with **mechanical receipts**.

But CVS cannot simply be "turned on."

It must be **integrated carefully**, or it risks:

- performance degradation
- partial observability
- false confidence

That integration work is non-trivial — and critical.

---

## Core Responsibilities

A CVS Systems Integrator typically performs:

### 1. Evidence Surface Mapping
- Identify which systems produce execution that matters
- Distinguish execution from simulation, planning, or intent
- Determine which events must be cryptographically recorded

### 2. Observation Point Design
- Define where CVS listens without touching the hot path
- Avoid introducing latency, coupling, or failure modes
- Preserve system autonomy

### 3. Infrastructure Integration
- Deploy CVS alongside:
  - transaction systems
  - agent frameworks
  - data pipelines
  - industrial control systems
- Ensure compatibility with existing security and conformance tooling

### 4. Evidence Integrity Assurance
- Guarantee immutability
- Maintain provenance
- Prevent evidence gaps or duplication

### 5. Replay & Forensics Enablement
- Ensure evidence can be replayed deterministically
- Support audit, investigation, and attribution use cases
- Enable downstream analytics without reinterpreting execution

---

## Ideal Backgrounds

Strong CVS Systems Integrators often come from:

- systems integration & enterprise architecture
- distributed systems engineering
- observability / telemetry infrastructure
- audit systems engineering
- regulated industry IT (finance, energy, manufacturing)

They are typically trusted with production systems because they
**do not change behavior** — they observe it.

---

## Relationship to Other Roles

- **Constraint Architect**
  Defines execution boundaries and canonical primitives. Does not
  integrate systems.

- **512 Integration Specialist**
  Ensures systems satisfy 512's properties at the commit boundary.
  Works upstream of CVS.

- **CVS Specialist**
  Analyzes, replays, and interprets evidence after it exists.

- **CVS Systems Integrator**
  Makes evidence exist in the first place — cleanly and safely.

---

## Value to the Organization

A properly integrated CVS:

- reduces audit cost
- shortens incident resolution
- compresses liability exposure
- replaces narrative trust with evidence

A CVS Systems Integrator ensures this value is achieved
**without destabilizing execution**.

---

## Final Note

CVS succeeds precisely because it does not intervene.

The CVS Systems Integrator's job is to preserve that separation —
even under pressure to "just add control."

That restraint is the skill.
