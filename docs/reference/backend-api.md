# Backend API

| Method | Endpoint | Used by |
|--------|----------|---------|
| `GET` | `/cli/me` | `whoami`, auth validation |
| `GET` | `/cli/hooks/projects` | Hook setup, init |
| `POST` | Hook ingest URL (default `https://alb.permiso.io/hooks`) | `hooks send-event` |
| `GET` | `/cli/releases/latest` | `updates cli` |
| `GET` | `/cli/hooks/integrations/manifests/:runtime` | Hook setup, updates |
| `POST` | `/cli/discovery/reports` | `ai discover --send` |
| `POST` | `/cli/backfill/sessions` | `backfill --send` |

Override base URL with `permiso config set backend_url` or `PERMISO_BACKEND_URL`.

## Local testing

Use the [dummy backend](#) with `test-key`.

## Related

- [Authentication](../getting-started/authentication.md)
- [AI discovery](../guides/ai-discovery.md)
- [Backfill](../guides/backfill.md)
