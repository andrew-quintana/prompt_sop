# 📁 prompt_sops/

This folder contains modular Standard Operating Procedures (SOPs) used to guide agent reasoning, debugging, testing, and code management in the Vibe Coding environment.

## How to Use

Each `.md` file is meant to be context-loadable or read manually:

| File | Purpose |
|------|---------|
| `rca_self_consistency.md` | Root cause analysis with hierarchical, beam-like tree-of-thought reasoning |
| `git_testing_protocol.md` | Git strategy + tiered test execution rules |
| `agent_prompt_schema.md` | Defines role, boundaries, and thinking patterns of reasoning agents |

## Recommended Load Order (if using in agents)

1. `agent_prompt_schema.md`
2. Task-specific SOP (e.g. RCA or Git)
3. Supplemental memory (e.g. file structure, task queue)

_You may also reference the complete version in `vibe_coding_manifesto.md`._
