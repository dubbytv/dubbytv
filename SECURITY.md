# Security Policy

## Reporting a Vulnerability

**Do not report security vulnerabilities through public GitHub issues.**

If you discover a security vulnerability in Dubby, please report it through GitHub's private security advisory feature:

1. Go to the [Security Advisories](https://github.com/dubbytv/dubbytv/security/advisories/new) page.
2. Click **"Report a vulnerability"**.
3. Fill in the details and submit.

### What to expect

- **Acknowledgment** within 48 hours of your report.
- **Assessment** of severity and impact. We will confirm whether it is a valid vulnerability.
- **Fix and disclosure** — we develop the fix privately, ship it via our hotfix process, and disclose the vulnerability in the release notes after the fix is available.

### What qualifies as a security issue

- Authentication or authorization bypasses
- Remote code execution
- SQL injection, XSS, or other injection attacks
- Information disclosure (leaking sensitive data)
- Denial of service vulnerabilities that affect availability
- Privilege escalation

### What does NOT qualify

- Bugs that require physical access to the host machine
- Self-hosted configuration issues (e.g., exposing the instance without a reverse proxy)
- Feature requests or general bugs — please use the [issue tracker](https://github.com/dubbytv/dubbytv/issues) for these

## Supported Versions

Only the **latest stable release** receives security patches. If you are running an older version, the fix is to upgrade to the latest stable release.

## CVE Assignment

For significant vulnerabilities, we request a CVE through GitHub's security advisory tooling to provide a standard identifier for tracking.
