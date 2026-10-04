# .github

Service repo for:

- [Organization Discussions](https://github.com/orgs/ara-peaha-ai/discussions)  
  There is no content yet, but it is open for visitor inquiries.

- [BTCPay Server wallets setup](https://github.com/ara-peaha-ai/.github/wiki/BTCPay-wallets-setup)  
  It contains step-by-step screenshots showing how to set up BTC on-chain and Lightning wallets on mobile for BTCPay pairing.  
  This is deprecated in our setup, which is based on the Aqua fork with Shamrock protocol support, but it is still useful for other use cases.

- Quality gates (CI)  
  Each repo carries its own copy of the workflows, so it runs unchanged on GitHub Actions and on a self-hosted Gitea Actions runner. Reference implementation in orchestrator:
  - [pr-review.yml](https://github.com/ara-peaha-ai/orchestrator/blob/main/.github/workflows/pr-review.yml): on every PR, ship-safe security gate plus a Claude correctness review and ponytail over-engineering review.
  - [monthly-audit.yml](https://github.com/ara-peaha-ai/orchestrator/blob/main/.github/workflows/monthly-audit.yml): on the 1st of each month, opens an issue with ponytail audit, ponytail debt ledger and a full ship-safe scan.
  - [merge-ready.yml](https://github.com/ara-peaha-ai/orchestrator/blob/main/.github/workflows/merge-ready.yml): aggregates reviewer verdicts and check results into one `merge-ready` status.
  - Skills used by the workflows are vendored in [.claude/skills](https://github.com/ara-peaha-ai/orchestrator/tree/main/.claude/skills). Required secret: `CLAUDE_CODE_OAUTH_TOKEN`.
