# Atomic

High‑performance, PSR‑friendly PHP building blocks. Our focus is on:

- Performance first: compile‑time optimizations and zero‑overhead execution paths
- Simplicity: small, focused libraries with clear responsibilities
- Interop: strict adherence to PSR standards (PSR‑7/11/12/15)
- Quality: comprehensive tests, static analysis, and consistent code style

Packages
- http-kernel — Ultra‑slim PSR‑15 kernel with compile‑time middleware pipelines
- router — Blazingly fast PSR‑7/15 router with static and parameterized routes

Guiding principle
“An idiot admires complexity, a genius admires simplicity.” — Terry A. Davis

## Roadmap

Phase 1 — Core HTTP (Now)
- Stabilize http-kernel and router (v1.x)
- Publish performance benchmarks and guides
- Tighten CI: test matrix, composer validate, Psalm, CS, coverage

Phase 2 — Foundation Libraries
- http-foundation: PSR‑7 factories/utilities and request/response helpers
- container: PSR‑11 minimal container + service provider pattern
- events: lightweight event dispatcher
- config: environment + config loader (immutability, caching)

Phase 3 — Platform Utilities
- cache: simple, fast in‑memory + file backends
- console: commands, IO, help, and minimal task runner
- view: template integration guidelines (framework‑agnostic)
- auth/middleware: common route‑aware middleware (authz, rate limit, CORS)

Phase 4 — Integrations & DX
- HTTP server adapters and quick‑start app skeleton
- Router/Kernel dev server + hot reload (where feasible)
- Recipes and examples repository
- Website and documentation: https://atomic.thavarshan.com

## Project Plan

Principles
- Performance over abstraction; compile‑time where possible
- Small, composable components with clear responsibilities
- “PSR‑first”: prefer standards to custom types

Practices
- 100% static analysis clean (Psalm)
- Enforced code style (PHP‑CS‑Fixer) and EditorConfig
- CI: tests with coverage, psalm, cs‑check, composer validate
- Semantic versioning, changelogs on each release

Community
- Issues and RFCs for significant design changes
- Clear contribution guidelines and a welcoming code of conduct
