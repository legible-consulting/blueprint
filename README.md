# blueprint

Legible Consulting's method, public: one copier template with a `tier` question that renders
a client build (`site`, `app`, `platform`) or a client's own ICM workspace (`workspace`), the
conventions every rendered repo follows, and the workshop kit. An `app` also answers `uat`: yes
renders a client UAT environment, its Neon branch and the promotion to production
(`templates/README.md` → UAT).

```bash
copier copy gh:legible-consulting/blueprint ~/Desktop/Apps/projects/<slug>
copier update   # inside a rendered repo, after a new tag here
```

Tags are the versions `copier update` compares (PEP 440: `v0.1.0`, `v0.2.0`, …). Nothing
client-specific is ever committed here.

| Folder | Holds |
|---|---|
| `templates/<tier>/` | the files a tier renders. `{{ _copier_conf.answers_file }}.jinja` records the answers |
| `conventions/` | what a rendered repo must keep: `CLAUDE.md` shape, tickets, pull requests and gates, commits, writing, CI, guards, secrets |
| `workshop-kit/` | the one-day workshop (Marp) and course material |

`check.yml` renders every tier on each push, the `app` tier with and without `uat`, lints the
rendered workflows, hooks and scripts, and checks that the files the tiers share are
byte-identical.
