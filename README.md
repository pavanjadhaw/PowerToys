# PowerToys fork CI

This orphan branch is the fork's default branch and holds only the fork's CI, so upstream's own workflows never run here.

- Feature branch: `grab-anywhere` (upstream release tag + a few small commits in `src/modules/GrabAndMove` and its settings page).
- `.github/workflows/fork-build.yml`: daily and on demand, rebases `grab-anywhere` onto the latest upstream release tag when there is a newer one, builds the per-user x64 installer and publishes it as a prerelease named `build-<tag>-<sha>`.
- Optional secrets: `FORK_PUSH_TOKEN` (token with `contents` + `workflows` write on this repo, to push the rebased branch back), `SIGNING_PFX_BASE64` / `SIGNING_PFX_PASSWORD` (a fixed MSIX signing cert; without them each build makes its own and ships its `.cer`).
