# Glossary

**Execution** — The act of changing system state irreversibly.

**Runtime** — The period after execution has begun.

**Constraint** — A pre-committed condition that must be satisfied for
execution to be admissible.

**Admissible** — Allowed to execute under defined constraints. The
determination of admissibility is made at the commit boundary by the
gate, not at runtime by a human.

**Commit Boundary** — The exact point at which a proposed action
becomes an irreversible state change. Before the boundary: the action
is a proposal. After the boundary: state has changed. The gate owns
the only path through this boundary.

**Exclusive Commit Authority** — The structural property of a correctly
positioned gate: there exists exactly one path to irreversible state
change, and that path does not open without the gate's authorisation
signal. Procedural controls do not satisfy this property. The path
must not exist, not merely be restricted.

**Gate Output** — The result produced by the gate upon completing
evaluation. Exactly two values: ALLOW or DENY. There is no third
output value. When the gate cannot complete evaluation, it produces
no output — execution proceeds under fail-open (Invariant 6) and the
witness layer records an evidence chain gap.

**Evidence Chain Gap** — A witness layer classification applied to an
ungoverned period in the evidence chain. Produced by CVS when the gate
is unavailable and execution proceeds without constraint evaluation.
Not a gate output. Records that evaluation did not occur.

**Compiled Constraint** — A domain-specific Boolean expression over
named, typed inputs that the gate can evaluate deterministically
without interpretation. The output of the Constraint Architect's
definition work. Identical inputs must produce identical outputs on
every invocation.

**Spec Hash** — The cryptographic commitment to the compiled constraint
set active at the moment of evaluation. Embedded in every Evidence
Object. Binds each evidence record to the exact constraint
specification that was evaluated against.

**Proposal Object** — A complete, structured record of a proposed
action, constructed before the commit boundary is crossed and submitted
to the gate for evaluation. All fields must be populated before
evaluation begins. Not reconstructed after the fact.

**512** — A specific Commit Gate: the discovered constraint set
defining the minimum conditions under which execution at machine speed
can be considered legitimate. Seven invariants. Binary output: ALLOW
or DENY. Enforced at the commit boundary.

**CVS** — Cryptographic Verification Sidecar. An invented witness
architecture that operates alongside systems satisfying 512's
properties. Observes execution events out-of-band. Produces immutable,
independently verifiable Evidence Objects. Does not influence execution.

**Fail-Open** — The behaviour required by Invariant 6 when a system
cannot complete evaluation at the commit boundary. Execution proceeds
— blocking on gate failure would itself violate Invariant 6. Governing
rules are disclosed. Control returns to the human party. The witness
layer records the ungoverned period as an evidence chain gap.

**Authority** — The ability to permit or deny execution before it
occurs. Authority exercised during or after execution does not function
at machine speed. At machine speed, authority must be pre-committed
into constraints.

**Latency** — Time between decision and action. At machine speed,
latency eliminates the possibility of human intervention between
decision and irreversible state change. Governance must occur before
the decision, not between the decision and the action.

**Machine-speed** — Faster than human intervention. The threshold
beyond which runtime authority becomes physically impossible and
pre-committed constraints become the only functional governance
mechanism.

**Upstream** — Work that occurs before execution. Upstream work can
still prevent execution. Once execution begins, upstream authority ends.

**Downstream** — Work that occurs after execution. Downstream work
can observe, record, and interpret. It cannot prevent or reverse.
