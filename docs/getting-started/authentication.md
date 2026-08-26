# Authentication

## When to use

Authenticate before any command that calls the Permiso backend (hook delivery, uploads, updates checks).

## Commands

```bash
permiso login
permiso login --api-key YOUR_KEY
permiso login --no-browser
permiso whoami
permiso logout
```

| Command | Description |
|---------|-------------|
| `permiso login` | Prompt for API key; stored in OS keyring when available |
| `permiso login --api-key KEY` | Pass API key on the command line; skips browser and interactive prompt |
| `permiso login --no-browser` | Skip opening the dashboard URL (still prompts unless `--api-key` is set) |
| `permiso whoami` | Show current user and org context |
| `permiso logout` | Remove stored credentials |

## API key via flag

Non-interactive login that persists the key to the keyring/file:

```bash
permiso login --api-key YOUR_KEY
```

> **Warning:** CLI arguments can appear in process listings (`ps`). Prefer `PERMISO_API_KEY` for long-lived CI, or paste interactively when possible.

## API key via environment

For CI and non-interactive rollouts (bypasses keyring/file storage):

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
