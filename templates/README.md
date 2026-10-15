# Tiers

| Tier | Renders | Notes |
|---|---|---|
| `site` | a static site: `CLAUDE.md`, `BUILD.md`, `ci.yml` calling `.github`'s `check-client` and `deploy-vercel`, `.claude/settings.json` with the local-checks hook, `vercel.json` | public by default |
| `app` | the site tier plus app scaffolding, release-please, `guard-main` | private by default; deploys from Actions only (`"git": {"deploymentEnabled": false}`) |
| `platform` | the app tier plus the heavier pipeline | private |
| `icm-workspace` | a client's own ICM workspace for coaching | rendered into the client's account |

Each tier folder is a complete template root for copier (`_subdirectory` points here). Only
the answers file and a README exist yet; the tier contents are Wave 1 (D2) work.
