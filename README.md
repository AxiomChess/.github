# .github

Org-level defaults for AxiomChess: issue/PR templates, shared Actions, and workflow templates.

Language: English only. No emoji.

## Contents

| Path | Purpose |
| --- | --- |
| `.github/ISSUE_TEMPLATE/` | Default bug and feature forms for product repos without their own templates |
| `.github/PULL_REQUEST_TEMPLATE.md` | Default PR body with no-emoji / no-AI-co-author / secrets checklist |
| `actions/lint-placeholder/` | Composite action stub other repos can call |
| `workflow-templates/lint-placeholder.yml` | Appears in the Actions "new workflow" picker for org repos |
| `docs/CODEOWNERS.md` | How to add CODEOWNERS in product repos (does not cascade) |
| `CODEOWNERS` | Owners for this `.github` repo only |

## How product repos consume shared actions

### Option A -- call the composite action

In a product repo workflow (for example `api/.github/workflows/ci.yml`):

```yaml
jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: AxiomChess/.github/actions/lint-placeholder@main
```

Pin to a tag or commit SHA once releases exist. Until then `@main` is acceptable for the stub.

### Option B -- start from the org workflow template

In a product repo: Actions -> New workflow -> choose **AxiomChess lint placeholder**. GitHub copies `workflow-templates/lint-placeholder.yml` into that repo and substitutes `$default-branch`.

### Replacing the stub

When a product repo has real `pnpm lint` (or equivalent):

1. Keep calling a shared action only if several repos share the same steps.
2. Otherwise replace the stub step with the repo's own lint command in that repo's workflow.
3. Do not invent lint results; CI must run the real script.

## License

MIT. See `LICENSE`.
