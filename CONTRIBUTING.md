# Contributing to Analytics Agent

Thanks for helping improve Analytics Agent. This guide keeps local changes reproducible and makes it easier to review backend, frontend, and DataHub-related work.

## Development setup

1. Install the prerequisites listed in the README: Python 3.11+, `uv`, `mise`, Node.js, and `pnpm`.
2. Clone the repository and run:

   ```bash
   mise install
   make install
   ```

3. Start the application with:

   ```bash
   make start
   ```

   The development server runs at `http://localhost:8100`.

## Before opening a pull request

- Keep changes focused on one feature, bug fix, or documentation improvement.
- Run the relevant backend and frontend checks available in the repository.
- If you change SQL generation, connection handling, or DataHub context behavior, add or update a regression test.
- Update documentation when setup steps, configuration, commands, or user-visible behavior change.
- Avoid committing API keys, database credentials, local config files, generated build output, or personal datasets.

## Suggested validation checklist

### Backend

- Start the backend locally and verify the health or root endpoint responds.
- Exercise the changed path with a representative question or fixture.
- Confirm errors are actionable and do not expose secrets.

### Frontend

- Check the affected flow in both light and dark themes.
- Verify loading, empty, success, and error states.
- Confirm charts and tables remain readable at common desktop widths.

### Data and integrations

- Use sample or synthetic data for tests whenever possible.
- Document required environment variables and safe defaults.
- For DataHub changes, describe the expected metadata or context improvement in the PR.

## Commit messages

Use a short imperative subject, for example:

```text
fix: preserve chart filters across follow-up questions
```

Prefer one logical change per commit. Pull requests should explain what changed, how it was tested, and any setup or migration notes.

## Reporting issues

Include the operating system, Python and Node versions, the command that failed, the relevant logs, and a minimal reproduction. Remove secrets before sharing logs publicly.
