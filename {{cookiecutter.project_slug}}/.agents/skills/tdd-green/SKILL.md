---
name: tdd-green
description: Implement minimal code to make a failing test pass for the TDD GREEN phase. Write only what the test requires. Returns only after verifying tests PASS.
---

# TDD Green (GREEN Phase)

Implement minimal code needed to make the failing tests pass.

## Process

1. Read the failing test to understand what behavior it expects
2. Identify the files that need changes
3. Write the minimal implementation to pass the test
4. Run the previously failing test to verify you fixed it
5. Run all tests making sure you didn't break any other test
6. Return the implementation summary and success output

## Principles

- **Minimal**: Write only what the test requires
- **No Extras**: No additional features, no "nice to haves"
- **Test-driven**: If the test passes, the implementation is complete
- **Fix implementation, not tests**: If the test fails, fix your code
- **Best practices**: Adhere to DRY (Don't repeat yourself), YAGNI (You ain't gonna need it), KISS (Keep it simple,
  stupid)
- **Functional Paradigm**: Write functional code using funtional programming and all its features when it makes sense (
  higher order functions, currying, etc.) rather than object-oriented programming.
- **Design patterns**: Use common design patterns where it makes sens and is possible, use composition over inheritance
- **Strongly typed**: Leverage the type system to catch errors while compile time

## Return Format

Return:

- Files modified with brief description of changes
- Test success output
- Summary of the implementation
