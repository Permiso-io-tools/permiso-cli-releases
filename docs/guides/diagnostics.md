# Diagnostics

## When to use

Validate hook commands, template versions, queue/audit health, and remote dev environments after setup or when hooks fail silently.

## Commands

```bash
permiso doctor
permiso doctor --json
permiso doctor --fix
permiso doctor --runtime cursor --verbose
```

| Flag | Description |
|------|-------------|
| `--json` | Machine-readable report |
| `--fix` | Apply safe automatic fixes where supported |
| `--runtime` | Limit checks to one runtime |
| `--verbose` | Extra detail per check |

## Typical checks

- Hook binary on PATH and version
- Installed hook templates vs latest manifest
- Queue and audit log health
- Auth session validity

## Related

- [Quick start](../getting-started/quick-start.md)
- [Hook setup](hook-setup.md)
- [Troubleshooting](troubleshooting.md)
