# blueprint

Public template, conventions and workshop kit repo. Everything here is rendered into other
repositories or read by workshop attendees, so: no client names, no contact details, no
secrets, no internal notes. The template is one root, `template/`. It renders a client build,
or with `workspace` yes a client's ICM workspace. Its files are Jinja (`.jinja` suffix) or
copied as is, and a file or folder whose name carries a question renders only on yes. The
questions are the bank in `copier.yml`: every functionality question has a default and a help
line. Test a change by rendering into a scratch folder with `copier copy --vcs-ref HEAD .
/tmp/zz`, never by editing a client repo by hand. `check.yml` renders the proof answer sets on
each pull request and on push to `main`. It lints the rendered workflows, hooks and scripts,
runs the router's fixture test in each build, and proves `copier update` from an older tag to
`HEAD`. Technical text in Simplified Technical English.
