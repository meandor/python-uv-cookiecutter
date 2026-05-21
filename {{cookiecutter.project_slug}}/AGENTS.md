# AGENTS.md

Behavioral guidelines to reduce common LLM coding mistakes. Merge with project-specific instructions as needed.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

## 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

## 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.

When your changes create orphans:
- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

---

**These guidelines are working if:** fewer unnecessary changes in diffs, fewer rewrites due to overcomplication, and clarifying questions come before implementation rather than after mistakes.

## Project-Specific Guidelines
A scalable, fault-tolerant, highly-available, robust RDF based graph database. It is based on erlang and erlang OTP and
built with rebar3 and using RocksDB for storage management. It draws inspiration from cassandra using concepts like a token ring, gossip protocol or accrual failure detection.

- Uses the default erlangfmt coding style
- Use TDD to write code, run through the red-green-refactor cycle to do TDD
- Adhere to the testing pyramid to favor unit tests over integration tests over e2e tests
- Use functional programming paradigms as much as possible
- Use erlang otp wherever it makes sense
- Use hexagonal architecture
- Adhere to DRY, YAGNI, KISS
- No magic numbers or strings, prefer configuration instead

### Setup commands

- Install deps: `rebar3 compile`
- Start dev server: `rebar3 shell`
- Run tests: `rebar3 eunit`
- Run autoformat: `rebar3 fmt`
- Run type checker: `rebar3 dialyzer`

Usually you want to run while testing: `rebar3 fmt && rebar3 dialyzer && rebar3 eunit`

### Technical Considerations

- munchkindb uses gossip protocol to manage the cluster (fault tolerancy, cluster membership, state management)
- munchkindb uses phi accrual failure detection to detect offline cluster members
- munchkindb uses a token ring using md5 hashes to distribute data over the cluster
- munchkindb uses rocksdb as the internal data store
- api documentation can be found in `docs/openapi.yaml`
- architectural decision records can be found in `docs/decisions`

### Folder structure

The project uses hexagonal architecture, rough overview can be found in the svg diagram at
`docs/hexagonal-components.svg`

- `docs` contains documentation
- `src` contains the source code
  - `application` contains the application layer in hexagonal architecture (incoming adapters)
  - `domain` contains all domain layer files in hexagonal architecture with the domain logic
    - `api` contains the ports for the domain
    - `spi` contains the ports for the infrastructure
    - `processes` contains erlang otp processes
  - `infrastructure` contains all infrastructure related adapters
- `test` contains the test code

`./docs/knowledge_graph.nt` Contains a knowledge graph representation that should help you navigate the code. 
