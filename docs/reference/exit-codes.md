# Exit Codes

| Code | Meaning |
|------|---------|
| `0` | Success |
| `1` | General error |
| `2` | Partial failure (e.g. some replay items failed) |

Replay commands return exit code `2` when some items succeed and others fail:

```bash
permiso hooks replay queue --dead-letter --yes
echo $?   # 2 if any item failed
```

## Related

- [Troubleshooting](../guides/troubleshooting.md)
