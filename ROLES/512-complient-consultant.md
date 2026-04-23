# 512 Integration Specialist

A **512 Integration Specialist** helps organisations prepare systems
and workflows to satisfy 512's properties at the commit boundary.

This role is about execution fitness — structural alignment between
how a system executes and what 512's properties require at the
point of irreversible state change.

---

## What This Role Does

A 512 Integration Specialist:

- identifies every commit boundary in the target system
- audits execution paths for parallel routes that bypass evaluation
- maps each execution path to the seven invariant requirements
- verifies that exactly one path reaches each commit boundary —
  through gate evaluation
- confirms structural elimination of bypass paths, not procedural
  restriction
- prepares the organisation for observation mode and enforcement mode

They work with reality as defined — not negotiated.

---

## What This Role Is Not

This role does not:

- define domain constraints — that is the Constraint Architect's function
- grant approvals or certifications
- interpret failures after execution
- override constraints
- introduce procedural controls as substitutes for structural ones

If a workflow cannot satisfy 512's properties, it must be
refactored or moved downstream.
There is no partial pass.

---

## The Distinction from Constraint Architect

The Constraint Architect defines what is admissible — the compiled
constraint set that the gate evaluates.

The 512 Integration Specialist ensures the gate is correctly
positioned — that the commit boundary is real, that the gate holds
exclusive commit authority, and that no execution path reaches the
commit surface without passing through gate evaluation.

Both roles are required. Neither substitutes for the other.

---

## Typical Engagements

- execution boundary audits
- bypass path identification and structural elimination
- integration workflow preparation (Steps 1–4 of 512 integration)
- observation mode deployment and gap analysis
- pre-enforcement verification against the Properties Checklist

Deliverables are structural and binary.
A boundary either satisfies 512's properties or it does not.

---

## Ideal Backgrounds

- enterprise architects
- systems integration engineers
- compliance and risk professionals with systems exposure
- auditors with execution path experience
- operations engineers who understand irreversibility

Experience identifying where systems break under edge cases
is the asset — now applied upstream, before execution occurs.

---

## Final Note

512 Integration Specialists do not make systems safer by adding
controls.

They make systems satisfy 512's properties by ensuring the gate
holds the only path to irreversible state change — and that no
other path exists.

---

## Related Files

- `CONSTRAINT_TOOLS/boundary-mapping.md` — execution boundary
  identification methodology
- `CONSTRAINT_TOOLS/readiness-assessment.md` — readiness
  evaluation framework
- `ROLES/constraint-architect.md` — upstream role that produces
  the compiled constraint set this role integrates against
