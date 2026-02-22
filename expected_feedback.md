# Expected PR Review Feedback

Compare your comments against these expected findings:

---

## Issue 1: Bug — `get_discount` doesn't handle quantity <= 50
**Severity:** Must Fix
`get_discount()` only handles `quantity > 100` and `quantity > 50`.
If quantity is 50 or less, `discount` is never defined → `UnboundLocalError`.
Fix: Add an `else: discount = 0` clause.

## Issue 2: Bug — Discount calculation is wrong
**Severity:** Must Fix
`discount = quantity * 0.1` discounts based on QUANTITY, not PRICE.
A 10% discount should be `subtotal * 0.1`, not `quantity * 0.1`.

## Issue 3: Missing tests
**Severity:** Must Fix
No test file was added. Every code change needs tests.
At minimum: test normal price, test bulk discount, test zero quantity.

## Issue 4: Weak PR description
**Severity:** Suggestion
"It works for basic cases" doesn't inspire confidence.
PR descriptions should explain WHAT changed, WHY, and HOW to test it.

## Expected Verdict: **Request Changes**
There are bugs in the discount logic and no tests. This cannot be merged.
