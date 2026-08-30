# Contributing

Thank you for your interest in contributing to Analytics Agent!

## Prerequisites

Before starting development, make sure you have:

- Python 3.11 or newer
- `uv`
- Node.js 20 or newer
- `pnpm`

## Development setup

1. Fork the repository and clone your fork.
2. Create a feature branch from `main`.
3. Follow the development setup described in `README.md`.
4. Install the project dependencies using the repository's documented `make install` (or equivalent manual) steps.
5. Start the development environment using the documented `make dev` command or equivalent manual steps.

## Running tests

Run the project's test suite before opening a pull request. Follow the test commands documented in `README.md` and make sure the checks relevant to your change pass locally.

If you add or modify behavior, include appropriate tests when practical.

## Commit messages

This project uses Conventional Commits. Keep commit messages concise and use an appropriate type, for example:

```text
feat: add analytics filter
fix: handle missing connector data
docs: clarify local development setup
chore: update dependencies
```

## Pull request process

1. Create a focused branch for your change.
2. Keep the change small and related to one problem.
3. Run relevant tests and checks locally.
4. Use a clear PR title and description explaining what changed and why.
5. Link the relevant issue when applicable.
6. Be responsive to review feedback and update the branch as needed.
7. Wait for CI checks and maintainer review before merging.

## Good first contributions

Documentation improvements, tests, bug fixes, and small usability improvements are all welcome. If you are unsure where to start, look for issues labeled `good first issue` or `documentation`.

## Questions

For questions about contributing or the development environment, please use the repository's existing issue and discussion channels.
