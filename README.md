# Nite Install Releases

This repository publishes installable Nite framework releases from the private source repository.

## Install

Download the installer into an empty project directory, then run the latest public release:

```bash
curl -fsSL https://raw.githubusercontent.com/fredricknsanhewe/nite-install/main/install -o install
php install
```

Install an exact release:

```bash
php install --version=v1.0.0
php install --version=v2.2.0
```

## Upgrade

From an existing Nite application directory:

```bash
php install --upgrade
```

Read the packaged `UPGRADE.md` before upgrading a production application.

## Downgrade

From an existing Nite application directory:

```bash
php install --downgrade=v1.0.0
```

## How Versioning Works

- `latest.json` is the public release index that the installer reads first.
- Every published version is stored separately under `releases/<tag>/`.
- Older versions are preserved and can still be installed later.
- The installer validates the requested version before it downloads the package.
- Nite preserves `.env`, `.env.docker`, `storage/`, `public/uploads/`, and `routes/generated/` during managed updates.
- Managed file backups are written under `storage/console/backups/` unless you disable backups explicitly.

## Release Layout

- `latest.json`
  Tracks the latest stable tag and the full published version list.
- `releases/vX.Y.Z/package.zip`
  The curated installable framework package for that version.
- `releases/vX.Y.Z/release.json`
  Metadata for that package, including the checksum used by the installer.

The release package includes Nite's runtime source layers such as controllers, routes, services, models, starter docs, sample definitions, and runnable example assets so downstream developers can learn from the framework in-place after installation.

## Repository

- Public install repository: https://github.com/fredricknsanhewe/nite-install
- Public release index: `latest.json`
- Public branch/ref: `main`
