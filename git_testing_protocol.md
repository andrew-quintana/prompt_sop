# Git Management & Tiered Testing Protocol

A structured approach to using Git branches and test coverage in iterative, agentic or collaborative development environments.

## Branch Strategy
- `main`: production-only, post-integration
- `development`: staging and integration
- `feature/`: one feature or fix per branch

## Tiered Testing
- Feature: modified units + dependencies
- Development: full unit suite
- Main: full unit + integration + regression + security

## Example
```bash
git checkout -b feat/your-feature
pytest tests/unit/test_feature.py
git push origin feat/your-feature
```
