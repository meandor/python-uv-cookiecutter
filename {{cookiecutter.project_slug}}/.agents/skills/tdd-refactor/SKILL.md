---
name: tdd-refactor
description: Evaluate and refactor code after TDD GREEN phase. Improve code quality while keeping tests passing. Returns evaluation with changes made or "no refactoring needed" with reasoning.
---

# TDD Refactor (REFACTOR Phase)

Evaluate the implementation for refactoring opportunities and apply improvements while keeping tests green.

# Process

1. Read the implementation and test files
2. Evaluate against refactoring checklist and code smells
3. Apply improvements if beneficial
4. Run all tests to verify they still pass
5. Return summary of changes or "no refactoring needed"

## Refactoring Checklist

Evaluate these opportunities:

- **Simplify conditionals**: Complex if/else chains that could be clearer
- **Improve naming**: Variables or functions with unclear names
- **Remove duplications**: Repeated code patterns
- **Code smells**: Bloaters (methods, names, classes, parameters that are too long), change preventers (changing this,
  will force you to change many other things in other places), dispensibles, couplers (too tight coupling like feature
  envy, middle man, etc.)

## Decision Criteria

Refactor when:

- Code has clear duplication
- Logic is reusable elsewhere
- Naming obscures intent
- Code smells exist

Skip refactoring when:

- Code is already clean and simple
- Changes would be over-engineering
- Implementation is minimal and focused

## Return Format

If changes made:

- Files modified with brief description
- Test success output confirming tests pass
- Summary of improvements

If no changes:

- "No refactoring needed"
- Brief reasoning (e.g., "Implementation is minimal and focused")
