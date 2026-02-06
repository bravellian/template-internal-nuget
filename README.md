# Incursa .NET Library Template

This repository is a **template** for private Incursa .NET libraries.

## Layout

- `src/` — packable libraries
- `tests/` — unit tests
- `*.slnx` — solution (use this for build/test/pack)

## Build

```bash
dotnet restore Incursa.Template.slnx
dotnet build Incursa.Template.slnx -c Release
```

## Test

```bash
dotnet test Incursa.Template.slnx -c Release
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
