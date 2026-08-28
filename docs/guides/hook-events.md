# Hook Events

## When to use

IDE hooks pipe JSON to `permiso hooks send-event`. Use this guide to understand delivery, normalization, and privacy defaults.

## send-event

```bash
echo '{"hook_event_name":"PreToolUse","tool_name":"Bash"}' | \
  permiso hooks send-event --runtime claude

permiso hooks send-event --runtime claude \
  --file fixtures/hook-events/claude/pre_tool_use.json --dry-run
```

| Flag | Description |
|------|-------------|
| `--runtime` | IDE runtime name (required) |
| `--file` | Read payload from file instead of stdin |
| `--dry-run` | Build envelope locally; no network |
| `--normalize` | Include canonical event block in envelope |
| `--async` | Enqueue for background delivery |
| `--via-daemon` | Send through local daemon HTTP ingest |
| `--redact` | Enable send-path redaction for this event |
| `--no-redact` | Disable send-path redaction (when enabled globally or via `--redact`) |
| `--verbose-redact` | Log matched redaction rule names to stderr |

### Policy decisions (IDE blocking)

On **sync** `send-event` (the default hook command), the CLI POSTs the vendor payload and writes the hooks API response body to **stdout**. Cursor and other IDEs read that JSON to allow or deny the next step (for example `{"permission":"deny"}` or `{"continue":false}`).

- If the API returns an empty/`204` body for a known gate event, the CLI emits a small allow/continue default so the IDE never sees silent empty stdout on success.
- If send fails (network, auth, or API error), the CLI logs a warning to **stderr**, records the failure in the audit log, writes the same allow/continue default when applicable, and exits `0` (**fail open**). Backend outages must not block the agent.
- `--async`, `--via-daemon`, and queue flush are **observational only** — they do not write policy JSON for the IDE and **cannot** enforce allow/deny.

Keep diagnostics on stderr; only policy JSON belongs on stdout when hooks invoke the CLI.

## normalize

Inspect canonical normalization without sending:

```bash
permiso hooks normalize --runtime claude \
  --file fixtures/hook-events/claude/pre_tool_use.json
```

## Event envelope

Every delivery wraps vendor JSON with machine and CLI context:

```json
{
  "machine": { "machine_id": "mch_…", "host": { "os": "linux" } },
  "cli": { "runtime": "claude", "repo_root": "/path", "cli_version": "0.1.0", "user_email": "user@example.com" },
  "event": { "hook_event_name": "PreToolUse", "user_email": "user@example.com" },
  "canonical": null
}
```

Pass `--normalize` to populate `canonical`. **Send-path redaction is off by default.** Pass `--redact` per event, set `redaction.enabled` in config, or use `PERMISO_REDACTION_ENABLED=1` to enable globally. Configure rules in `~/.config/permiso/redaction.yaml`.

## User identity enrichment

Before sending, the CLI best-effort enriches the **vendor payload** (and `cli.user_email`) so backends can attribute events:

| Runtime | Source order |
|---------|--------------|
| **cursor** | Payload `user_email` / `email` / `user.email` |
| **claude** | Payload → `claude auth status` → `~/.claude.json` `oauthAccount.emailAddress` (IDE extension fallback; not `settings.json`) |
| **codex** | Payload → `~/.codex/auth.json` JWT `tokens.id_token` `.email` |
| **vscode** | Payload → OS `machine_id` as `user.id` + `machine_id` (no invented email) |

Existing payload emails are never overwritten. Enrichment failures never block delivery.

## Related

- [Local audit](local-audit.md)
- [Async delivery](async-delivery.md)
- [Configuration](configuration.md)
- [Troubleshooting](troubleshooting.md)
