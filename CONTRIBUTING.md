# Contributing Guidelines

These rules apply to all repositories in this organization unless a repository defines stricter requirements.

The objective is simple: developers should move independently, while the default branch remains stable and protected.

## Development Workflow

1. Create a feature or fix branch from the latest default branch.
2. Make focused commits on that branch.
3. Push the branch and open a pull request.
4. Request review from another developer.
5. Address or resolve all review comments.
6. Merge using **Squash merge** once the pull request is approved.

Do not push directly to the default branch.

## Branch Naming

Use short, descriptive branch names:

```text
feature/customer-import
fix/token-refresh
refactor/pricing-engine
chore/update-dependencies
```

Avoid vague or personal branch names such as:

```text
john-work
test-branch
changes
```

## Pull Request Requirements

Every pull request into the default branch requires:

- At least **one approval** from another developer
- Approval of the **most recent reviewable push**
- All review conversations resolved
- A clean squash merge

The person who made the latest reviewable push cannot approve that push.

Either the pull request author or another developer may merge once all requirements are satisfied. CTO approval is not required for normal development work.

## Pull Request Scope

Keep pull requests small and focused.

A pull request should ideally contain one logical change:

- One feature
- One bug fix
- One refactoring objective
- One infrastructure change

Avoid combining unrelated changes into the same pull request.

## Pull Request Description

Include:

- What changed
- Why it changed
- How it was tested
- Any risks, limitations, or follow-up work

Example:

```markdown
## Summary

Adds validation for imported customer records.

## Testing

- Added unit tests for invalid email addresses
- Tested CSV import locally
- Verified existing imports remain unchanged

## Risks

Large CSV performance has not yet been tested.
```

## Reviews

Reviewers should check:

- Correctness
- Security implications
- Error handling
- Test coverage
- Maintainability
- Unnecessary complexity
- Compatibility with existing behaviour

Review the code, not the person. Be direct, specific, and constructive.

Use blocking comments only for issues that must be fixed before merging. Clearly distinguish optional suggestions from required changes.

## Updating a Reviewed Pull Request

When new code is pushed after approval, the latest reviewable push must be approved by someone other than the person who pushed it.

For this reason, avoid pushing fixes directly to another developer’s branch unless necessary. Prefer leaving review comments and allowing the author to make the changes.

## Merge Policy

The organization uses **Squash merge**.

Before merging:

- Confirm the pull request has the required approval
- Confirm all conversations are resolved
- Confirm the final title clearly describes the change
- Remove temporary debugging code
- Remove commented-out code
- Remove secrets, credentials, tokens, and local configuration

The squash commit title should be clear and suitable for the repository history.

Example:

```text
Add validation for imported customer records
```

## Protected Branch Rules

The default branch is protected.

The following actions are blocked:

- Direct pushes
- Force pushes
- Branch deletion
- Merge commits
- Merging without peer approval

Do not attempt to bypass these protections.

## Testing and CI

Run the relevant tests and checks locally before requesting review.

Required automated status checks may be introduced as repository CI pipelines are established. Once enabled, failing checks must be corrected before merging.

## Sensitive Changes

Escalate changes involving the following areas when the impact is unclear:

- Authentication or authorization
- Credentials and secrets
- Production infrastructure
- Deployment workflows
- Billing or payments
- Customer data
- Destructive database migrations
- Security controls
- Organization-wide shared libraries

Do not merge high-risk changes merely because the technical branch rules allow it.

## Emergencies

Emergency changes should still use a pull request wherever possible.

Bypassing branch protection is reserved for genuine incidents where the normal process would create material operational harm. Any bypass must be documented and reviewed afterward.

## Current Operating Model

Developers are expected to review and merge each other’s work without routine CTO involvement.

This model will later be refined by the development lead. Until then, use sound engineering judgement, keep changes reviewable, and escalate only material risks or architectural decisions.
