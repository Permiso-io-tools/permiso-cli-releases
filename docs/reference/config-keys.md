# Config Keys

| Key | Description | Env var |
|-----|-------------|---------|
| `backend_url` | API base URL | `PERMISO_BACKEND_URL` |
| `hooks_events_url` | Hook ingest URL | `PERMISO_HOOKS_EVENTS_URL` |
| `login_url` | Browser login URL | `PERMISO_LOGIN_URL` |
| `organization_id` | Organization context | `PERMISO_ORGANIZATION_ID` |
| `audit_log.enabled` | Local hook audit log | `PERMISO_AUDIT_LOG_ENABLED` |
| `redaction.enabled` | Send-path redaction (default: `false`) | `PERMISO_REDACTION_ENABLED` |
| `trusted_signing_keys` | Pinned signing key IDs (JSON array) | — |

```bash
permiso config list
permiso config get backend_url
permiso config set trusted_signing_keys '["abc123"]'
```

Future: `docs_url` for `permiso open docs` (Epic 22).

## Related

- [Configuration guide](../guides/configuration.md)
- [File paths](file-paths.md)
