# AI Discovery

## When to use

Discover MCP servers, hook configs, agent instruction files, and AI-related dependencies in a repo before rollout.

> **Warning:** Scans are **local-only by default**. Nothing is sent unless you pass `--send`.

## Commands

```bash
permiso ai discover --current-repo
permiso ai discover --path ./my-app --json
permiso ai discover --dry-run
permiso ai discover --current-repo --send --yes
```

| Flag | Description |
|------|-------------|
| `--path` | Directory to scan (default: current git repo) |
| `--current-repo` | Restrict to git root |
| `--json` | Structured JSON report |
| `--dry-run` | List scanners and scope only |
| `--send` | Upload report after confirmation |
| `--yes` | Skip upload confirmation |
| `--redact` | Redact home directory and username segments in paths |
| `--no-redact` | Disable path redaction (when enabled globally or via `--redact`) |

Path redaction is **off by default**. Pass `--redact` to mask home directory and username segments in output.

## Related

- [Onboarding pipeline](onboarding-pipeline.md)
- [Backend API](../reference/backend-api.md)
- [Team rollout](../getting-started/team-rollout.md)
