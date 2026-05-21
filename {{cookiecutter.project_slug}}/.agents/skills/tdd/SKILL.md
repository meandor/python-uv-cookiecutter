---
name: tdd
description: "Enfore Test-Driven Development (TDD) with strict Red-Green-Refactor cycles. Auto-triggers after a design was planned when implementing new features or functionality. Trigger phrases include: now implement, now add feature, build, create functionality, or any request to add new behavior. Does NOT trigger for designing a new plan, bug fixes, documentation, or configuration changes." 
---

# TDD

Enforce strict Test-Driven Development using Red-Green-Refactor cycles with dedicated subagents. Translates a design
proposal into small achievable chunks and pass them into the TDD cycles. Continue until the feature is fully implemented
and all chunks of work are done.

## Mandatory Workflow

Every new feature MUST follow this strict 3-phase cycle. Do NOT skip phases. Apply the cycle multiple times, until the
wanted feature and implementation is fully there.

### Phase 1: RED - Writing Failing Test

🔴 RED PHASE: Delegating to tdd-red...

Invoke the `tdd-red` subagent with:

- Design plan or feature requirement in a Markdown file from the `designer` subagent or user input
- Expected behavior to test

The subagent returns:

- Test file path
- Failure output confirming the test fails for the right reasons
- Summary of what the test verifies

**Do NOT proceed to the Green phase until test failure is confirmed.**

### Phase 2: GREEN - Make it Pass

🟢 GREEN PHASE: Delegating to tdd-green...

Invoke the `tdd-green` subagent with:

- Test file path from RED phase
- Design plan context or feature requirement context

The subagent returns:

- Files modified
- Success output confirming test passes
- Implementation summary

**Do NOT proceed to Refactor phase until test passes.**

### Phase 3: REFACTOR - Improve

🔵 REFACTOR PHASE: Delegating to tdd-refactor...

Invoke the `tdd-refactor` subagent with:

- Test file path
- Implementation files from GREEN phase

The subagent returns either:

- Changes made + test success output, OR
- "No refactoring needed" with reasoning

**One cycle completes when refactor phase returns. To completely implement one feature, run multiple cycles of this.**

Never:

- Write implementation before the test
- Proceed to Green without seeing Red fails for the right reason
- Skip Refactor evaluation
- Star a new feature before completing the current cycle
