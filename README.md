# Bravellian .NET Library Template

This repository is a **template** for private Bravellian .NET libraries.

## Layout

- `src/` — packable libraries
- `tests/` — unit tests
- `*.slnx` — solution (use this for build/test/pack)

## Build

```bash
dotnet restore Bravellian.Template.slnx
dotnet build Bravellian.Template.slnx -c Release
```

## Test

```bash
dotnet test --solution Bravellian.Template.slnx -c Release
```

## Pack (local)

```bash
pwsh -File scripts/pack.ps1
```

## Release (GitHub Packages)

Create a tag like `v1.2.3` and push it. The `Release` workflow packs and pushes to GitHub Packages (NuGet).

## How To Publish

1. Pack locally (optional verification):
```powershell
pwsh -File scripts/pack.ps1 -Version 1.2.3
```
Packages are written to `./artifacts/packages` (`.nupkg` + `.snupkg`).

2. Publish via CI:
Tag and push a SemVer tag (for example `v1.2.3`). The release workflow will:
- restore/build/test the repo solution,
- pack with `PackageVersion=1.2.3`,
- push packages to GitHub Packages using `GITHUB_TOKEN`.

## Template Self-Test

Run a full template smoke test (copy -> init -> build -> test -> placeholder scan):

```powershell
pwsh -File scripts/self-test-template.ps1
```

## Workbench Baseline

This template includes a baseline Workbench setup:

- Repo config: `.workbench/config.json`
- Workbench docs/work-item scaffold: `docs/` (including `docs/70-work/*`)
- Codex skills: `skills/workbench-*`
- Daily automation:
  - `.github/workflows/workbench-sync-normalize.yml`
  - `.github/workflows/workbench-item-issue-sync.yml`

Notes:

- Drift-check excludes are configured in `.workbench/config.json` under `validation.linkExclude` and `validation.docExclude`.
- Workbench workflows use `WORKBENCH_GITHUB_TOKEN` when available, otherwise `GITHUB_TOKEN`.
