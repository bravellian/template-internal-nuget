---
workbench:
  type: doc
  workItems: []
  codeRefs: []
  pathHistory: []
  path: /docs/template-readiness.md
---

# Template Readiness Report

## Scope
Repository scanned at `C:\src\bravellian\repomanager` to assess reuse readiness as a private Bravellian library template.

## File Tree (top 2-3 levels)
```text
.
├── .codex/
│   └── skills/
│       ├── dotnet-build-diagnostics/
│       ├── dotnet-format-analyzers/
│       ├── dotnet-repo-discovery/
│       ├── dotnet-symbol-grep-recipes/
│       └── dotnet-test-triage/
├── .github/
│   └── workflows/
│       ├── ci.yml
│       ├── quality.yml
│       └── release.yml
├── .opencode/
│   ├── agents/
│   ├── .gitignore
│   └── package.json
├── src/
│   └── Bravellian.Template/
│       ├── Class1.cs
│       └── Bravellian.Template.csproj
├── tests/
│   └── Bravellian.Template.Tests/
│       ├── Bravellian.Template.Tests.csproj
│       └── SanityTests.cs
├── .editorconfig
├── .gitattributes
├── .gitignore
├── .pre-commit-config.yaml
├── AGENTS.md
├── Directory.Build.props
├── Directory.Build.targets
├── Directory.Packages.props
├── global.json
├── Bravellian.Template.slnx
├── README.md
├── NOTICE.md
└── *.props / scripts / metadata files
```

## Required Files Present Checklist
- [x] `global.json`
- [x] `Directory.Build.props`
- [x] `Directory.Build.targets`
- [x] `Directory.Packages.props`
- [x] `*.props` present (`analyzers.props`, `common.props`, `metadata.props`, `non-tests.props`, `strongvalidation.props`, `tests.props`)
- [x] `.editorconfig`
- [x] pre-commit config (`.pre-commit-config.yaml`)
- [x] workflows (`.github/workflows/*.yml`)
- [x] `AGENTS.md`
- [x] `README.md`
- [ ] `NOTICE` (exact filename)
- [x] `NOTICE.md` (present, likely intended equivalent)

## Placeholder Locations
### Bravellian.Template / template naming
- `Bravellian.Template.slnx`
- `src/Bravellian.Template/Bravellian.Template.csproj`
- `tests/Bravellian.Template.Tests/Bravellian.Template.Tests.csproj`
- `src/Bravellian.Template/Class1.cs` (namespace `Bravellian.Template`)
- `tests/Bravellian.Template.Tests/SanityTests.cs` (namespace + type usage)
- `README.md` build/test/pack commands
- `llms.txt` solution and command examples
- `Init-Repo.ps1` (`$old = "Bravellian.Template"` used for rename flow)

### Class1 placeholder
- `src/Bravellian.Template/Class1.cs`
- `tests/Bravellian.Template.Tests/SanityTests.cs`

### TODOs / obvious incomplete markers
- No `TODO`/`FIXME` markers found in template project/workflow files.

## Obvious Inconsistencies
- Skill docs reference a non-existent solution path `src/Bravellian.slnx`:
  - `.codex/skills/dotnet-format-analyzers/SKILL.md`
  - `.codex/skills/dotnet-test-triage/SKILL.md`
- `NOTICE` vs `NOTICE.md` naming mismatch relative to strict checklist expectations.

## Small Safe Fixes Applied
- Fixed broken default target resolution in format/analyzer helper scripts so they now auto-detect repo-root `.slnx`/`.sln` when `DOTNET_FORMAT_TARGET` is not set:
  - `.codex/skills/dotnet-format-analyzers/scripts/run-format-analyzers.ps1`
  - `.codex/skills/dotnet-format-analyzers/scripts/run-format-analyzers.sh`
- Also corrected shell argument display handling in the bash script to avoid parse issues.
