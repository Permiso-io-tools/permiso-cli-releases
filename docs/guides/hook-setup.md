# Hook Setup

## When to use

After authentication, install Permiso-managed hooks so IDEs invoke `permiso hooks send-event` on tool events.

## Prerequisites

- `permiso login` or `PERMISO_API_KEY`
- Supported runtime: claude, cursor, codex, vscode

## Commands

```bash
permiso hooks setup ide
permiso hooks setup ide --runtime claude --scope repo --dry-run
permiso hooks setup all --update --yes
permiso hooks uninstall ide --runtime cursor
```

| Command | Key flags |
|---------|-----------|
| `hooks setup ide` | `--runtime`, `--scope`, `--all-runtimes`, `--dry-run`, `--update` |
| `hooks setup all --update` | `--yes`, `--dry-run` |
| `hooks uninstall ide` | `--runtime`, `--scope` |

## Scopes

| Scope | Effect |
|-------|--------|
| `repo` | Hook config in the current git repository |
| `user` | User-level IDE configuration |

## Supported runtimes

See the [runtimes matrix](../reference/runtimes.md) for detect paths and hook file locations.

> **Warning:** When discovery finds existing hook configs not managed by Permiso, the CLI prompts before replacing files. Test with `--dry-run` in a staging repo first.

## Related

- [Hook events](hook-events.md)
- [Updates](updates.md)
- [Runtimes reference](../reference/runtimes.md)
