# Decision Memo: _short title here_

> Copy to `delivery-leadership-package/decision-memo.md`. Target length: ~250 words. Write for a non-technical reader. Name the options you **rejected**, not just the one you picked.

**Date:** Nov 9th, 2026
**Author:** Kristen Marturano
**Decision area:** Rely on the automated test suite instead of manual checks for validation

## Context

On day 2, I tried to confirm by hand that the Evergreen Quote API rejects bad requests (for ex, a 5 yr old applicant or a "boat" policy). The manual checks kept failing for reasons unrelated to the product: the rest requests were getting garbled while being typed, which cost about 30 minutes and produced misleading "Server error" results.

## Options considered

1. **Option A: _name_.** Keep troubleshooting the manual checks until each one works. This gives me first-hand confirmation, but costs more time and risks the morning's assembly schedule.
2. **Option B: _name_.** Move on and rely on the automated test suite, which already includes checks for these exact cases (age under 18, coverage too low, unknown policy type).

## Recommendation

Option 2, rely on test suite.



## Why

- The test suite ran all 3 validation checks in under a second, and all passed.
- The same suite caught a real pricing bug (a .$35 premium) that a manual demo had made look fine, so it has proven more trustworthy than hand checks.
- It kept the morning on track: routes, the fix, config, and GraphQL were all fininished before lunch.
- The suite also runs automatically in CI from Weds, so this check repeats on every change and doesnt depend on someone typing perfectly.

## What would change my mind

If a test were missing for a rule we care about, or if the suite and the live product ever disagreed, I'd go back to manual checks and ask engineering to add the missing test.
