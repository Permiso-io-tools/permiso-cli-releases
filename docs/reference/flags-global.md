# Global Flags & Conventions

## Common flags

| Flag | Description |
|------|-------------|
| `--json` | Machine-readable output (where supported) |
| `--yes` | Skip confirmation prompts |
| `--dry-run` | Preview without side effects |
| `--verbose` | Extra diagnostic output |
| `-h`, `--help` | Command help |

## Conventions

- **stdin vs `--file`**: Hook commands accept JSON on stdin or via `--file` for replay and testing.
- **Runtime**: Required on most hook commands; values: `claude`, `cursor`, `codex`, `vscode`.
- **Scope**: `repo` or `user` for hook setup commands.
- **Send/upload**: `--send` always implies backend upload; pair with `--yes` in automation only when policy allows.

## Related

- [Command index](command-index.md)
- [Exit codes](exit-codes.md)
