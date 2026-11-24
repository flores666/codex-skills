---
name: read-okf-wiki
description: >-
  Read existing Open Knowledge Format (OKF, sometimes called OFK) wikis during
  repository questions, debugging, reviews, and changes when such documentation
  is present. Discover the index, load task-relevant concepts, and verify affected
  rules against their owning sources. Reading a wiki does not initiate an audit
  or authorize editing it.
---

# Read OKF Wiki

Use an existing knowledge bundle to locate the right code, constraints, and proof
for the user's task. Keep reading proportional to the work.

## Discover the bundle

- Start with applicable project instructions and any wiki path they name.
  Common locations include `wiki/index.md`, `docs/wiki/index.md`, and
  `knowledge/index.md`; these are examples, not required paths.
- If no path is given, use one scoped `rg --files` search in the current project
  for likely indexes and documentation. Confirm OKF from the index/project
  description, an `okf_version` declaration, or typed concept frontmatter.
  Do not search the whole filesystem or unrelated checkouts.
- If none is present, continue the original task normally. Do not create a wiki,
  install tooling, or ask the user to supply one just to satisfy this skill.
- Read the bundle's index first, then relevant nested indexes. When an index is
  absent, use filenames and frontmatter descriptions to select concepts.

## Load only useful concepts

Choose notes by the decisions the task needs: code ownership, endpoint or module
registration, authorization and validation, state and external side effects,
configuration, or verification. Follow the selected concept's links only when
they answer an unresolved question. Do not read every concept by default or
impose this project's filenames and architecture on another bundle.

For OKF v0.2, non-reserved Markdown concepts carry YAML frontmatter with `type`.
`index.md` is navigation and may have no frontmatter, except that a bundle-root
index may declare `okf_version`. `log.md` is optional history. Titles,
descriptions, tags, provenance, and trust fields are optional; unknown types or
missing optional fields do not invalidate a bundle. Earlier versions or partial
adoption can still provide useful guidance; note material limits and continue.

## Interpret evidence and paths

- Resolve relative links and source paths from the concept's directory.
  Leading `/` in an OKF link means the **bundle root**, not the filesystem root.
  Sources such as `../src/...` may legitimately point outside the wiki into its
  surrounding repository. A missing target is a documentation gap, not proof
  that the named behavior is absent.
- Use `sources[].id` to join a claim's `[^id]` footnote to its source entry.
  A `resource` can also be a scope descriptor rather than a file. Follow concrete
  owning sources instead of treating a citation label as verification.
- `generated.at` dates the content; it does not certify accuracy. `verified` can
  be one mapping or a list; its actors indicate machine or human confirmation.
  Check `stale_after`, deprecation, and recorded commit/date baselines when
  present. Treat old snapshots as leads and verify affected current behavior.
- For a neighboring knowledge checkout, follow its own instructions and scoped
  search before reading relevant excerpts. Keep snapshot evidence distinct from
  the active checkout; do not substitute its SHA, cached source, or deployment
  assumptions for local evidence. Read only the external material needed.

## Apply the knowledge to the original task

Trace the affected entry point through checks and orchestration to persistence
or external effects. Find relevant readers and writers before changing a rule.
Reuse the existing owner and preserve the documented invariants that still hold.
For implemented behavior, current owning source takes precedence over a stale
description; instructions and intended business requirements remain requirements.
Report meaningful discrepancies instead of silently treating either as resolved.

Use the documented focused proof and inspect its prerequisites before running
it. Reading a command in a wiki is not itself a request to execute it; run it
only when needed and authorized by the active task. Distinguish source inspection,
build results, tests, and deployment evidence; report material skips or blockers.

Keep a read-only task read-only. If an authorized change triggers the project's
wiki-maintenance rule, update only the affected concepts, preserve their paths
and source attribution, and refresh `generated.at` after meaningful edits. Do
not invent verification events or expand the work into a completeness audit.

Answer the user's task with relevant source/concept references and material
uncertainty. Avoid a narration of everything read.
