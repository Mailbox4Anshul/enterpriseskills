You are a senior software architect creating an Architecture Decision Record (ADR) to document a significant technical decision for an enterprise engineering team.

Decision to document: $ARGUMENTS

ADRs capture the context, reasoning, and consequences of architecture decisions so future engineers understand not just *what* was decided, but *why*, and what trade-offs were made. Write this as a permanent artifact — it should still make sense years from now with no additional context.

---

# ADR-[NNN]: [Short, imperative title — e.g., "Use PostgreSQL as the primary data store for the Order Service"]

**Date:** [YYYY-MM-DD]
**Status:** Proposed | Accepted | Deprecated | Superseded by ADR-[NNN]
**Deciders:** [Names or roles of people who participated in the decision]
**Consulted:** [People whose input was sought]
**Informed:** [People who need to be made aware]

---

## Context

Describe the situation and the forces at play that led to this decision needing to be made. Include:
- The problem or need being addressed
- Relevant technical constraints (existing systems, team skills, performance requirements)
- Relevant business constraints (cost, timeline, compliance, strategic direction)
- Any assumptions this decision depends on

Write this section as if explaining to an engineer who joins the team three years from now — they should understand the situation without needing to know the people or priorities of today.

## Decision Drivers

List the key quality attributes and requirements that most influenced the decision:
- [ ] Performance: [specific target]
- [ ] Developer experience: [specific goal]
- [ ] Operational simplicity: [specific goal]
- [ ] Cost: [specific constraint]
- [ ] Compliance: [specific requirement]
- [ ] ...

## Considered Options

List all options that were meaningfully evaluated:

1. [Option A — the chosen option]
2. [Option B]
3. [Option C]

## Decision

**We will [chosen option].**

Explain the decision in 2–4 sentences. State it clearly and directly — someone should be able to read this sentence and immediately know what was decided.

## Rationale

### Why [chosen option]
Explain the specific reasons this option was selected over the alternatives. Reference the decision drivers above. Be concrete — avoid vague statements like "it was the best option."

### Option Comparison

| Criterion | [Option A — chosen] | [Option B] | [Option C] |
|-----------|---------------------|------------|------------|
| [Performance] | ✅ Meets target | ⚠️ Borderline | ❌ Below target |
| [Operational cost] | ⚠️ Higher setup cost | ✅ Low | ✅ Low |
| [Team familiarity] | ✅ High | ⚠️ Medium | ❌ Low |
| [Vendor lock-in] | ⚠️ Moderate | ✅ None | ✅ None |

### Why not [Option B]
Explain the key reason(s) this was not chosen despite any advantages it had.

### Why not [Option C]
Explain the key reason(s) this was not chosen.

## Consequences

### Positive
- ...
- ...

### Negative / Trade-offs
- ...
- ...

### Neutral
- ...

## Risks & Mitigations

| Risk | Likelihood | Mitigation |
|------|-----------|------------|
| [e.g., Vendor discontinues support] | Low | Migration path to [alternative] documented in runbook |

## Implementation Notes

Key things the engineering team should know when implementing this decision:
- ...

## Review Criteria

Under what circumstances should this decision be revisited?
- If [condition], we should reconsider [aspect of the decision]
- Schedule a review if [metric] trends in [direction]

## References
- [Link to relevant RFC, design doc, or spike]
- [Link to PoC or benchmark results]
- [Link to relevant industry article or documentation]
