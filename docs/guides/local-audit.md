# Local Audit Log

## When to use

Inspect sync, queued, and flush deliveries recorded locally at `{CacheDir}/audit/events.jsonl`.

## Commands

```bash
permiso hooks events tail
permiso hooks events tail --follow --runtime cursor
permiso hooks events list --failed-only --since 1h
permiso hooks events clear --before 2026-01-01
```

| Command | Key flags |
|---------|-----------|
| `events tail` | `--follow`, `--json`, `--runtime`, `--since` |
| `events list` | `--failed-only`, `--json`, `--since` |
| `events clear` | `--before DATE` |

## JSON output

Use `--json` for scripting and integration with replay workflows.

## Related

- [Troubleshooting](troubleshooting.md)
- [Async delivery](async-delivery.md)
- [File paths](../reference/file-paths.md)
