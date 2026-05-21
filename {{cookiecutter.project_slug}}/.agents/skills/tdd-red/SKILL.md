---
name: tdd-red
description: Write failing tests for TDD RED phase. Use when implementing new features with TDD. Returns only after verifying test FAILS for the right reason.
---

# TDD Red (RED Phase)

Interpret from a given feature/functionality a test case that implements either a part or the whole functionality.
Adheres to the testing pyramid, favoring unit tests over integration tests, integration tests over component or e2e
tests.

## Process

1. Understand the feature requirement from the prompt, context and the plan
2. Write a test that encapsulates one example of the behavior you are expecting to implement the feature (can be smaller
   chunk not the whole behavior)
3. Treat the tests you create like mathmatical induction in order to prove that the overall feature works. Start with an
   example with n=1, then show it also works for n=n+1 which then means it works in general
4. Run the test to verify it fails
5. Return the test file path and failure output

## Requirements

- Test must describe behavior, not necessarily state
- Use mocks to test in isolation
- Test MUST fail when run - verify before returning

## Return Format

Return:

- Test file path
- Failure output showing the test fails
- Brief summary of what the test verifies
