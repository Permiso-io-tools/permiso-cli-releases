# Installation

## When to use

Install the Permiso CLI on a developer machine or golden image before `login` and hook setup.

## Pre-built binaries (recommended)

Download from [GitHub Releases](https://github.com/Permiso-io/permiso-cli-releases/releases). Assets are named `permiso-cli_<version>_<os>_<arch>.tar.gz` (`.zip` on Windows).

```bash
VERSION=0.1.0
curl -fsSL -o permiso.tar.gz \
  "https://github.com/Permiso-io/permiso-cli-releases/releases/download/v${VERSION}/permiso-cli_${VERSION}_linux_amd64.tar.gz"
tar -xzf permiso.tar.gz permiso
chmod +x permiso
sudo mv permiso /usr/local/bin/

permiso version
permiso login
```

| Platform | Asset suffix |
|----------|----------------|
| Linux amd64 | `linux_amd64.tar.gz` |
| Linux arm64 | `linux_arm64.tar.gz` |
| macOS | `darwin_amd64` / `darwin_arm64` |
| Windows | `windows_* .zip` |

**WSL** uses the Linux build (`linux_amd64` on typical WSL2).

Verify downloads with `checksums.txt` from the same release.

Source code is not publicly distributed; use the pre-built binaries above.

## Shell completions

| Shell | Install |
|-------|---------|
| Bash | `permiso completion bash \| sudo tee /etc/bash_completion.d/permiso` |
| Zsh | `permiso completion zsh > "\${fpath[1]}/_permiso"` |
| Fish | `permiso completion fish > ~/.config/fish/completions/permiso.fish` |

Restart your shell. Tab-complete runtimes on `permiso hooks setup ide --runtime <TAB>`.

## Environment variables

| Variable | Description |
|----------|-------------|
| `PERMISO_API_KEY` | API key (bypasses keyring/file storage) |
| `PERMISO_BACKEND_URL` | Override API base URL |
| `PERMISO_HOOKS_EVENTS_URL` | Override hook ingest URL |
| `PERMISO_LOGIN_URL` | Override browser login URL |
| `PERMISO_ORGANIZATION_ID` | Organization context |
| `PERMISO_AUDIT_LOG_ENABLED` | Enable/disable local audit log |
| `PERMISO_REDACTION_ENABLED` | Enable send-path redaction globally (default: off) |

## Related

- [Authentication](authentication.md)
- [Quick start](quick-start.md)
