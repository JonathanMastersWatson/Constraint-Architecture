# Constraint Definition Method

This document defines the method a Constraint Architect uses to
translate domain policy into compiled constraints ready for gate
evaluation.

This is the upstream work. The gate does not define constraints.
The gate evaluates them. Everything in this document occurs before
a Proposal Object reaches the boundary.

---

## The Output of This Work

The output of the Constraint Architect's definition work is a
**compiled constraint set** — a collection of deterministic Boolean
expressions over named, typed inputs that the gate can evaluate
in microseconds without interpretation.

The output is not:
- a policy document
- a set of principles
- a risk framework
- a natural language specification
- a checklist

If the output cannot be reduced to Boolean expressions over named
inputs, the definition work is not complete.

---

## Why Compilation Is Required

The seven canonical invariants are written in plain language.
They are governance intent, not machine instructions.

Three of the seven are directly computable — they can be evaluated
mechanically against named inputs without domain-specific
interpretation:

| Invariant | Why directly computable |
|---|---|
| I5 — No hidden or unilateral rules | Spec hash comparison: declared hash matches gate's loaded hash — binary |
| I6 — Fail-open | Structural property of the gate deployment — verifiable at startup |
| I7 — Immutability and binary satisfaction | Kernel hash verification at startup — binary |

Four require compilation via proxy — the Constraint Architect must
define domain-specific Boolean expressions that represent the
invariant's intent in the specific operational context:

| Invariant | Why proxy is required |
|---|---|
| I1 — No force or fraud | "Force" and "fraud" are semantic concepts; the gate evaluates a named proxy: `action_type NOT IN {coercive_action_set} AND NOT is_deceptive` |
| I2 — Explicit consent | "Voluntary" and "explicit" are not directly computable; the gate evaluates: `consent_token present AND not expired AND matches action_type` |
| I3 — Consent withdrawal and exit | "Withdrawable" and "always possible" require domain definition; the gate evaluates: `revocation_flag == false AND exit_path_available == true` |
| I4 — Contractual clarity | "Readable" and "equally enforceable" are not computable; the gate evaluates: `contract_hash present AND matches canonical reference AND acknowledged by all parties` |

**The strength of enforcement is a function of the accuracy of
compilation.** Poorly compiled proxies produce precisely wrong
enforcement. The gate is deterministic — it enforces exactly what
it is given. Constraint quality is a human governance problem,
not a technical one.

---

## The Four-Field Definition Model

Every constraint must be defined using this structure before it
can be expressed as executable logic.

### Field 1 — Intent

State the property the constraint enforces in one sentence.
Not the rule. The property.

> "No execution may transfer funds from a party without their
> current explicit authorisation."

The intent statement is not evaluated by the gate. It is the
human-readable anchor that justifies the compiled expression
and makes drift detectable. If the compiled expression drifts
from the intent, the drift is visible.

---

### Field 2 — Signal

Name the specific data field or record that proves the property
holds.

> `consent_token` present in consent registry for
> `target_party_id`, with `consent_expiry` greater than
> `evaluation_timestamp`.

If you cannot name a specific data source, the constraint is not
ready for expression. "Evidence of consent" is not a signal.
`consent_registry.tokens[party_id].expiry` is a signal.

**A constraint without a named signal cannot be compiled.**

---

### Field 3 — Threshold

Express the signal as a deterministic true/false condition.
This is the expression the gate evaluates. It must be reducible
to a single Boolean without interpretation.

> `consent_token != null`
> `AND evaluation_timestamp < consent_expiry`
> `AND consent_token.action_type == proposal.action_type`

If the threshold requires a human to decide what it means, it
is not a threshold. It is a policy statement.

---

### Field 4 — Authority

Name the system that holds the data the threshold evaluates
against.

> Consent registry — append-only, write-audited, accessible
> to the gate at evaluation time.

The authority field defines where the gate fetches inputs during
context binding. If the named system is unavailable at context
binding time, the constraint input is missing. The gate's
`failure_mode_on_missing_input` field determines whether that
produces DENY or unevaluated.

---

## Binary Reducibility — The Compilation Test

Every constraint must pass this test before it is ready for
expression:

**Can this constraint be expressed as a Boolean over named,
typed inputs from declared sources?**

If yes: the constraint is ready for compilation.
If no: return to definition. The policy has not yet been
translated into a constraint.

### Prohibited language — definition is incomplete when these appear

| Term | Why it blocks compilation |
|---|---|
| "reasonable" | Requires judgment — not a Boolean |
| "appropriate" | Context-dependent — not deterministic |
| "high risk" | A scoring concept — not a binary condition |
| "likely" | Probabilistic — not deterministic |
| "significant" | Requires threshold definition before use |
| "material" | Legal interpretation required |
| "where feasible" | Introduces conditionality |
| "subject to policy" | Defers definition to runtime |

Replace each with a measurable, testable condition before
proceeding to expression.

### Translation examples

**❌ Not binary-reducible:**
> "Transactions must not be high risk."

**✅ Binary-reducible:**
> `current_exposure + proposed_value <= exposure_limit`
> where `exposure_limit` is sourced from the counterparty
> registry and `current_exposure` from the accumulator.

---

**❌ Not binary-reducible:**
> "Consent must be reasonably current."

**✅ Binary-reducible:**
> `consent_expiry > evaluation_timestamp`
> where `consent_expiry` is sourced from the consent registry
> and `evaluation_timestamp` is the gate's clock at evaluation.

---

**❌ Not binary-reducible:**
> "The agent should not take actions that seem coercive."

**✅ Binary-reducible:**
> `action_type NOT IN coercive_action_set`
> `AND is_deceptive == false`
> where `coercive_action_set` is a declared enumeration and
> `is_deceptive` is computed upstream from action classification.

---

## The Anglo-Saxon Test

Natural language has two registers with opposing enforcement
properties.

**Abstract / Latinate language** — "material adverse effect",
"reasonable care", "appropriate safeguards", "proportionate
response". These terms require human judgment to evaluate. They
are written for interpretation, not computation.

**Concrete / plain language** — "funds transferred", "consent
token present", "exit path available", "contract hash matches".
These terms are directly testable.

The test: read your constraint definition aloud. If it contains
words a lawyer would argue about, it is not compiled. Translate
every interpretable term into a concrete, named condition before
proceeding.

This is not a style preference. Abstract language at the
constraint definition stage produces interpretable enforcement —
which is no enforcement at all.

---

## Per-Invariant Definition Checklist

Use this checklist when defining constraints for each invariant.
A constraint definition is complete only when all four fields
are populated and the threshold is binary-reducible.

| Invariant | Definition complete when... |
|---|---|
| I1 — No force or fraud | You have named the specific action types that constitute force or fraud in your domain, expressed as a Boolean over a declared enumeration |
| I2 — Explicit consent | You have named the consent registry, the token structure, the expiry field, and the action-type match condition |
| I3 — Consent withdrawal and exit | You have defined the revocation propagation window and the binary condition that detects revoked or exit-blocked states |
| I4 — Contractual clarity | You have named the contract registry, defined the hash comparison method, and confirmed all parties have acknowledged the terms |
| I5 — No hidden rules | You have defined how the active spec hash is disclosed, to whom, and how acknowledgement is recorded — and confirmed it matches the gate's loaded hash |
| I6 — Fail-open | You have confirmed the gate deployment is structurally fail-open and the witness layer generates gap records on gate unavailability |
| I7 — Immutability | You have confirmed the gate verifies the canonical hash at startup and refuses to start on mismatch |

---

## What the Constraint Architect Hands Off

The Constraint Architect's deliverable to the expression and
enforcement stages is a complete constraint definition for each
invariant containing:

- Intent statement (human-readable, one sentence)
- Signal (named data source with field path and type)
- Threshold (Boolean expression, binary-reducible)
- Authority (named source system, access confirmed)
- Failure mode on missing input (DENY or UNEVALUATED)

This package is the input to the compiled constraint format
defined in `512-ops/COMPILED_CONSTRAINT_FORMAT.md` in the
512 repository.

**The gate evaluates what it receives. It does not correct
poorly defined constraints. It enforces them precisely.**

---

## Common Failure Modes

### Vague policy language reaches the expression stage

Policy is written for human interpretation. It arrives at
expression without translation.

> "Agents must act in the customer's best interest."

This is a principle. It cannot be evaluated deterministically.
Resolution: identify the specific observable signal that
indicates the principle is satisfied in a given execution
context. Express that signal as a binary threshold.

---

### Hidden assumptions

A constraint references data that is assumed to exist without
being explicitly declared.

> `transfer_amount <= authorised_limit`

If `authorised_limit` is not declared as a named input sourced
from a specific registry, the gate cannot evaluate this
constraint. The assumption must become an explicit declaration.

---

### Runtime interpretation

A constraint is expressed in a form that requires judgment
at evaluation time.

> "Deny if the request appears unusual for this agent."

"Unusual" is not a binary condition. Resolution: define what
unusual means in terms of specific, measurable deviations from
declared parameters.

---

### Proxy drift

The compiled proxy no longer represents the invariant's intent.
This is the most dangerous failure mode because the gate
continues to enforce — precisely and incorrectly.

Detection: compare the intent statement against the threshold
expression. If a behaviour that satisfies the threshold could
violate the intent, the proxy has drifted.

Resolution: restate the intent, identify the new signal,
recompile the threshold. Produce a new spec hash. Disclose
the new constraint set to affected parties before enforcement.

---

## Relationship to Other Documents

- `512-ops/CONSTRAINT_DEFINITION_LAYER.md` — the gate-side
  view of the same process; defines what the gate receives
  and requires
- `512-ops/COMPILED_CONSTRAINT_FORMAT.md` — the canonical
  format for compiled constraints
- `512-ops/PROPOSAL_OBJECT.md` — the structure the compiled
  constraints evaluate against
- `CONSTRAINT_TOOLS/boundary-mapping.md` — identifies where
  constraints are needed before definition begins
- `ROLES/constraint-architect.md` — the role that performs
  this work
- `GLOSSARY.md` — canonical definitions for compiled
  constraint, spec hash, gate output, and related terms
