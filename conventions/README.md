# Conventions

What every rendered repo keeps, whatever its tier. Estate conformance (D4 in the house)
compares a repo against this list and against the blueprint tag its `.copier-answers.yml`
names.

| Convention | Rule |
|---|---|
| `CLAUDE.md` | Identity and routing only. Under 80 lines. Every rule carries its why where the why is not obvious. |
| Tickets | `.icm/intake/`: an epic is a folder with `breakdown.md` and one stub per unit of work. A one-off is a triage stub. The path is the identity. The folder is the status. The contract is `.icm/intake/CONTEXT.md`, rendered by the blueprint. A user story becomes one epic. The story stays in the client's Drive. The breakdown's `Criteria → stubs` table shows where each criterion went. |
| Pull requests | One ticket is one branch and one pull request. The body follows `.github/pull_request_template.md`: the two gates at the top, anchored by `<!-- gate:spec-approved -->` and `<!-- gate:ready-to-merge -->`, then the ticket path, what changes, the acceptance criteria and how to test. The pull request moves the stub into `_done/`. |
| Scripts | `.icm/scripts/new-run.sh` starts a ticket and `.icm/scripts/close-out.sh` finishes an epic. Both are the blueprint's. They do the mechanics of one step each and decide nothing. |
| Gates | Human checkboxes. A session reads them and never ticks them. Jamie ticks on GitHub or from the desk. A missing anchor means not required. |
| Commits | Conventional Commits. An app's release is the merge of the release-please pull request. A platform names its own release model in `CLAUDE.md`. |
| Writing | Technical text in Simplified Technical English: stubs, breakdowns, pull request bodies, commit messages, hook text. Questions for Jamie are numbered and carry a default answer. Client-facing text in the client's language. |
| CI | `ci.yml` calls the reusable workflows in `legible-consulting/.github`. Nothing is copied in. Never run build, lint, typecheck, test, format or dev locally. |
| Guards | `.claude/settings.json` and the three hooks in `.claude/hooks/` are the blueprint's, byte for byte, so cloud sessions are guarded too. |
| Secrets | Never in git. Names only, in an `.env.example`. Values in GitHub or Vercel settings. |
