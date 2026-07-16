# Team Rollout

## Recommended sequence

1. **Authenticate** — `permiso login` (or `PERMISO_API_KEY` per org policy)
2. **Scan the repo** — `permiso ai discover --current-repo` (local-only unless `--send`)
3. **Instrument hooks** — `permiso init` or `permiso hooks setup ide --runtime <name> --scope repo`
4. **Verify** — `permiso doctor` (use `--fix` for common issues)
5. **Optional history** — `permiso backfill --current-repo --send` only when explicitly approved

Check progress: `permiso onboard status`

## Non-interactive rollout (CI / golden images)

```bash
permiso login   # or export PERMISO_API_KEY=...
permiso init --yes --runtime cursor --scope repo --skip-discovery
permiso doctor --runtime cursor
permiso onboard status --json
```

Use `--dry-run` first to preview hook file changes.

## Data handling

| Step | Uploads data? |
|------|----------------|
| `ai discover` | No (unless `--send`) |
| `init` / hook setup | No |
| `doctor` | No |
| `backfill` | No (unless `--send`) |
| `hooks send-event` | Yes (live hook events) |

> **Warning:** Never pass `--send` on discovery or backfill in regulated environments without explicit approval.

## Support checklist

- `permiso onboard suggest` — next recommended command
- `permiso config show-paths` — local config, queue, audit locations
- `permiso hooks events list --failed-only` — delivery failures
- `permiso hooks replay queue --dead-letter --yes` — after backend/auth fix

## Related

- [Onboarding pipeline](../guides/onboarding-pipeline.md)
- [AI discovery](../guides/ai-discovery.md)
- [Backfill](../guides/backfill.md)
