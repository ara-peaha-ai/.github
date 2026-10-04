# Ára Pe'aha Aĩ

**One key. Your money, your knowledge, your AI.**

Self-custodial payment and AI tools for businesses in emerging markets, starting in Paraguay.

The same rule drives both: whoever holds the key holds the asset. In payments, the seed holds the funds. In AI, the company's knowledge stays in its own git repo, and model vendors are meant to see one isolated task at a time, never the whole.

---

## Two stacks, two servers

Each stack runs in Docker on its own VPS. Both can be self-hosted.

| Stack | What it does | Repos |
|-------|--------------|-------|
| **PAY** | Multi-rail inbound payments (Bitcoin, stablecoins, P2P and fiat rails) with self-custodial settlement, on top of BTCPay Server | [/orchestrator](https://github.com/ara-peaha-ai/orchestrator) (MIT) |
| **AI** | Company memory as Markdown in git, a knowledge graph of it (testing), and a CPU router (planned) that sends each task to commercial or self-hosted models with only the context that task needs | [/wisdom](https://github.com/ara-peaha-ai/wisdom) (MIT engine) + sovereign (private memory) |

Architecture, rails, and roadmap for PAY: [orchestrator README](https://github.com/ara-peaha-ai/orchestrator#readme).
The AI model, markers, and router: [wisdom README](https://github.com/ara-peaha-ai/wisdom#readme).

---

## Principles

- **Self-custodial by default**: funds and knowledge never sit with a platform
- **Agnostic in practice**: the usable rail or model matters more than ideology
- **Modular**: rails, services, and models can be enabled or left out per use case
- **Open source**: public components are MIT; a paid closed-source offering funds their long-term maintenance
- **Dogfooded**: the company building this runs on it every day

---

## Community & Contact

- [ara.peaha.ai](https://ara.peaha.ai) · [ara@peaha.ai](mailto:ara@peaha.ai)
- [GitHub Discussions](https://github.com/orgs/ara-peaha-ai/discussions)
- [Signal in Spanish](https://signal.group/#CjQKINeqtWYuRXjYo9GtrlCEOWMJ2nWQXNG6iyds3wrRYxooEhD6gXXKAHllZUT53I5Lsxbh)
- [Signal in Portuguese](https://signal.group/#CjQKIG98LmLuz2PTC6sfsmCqDSPcfr-K2Ik3f7jzBZxBgnHtEhCvxiDfadchzN5SsVX80uBC)
