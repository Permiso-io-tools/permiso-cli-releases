# File Paths

Run `permiso config show-paths` for resolved paths on your machine.

## Default layout

| Path | Purpose |
|------|---------|
| `~/.config/permiso/config.json` | User config overrides |
| `~/.config/permiso/state.json` | Onboarding progress |
| `~/.config/permiso/.credentials` | Credential fallback |
| `~/.config/permiso/redaction.yaml` | Redaction rules |
| `~/.config/permiso/machine.json` | Cached machine ID |
| `~/.cache/permiso/queue/` | Async delivery queue |
| `~/.cache/permiso/audit/events.jsonl` | Hook delivery audit log |
| `~/.cache/permiso/manifests/` | Cached hook manifests |
| `~/.cache/permiso/logs/` | CLI logs |

## Related

- [Configuration](../guides/configuration.md)
- [Local audit](../guides/local-audit.md)
- [Async delivery](../guides/async-delivery.md)
