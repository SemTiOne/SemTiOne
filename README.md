# Dane Parin

Backend & DevOps Engineer. I build CLI tools, databases, automations, and containerized applications using Python, Java, C++, Docker, CI/CD, and MySQL. Three CLI tools I currently maintain, both open source.

---

**[standup-bot](https://github.com/SemTiOne/standup-bot)** — turns git history into a daily standup, using a local LLM (Ollama) or a free cloud one (Groq) if you'd rather not run a model locally.

`Python 3.10–3.13` · `SQLite, WAL mode` · `Rich`

v0.2.3 shipped with a real bug: `options={"timeout": 60}` was passed as a model parameter instead of an HTTP timeout, so Ollama silently ignored it and requests could hang indefinitely. Found it, fixed it by moving the timeout into `ollama.Client(...)`, and wrote a regression test so it can't come back quietly. It's in the changelog under v0.2.3, dated the day it was fixed.

- CI runs ruff, mypy, bandit, and pip-audit before any test executes
- Four Python versions (3.10–3.13), sixteen test modules
- All SQL parameterized
- All output paths (logs and terminal) pass through redaction, including type-tagged detection for GitHub tokens, LLM API keys, AWS keys, Slack tokens, and credentialed URIs

**[env-auditor](https://github.com/SemTiOne/env-auditor)** — diffs the env vars your code actually references against your `.env.example`, across six languages. Catches undocumented, stale, and missing-default variables.

`Python 3.10+` · zero runtime dependencies

It scans source trees it doesn't control, so it's written defensively on purpose. Lines over 2000 characters are skipped to avoid ReDoS, symlinks are never followed, and `--exclude` paths that try to escape the scan root are rejected outright.

- 141 tests, 85% coverage floor enforced in CI
- Matrix-tested across three operating systems and three Python versions
- `mypy --strict` is a hard CI gate, zero errors

**[chess-review-bot](https://github.com/SemTiOne/chess-review-bot)** — reviews a pull request's diff and labels each changed file with chess Game Review vocabulary (Brilliant, Great, Good, Inaccuracy, Blunder...), using a fully deterministic rule table instead of an LLM judgment call — the reasoning is documented in an ADR, not just a code comment.

`Python 3.10+` · GitHub Action + PyPI CLI

Shipped as a GitHub Action before it had ever run against a real PR: `github.action_path` already points at the directory containing `action.yml`, but the workflow appended `/action/entrypoint.py` on top of it, doubling the path. Every single Action run failed with exit code 2 before classifying anything — caught immediately by dogfooding it against this repo's own PRs, fixed in v0.1.1.

- Published on PyPI (0.1.3), version kept in sync with the Action's manifest
- OIDC Trusted Publishing to PyPI — no stored API token
- `GITHUB_TOKEN` and `GEMINI_API_KEY` are stripped from subprocess environments before any `git` call
- Force-push detection returns unknown rather than guessing when git history is ambiguous, instead of risking a false accusation

---

Also built [position-evaluator](https://github.com/SemTiOne/position-evaluator) for a weekend hackathon (DEV Weekend Challenge), a MySQL-backed Flask app that logs personal decisions and classifies them into chess concepts via Gemini structured output. The schema uses a generated `STORED` column (`SHA2(situation_text, 256)`) to put a uniqueness constraint on an arbitrary-length text field, and the Pydantic response model declares `reasoning` before `classification` on purpose. Gemini fills structured fields in schema order, so this makes "reason before answering" happen mechanically instead of just being a prompt suggestion. The lessons from wrangling reliable structured output out of an LLM here are why chess-review-bot's classifier above is fully deterministic instead.

---

**Open source contributions** — three fixes merged into [Termstory](https://github.com/bitflicker64/Termstory) on three consecutive days (Jun 29 – Jul 1, 2026), each closing a tracked issue in a different subsystem: circuit breaker limits ([#179](https://github.com/bitflicker64/Termstory/pull/179), closes #118), clustering threshold ([#186](https://github.com/bitflicker64/Termstory/pull/186), closes #119), and SQLite connection timeout ([#187](https://github.com/bitflicker64/Termstory/pull/187), closes #123). The circuit breaker fix went through five rounds of automated review before merge, catching a race condition in the config cache and a silent-mutation trap in the backward-compatibility shim along the way. Two more fixes followed over the next two weeks: narrowing three bare-except blocks that were silently swallowing errors during snapshot capture ([#231](https://github.com/bitflicker64/Termstory/pull/231)), and replacing hardcoded timeout and token-limit values with validated config that guards against non-numeric, negative, and infinite inputs ([#248](https://github.com/bitflicker64/Termstory/pull/248)).

Root-caused four separate bugs behind [AynOps](https://github.com/AynOps/AynOps)' header analyzer producing different results than browser DevTools ([#68](https://github.com/AynOps/AynOps/pull/68)): a duplicate-header collapse, Cloudflare's bot-challenge page being silently analyzed as if it were the real site, an invisible redirect chain, and three scoring-logic bugs; confirmed against a live production site, with a maintainer-flagged edge case fixed before merge.

Did two rounds of container-security hardening on [composable-data-stack](https://github.com/RonaldHensbergen/composable-data-stack): pinned its Docker base image to an immutable digest and moved the service off root to a dedicated non-root user, validated by building the image and writing a file to a mounted volume as that user ([#199](https://github.com/RonaldHensbergen/composable-data-stack/pull/199)); and separately closed a build-context leak where the repo's own onboarding docs told contributors to populate a root-level `.env` that was never excluded from the Docker build ([#197](https://github.com/RonaldHensbergen/composable-data-stack/pull/197)).

Also added ruff linting to CI along with fixing the violations it caught in [thumper](https://github.com/jestasecurity/thumper/pull/177), and closed a session-hijack path where re-enrolling a known `machine_id` required no proof of ownership, fixed with a constant-time token comparison ([#249](https://github.com/jestasecurity/thumper/pull/249)). Three merged fixes to [odys](https://github.com/ramirocrc/odys), an energy-dispatch optimization model, including one where the linked issue's own suggested approach was mathematically wrong; implemented a corrected version that actually captures sustained-state behavior instead ([#75](https://github.com/ramirocrc/odys/pull/75)). More merged PRs across other repositories: [full list](https://github.com/pulls?q=is%3Apr+is%3Amerged+author%3ASemTiOne+archived%3Afalse).

---

**Stats**

![Stats](./profile/stats.svg)
![Top Languages](./profile/top-langs.svg)

---

[X / Twitter](https://twitter.com/DParin28178) — build-in-public updates.
