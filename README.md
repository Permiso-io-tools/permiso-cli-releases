# Permiso CLI

Cross-platform CLI that connects IDE and AI coding tool hook events to the [Permiso](https://permiso.io) backend.

**Documentation:** [docs/](docs/README.md)

This repository publishes **pre-built binaries** and **user documentation** only. Source code is not public.

## Install

Download the archive for your platform from [Releases](https://github.com/Permiso-io-tools/permiso-cli-releases/releases).
Assets are named `permiso-cli_<version>_<os>_<arch>.tar.gz` (`.zip` on Windows). **WSL** uses the Linux build.

```bash
VERSION=0.1.0
curl -fsSL -o permiso.tar.gz \
  "https://github.com/Permiso-io-tools/permiso-cli-releases/releases/download/v${VERSION}/permiso-cli_${VERSION}_linux_amd64.tar.gz"
tar -xzf permiso.tar.gz permiso
chmod +x permiso
sudo mv permiso /usr/local/bin/   # or ~/.local/bin

permiso version
permiso login
```

| Platform | Archive suffix |
|----------|----------------|
| Linux / WSL (x64) | `linux_amd64.tar.gz` |
| Linux / WSL (arm64) | `linux_arm64.tar.gz` |
| macOS (Apple Silicon) | `darwin_arm64.tar.gz` |
| macOS (Intel) | `darwin_amd64.tar.gz` |
| Windows (x64) | `windows_amd64.zip` |
| Windows (arm64) | `windows_arm64.zip` |

Verify downloads with `checksums.txt` from the same release.

Then see [Quick start](docs/getting-started/quick-start.md) and [Authentication](docs/getting-started/authentication.md).

## Updates

```bash
permiso updates cli
permiso updates cli --install   # direct binary installs
```

## License

See [LICENSE](LICENSE).
