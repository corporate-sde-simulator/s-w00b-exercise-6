# Module 06: The PR Process 🔀

> When you fix a bug, you don't just copy-paste code to your manager.
> You create a **Pull Request (PR)** — a formal request to merge your
> changes into the main codebase. This is how ALL code gets delivered.

---

## What Is a Pull Request?

A PR is:
1. Your code changes (the diff)
2. A description of WHAT you changed and WHY
3. A request for someone to REVIEW your work
4. A discussion thread for feedback

Think of it as submitting a homework assignment with a cover page
explaining your work.

---

## The PR Workflow

```
1. Read the ticket
2. Create a new branch
3. Fix the bug / write the code
4. Run ALL tests to make sure nothing broke
5. Write your PR title and description
6. Submit the PR
7. Address review feedback
8. PR gets merged → ticket is done!
```

---

## How to Write a Good PR Title

### The Formula:
```
[Action] [Ticket-ID]: [Short description of change]
```

### Good Examples:
```
Fix PLATFORM-2835: Correct sliding window calculation in rate limiter
Fix PLATFORM-2830: Handle empty queue in task scheduler
Add INVENTORY-401: Unit tests for low-stock threshold alerts
Refactor AUTH-115: Extract token validation into middleware
```

### Bad Examples:
```
Fixed stuff                          ← What stuff? Where?
Changes                              ← Meaningless
PLATFORM-2835                        ← No description
Update rateLimiter.js                ← Just the filename, no context
Fixed the bug in the thing           ← Too vague
```

---

## How to Write a PR Description

Use this template:

```markdown
## What Changed
- Fixed the sliding window calculation that was using `<` instead of `<=`
- Added boundary check for the token refill rate

## Why
The rate limiter was allowing 101 requests instead of 100 because
the window boundary check was exclusive instead of inclusive.

Ticket: PLATFORM-2835

## How to Test
1. Run: `npm test`
2. All 12 tests should pass
3. Specifically check: `test_rate_limiter_at_boundary`

## Screenshots / Evidence
(paste test output here if helpful)
```

---

## The Review Process

After you submit a PR, a senior dev will review it. Here's what they look for:

### ✅ What Gets Approved
- Clean, focused changes (only what the ticket asks for)
- Tests added for the fix
- Clear PR description
- No debug `console.log` or `print` statements left in
- Proper variable names

### ❌ What Gets Rejected
- Missing tests
- Unrelated changes mixed in ("while I was here, I also...")
- No PR description or description says "Fixed it"
- Code that works but is messy / unreadable
- Changes to files you weren't asked to change

---

## Responding to Review Feedback

When a reviewer leaves comments:

### Good Responses:
```
"Good catch! Fixed in the latest commit."
"I chose this approach because [reason]. Would you prefer [alternative]?"
"I wasn't sure about this part. Here's my reasoning: [explain]"
```

### Bad Responses:
```
"It works though"                    ← Doesn't address the feedback
(no response)                        ← Don't ignore comments
"I'll fix it later"                  ← Fix it NOW, in this PR
```

---

## Common PR Mistakes

| Mistake | Why It's Bad | What to Do Instead |
|---------|-------------|-------------------|
| Giant PR (500+ lines changed) | Hard to review, likely to have bugs | Keep PRs small and focused |
| No description | Reviewer has no context | Always explain what and why |
| Leaving debug logs | Unprofessional, clutters output | Search for `console.log` and `print` before submitting |
| Not running tests locally | PR fails in CI, wastes everyone's time | Always run `npm test` / `pytest` first |
| Changing unrelated files | Confuses the review, may break things | Only change what the ticket requires |

---

## Your PR Checklist

Before submitting any PR in this simulator, check these:

- [ ] PR title follows the formula: `Fix TICKET-ID: Description`
- [ ] PR description has: What Changed, Why, How to Test
- [ ] All existing tests pass
- [ ] New tests added for the fix
- [ ] No `console.log`, `print`, or debug statements left
- [ ] Only files related to the ticket are changed
- [ ] I understand WHY my fix works, not just THAT it works

---

## Summary

> The quality of your PR is just as important as the quality of your code.
>
> A brilliant fix with a terrible PR description = your reviewer can't
> understand it = delay = bad KPI.
>
> An OK fix with a clear PR = quick review = merged = done = good KPI.
