# Async Delivery & Daemon

## When to use

When hook callbacks must return quickly, use `--async` to enqueue events and flush via queue commands or the local daemon.

## Queue commands

```bash
echo '{"hook_event_name":"PreToolUse"}' | \
  permiso hooks send-event --runtime claude --async

permiso hooks queue inspect
permiso hooks queue flush
```

| Command | Description |
|---------|-------------|
| `hooks queue inspect` | Show pending and dead-letter items |
| `hooks queue flush` | Deliver queued events to backend |

## Daemon

```bash
permiso daemon start --port 9473 --flush-interval 30s
permiso daemon status
permiso daemon stop
permiso daemon install    # user-level systemd/launchd
permiso daemon uninstall
```

Send via daemon: `permiso hooks send-event --via-daemon --runtime claude`

## Related

- [Hook events](hook-events.md)
- [Troubleshooting](troubleshooting.md)
- [File paths](../reference/file-paths.md)
