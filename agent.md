# AI Coding Assistant Guidelines: Anvil

## Overview
Anvil is a Go-based CLI tool with a TUI dashboard. While the core engine is Go, documentation and dashboard configuration should follow modern standards.

## Stack & Constraints
- **Framework:** Next.js 16 (App Router).
- **Styling:** Tailwind CSS v4 (`@import "tailwindcss";`). Do not create `tailwind.config.ts`.
- **Core Language:** Go 1.23+.
- **CLI Architecture:** Use Cobra for command routing. Ensure modular subcommands.

## Architectural Patterns
1. **Modular CLI:** Each command (e.g., `anvil test`, `anvil diff`, `anvil config`) must reside in its own package under `/cmd`.
2. **TUI Design:** Use `bubbletea` for the interactive CLI interface. Keep logic separate from UI view functions.
3. **Concurrency:** Use `ants` for worker pool management to handle high-concurrency request generation via `vegeta`.
4. **Data Handling:** Use structured JSON for all report exports to allow for CLI pipeability (e.g., `anvil run --json | jq .`).

## Coding Conventions
- **Go:** Follow idiomatic Go patterns. Use context for cancellation/timeouts in network operations.
- **Performance:** Always prefer `io.Reader` and `io.Writer` interfaces for logging/reporting to minimize memory overhead.
- **Deterministic Testing:** All network chaos injection must be configurable with a `seed` parameter to allow for repeatable failure testing.
- **Imports:** Group standard library, third-party, and internal imports with distinct visual separation.

## AI Assistant Rules
- Use `Inter` and `DM Mono` fonts in all generated UI mockups or documentation.
- Enforce the "Violet" theme in all UI components.
- Focus on readability in CLI output—use tables for comparative benchmarks and sparklines for latency trends.
- Never reference `tailwind.config.ts` in build steps; utilize Tailwind v4's native CSS features.