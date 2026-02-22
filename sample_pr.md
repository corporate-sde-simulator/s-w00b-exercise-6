# PR #256: Add discount calculation to pricing engine

**Author:** Intern A · **Reviewers:** You (Reviewer)
**Branch:** feature/discount-calc → main
**Status:** Ready for Review

---

## Description
Added discount calculation. It works for basic cases.

## Changes

### Modified: `src/pricingEngine.py`

`python
class PricingEngine:
    def calculate_price(self, base_price, quantity):
        subtotal = base_price * quantity
        discount = self.get_discount(quantity)
        return subtotal - discount

    def get_discount(self, quantity):
        # 10% discount for bulk orders
        if quantity > 100:
            discount = quantity * 0.1
        elif quantity > 50:
            discount = quantity * 0.05
        return discount

    def format_receipt(self, items):
        lines = []
        for item in items:
            line = f"{item['name']}: {item['price']}"
            lines.append(line)
        return "\n".join(lines)
`

### No tests added.

---

## Your Review

Write your review comments below. For each comment, specify:
- **File and line:** Where the issue is
- **Severity:** Nit / Suggestion / Must Fix
- **Comment:** What's wrong and how to fix it

### Comment 1:
> File: ___
> Severity: ___
> Comment: ___

### Comment 2:
> File: ___
> Severity: ___
> Comment: ___

### Comment 3:
> File: ___
> Severity: ___
> Comment: ___

### Verdict: [ ] Approve / [ ] Request Changes / [ ] Comment
