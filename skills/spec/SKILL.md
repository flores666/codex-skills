---
name: spec
description: Write an implementation-ready Markdown specification for software development. Use when a nontrivial software task has unresolved requirements that could change scope, architecture, behavior, or acceptance criteria.
---

# Software specification

1. Before the interview, read applicable repository instructions and trace the closest analogous flows from entry points through validation, dependencies, side effects, and tests. Identify ownership, invariants, and established patterns. For greenfield work, start from the user's constraints.
2. Ask focused questions in rounds about material gaps. Ask explicitly which changes are forbidden if the boundaries are unclear. For unresolved design choices that matter, including conflicting repository patterns, offer three distinct, viable options when available. Present the simplest solution that meets the requirements, a balanced approach, and the most robust solution. Compare effort, benefits, and tradeoffs. Recommend the best fit and explain if fewer options are viable. Get the user's decision or explicit delegation to choose. Continue until an implementer can proceed without unresolved requirements or architectural choices.
3. Save a detailed, numbered requirements list as a `.md` file. Specify scope, exclusions, behavior, relevant failure and edge cases, component ownership, architectural decisions with rationale, and verifiable acceptance checks. Turn applicable repository conventions into concrete requirements and cite representative file paths.
4. Require the implementing agent to follow the approved spec, reuse the specified patterns, and keep changes in scope. If it encounters a contradiction, a missing architectural decision, or a need to deviate or expand scope, it must pause the affected work and obtain the user's approval of a revised spec.
5. Share the saved file and request explicit approval of that version. Begin implementation, including tests, only after approval and only if the user requested implementation.
