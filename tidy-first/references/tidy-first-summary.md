# Tidy First - actionable summary

## Core principles
- Distinguish structural changes (tidyings) from behavior changes; keep them separate.
- Keep tidyings tiny; do only what makes the next behavior change easier.
- Avoid speculative cleanup; tidy in the areas you are actively changing.
- Stop when the behavior change is easy; do not let tidying become the goal.
- Favor cohesion and lower coupling to improve readability and changeability.

## Tidyings catalog
- Guard clauses: replace nested conditionals that wrap the rest of a routine with early returns; avoid many guard clauses.
- Dead code: delete code that is not executed; if unsure, add logging to confirm; remove a small, reversible chunk at a time.
- Normalize symmetries: pick one pattern for similar code and normalize to it; make identical code look identical.
- New interface, old implementation: create the interface you wish existed and delegate to the old one; migrate callers over time.
- Reading order: reorder code to match how a reader would prefer to encounter it; avoid mixing with other tidyings.
- Cohesion order: move related routines or files next to each other; group coupled elements to reduce scattered edits.
- Move declaration and initialization together: keep declarations close to first use; respect data dependencies.
- Explaining variables: extract subexpressions into well-named variables to capture intent.
- Explaining constants: replace meaningful literals with named constants; avoid generic constants that add no meaning.
- Explicit parameters: split routines so inputs are passed explicitly instead of hidden in globals, env vars, or maps.
- Chunk statements: add blank lines between logical steps to reveal structure.
- Extract helper: extract a cohesive block into a helper named by intent; use it to isolate the part you need to change.
- One pile: inline too many tiny helpers when they obscure understanding, then re-extract clearer pieces.
- Explaining comments: write comments for context not obvious from code; target a specific future reader.
- Delete redundant comments: remove comments that only restate the code.

## Common chaining paths
- Guard clause -> explaining variable/helper for the condition.
- Chunk statements -> explaining comments or extract helper.
- Explaining variables/constants -> delete redundant comments; group related constants.
- Extract helper -> guard clause or explaining variables/constants.

## Managing tidyings
- Separate tidyings from behavior changes; use separate PRs or commits when possible.
- Keep batches small to reduce merge conflicts, interactions, and speculative cleanup.
- Maintain rhythm: tidy in minutes up to about an hour; longer usually means drift into refactoring.
- If work is tangled, consider restarting with a tidy-only sequence then a behavior-change sequence.

## When to tidy
- Tidy first when it immediately makes the change easier or improves comprehension, and you know what to tidy.
- Tidy after when you just learned a better structure and doing it now is cheaper than later.
- Tidy later when the payoff is real but not immediate; keep a short list and do it in small batches.
- Tidy never when the code will not change and there is nothing to learn by improving it.

## Minimal checklist
- Identify the exact files and functions your plan will touch.
- Pick one to three tidyings that reduce friction for those changes.
- Apply tidyings in small, behavior-preserving steps.
- Separate tidyings from behavior changes.
