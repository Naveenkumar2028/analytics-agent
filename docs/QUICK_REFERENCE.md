# Analytics Agent Quick Reference

This page is a compact checklist for running the project locally and diagnosing the most common setup issues.

## Start the application

1. Copy the example environment file and fill in the required values.
2. Start the backend from the repository root.
3. Start the frontend in a second terminal when using frontend HMR.
4. Open the local frontend URL in a browser.

### Recommended local development flow

```bash
uv sync
cd frontend && pnpm install && pnpm build && cd ..
uv run analytics-agent bootstrap
uv run uvicorn analytics_agent.main:app --port 8100
```

For frontend hot reload, use a second terminal:

```bash
cd frontend
pnpm dev
```

The exact commands in the main `README.md` remain the source of truth for Docker and packaged-install flows.

## Minimum configuration checklist

- LLM provider and model are configured.
- API keys are present in the local environment file.
- DataHub is reachable when metadata-backed features are enabled.
- The analytical database connection string is valid.
- No secrets are committed to Git.

## First verification steps

Run these checks before debugging the UI:

```bash
# Confirm the service is listening
curl -i http://localhost:8100/

# Verify DataHub connectivity when configured
curl -s -X POST http://localhost:8100/api/settings/connections/datahub/test
```

Then:

- confirm the backend process starts without import errors;
- open the UI and submit a simple natural-language question;
- check backend logs if the UI is blank or the request fails.

## Common symptoms

| Symptom | First thing to check |
| --- | --- |
| Backend exits immediately | Environment variables, migration/bootstrap step, and Python dependencies |
| Root URL returns an error | Backend port, startup logs, and whether the service is fully initialized |
| LLM request fails | Provider, model name, API key, and network access |
| Metadata lookup fails | DataHub URL, token, and service availability |
| SQL query fails | Database URL, credentials, and schema/table names |
| UI shows stale content | Frontend dev server, browser cache, and API base URL |

For detailed recovery steps, see [`TROUBLESHOOTING.md`](./TROUBLESHOOTING.md).
