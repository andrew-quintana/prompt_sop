# Git Management & Tiered Testing Protocol

A structured approach to using Git branches and test coverage in iterative, agentic or collaborative development environments.

## Branch Strategy
- `main`: production-ready code
- `main/feature-name`: feature branches directly off main
- Use `/` only when a feature implementation is large enough to have its own sub-features

## Branch Naming
- Keep it simple: `main/feature-name`
- Only use additional levels if feature has significant sub-components:
  ```
  main/feature-name
  main/feature-name/sub-feature
  ```
- Avoid unnecessary nesting

## Tiered Testing
- Feature: modified units + dependencies
- Main: full unit + integration + regression + security

## Example
```bash
# Simple feature
git checkout -b main/your-feature
pytest tests/unit/test_feature.py
git push origin main/your-feature

# Feature with sub-components
git checkout -b main/your-feature
# ... work on main feature ...
git checkout -b main/your-feature/sub-component
# ... work on sub-component ...
```

## Best Practices
1. Start with `main/feature-name`
2. Only create sub-branches if the feature implementation is large enough to warrant it
3. Keep the structure as flat as possible
4. Merge back to main when feature is complete
