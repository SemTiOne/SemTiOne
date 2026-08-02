<p align="center">
  <img src="profile/roxy-banner.webp" alt="Roxy Migurdia">
</p>

<p align="center">
  <a href="https://x.com/DParin28178"><img src="https://img.shields.io/badge/X-@DParin28178-000?style=for-the-badge&logo=x&logoColor=white" alt="X"></a>
  <a href="https://bsky.app/profile/daneparin.bsky.social"><img src="https://img.shields.io/badge/Bluesky-@daneparin.bsky.social-0085FF?style=for-the-badge&logo=bluesky&logoColor=white" alt="Bluesky"></a>
  <a href="mailto:emphyst80@gmail.com"><img src="https://img.shields.io/badge/Email-emphyst80@gmail.com-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"></a>
</p>

---

## Tech Stack

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Java-007396?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java">
  <img src="https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=cplusplus&logoColor=white" alt="C++">
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker">
  <img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL">
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git">
  <img src="https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black" alt="Linux">
  <img src="https://img.shields.io/badge/CI/CD-4CAF50?style=for-the-badge&logo=githubactions&logoColor=white" alt="CI/CD">
</p>

---

**[standup-bot](https://github.com/SemTiOne/standup-bot)**: turns git history into a daily standup via local (Ollama) or free cloud (Groq) LLM.
`Python` · `SQLite (WAL)` · `Rich`
Fixed a real v0.2.3 bug (timeout passed as model param → requests hung forever) with a regression test. CI: ruff, mypy, bandit, pip-audit; SQL parameterized; secrets redacted from all output.

**[env-auditor](https://github.com/SemTiOne/env-auditor)**: diffs env vars your code references against `.env.example` across six languages.
`Python` · zero runtime dependencies
Written defensively: skips long lines (ReDoS), never follows symlinks, `--exclude` can't escape the scan root. 141 tests, 85% coverage, three OSes × three Python versions, `mypy --strict`.

**[chess-review-bot](https://github.com/SemTiOne/chess-review-bot)**: labels each PR file with chess Game Review vocabulary (Brilliant, Blunder...) via a deterministic rule table (no LLM call, reasoning in an ADR).
`Python` · GitHub Action + PyPI CLI
Shipped broken (Action doubled its own path, exit 2); caught by dogfooding on its own PRs, fixed in v0.1.1. Published via OIDC; secrets stripped from subprocess calls.

Also built [position-evaluator](https://github.com/SemTiOne/position-evaluator) for a weekend hackathon: MySQL + Flask + Gemini structured output; the LLM-reliability lessons made chess-review-bot deterministic instead.

**Open source contributions**
- **Termstory**: three fixes in three days, three subsystems; the circuit-breaker fix survived five review rounds (race condition + silent mutation trap).
- **AynOps**: root-caused four bugs behind its header analyzer vs. browser DevTools.
- **composable-data-stack**: hardened Docker image (pinned digest, non-root); closed a `.env` leak into the build context.
- **thumper**: fixed a session-hijack path + added ruff linting.
- **odys**: three fixes, incl. one where the issue's own suggested fix was mathematically wrong.
- [Full list](https://github.com/pulls?q=is%3Apr+is%3Amerged+author%3ASemTiOne+archived%3Afalse)

---

**Stats**

<p align="center">
  <img src="./profile/stats.svg" alt="Stats">
  <img src="./profile/top-langs.svg" alt="Top Languages">
</p>
