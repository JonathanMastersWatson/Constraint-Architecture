# TDBO AHTM Integration — State-Coupled Constraint Definition

**Contributor:** The Digital Blue Ocean Ltd. (TDBO) with STARGA, Inc. as implementation technology partner  
**Date:** 25 March 2026  
**Reference:** AHTM-512-CVS State-Coupled Governance Architecture Technical White Paper v2.0 (24 March 2026)  
**Upstream Invariant Guardian:** Jon M. Watson, 512 Chief Architect  

---

## The Structural Gap This Solves

The 512 Kernel enforces binary admissibility at execution time — ALLOW or DENY — with fixed constraint thresholds declared at initialisation via `spec_hash` binding. This is correct by design. However, static constraints are **blind to operational drift**: a parameter that was safe at initialisation may become unsafe two hours into an undetected environmental state change.

The gap is not a monitoring gap. It is a **coupling gap**: static constraints are not coupled to the state of the system as it evolves.

Accelerated Hierarchical Temporal Memory (AHTM) resolves this by integrating as an upstream **State Observation Layer** that feeds real-time environmental state signals into the 512 Kernel's admissibility logic — making the operative constraint definition state-coupled.

> **Architectural principle (Alexanja, 24 March 2026):** AHTM does not replace or modify the 512 Kernel. It makes the Kernel intelligent about *what constraint to enforce* given the current environmental state — not just whether to enforce the constraint. The Kernel remains deterministic; what becomes state-coupled is the real-time operational envelope it enforces.

---

## Four-Layer AHTM Architecture

```
LAYER 0 — AHTM STATE OBSERVATION (Constraint Architecture)
  Continuous, unsupervised, online environmental state observation
  anomaly_score(t) = 1 - |predicted_active ∩ actual_active| / |actual_active|
  Output: Dynamic Constraint Signal (DCS) — current-state deviation
  Q16.16 fixed-point arithmetic throughout
        ↓
LAYER 1 — 512 KERNEL (Deterministic Execution Boundary)
  operative_limit = min(spec_limit, htm_adjusted_limit)
  Binary ALLOW/DENY gate — 5ms latency — Non-bypassable (SOP-1, SOP-2)
        ↓
LAYER 2 — ICL (Economic Binding — Optional, TDBO Proprietary)
  Capital lock before side effects — risk pricing (SOP-6)
        ↓
LAYER 3 — CVS-512 (Evidentiary Sidecar)
  Witness-only — Fail-open — Hash chain — Merkle batching — Ethereum L2
  Records AHTM signal, 512 decision, ICL commitment, outcome
  Independently verifiable without operator cooperation (SOP-4)
```

---

## HTM Technical Foundation

**Algorithm:** Hierarchical Temporal Memory (Numenta, Apache 2.0)

**Two algorithmic modules:**
- **Spatial Pooler (SP):** Converts arbitrary binary input into Sparse Distributed Representations (SDRs) with fixed sparsity. Typical: 2,048 columns, 64K artificial neurons, 40 active at once (2% sparsity).
- **Temporal Memory (TM):** Learns temporal sequences and generates context-sensitive predictions. Online learning — absorbs new patterns continuously without catastrophic forgetting.

**Q16.16 Fixed-Point Arithmetic (STARGA MIND Runtime):**  
All governance path computations use Q16.16 32-bit fixed-point arithmetic exclusively. No IEEE 754 floating-point in the evidence-producing pipeline. Eliminates platform-dependent ULP divergence — `spec_hash` validity is hardware-independent, satisfying SOP-3 and SOP-5 at silicon level across x86, ARM, CUDA, ROCm, Metal, WebGPU backends.

---

## Five-Phase FSM — MIND Runtime Mapping

| HTM-512-CVS Layer | MIND Phase | Execution Semantics |
|-------------------|-----------|---------------------|
| Layer 0 — HTM Pattern | SENSE | HTM processes input stream, computes anomaly score (Q16.16), emits Dynamic Constraint Signal |
| DCS Generation | THINK | Anomaly scores map to constraint adjustments via Linear/Exponential/Step functions |
| Layer 1 — 512 Kernel | ACT | `operative_limit = min(spec_limit, htm_adjusted_limit)` — deterministic ALLOW/DENY |
| Layer 3 — CVS-512 | VERIFY | State hash (incl. `dcs_hash`) → Evidence Object → triple-hash verification |
| HTM Online Learning | LEARN | HTM absorbs outcome, updates synaptic permanence, commits snapshot |

Three-plane isolation: Control, Memory, Verification — no shared mutable state between phases.

---

## Convergence — Five Independent Discovery Paths

Between October 2025 and March 2026, five practitioners arrived at the same structural physics from entirely different directions:

1. **Jon Watson (Protocol Physics):** SOP-1–SOP-6 as minimum necessary conditions for a governance boundary that is not theatre.
2. **Timothy Gough (Infrastructure, DAIOS):** Trust lives in the motor circuit — governance compiled into execution substrate is preventive, not reconstructive.
3. **Inward (Human Interface):** Suspended Handoff (512 HOLD state), Sovereign Extraction Point, AuthHash (human cryptographic signature in state hash preimage).
4. **Nikolai / STARGA (Implementation):** Q16.16 fixed-point designed for cross-platform determinism — pre-aligned to SOP-3 before integration.
5. **Alexanja (State Semantics):** State is not memory — it is responsibility. Admissible region continuously defined by intersection of current state and applicable conditions.

---

## Tiered Evidence Objects

| Tier | Size | Use Case |
|------|------|----------|
| Lightweight | 73 bytes | Routine ALLOW decisions |
| Standard | 121 bytes | Normal constraint evaluation with DCS signal |
| Full | ~25 KB | Cross-entity METBP events, fault records, multi-agent coordination |

---

## SOP Compliance Statement

| SOP | How AHTM Integration Satisfies It |
|-----|-----------------------------------|
| SOP-1 | AHTM does not create a second gateway. The 512 Kernel's single non-bypassable gate remains sole enforcement point. AHTM feeds a signal into the spec; it does not evaluate admissibility independently. |
| SOP-2 | Commit Buffer Architecture: no ALLOW/DENY decision visible downstream without its corresponding Evidence Object. Decision held in `PendingEvidence` state until hash committed. |
| SOP-3 | Q16.16 arithmetic throughout — deterministic, reproducible, platform-independent. |
| SOP-4 | CVS-512 Evidence Objects anchored to Ethereum L2 — independently verifiable without operator cooperation. |
| SOP-5 | `spec_hash` includes AHTM spec parameters at initialisation — any spec change detectable via hash mismatch. |
| SOP-6 | ICL capital lock applied before any real-world side effect when Layer 2 is deployed. |

---

## Industrial Application — Turnwell JV (Oil & Gas Reference Deployment)

**Problem:** 144-well autonomous drilling programme, 7 AI agent classes, thousands of ungoverned decisions per well per day. Static constraints blind to formation transitions produce stuck pipe events, cascade failures, $8M+ recovery operations.

**AHTM deployment:** Continuous WOB (Weight on Bit) pattern observation → DCS signal → state-coupled operative limit → SOP-1 enforcement → CVS-512 evidence anchoring.

**Phase A deliverable (STARGA, target 30 March 2026):** Single HTM instance, DrillOps WOB, full pipeline, bit-identity across x86/ARM. Phase A report against 8 quantitative criteria.
