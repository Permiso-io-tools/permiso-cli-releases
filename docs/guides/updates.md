# Updates

## When to use

Keep the CLI binary and IDE hook templates current. Manifests and releases are verified with Ed25519 signatures.

## CLI updates

```bash
permiso updates cli
permiso updates cli --install
permiso updates cli --verify-only
```

| Flag | Description |
|------|-------------|
| `--install` | Direct binary install (homebrew/winget/scoop get hints otherwise) |
| `--version` | Target a specific version |
| `--verify-only` | Check signatures without installing |
| `--insecure-skip-verify` | Skip verification (requires `PERMISO_INSECURE_SKIP_VERIFY=1`) |

## Hook template updates

```bash
permiso hooks updates all --json
permiso hooks updates ide --runtime claude
permiso hooks setup all --update --yes
```

## Signing

Release and manifest signatures use Ed25519. Pin keys with `permiso config set trusted_signing_keys '["key-id"]'`.

## Related

- [Hook setup](hook-setup.md)
- [Configuration](configuration.md)
