# Global development workflow

- Maximize correctness, reliability, and engineering quality over speed, token consumption, or agent count; apply this across languages and frameworks.
- Read applicable project instructions and preserve existing architecture, conventions, public contracts, and unrelated work.
- Before editing, trace behavior, ownership, dependencies, invariants, failure modes, and relevant concurrency boundaries.
- Use the newest released Sol model available in the current client for the main agent and each subagent. As of this update, that model is GPT-6.2 Sol (`gpt-6.2-sol`). Adopt newer Sol releases as they become available. If the latest release is unavailable or the client fixes the model, use the newest Sol version the client supports or the fixed model, and disclose the limitation. If no Sol model is available and the choice is configurable, use the newest available model suitable for the task and disclose the fallback.
- Scale reasoning effort to complexity and risk: low for simple deterministic work; medium for routine development and straightforward investigations.
- Use high for complex implementation, debugging, architecture, and reviews, and xhigh for difficult problems, extensive edge-case analysis, exceptional complexity, or critical risk. For Sol models, xhigh is the ceiling for the main agent and all subagents. Choose the highest supported level at or below the intended level when needed.
- Choose supported effort independently for each subagent and set it explicitly when tools allow; provide sufficient task context when overrides require a fresh context.
- Select the main-agent model and effort through supported client controls when possible. Treat this file as selection guidance and disclose material limitations when the client fixes either setting.
- Dynamically use 1–5 active agents total, including the main agent and all descendants; honor stricter client limits and never open more than four spawned threads.
- The main agent owns the shared agent budget and all spawning; subagents must not redelegate.
- Delegate independent work when it materially improves quality and current tools and higher-priority instructions permit it; simple tasks may use one agent.
- Give each delegate a clear responsibility, scope, inputs, expected evidence, and validation; assign exclusive file ownership or sequence overlapping edits.
- Encourage independent reasoning, alternative hypotheses, and critical disagreement; do not lead reviewers toward the author's conclusions.
- Require an independent subagent review for significant changes when available; reviewers inspect requirements and actual code or diffs, actively seeking defects.
- Review correctness, edge cases, regressions, security, concurrency, performance, and maintainability where relevant; support findings with concrete code evidence.
- The main agent critically evaluates findings, verifies disputed claims, resolves conflicting conclusions, and remains responsible for final integration.
- Never substitute agent consensus for verified correctness; use appropriate tests, builds, and focused checks scaled to the change's complexity and risk.
- Run all tests in the background. Configure GUI tests and fixtures for headless or hidden execution before launch so no test window appears on or takes focus from the user's desktop.
- For any work with a visual component, run visual tests and inspect rendered captures of the affected states.
- Resolve confirmed defects and rerun affected checks before completion; if validation or independent review is unavailable, state the remaining limitation.
- Prefer the simplest complete solution; avoid unnecessary abstractions, redundant work, and excessive coordination.
- Report material changes, verification evidence, and unresolved risks concisely; do not claim unverified behavior is working.

# Code organization and refactoring

- Before implementing or refactoring, inspect analogous code and trace the complete flow from its entry point through checks and dependencies to state changes and external effects.
- Place each rule in the module, component, or layer that owns its responsibility and invariants; keep shared code limited to behavior genuinely reused across those boundaries.
- Give each operation a clear owner for coordinating its lifecycle, from preparation and execution through completion, failure handling, and recovery.
- Replace repeated branching over known variants with a small contract when existing implementations demonstrate the need.
- Evaluate simplification through preserved observable behavior and execution/resource costs; treat line count as a secondary metric.
