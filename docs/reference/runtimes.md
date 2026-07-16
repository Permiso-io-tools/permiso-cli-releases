# Runtimes Matrix

| Runtime | Hook setup | send-event | Backfill | Discovery |
|---------|------------|------------|----------|-----------|
| **claude** | ✅ | ✅ | ✅ | ✅ |
| **cursor** | ✅ | ✅ | ✅ | ✅ |
| **codex** | ✅ | ✅ | ✅ | ✅ |
| **vscode** | ✅ | ✅ | ✅ | ✅ |

Each runtime supports detect, install, uninstall, normalize, and hook command generation.

## Hook commands

IDE configs invoke:

```bash
permiso hooks send-event --runtime <name>
```

## Manifests

Template versions are fetched from `GET /cli/hooks/integrations/manifests/:runtime` and published by the Permiso control plane.

## Related

- [Hook setup](../guides/hook-setup.md)
- [Hook events](../guides/hook-events.md)
- [Updates](../guides/updates.md)
