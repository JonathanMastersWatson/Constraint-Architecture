# TDBO SOP Enforcement — SOP-1 Through SOP-6

**Contributor:** The Digital Blue Ocean Ltd. (TDBO)  
**Date:** 25 March 2026  
**Upstream source:** `512ARCHITECTUREv2.0.md` — Jon M. Watson  

---

## Canonical Invariant Table

Every TDBO deployment is governed by six non-negotiable invariants, canonically labelled **SOP-1 through SOP-6** as established by Jon Watson.

> All prior TDBO materials that listed invariants with bare numerals (1–6) or without SOP labels have been updated as of 25 March 2026.

| SOP Label | Name | Requirement |
|-----------|------|-------------|
| **SOP-1** | Single Non-Bypassable Gateway | One single, non-bypassable execution gateway controls all consequential state transitions |
| **SOP-2** | No Async Boundary | No asynchronous boundary between validation and execution |
| **SOP-3** | Deterministic State Hash Export | State hash export is deterministic and reproducible (canonical serialisation) |
| **SOP-4** | External Verification Without Operator Cooperation | External verification does not require operator cooperation (public anchors, Merkle proofs) |
| **SOP-5** | Spec Hash Binding (when used) | `spec_hash` computed from canonical serialisation, captured at initialisation, injected into state hash preimage, propagated into Evidence Objects |
| **SOP-6** | Economic Commitment Before Side Effects | When ICL layer is deployed, real-world actions require pre-commitment of capital |

---

## Derivative Variant Definition

**Any implementation that allows a bypass of SOP-1, SOP-2, or SOP-4 is classified as a derivative variant — not 512/CVS-aligned.**

This classification is structural, not a value judgement. Derivative variants may be valid engineering choices but must not be described as "512/CVS-aligned" in any TDBO, DIFC, DFSA, or institutional material.

---

## TDBO Runtime Mapping — AHTM × MIND Five-Phase FSM

In TDBO's AHTM integration with STARGA's MIND Cognitive Runtime, the five-phase FSM maps to Watson SOPs as follows:

| MIND Phase | Watson SOP | What Happens |
|------------|-----------|---------------|
| SENSE (Layer 0) | — | HTM processes input stream, computes anomaly score (Q16.16), emits Dynamic Constraint Signal |
| THINK (DCS) | — | Anomaly scores map to constraint adjustments via Linear/Exponential/Step functions |
| ACT (Layer 1) | SOP-1, SOP-2 | `operative_limit = min(spec_limit, htm_adjusted_limit)` — deterministic ALLOW/DENY |
| VERIFY (Layer 3) | SOP-3, SOP-4, SOP-5 | State hash (incl. `dcs_hash`) → Evidence Object → triple-hash verification |
| LEARN | — | HTM absorbs outcome, updates synaptic permanence, commits snapshot |

**Q16.16 fixed-point arithmetic** is mandatory throughout the governance path. This satisfies SOP-3 and SOP-5 at the silicon level — results are identical across x86, ARM, CUDA, ROCm, Metal, WebGPU backends.

---

## Spec Binding Requirements

When spec binding is deployed, the following conditions are mandatory. Where any condition cannot be met, spec binding is treated as **declarative only** — no cryptographic guarantee is claimed.

1. `spec_hash` derived from a **canonical serialisation** of the spec (JCS RFC 8785).
2. Captured **once at initialisation** of the kernel.
3. Included in both the **internal state hash** and the **external CVS-512 Evidence Object**.
4. Registry governance: **outside the operator** — independent or multi-party governance process, not TDBO alone.

---

## Watson Determination Requests (W-n)

Any feature touching the SOP boundary requires a Watson Determination Request before deployment. Current pending determinations:

| W-n | Topic | Status |
|-----|-------|--------|
| W-1 | `solvency.mind` I-10 classification | Pending Watson written classification |
| W-2 | `highthroughput.mind` async hash / SOP-2 conflict | Pending Watson determination |
| W-3 | (As submitted) | Pending Watson response |
| W-4 | Continuous per-invariant confidence telemetry | Pending Watson written determination |

**Neither TDBO nor STARGA will implement or market any W-n pending feature until Watson's written determination is received.**
