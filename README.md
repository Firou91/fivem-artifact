# fivem-artifact

Pre-built FiveM server artifacts, automatically published and kept up-to-date via GitHub Actions.

## Branches

Each branch contains a ready-to-use FiveM server artifact for a specific platform and release channel:

| Branch | Platform | Channel | Description |
|--------|----------|---------|-------------|
| `stable-windows` | Windows | Stable | Latest recommended build |
| `stable-linux` | Linux | Stable | Latest recommended build |
| `latest-windows` | Windows | Latest | Bleeding-edge build |
| `latest-linux` | Linux | Latest | Bleeding-edge build |

## Usage

### 1. Clone the branch you need

```bash
# Example: stable or latest Windows artifact
git clone -b stable-windows https://github.com/Firou91/fivem-artifact.git
git clone -b latest-windows https://github.com/Firou91/fivem-artifact.git

# Example: stable or latest Linux artifact
git clone -b stable-linux https://github.com/Firou91/fivem-artifact.git
git clone -b latest-linux https://github.com/Firou91/fivem-artifact.git
```

### 2. Update when a new version is available

When the workflow publishes a newer artifact, simply pull to get it:

```bash
git pull
```

If you manage your server from an IDE or editor, pull from there when you see that the remote branch has been updated.
If your IDE or editor supports it, you can schedule git fetch operations at regular intervals to automatically check for updates.

## Maintainers

The root `.gitignore` is synced from `main` to artifact branches to protect repository maintainers from accidentally pushing local sensitive files (`server-monitor-token.key`, `server-tls.crt`, `server-tls.key`).
This is a maintainer-side safety measure; users without push permissions cannot publish changes to this repository.

## How it works

`publish-stable.yml` and `publish-latest.yml` run on schedule and via **workflow_dispatch**. Each run checks the official FiveM changelog API for the current version, compares it with the version stored in the branch (`artifact-version.txt`), and publishes a new commit only when the artifact has changed.

`sync-gitignore.yml` runs when `.gitignore` changes on `main` (and via **workflow_dispatch**) to propagate only the root `.gitignore` to artifact branches.

## License

This repository's tooling (workflows, scripts, documentation) is licensed under the [MIT License](LICENSE).

FiveM server artifacts are the property of [Cfx.re](https://cfx.re) / [Rockstar Games](https://www.rockstargames.com) and are subject to their respective terms of use.
