# Permiso CLI

The Permiso CLI is a cross-platform binary that:

- **Onboards** developers (`permiso init`, `permiso onboard`)
- **Installs IDE hooks** for Claude, Cursor, Codex, and VS Code
- **Delivers hook events** to the Permiso backend with machine context and optional normalization
- **Diagnoses** local setup (`permiso doctor`)
- **Scans** repositories for AI tooling (`permiso ai discover`)
- **Backfills** historical IDE sessions (optional upload)

> **Warning:** Discovery and backfill are **local by default**. Upload requires explicit `--send` (and usually confirmation).

## Recommended path

1. [Installation](getting-started/installation.md)
2. [Authentication](getting-started/authentication.md)
3. [Quick start](getting-started/quick-start.md) — init → doctor → dry-run hook event
4. [Command index](reference/command-index.md) — every shipped command
