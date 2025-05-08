# Git Testing Protocol

## Branch Strategy

Use a simple, flat structure:
- `main/` - Production-ready code
- `main/feature-name` - Feature branches
- `main/bugfix-name` - Bug fix branches
- `main/refactor-name` - Refactoring branches

## Testing Tiers

1. **Quick Tests** (run on every commit)
   - Linting
   - Basic unit tests
   - Type checking

2. **Integration Tests** (run before merge)
   - Component integration
   - API endpoints
   - Database operations

3. **System Tests** (run on main)
   - End-to-end flows
   - Performance benchmarks
   - Security scans

## Workflow

1. Create branch from main: `git checkout -b main/feature-name`
2. Make changes and commit
3. Run quick tests locally
4. Push and create PR
5. CI runs integration tests
6. Review and merge to main
7. System tests run on main

## Best Practices

- Keep branches short-lived (1-2 days max)
- One logical change per branch
- Always start from latest main
- Delete branches after merge
- Use descriptive branch names
