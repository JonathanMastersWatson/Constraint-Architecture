# TDBO Anti-Drift Checklist

**Contributor:** The Digital Blue Ocean Ltd. (TDBO)  
**Date:** 25 March 2026  
**Purpose:** Pre-release verification — must be cleared before any document, presentation, or submission is released externally

---

## What Drift Means

In the context of the 512/CVS stack, "drift" means any material departure — in implementation, documentation, or language — from the canonical invariants, layer separation, and evidence mechanics defined by Jon Watson.

Drift occurs when:
- Older documents use pre-hardening language
- Layer 0 is omitted from stack descriptions
- Invariants are referenced without SOP labels
- Forbidden phrases survive editing rounds
- Verticals are described as part of the primitive instead of as deployment contexts

---

## Pre-Release Checklist

### Layer Structure
- [ ] Four layers named explicitly: Layer 0 (Constraint Architecture) + Layers 1–3
- [ ] Layers are NOT collapsed into a single "institutional compliance" construct
- [ ] Layer 2 (ICL) explicitly labelled as TDBO-proprietary and optional
- [ ] Layer 0 attributed to Jon Watson as upstream definition
- [ ] "Three-layer architecture" language absent throughout

### SOP Invariants
- [ ] All six invariants referenced as **SOP-1 through SOP-6** (never bare numbers)
- [ ] No document references "nine invariants" as canonical (STARGA I-1–I-9 are subordinate)
- [ ] SOP-1: Single non-bypassable gateway confirmed — no bypass path present
- [ ] SOP-2: No async gap between validation and execution
- [ ] SOP-3: Canonical serialisation used throughout governance path
- [ ] SOP-4: External verification possible without operator cooperation
- [ ] SOP-5: If spec binding used — canonical serialisation, initialisation capture, preimage + Evidence Objects
- [ ] SOP-6: Economic commitment before side effects when ICL is deployed

### Language Discipline
- [ ] "CVS certifies compliance" — absent
- [ ] "512/CVS-compliant" — absent
- [ ] "Validated by 512/CVS" — absent
- [ ] "Institutionally compliant" (re: primitives) — absent
- [ ] "Requirement satisfied" (re: primitives) — absent
- [ ] "Only solution" — absent
- [ ] "Six invariants" without SOP labels — absent
- [ ] "Three-layer architecture" — absent

### Spec Binding (when deployed)
- [ ] `spec_hash` from canonical serialisation (JCS RFC 8785)
- [ ] Captured at initialisation (once)
- [ ] Embedded in internal state hash AND external CVS-512 Evidence Objects
- [ ] Registry governance: outside the operator

### Verticals
- [ ] Verticals described as deployment contexts, NOT as part of the primitive
- [ ] Deployment conditions in solution/deployment guides only — not in primitive definition

### Watson Determination Requests
- [ ] No W-n pending feature implemented or marketed before Watson's written determination
- [ ] Current pending: W-1 (`solvency.mind`), W-2 (`highthroughput.mind`), W-3, W-4 (confidence telemetry)

### Attribution
- [ ] Apache 2.0 attribution to Jonathan M. Watson present in all public-facing materials
- [ ] TDBO proprietary derivatives correctly distinguished from upstream

---

## Derivative Variant Flag

If any SOP-1, SOP-2, or SOP-4 check fails, the implementation must be classified as a **derivative variant** before release. It must not be described as "512/CVS-aligned" until the bypass is resolved.
