# .github

Service repo for:

- [Organization Discussions](https://github.com/orgs/ara-peaha-ai/discussions)  
  There is no content yet, but it is open for visitor inquiries.

- [BTCPay Server wallets setup](https://github.com/ara-peaha-ai/.github/wiki/BTCPay-wallets-setup)  
  It contains step-by-step screenshots showing how to set up BTC on-chain and Lightning wallets on mobile for BTCPay pairing.  
  This is deprecated in our setup, which is based on the Aqua fork with Shamrock protocol support, but it is still useful for other use cases.

- Quality gates (CI)  
  Each repo keeps its own copy of the workflows, so the same files work on GitHub Actions and on a self-hosted Gitea Actions runner (Gitea >= 1.26; SARIF upload is GitHub-only). Reference implementation in orchestrator, copy from there:
  - [pr-review.yml](https://github.com/ara-peaha-ai/orchestrator/blob/main/.github/workflows/pr-review.yml): on same-repo PRs, ship-safe fails the check on new high or critical findings; Claude runs a correctness review (fails the check on a real bug) and a ponytail over-engineering review (advisory only). Fork PRs get the ship-safe scan only.
  - [monthly-audit.yml](https://github.com/ara-peaha-ai/orchestrator/blob/main/.github/workflows/monthly-audit.yml): on the 1st of each month at 06:00 UTC, or by hand, opens a report-only issue with ponytail audit, ponytail debt ledger and a full ship-safe scan.
  - [merge-ready.yml](https://github.com/ara-peaha-ai/orchestrator/blob/main/.github/workflows/merge-ready.yml): aggregates reviewer verdicts and check results into one `merge-ready` status. [signed-main.yml](https://github.com/ara-peaha-ai/orchestrator/blob/main/.github/workflows/signed-main.yml) rejects unsigned commits on `main`.
  - The ponytail skills are vendored in [.claude/skills](https://github.com/ara-peaha-ai/orchestrator/tree/main/.claude/skills); the correctness pass uses Claude Code's built-in code-review skill. Claude jobs need the `CLAUDE_CODE_OAUTH_TOKEN` secret and send the PR diff and repo files to Anthropic: check that this is acceptable before copying them into a private repo.
