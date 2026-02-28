# 🛡️ AI DevSecOps Autopilot

Automated security scanning pipeline for Pull Requests — secrets detection, vulnerability scanning, one-comment PR summary, and merge gating.

## What It Does

On every Pull Request to `main`, this pipeline automatically:

1. **Secrets Detection** — Runs [Gitleaks](https://github.com/gitleaks/gitleaks) to scan for hardcoded API keys, tokens, and passwords
2. **Vulnerability Scanning** — Runs [Trivy](https://github.com/aquasecurity/trivy) to detect HIGH and CRITICAL dependency vulnerabilities
3. **PR Summary Comment** — Posts (or updates) a single sticky comment with scan results — no comment spam
4. **Merge Gating** — Fails the PR check and blocks merge if secrets or critical vulnerabilities are found

## Example PR Comment

| Check | Status | Details |
|-------|--------|---------|
| **Gitleaks** (secrets) | 🟢 PASS | No secrets found. |
| **Trivy** (vulnerabilities) | 🟢 PASS | No HIGH/CRITICAL vulnerabilities. |

## Tech Stack

- **GitHub Actions** — CI/CD orchestration
- **Gitleaks** — Secret detection
- **Trivy** — Filesystem vulnerability scanner
- **sticky-pull-request-comment** — Single-comment PR updates

## Setup

1. Copy `.github/workflows/autopilot.yml` into your repository
2. Ensure GitHub Actions has **read/write permissions** (Settings → Actions → General)
3. Open a Pull Request — the pipeline runs automatically

No API keys or secrets required for public repos.

## Repository Structure
```
.
├── .github/workflows/
│   └── autopilot.yml    # The DevSecOps pipeline
├── app.py               # Sample application
└── README.md
```

## License

MIT
