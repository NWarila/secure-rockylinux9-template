# Security Policy

## Supported Versions

Only the latest commit on the `main` branch is actively maintained. Security fixes are applied
to `main` and released promptly.

## Reporting a Vulnerability

This project follows a coordinated disclosure process. **Do not open a public issue for
security vulnerabilities.**

**Email:** reports@TrinityTechnicalServices.com

Please include:

- Description of the vulnerability
- Affected component (Packer config, workflow, kickstart, etc.)
- Steps to reproduce
- Suggested remediation (if any)

### Response Timeline

| Stage | Timeline |
|---|---|
| Acknowledgement | Within 48 hours |
| Assessment | Within 5 business days |
| Resolution | Before public disclosure |

## Security Controls

This repository enforces multiple layers of security controls:

### Local (Pre-Commit)

- **Gitleaks** - scans for hardcoded secrets on every commit and push
- **detect-private-key** - prevents accidental private key commits
- **check-added-large-files** - blocks files over 1 MB

### CI (GitHub Actions)

- **Trivy** - filesystem and misconfiguration scanning (HIGH/CRITICAL severity)
- **Gitleaks** - full repository history secret scan
- **CodeQL** - static analysis of GitHub Actions workflows

### Supply Chain

- **Dependabot** - automated dependency updates for GitHub Actions
- **persist-credentials: false** - credentials not persisted in CI checkout steps

## Scope

### In Scope

- Secrets or credentials exposed in repository content
- CI/CD workflow vulnerabilities
- Insecure Packer or kickstart defaults
- Known dependency vulnerabilities

### Out of Scope

- Downstream infrastructure built from this template
- Third-party tool vulnerabilities (report to upstream maintainers)
- Proxmox VE platform vulnerabilities
- Physical or network access issues
