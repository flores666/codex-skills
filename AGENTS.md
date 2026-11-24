- Read applicable project instructions. Preserve architecture, conventions, public contracts, and out-of-scope work.
- Before editing, trace behavior, ownership, dependencies, invariants, failure modes, and relevant concurrency boundaries. Before implementing or refactoring, inspect analogous code and trace the full execution path from entry points through checks and dependencies to state changes and external effects.
- Choose the simplest complete solution. Avoid unnecessary abstractions, duplicated work, and excessive coordination. Judge simplification by preserved observable behavior, execution costs, and resource use. Line count is secondary.
- Put rules with the module, component, or layer that owns the behavior and its invariants. Share code only for behavior reused across those boundaries.
- Give each operation a clear owner to coordinate its lifecycle from preparation and execution through completion, failure handling, and recovery. Replace repeated branching over known variants with a small contract when existing implementations show the need.

# Agents

- Use supported client controls and this guidance to set the main agent's model and reasoning effort when possible. Disclose material limitations if the client fixes either setting.
- Delegate independent work when it materially improves quality and tools and higher-priority instructions permit it. When delegating, use one to three concurrently active subagents as the task warrants. One agent suffices for simple tasks.
- The main agent manages the shared budget, spawns all subagents, writes all code, performs core work, and owns final integration. Subagents assist without redelegating.
- Use the newest released Sol model available in the client for each subagent, or the client-fixed model. Set supported reasoning effort individually and explicitly when possible. Use `medium` for straightforward investigations and otherwise the highest supported effort up to `xhigh`. Give the subagent enough task context if overrides require a fresh context.
- Define each delegate's responsibility, scope, inputs, expected evidence, and how to verify results. Assign exclusive file ownership or sequence overlapping edits. Encourage independent reasoning, alternative hypotheses, and reasoned disagreement. Let reviewers form their own conclusions without steering them toward the author's.

# Verification

- Require independent subagent review for significant changes when available. Reviewers actively seek defects by inspecting requirements and actual code or diffs. Assess correctness, edge cases, regressions, security, concurrency, performance, and maintainability as relevant. Cite concrete code evidence.
- The main agent critically evaluates findings, verifies disputed claims, and reconciles conflicting conclusions.
- Verify correctness even when agents agree. Use tests, builds, and focused checks proportionate to complexity and risk. Run all tests in the background. Before launch, configure GUI tests and fixtures to run headlessly or hidden to prevent desktop windows and focus changes. For any work with a visual component, run visual tests and inspect captures of affected rendered states.
- Fix confirmed defects and rerun affected checks before finishing. Concisely report material changes, verification results, remaining risks, and limitations from unavailable verification or independent review. Claim that behavior works only when verification supports it.
