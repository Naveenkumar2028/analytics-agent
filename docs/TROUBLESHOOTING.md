# Troubleshooting

Use this guide when Analytics Agent does not start cleanly or cannot reach a model, DataHub, or warehouse.

## Server does not start

1. Confirm the supported runtime:
   - Python 3.11+
   - `uv` installed for contributor setup
   - Node/pnpm available when rebuilding the frontend
2. Run the bootstrap step once after cloning or after pulling migration changes:

   ```bash
   uv run analytics-agent bootstrap
   ```

3. Check the backend logs:

   ```bash
   make logs
   ```

   For a packaged install, inspect `~/.datahub/analytics-agent/logs/agent.log`.

## Setup wizard or configuration errors

- Copy `.env.example` to `.env` only when you need environment-based configuration.
- Keep secrets in `.env` or your secret manager; do not commit them to Git.
- If you changed provider or connection settings, restart the server so the new values are loaded.
- When using `config.yaml`, verify YAML indentation and confirm every `${ENV_VAR}` placeholder is defined.

## LLM requests fail

- Confirm `LLM_PROVIDER` matches the credentials you supplied.
- Check that the selected model is available for the account or region.
- Verify the API key is active and has enough quota.
- For AWS Bedrock, check the active AWS profile and region before starting the app.

## DataHub connection fails

Test the connection from the running app:

```bash
curl -s -X POST http://localhost:8100/api/settings/connections/datahub/test
```

If the test fails, verify:

- the GMS URL ends with `/gms` when required by the deployment
- the token or SSO session is valid
- the DataHub host is reachable from the machine or container running Analytics Agent
- self-hosted DataHub credentials are correct

## Warehouse connection fails

- Confirm the driver for the selected warehouse is installed.
- Check account, host, database, schema, warehouse, and project identifiers for typos.
- For BigQuery, ensure the service account has access to the project and dataset.
- For Snowflake, confirm the user can use the warehouse and access the target database/schema.
- Test the same credentials with the warehouse's native CLI or console when possible.

## Frontend looks stale or blank

Rebuild the frontend and restart the backend:

```bash
make start
```

For frontend hot reload during development:

```bash
cd frontend
pnpm dev
```

If browser assets still look stale, stop the dev server, remove the generated frontend build output, reinstall dependencies, and run the build again.

## Reset local state

Use this only when you intentionally want to remove local configuration and database state:

```bash
make nuke
```

This resets the local environment, so export or back up any configuration you want to keep first.
