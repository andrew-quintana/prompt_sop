# 📁 prompt_sops/

This folder contains modular Standard Operating Procedures (SOPs) used to guide agent reasoning, debugging, testing, and code management in the Vibe Coding environment.

## How to Use

Each `.md` file is meant to be context-loadable or read manually:

| File | Purpose |
|------|---------|
| `rca_self_consistency.md` | Systematic root cause analysis for complex errors after simpler fixes fail. Follows a workflow of: 1) Quick fix attempt 2) Brief step back and another attempt 3) Full RCA with reversible steps |
| `git_testing_protocol.md` | Git strategy + tiered test execution rules |
| `coding_agent_prompt_schema.md` | Defines role, boundaries, and thinking patterns of reasoning agents |

## Error Resolution Workflow

When encountering errors, follow this progressive approach:

1. **Quick Fix**: Attempt immediate solution based on obvious symptoms
2. **Brief Step Back**: If quick fix fails, undo to get back to the failure state then take a moment to reconsider and try another simple approach and attempt if confident
3. **Full RCA**: If simpler approaches don't work, use the systematic RCA protocol in `rca_self_consistency.md`

## Recommended Load Order (if using in agents)

1. `coding_agent_prompt_schema.md`
2. Task-specific SOP (e.g. RCA or Git)
3. Supplemental memory (e.g. file structure, task queue)