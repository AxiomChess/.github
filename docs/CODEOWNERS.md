# CODEOWNERS pattern notes

CODEOWNERS does not cascade from this org `.github` repository. Each product repo should add its own `CODEOWNERS` (root, `.github/`, or `docs/`) when collaborators join and branch protection is enabled.

## Org policy (from REPOS.md)

- Org admins own `*`.
- Require 1 review for protected `main` when collaborators join.

## Recommended starter (per product repo)

```
# CODEOWNERS
* @AxiomChess/admins
```

Replace `@AxiomChess/admins` with the real GitHub team slug once the team exists. Until then, list individual admin usernames.

## Protection checklist

1. Add `CODEOWNERS` to the product repo.
2. Enable branch protection on `main`: require PR, require 1 CODEOWNER review when the team is ready.
3. Do not require reviews that block the sole admin during solo bootstrap.
