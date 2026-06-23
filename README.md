# Dane Parin

Indie dev. Two CLI tools I currently maintain, both open source.

---

**[standup-bot](https://github.com/SemTiOne/standup-bot)** — turns git history into a daily standup, using a local LLM (Ollama) or a free cloud one (Groq) if you'd rather not run a model locally.

`Python 3.10–3.13` · `SQLite, WAL mode` · `Rich`

v0.2.3 shipped with a real bug: `options={"timeout": 60}` was passed as a model parameter instead of an HTTP timeout, so Ollama silently ignored it and requests could hang indefinitely. Found it, fixed it by moving the timeout into `ollama.Client(...)`, and wrote a regression test so it can't come back quietly. It's in the changelog under v0.2.3, dated the day it was fixed.

CI runs ruff, mypy, bandit, and pip-audit before any test executes, across four Python versions. Fourteen test modules. All SQL parameterized, all output paths pass through redaction before they reach a log or a terminal.

**[env-auditor](https://github.com/SemTiOne/env-auditor)** — diffs the env vars your code actually references against your `.env.example`, across six languages. Tells you what's undocumented, what's stale, and what has no default.

`Python 3.10+` · zero runtime dependencies

It scans source trees it doesn't control, so it's written defensively on purpose. Lines over 2000 characters are skipped to avoid ReDoS, symlinks are never followed, and `--exclude` paths that try to escape the scan root are rejected outright. 116 tests, an 85% coverage floor enforced in CI, matrix-tested across three operating systems and three Python versions.

---

**Stats**

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=SemTiOne&show_icons=true&hide_border=true&bg_color=0D1117&title_color=58A6FF&text_color=C9D1D9&icon_color=58A6FF&hide=issues)

![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=SemTiOne&layout=compact&hide_border=true&bg_color=0D1117&title_color=58A6FF&text_color=C9D1D9)

---

[X / Twitter](https://twitter.com/DParin28178) — build-in-public updates.
