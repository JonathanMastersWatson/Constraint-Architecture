# Pre-Hardening Notice

This repository is in an active hardening phase.

Language, terminology, and role definitions are being tightened
to align with the hardened vocabulary established across the
512 and CVS Evidence-Sidecar repositories.

---

## What This Means

**Constraints are directionally stable.** The three-layer stack,
the role definitions, and the upstream/downstream distinction
are not changing.

**Language is being tightened.** Prohibited terms are being
removed. Canonical vocabulary is being introduced. Role names
are being aligned with the terminology enforced in the 512 and
CVS repositories.

**Constraints clarify — they do not relax.** No hardening pass
will weaken any definition, expand any exception, or introduce
ambiguity that did not previously exist.

---

## Current Hardening Pass — April 2026

Issues identified and corrected in the current pass:

- `README.md` — binary gate output model corrected:
  "allow / deny / gap" → ALLOW or DENY only; fail-open path
  correctly described
- `CANON/CVS.md` — canonical name corrected:
  "Cryptographic Verification System" → "Cryptographic
  Verification Sidecar"
- `ROLES/512-complient-consultant.md` — renamed to
  `512-integration-specialist.md`; prohibited role name
  ("512-Compliant") and filename typo corrected; content
  rewritten to reflect correct role definition
- `GLOSSARY.md` — "Fail-fast" removed; nine canonical terms
  added covering the hardened vocabulary from the 512 and
  CVS repos
- `ROLES/cvs-systems-integrator.md` — CVS name corrected;
  role reference updated to 512 Integration Specialist
- `ROLES/constraint-architect.md` — fail-fast references
  replaced with fail-open model; vocabulary aligned
- `CONSTRAINT_TOOLS/constraint-definition-method.md` — new
  file defining the Constraint Architect's upstream
  methodology: four-field definition model, directly-computable
  vs proxy invariants, binary reducibility test, Anglo-Saxon
  test, per-invariant definition checklist

---

## This Repository Is Not Sealed

Unlike the 512 and CVS repositories, this repository does not
have a formal seal process. It is append-only and slow-moving
by design.

Hardening passes correct errors, align vocabulary, and add
missing methodology. They do not alter the architectural
positioning of this discipline relative to the 512 and CVS
layers.

---

## Related

- `512-main/PRE_HARDENING_NOTICE.md` — 512 repo hardening status
- `Evidence-Sidecar-main/PRE_HARDENING_NOTICE.md` — CVS repo
  hardening status
