# Contributing to Atomic

Thanks for your interest in contributing! We welcome pull requests and ideas.

- Discuss significant or breaking proposals with an issue before implementation.
- Keep changes focused, small, and performance‑conscious.
- Follow PSR‑12 and repository code style (php-cs-fixer config is provided).
- Ensure tests and static analysis pass locally (see scripts below).

## Getting Started

- PHP 8.4+
- Composer
- Install dependencies: `composer install`
- Run tests: `composer test`
- Static analysis: `composer psalm`
- Code style check: `composer cs-check`
- Auto-fix style: `composer cs-fix`

## Pull Requests

- Use a descriptive title and explain the rationale.
- Include tests for new features or fixes.
- Avoid public API breaks; if unavoidable, document in the PR description and CHANGELOG.
- For perf-sensitive areas, add/update benchmarks and include results.

## Reporting Issues

- Include environment info (PHP version, OS) and steps to reproduce.
- Share minimal, reproducible examples if possible.

## Security

Please report security issues privately. See SECURITY.md for instructions.

