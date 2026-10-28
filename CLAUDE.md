# blueprint

Public template, conventions and workshop kit repo. Copier renders everything here into other
repositories, or workshop attendees read it, so: no client names, no contact details, no
secrets, no internal notes. The template is one root, `template/`. It renders a client build,
or with `workspace` yes a client's ICM workspace. Its files are Jinja (`.jinja` suffix) or
copied as is, and a file or folder whose name carries a question renders only on yes. The
questions are the bank in `copier.yml`: every functionality question has a default and a help
line. Test a change by rendering into a scratch folder with `copier copy --vcs-ref HEAD .
/tmp/zz`, never by editing a client repo by hand. `check.yml` renders the proof answer sets on
each pull request and on push to `main`. It lints the rendered workflows, hooks and scripts,
runs the router's fixture test in each build, and proves `copier update` from an older tag to
`HEAD`. A rendered repo conforms only through `copier update`. A rule that a file of the
repo's own must follow lives in a blueprint file that the repo's file calls, never in a line
that each repo copies (why: a copied line changes only by hand in each repo, so a new tag does
not reach it · Jamie, 2026-10-28). Technical text in Simplified Technical English.
