# Configuration

## When to use

Inspect effective settings, override URLs for staging, and manage send-path redaction rules.

## Config subcommands

```bash
permiso config show
permiso config show --json
permiso config list
permiso config get backend_url
permiso config set backend_url http://localhost:3000/cli
permiso config unset backend_url
permiso config validate
permiso config export
permiso config import settings.json
permiso config show-paths
```

See [Config keys](../reference/config-keys.md) for the full registry.

## Redaction

```bash
permiso config redaction show
permiso config redaction validate
permiso config redaction test --file fixtures/redaction-samples/token.json
```

Rules live in `~/.config/permiso/redaction.yaml`. Send-path redaction is **off by default**. Enable globally with:

```bash
permiso config set redaction.enabled true
# or
export PERMISO_REDACTION_ENABLED=1
```

Per-event override: `permiso hooks send-event --redact`.

## Related

- [Hook events](hook-events.md)
- [File paths](../reference/file-paths.md)
- [Config keys reference](../reference/config-keys.md)
