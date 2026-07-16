# Backfill

## When to use

Inspect historical IDE sessions locally, or upload session metadata when explicitly approved.

> **Warning:** **Local by default.** Upload requires `--send` (and usually confirmation). Full message bodies require `--verbose --include-content`.

## Local read

```bash
permiso backfill --current-repo
permiso backfill --runtime cursor --verbose --limit 10
permiso backfill --dry-run --json
permiso backfill --session <uuid> --include-subagents
permiso backfill --redact
```

| Runtime | Typical log locations |
|---------|----------------------|
| cursor | `~/.cursor/projects/<project>/agent-transcripts/` |
| claude | `~/.claude/projects/<project>/<session>.jsonl` |
| vscode | `~/.config/Code/User/workspaceStorage/.../chatSessions/` |
| codex | `$CODEX_HOME` or `~/.codex/` |

## Upload

```bash
permiso backfill --current-repo --runtime cursor --send
permiso backfill --send --yes
permiso backfill --since 2026-05-01 --until 2026-06-01 --send
permiso backfill --dry-run --send
```

**Privacy tiers:** Default upload sends metadata only. Path redaction is **off by default**; pass `--redact` to mask sensitive path segments in output and uploads.

## Related

- [AI discovery](ai-discovery.md)
- [Backend API](../reference/backend-api.md)
- [Team rollout](../getting-started/team-rollout.md)
