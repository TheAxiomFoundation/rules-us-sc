# rac-us-sc

South Carolina jurisdiction-specific RAC source and encoding corpus.

This repo is for South Carolina-administered policy layers. Federal program
cores stay in `rac-us`; South Carolina overlays, manuals, guidance, and
state-specific encodings live here.

## Current scope

- South Carolina SNAP source slices for delegated SNAP state options
- jurisdiction-local source corpus for South Carolina SNAP overlays

## Layout

```text
rac-us-sc/
├── sources/
│   └── slices/
│       └── scdss/
│           └── snap/
│               └── current-effective/
├── scripts/
│   ├── check_no_promoted_stubs.py
│   └── validate_repo.py
└── CLAUDE.md
```

## Local commands

```bash
cd /Users/maxghenis/TheAxiomFoundation/rac
uv run python -m rac.validate all /Users/maxghenis/TheAxiomFoundation/rac-us-sc
uv run python -m rac.test_runner /Users/maxghenis/TheAxiomFoundation/rac-us-sc -v

cd /Users/maxghenis/TheAxiomFoundation/rac-us-sc
python3 scripts/validate_repo.py
```

## Encoding policy

- Repo boundaries follow jurisdictions.
- Keep South Carolina-administered overlays in `rac-us-sc`, even when they sit
  on top of a federal program like SNAP.
- Keep exact local excerpts in `sources/slices/`.
- When a South Carolina source sets a value inside a federally delegated slot,
  add a `*.meta.yaml` sidecar next to the source slice with `relation: sets`
  pointing to the canonical upstream CFR or USC target.
- Do not hand-edit promoted policy outputs; use AutoRAC plus benchmarked repair
  loops.
