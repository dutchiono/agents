# Pull Request Workflow

Standard operating procedure for creating, reviewing, and merging pull requests in ionoi-inc repositories.

## Overview

**Owners**: All agents (process applies to everyone)
**Primary Reviewers**: Nebula, GitHub Agent, or designated team members
**When to use**: Any code change to main/production branches
**Estimated time**: 15-30 minutes per PR (review time varies)

## Core Principles

1. **No direct commits to main** - Always use pull requests
2. **One PR = One feature/fix** - Keep PRs focused and atomic
3. **Clear descriptions** - Explain what, why, and how
4. **Tests must pass** - CI/CD green before merge
5. **Review required** - At least one approval before merge
6. **Clean history** - Squash or rebase when appropriate

## Step-by-Step Process

### Phase 1: Preparation

**1.1 Create Feature Branch**

Branch naming conventions:
```
feature/[description]     # New features
fix/[description]         # Bug fixes
refactor/[description]    # Code refactoring
docs/[description]        # Documentation only
test/[description]        # Test additions/changes
chore/[description]       # Maintenance tasks
```

Examples:
- `feature/user-authentication`
- `fix/login-button-crash`
- `docs/api-endpoints`
- `refactor/database-queries`

**1.2 Make Your Changes**
- Write clean, well-documented code
- Follow project coding standards
- Add/update tests as needed
- Update documentation if applicable

**1.3 Commit Messages**

Follow conventional commit format:
```
<type>(<scope>): <subject>

<body>

<footer>
```

Types:
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, no logic change)
- `refactor`: Code refactoring
- `test`: Test additions or changes
- `chore`: Build, CI, or tooling changes

Examples:
```
feat(auth): add password reset functionality

fix(api): resolve race condition in user creation

docs(readme): update installation instructions
```

### Phase 2: Creating the Pull Request

**2.1 Push Branch**
```bash
git push origin [branch-name]
```

**2.2 Open PR on GitHub**

Navigate to repository and click "Compare & pull request"

**2.3 Fill Out PR Template**

**Title**: Clear, concise summary
```
[Type] Brief description

Examples:
- Feature: Add user authentication
- Fix: Resolve login button crash
- Docs: Update API documentation
```

**Description** must include:

```markdown
## What
[What changes are being made]

## Why
[Why these changes are needed]

## How
[How the changes work, technical details]

## Testing
[How the changes were tested]
- [ ] Unit tests added/updated
- [ ] Integration tests added/updated
- [ ] Manual testing completed
- [ ] Tested in [environment]

## Screenshots/Videos
[If UI changes, include visuals]

## Related Issues
Closes #[issue-number]
Relates to #[issue-number]

## Checklist
- [ ] Code follows project style guidelines
- [ ] Tests added/updated and passing
- [ ] Documentation updated
- [ ] No new warnings or errors
- [ ] Backward compatible (or breaking changes documented)
```

**2.4 Set PR Metadata**
- **Reviewers**: Request review from appropriate agent/team member
- **Labels**: Add relevant labels (`enhancement`, `bug`, `documentation`, etc.)
- **Project**: Add to project board if applicable
- **Milestone**: Link to milestone if applicable

**2.5 Link Issues**

In PR description, use keywords to auto-close issues:
- `Closes #123` - Closes issue when PR merges
- `Fixes #123` - Same as closes
- `Resolves #123` - Same as closes
- `Relates to #123` - Links but doesn't close

### Phase 3: Review Process

**3.1 Automated Checks**

Wait for CI/CD to complete:
- [ ] Build succeeds
- [ ] Tests pass
- [ ] Linting passes
- [ ] Code coverage meets threshold
- [ ] Security scans pass

**3.2 Request Review**

**For Nebula/GitHub Agent:**
- Tag with `needs-review` label
- Request review from @nebula or @github-agent
- Add comment if specific areas need attention

**For other agents:**
- Mention specific agent in PR comments
- Create handoff issue if needed (use template)

**3.3 Address Review Comments**

**If changes requested:**
1. Read all comments carefully
2. Ask questions if unclear
3. Make requested changes
4. Commit and push updates
5. Reply to comments when addressed
6. Re-request review

**If approved:**
- Proceed to merge (see Phase 4)

**3.4 Review Guidelines**

What reviewers should check:
- **Functionality**: Does it work as intended?
- **Code quality**: Is it clean, readable, maintainable?
- **Tests**: Are there adequate tests?
- **Documentation**: Is documentation updated?
- **Performance**: Any performance concerns?
- **Security**: Any security issues?
- **Breaking changes**: Are they necessary and documented?

### Phase 4: Merging

**4.1 Pre-Merge Checklist**
- [ ] All CI/CD checks passing
- [ ] At least one approval received
- [ ] All review comments addressed
- [ ] Branch up-to-date with main
- [ ] No merge conflicts

**4.2 Update Branch** (if needed)
```bash
git checkout main
git pull
git checkout [branch-name]
git merge main  # or: git rebase main
git push
```

**4.3 Choose Merge Strategy**

**Squash and Merge** (recommended for most cases):
- Combines all commits into one
- Keeps main branch history clean
- Use for feature branches with many small commits

**Rebase and Merge**:
- Replays commits on top of main
- Linear history
- Use for clean, well-organized commit histories

**Merge Commit**:
- Preserves all individual commits
- Shows branch history
- Use for significant features with logical commit structure

**4.4 Merge the PR**

1. Click appropriate merge button on GitHub
2. Edit merge commit message if needed
3. Confirm merge
4. Delete branch (GitHub will prompt)

**4.5 Verify Merge**
- Check that linked issues were closed
- Verify main branch has the changes
- Monitor CI/CD on main branch
- Check deployment if auto-deploy is configured

### Phase 5: Post-Merge

**5.1 Update Local Repository**
```bash
git checkout main
git pull
git branch -d [branch-name]  # Delete local branch
```

**5.2 Verify in Production** (if applicable)
- Check that changes work in production
- Monitor logs for errors
- Watch metrics/monitoring dashboards

**5.3 Communicate**
- Update related issues with status
- Notify stakeholders if needed
- Document in changelog if applicable

## Special Scenarios

### Draft Pull Requests

Use for work-in-progress:
1. Open PR as draft
2. Mark "Ready for review" when complete
3. Good for getting early feedback

### Hotfix PRs

For urgent production fixes:
1. Create branch from main: `hotfix/[description]`
2. Make minimal, focused fix
3. Tag with `urgent` label
4. Request immediate review
5. Fast-track merge after approval
6. Monitor production closely

### Large PRs

If PR becomes too large:
1. Consider breaking into smaller PRs
2. Create tracking issue for overall feature
3. Submit incremental PRs that build on each other
4. Keep each PR focused and reviewable

### Stale PRs

If PR sits without activity:
1. Add comment to bump/remind
2. Re-request review if needed
3. Close if no longer relevant
4. Create new PR if requirements changed significantly

## Common Issues

**Issue**: Merge conflicts
**Solution**:
```bash
git checkout main
git pull
git checkout [branch-name]
git merge main
# Resolve conflicts in your editor
git add [resolved-files]
git commit
git push
```

**Issue**: CI/CD failing
**Solution**:
1. Check CI/CD logs for specific error
2. Run tests locally to reproduce
3. Fix the issue
4. Commit and push
5. Wait for CI/CD to re-run

**Issue**: Accidentally committed to main
**Solution**:
1. Don't panic!
2. Create branch from current main: `git checkout -b fix/revert-accidental-commit`
3. Reset main: `git checkout main && git reset --hard origin/main`
4. Push branch with changes
5. Create proper PR from branch

**Issue**: Need to update PR after review
**Solution**:
- Just commit and push to the same branch
- PR updates automatically
- No need to create new PR

## Best Practices

1. **Keep PRs small** - Easier to review, less likely to have issues
2. **Write clear descriptions** - Help reviewers understand your changes
3. **Respond to reviews promptly** - Don't let PRs go stale
4. **Be respectful** - Code review is about the code, not the person
5. **Learn from reviews** - Use feedback to improve future PRs
6. **Review others' PRs** - Helps everyone learn and improve
7. **Keep branch updated** - Merge main regularly to avoid conflicts
8. **Test before submitting** - Don't rely solely on CI/CD

## Templates

### PR Description Template
```markdown
## What
[Brief description of changes]

## Why
[Problem being solved or feature being added]

## How
[Technical approach and key decisions]

## Testing
- [ ] Unit tests
- [ ] Integration tests
- [ ] Manual testing

## Screenshots
[If applicable]

## Related Issues
Closes #

## Checklist
- [ ] Tests passing
- [ ] Documentation updated
- [ ] No breaking changes (or documented)
```

### Review Comment Templates

**Request changes:**
```
Thanks for the PR! I've left some comments that need to be addressed before we can merge:

1. [Specific issue with line reference]
2. [Another issue]

Please make these updates and re-request review. Let me know if you have questions!
```

**Approve:**
```
Looks good! Code is clean, tests are passing, and documentation is updated. Approved for merge.
```

**Approve with minor suggestions:**
```
Approving this PR. I've left a few minor suggestions that would be nice to have but aren't blocking. Feel free to address them before merging or create a follow-up issue.
```

## References

- [GitHub PR Documentation](https://docs.github.com/en/pull-requests)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Code Review Best Practices](https://google.github.io/eng-practices/review/)
- [ORG.md](https://github.com/ionoi-inc/agents/blob/main/ORG.md)

---

**Last Updated**: 2026-02-10
**Maintained By**: GitHub Agent