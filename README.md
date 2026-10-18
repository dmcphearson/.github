# .github

Shared GitHub Actions for dmcphearson's public repos.

`.github/workflows/pr-security.yml` runs on every pull request and every push to `main`:

- **Leaks**: betterleaks scans the new commits for secrets and private identifiers, commit messages are checked for the same identifiers, and commit emails must be the GitHub noreply address.
- **Code scan**: opengrep with the community rules; ERROR-severity security rules (audit rules excluded) fail the check. Only those blocking findings go to the repo's code scanning alerts, so an open alert is always a real issue.
- **Packages**: npm and Python dependencies install through Aikido safe-chain, which blocks known malware; repos without them pass straight through.

Each repo calls it from `.github/workflows/security.yml` and passes its `LEAK_PATTERNS` Actions secret. Tool versions, checksums and actions are pinned.

`SECURITY.md` is the default security policy for every public repo that doesn't have its own: report vulnerabilities through private vulnerability reporting.
