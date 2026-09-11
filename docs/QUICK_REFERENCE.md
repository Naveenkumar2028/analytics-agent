# Analytics Agent Quick Reference

This page is a compact checklist for running the project locally and diagnosing the most common setup issues.

## Start the application

1. Copy the example environment file and fill in the required values.
2. Start the backend from the repository root.
3. Start the frontend in a second terminal.
4. Open the local frontend URL in a browser.

Use the exact commands from the main `README.md` for the selected setup path (Docker or manual installation).

## Minimum configuration checklist

- LLM provider and model are configured.
- API keys are present in the local environment file.
- DataHub is reachable when metadata-backed features are enabled.
- The analytical database connection string is valid.
- No secrets are committed to Git.

## First verification steps

- Confirm the backend process starts without import errors.
- Call the health endpoint and verify a successful response.
- Open the UI and submit a simple natural-language question.
- Check backend logs if the UI is blank or the request fails.

## Common symptoms

| Symptom | First thing to check |
| --- | --- |
| Backend exits immediately | Environment variables and Python dependencies |
| LLM request fails | Provider, model name, API key, and network access |
| Metadata lookup fails | DataHub URL, token, and service availability |
| SQL query fails | Database URL, credentials, and schema/table names |
| UI shows stale content | Frontend dev server, browser cache, and API base URL |

For detailed recovery steps, see [`TROUBLESHOOTING.md`](./TROUBLESHOOTING.md).
