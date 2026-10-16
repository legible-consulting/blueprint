# blueprint

Public template and conventions repo. Everything here is rendered into other repositories or
read by workshop attendees, so: no client names, no contact details, no secrets, no internal
notes. Template files under `templates/<tier>/` are Jinja (`.jinja` suffix) or copied as is;
test a change by rendering into a scratch folder with
`copier copy --vcs-ref HEAD . /tmp/zz-<tier>`, never by editing a client repo by hand.
