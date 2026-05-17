# TDBO Four-Layer Stack — Canonical Architecture

**Contributor:** The Digital Blue Ocean Ltd. (TDBO)  
**Date:** 25 March 2026  
**Status:** Canonical — supersedes all prior three-layer references in TDBO materials  

---

## Overview

The Constraint Architecture upstream repository defines Layer 0 — the admissible state space — as a formally named, separately-scoped upstream layer. TDBO's derivative implementation builds a four-layer stack on top of this foundation.

> **Critical:** All prior TDBO materials that referenced a "three-layer architecture" have been updated to reflect the canonical four-layer stack as of 25 March 2026.

---

## The Four Layers

| Layer | Name | Description | Ownership |
|-------|------|-------------|-----------|
| **Layer 0** | Constraint Architecture — Admissible State Space | Defines which states a system may enter **before** execution. Upstream definition of what is permissible. Consumed by the 512 Kernel as `spec_hash`-bound input at initialisation. | Jon M. Watson (upstream, open) |
| **Layer 1** | 512 Kernel — Deterministic Execution Boundary | Admissibility logic and synchronous validation at execution time. Single non-bypassable gateway (SOP-1). Evaluates admissibility against the state space defined in Layer 0. | Jon M. Watson (Apache 2.0 base); TDBO implementation |
| **Layer 2** | ICL — Internal Consequence Bidding Layer (optional) | Economic gating wrapper. Risk pricing and capital commitment prior to any real-world side effect (SOP-6). TDBO-owned derivative — not part of the 512/CVS primitive. | The Digital Blue Ocean Ltd. (Proprietary) |
| **Layer 3** | CVS-512 — Evidentiary Sidecar | Evidentiary mechanics: hash formation, Merkle batching, public-ledger anchoring. Witness-only, fail-open, operator-independent. Records Layer 0 signal, Layer 1 decision, Layer 2 commitment, and outcome. | Jon M. Watson (Apache 2.0 base); TDBO derivative |

---

## Layer Separation Principle

These four layers must never be collapsed into a single "institutional compliance" construct.

- **Layer 0** = admissible state space definition (upstream, Jon Watson's domain)
- **Layer 1** = admissibility logic at execution time (512 Kernel)
- **Layer 2** = optional economic gate (ICL — TDBO proprietary)
- **Layer 3** = evidentiary rail (CVS-512)

Marketing the four layers as "automatic compliance" violates the language discipline.

---

## IP Ownership Table

| Tier | Owner | Licence | TDBO's Rights |
|------|-------|---------|---------------|
| Constraint Architecture (Layer 0) | Jonathan M. Watson | No licence asserted over constraint category | TDBO may define systems satisfying its requirements |
| 512 Kernel (Layer 1) | Jonathan M. Watson | No licence asserted over constraint set | TDBO may build systems satisfying 512's properties |
| CVS Base Architecture (Layer 3) | Jonathan M. Watson | Apache 2.0 | TDBO may build derivative implementations, retain ownership, commercialise freely |
| TDBO Derivatives (Layer 2 + implementations) | The Digital Blue Ocean Ltd. | Proprietary | TDBO wholly owns risk formulas, settlement intervals, escrow mechanics, DIFC-specific SLA wrappers |

---

## DIFC Deployment Context

TDBO deploys the four-layer stack as an Engineering Service Provider under the DIFC TechReg Innovation Licence framework. The deployment does not claim regulatory certification — it enables institutions to demonstrate constraint integrity to their own regulators, insurers, and auditors.

- **Settlement substrate:** Ethereum L2 (Arbitrum or Optimism). Ledger-agnostic by design.
- **Canonical serialisation:** JCS RFC 8785 as normative baseline; keccak256 (ABI-encoding) where EVM compatibility required.
- **Cost:** ~$1.08/month per client at 60-second Merkle batching.
