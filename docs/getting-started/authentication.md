# Authentication

## When to use

Authenticate before any command that calls the Permiso backend (hook delivery, uploads, updates checks).

## Commands

```bash
permiso login
permiso whoami
permiso logout
```

| Command | Description |
|---------|-------------|
| `permiso login` | Prompt for API key; stored in OS keyring when available |
| `permiso whoami` | Show current user and org context |
| `permiso logout` | Remove stored credentials |

## API key via environment

For CI and non-interactive rollouts:

```bash
export PERMISO_API_KEY=your-key
permiso whoami
```

> **Warning:** Never commit real API keys. Use `test-key` with the [local dummy backend](#) for development.

## Credential storage

The CLI stores the API key in the OS keyring when available **and** mirrors it to `~/.config/permiso/.credentials` (mode `0600`). Reads prefer `PERMISO_API_KEY`, then the keyring, then the file — so IDE hook subprocesses that cannot access the session keyring (common on Linux/WSL) still authenticate. `permiso logout` clears both. See [File paths](../reference/file-paths.md).

## Related

- [Quick start](quick-start.md)
- [Team rollout](team-rollout.md)
