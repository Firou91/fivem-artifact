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
# Example: stable Windows artifact
git clone -b stable-windows git@github.com:Firou91/fivem-artifact.git

# Example: latest Linux artifact
git clone -b latest-linux git@github.com:Firou91/fivem-artifact.git
```

### 2. Update when a new version is available

When the workflow publishes a newer artifact, simply pull to get it:

```bash
git pull
```

If you manage your server from an IDE or editor, pull from there when you see that the remote branch has been updated.

## How it works

Two GitHub Actions workflows (`publish-stable.yml` and `publish-latest.yml`) are triggered via **workflow_dispatch**. Each run checks the official FiveM changelog API for the current version, compares it with the version stored in the branch (`artifact-version.txt`), and publishes a new commit only when the artifact has changed.

## License

This repository's tooling (workflows, scripts, documentation) is licensed under the [MIT License](LICENSE).

FiveM server artifacts are the property of [Cfx.re](https://cfx.re) / [Rockstar Games](https://www.rockstargames.com) and are subject to their respective terms of use.
