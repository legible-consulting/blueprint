# Conventions

What every rendered repo keeps, whatever its answers. Estate conformance (D4 in the house)
compares a repo against this list and against the blueprint tag its `.copier-answers.yml`
names.

| Convention | Rule |
|---|---|
| `CLAUDE.md` | Identity and routing only. Under 80 lines. Every rule carries its why where the why is not obvious. |
| Tickets | `.icm/intake/`: an epic is a folder with `breakdown.md` and one stub per unit of work. A one-off is a triage stub. The path is the identity. The folder is the status. The contract is `.icm/intake/CONTEXT.md`, rendered by the blueprint. A user story becomes one epic. The story stays in the client's Drive. The breakdown's `Criteria → stubs` table shows where each criterion went. |
| Pull requests | One ticket is one branch and one pull request. The body follows `.github/pull_request_template.md`: the two gates at the top, anchored by `<!-- gate:spec-approved -->` and `<!-- gate:ready-to-merge -->`, then the ticket path, what changes, the acceptance criteria and how to test. The pull request moves the stub into `_done/`. |
| Scripts | `.icm/scripts/new-run.sh` starts a ticket and `.icm/scripts/close-out.sh` finishes an epic. Both are the blueprint's. They do the mechanics of one step each and decide nothing. |
| UAT | A build that answered yes to `uat` carries `.icm/uat/CONTEXT.md`, the blueprint's. Every merge to `main` deploys the Vercel custom environment `uat` and builds a staged production deployment. The client tests the batch at the UAT address. `promote.sh approve --by` records the sign-off on the release pull request. Jamie's merge of that pull request is the promotion: `promote.yml` migrates production, then promotes the staged build. The UAT database is the Neon branch `uat`, schema only, made by `uat-db.sh`, never by hand. A rollback is `rollback.sh`'s printed command, Jamie's to run. Without UAT the pull request preview is the UAT and production follows `main`. |
| Gates | Human checkboxes. A session reads them and never ticks them. Jamie ticks on GitHub or from the desk. A missing anchor means not required. |
| Commits | Conventional Commits. With `release` yes, the release is Jamie's merge of the release-please pull request. With no, production follows `main` and the merge is the release. |
| Writing | Technical text in Simplified Technical English: stubs, breakdowns, pull request bodies, commit messages, hook text. Questions for Jamie are numbered and carry a default answer. Client-facing text in the client's language. |
| CI | `ci.yml` calls the reusable workflows in `legible-consulting/.github`. Nothing is copied in. Never run build, lint, typecheck, test, format or dev locally. |
| Guards | `.claude/settings.json` and the three hooks in `.claude/hooks/` are the blueprint's, byte for byte, so cloud sessions are guarded too. |
| Secrets | Never in git. Names only, in an `.env.example`. Values in GitHub or Vercel settings. A UAT build's scripts and workflows read `VERCEL_TOKEN`, `NEON_API_KEY` and `DATABASE_URL` as secrets, `VERCEL_TEAM`, `VERCEL_PROJECT` and `NEON_PROJECT_ID` as variables. |
