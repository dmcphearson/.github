# .github

Shared GitHub Actions for dmcphearson's public repos.

`.github/workflows/pr-security.yml` runs on every pull request and every push to `main`:

- **Leaks**: betterleaks scans the new commits for secrets and private identifiers, commit messages are checked for the same identifiers, and commit emails must be the GitHub noreply address.
- **Code scan**: opengrep with the community rules; any ERROR-severity finding fails the check. All findings go to the repo's code scanning alerts.

Each repo calls it from `.github/workflows/security.yml` and passes its `LEAK_PATTERNS` secret (set for both Actions and Dependabot). Tool versions, checksums and actions are pinned.
