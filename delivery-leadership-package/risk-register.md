# Risk Register

> Copy to `delivery-leadership-package/risk-register.md`. At least 5 rows. **No boilerplate**; your peers will grade you on whether these are real.

| # | Risk | Owner | Likelihood (L/M/H) | Impact (L/M/H) | Mitigation | Trigger to escalate |
|---|---|---|---|---|---|---|
| R1 | AI-drafted code looks right but computes wrong (the POST returned 201 witha  $.35 premium | Engineering Team | M | H | Tests, not demos are the gate. No merge without green CI | Any red test on delivery/lead or main |
| R2 | Bad data outlives bad code (the $.35 quote is still in the db after the fix | Kristen Marturano (delivery lead) | H | M | Run npm run seed before Thursday's demo; scan /api/quotes for absurd premiums | Any premium that looks implausibly low or high |
| R3 | Malformed requests get a vague 500 "Server error" instead of a clear 400 with the reason | Engineering Team | M | M | Log as a backlog item for engineering (not fixing this week; assembly only) | A partner or Customer Service reports unexplained errors |
| R4 | Starter kit arrived without .env or .gitignore, so config could drift between envts | Me + instructor | H | M | Recreated both from the docs and code defaults; confirmed node_modules/ is not committed | Serivce won't start, or node_modules appears in git status |
| R5 | Leftover dev server holds port 3000 (happened twice) | Kristen Marturano | H | L | Ctrl +C at daily wrap, recover with ss + kill | Port stays busy after kill, so ask the instructor |
| R6 | Marketing site and API may quote different prices (site still uses old rates) | Sponsor/Marketing| M | H | Flag at check-in; add "align site to API" to the roadmap | Customer sees two different prices for the same quote
 | R8 | Moderate CVE on the pinned base image node:22-alpine; patch not available until next week | Platform Team | M | M | Ship this week (API not internet exposed); adopt the patched tag in next week's window | Severity raised, or the API becomes internet - facing before the patch
 | R8 | Scope creep: partner pushes renters coverage into this week ("just one dropdown") | Kristen Marturano + Sponsor | H | H | Deferred to next round; needs a sponsor renters rate; cost shown with the "boat" 400 evidence | Sponsor overrides the deferral, so re-plan and name what gets cut

## How I'll use this register

I review this register at the start of each day, update likelihoods as things change, and escalate to the sponsor (instructor) as soon as trigger fires.
