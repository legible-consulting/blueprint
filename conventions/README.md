# Conventions

What every rendered repo keeps, so that conformance (D4) has something to compare against:

- `CLAUDE.md` under 80 lines: identity and routing only.
- Every stage folder carries a `CONTEXT.md` with Inputs, Process, Outputs.
- `ci.yml` calls `legible-consulting/.github` reusable workflows; nothing is copied in.
- Conventional Commits; the release is the merge of the release-please PR.
- Secrets never in git; names only in the access table.
