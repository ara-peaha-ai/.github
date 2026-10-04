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
  - [audit.yml](https://github.com/ara-peaha-ai/orchestrator/blob/main/.github/workflows/audit.yml): every 4032 Bitcoin blocks (two difficulty epochs, about 28 days), or by hand, opens a report-only issue `Audit at block <height>` with ponytail audit, ponytail debt ledger and a full ship-safe scan. Actions cannot trigger on a block, so a daily check reads the tip height from `MEMPOOL_URL` (repo or org variable, any Esplora-compatible API, mempool.space by default; point it at our own node on the VPS) and runs once per epoch.
  - [merge-ready.yml](https://github.com/ara-peaha-ai/orchestrator/blob/main/.github/workflows/merge-ready.yml): aggregates reviewer verdicts and check results into one `merge-ready` status. [signed-main.yml](https://github.com/ara-peaha-ai/orchestrator/blob/main/.github/workflows/signed-main.yml) rejects unsigned commits on `main`.
  - The ponytail skills are vendored in [.claude/skills](https://github.com/ara-peaha-ai/orchestrator/tree/main/.claude/skills); the correctness pass uses Claude Code's built-in code-review skill. Claude jobs need the `CLAUDE_CODE_OAUTH_TOKEN` secret and send the PR diff and repo files to Anthropic: check that this is acceptable before copying them into a private repo.
