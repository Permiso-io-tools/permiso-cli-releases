# Troubleshooting

## When to use

Hook events fail silently or queue items accumulate — use these recipes without a live IDE.

## Dry-run and normalize

```bash
permiso hooks send-event --runtime claude \
  --file fixtures/hook-events/claude/pre_tool_use.json --dry-run

permiso hooks normalize --runtime claude \
  --file fixtures/hook-events/claude/pre_tool_use.json
```

## Audit failures

```bash
permiso hooks events list --failed-only --since 1h
permiso hooks events tail --follow
```

## Replay queue and audit

```bash
permiso hooks replay queue --id QUEUE_ITEM_ID
permiso hooks replay queue --dead-letter --yes
permiso hooks replay audit --since 1h --filter runtime=cursor --yes
```

Exit code `2` means partial replay failure (some items failed). See [Exit codes](../reference/exit-codes.md).

## Common fixes

1. `permiso doctor --fix`
2. Re-auth: `permiso login`
3. Flush queue: `permiso hooks queue flush`
4. Check paths: `permiso config show-paths`

## Related

- [Local audit](local-audit.md)
- [Async delivery](async-delivery.md)
- [Diagnostics](diagnostics.md)
