# Go / No-Go: Merge Decision

> Copy to `delivery-leadership-package/go-no-go.md`. Make this call **from** the CI result, not in spite of it.

**Date / time:** 11/10/26
**Decision:** ☐ GO   X NO-GO   ☐ GO WITH CONDITIONS

## CI evidence

- Latest run on `delivery/lead`: **green** (8/8 tests) link: https://github.com/asc1-student06/evergreen-quote-api-delivery/actions
- Workflow file: `.github/workflows/ci.yml`
- What the workflow actually checked: check out the code --> setup Node 22 --> start a temp MongoDB (mongo:7) --> install dependencies from the lock file ('npm ci' --> run the API test suite ('npm test'))

## What "GO" would mean

- Merge `delivery/lead` → `main`, squash, delete branch.
- Tag the merge commit `phase-3`.

## What "NO-GO" would mean

- Hold the merge until: 'main' has a green ci run, customers can get quotes again, and we know how the change reached prod around the pipeline.
- Owner of that condition: Engineering on call (fix and investigation); me, the delivery lead (comm and merge plan).
- Re-evaluate at: Thurs, 10am, at the daily check-in.

## My call

NO-GO. My branch is green and doesn't contain the hotfix, but 'main' is read and customers are being rejected, so I won't merge onto a broken 'main' during a live incident. What would flip it: a green run on 'main', customers quoting again, and an answer on how the change got around the gate.

## Incident response (Inject #2 routing message)
To: Engineering on-call; cc Support and Priya (Sponsor)
Observed: Support reports every quote request is returning a 400 ("age(34) is less than min allowed value (110)"). Separately, CI on main has been red at the test step since the validation hotfix about 40 mins ago. A red run doesn't procude a build, so the change customers are hitting must have reached prod some other way.
Asking for: Can on-call confirm what is actually deployed in front of customers right now, and whether anything went out around the pipeline (for example, a deploy from a branch or a manual change)? Can the team also look at what changed in the last hour and get customers quoting again, rolling back if that's fastest? Support, please share roughly how many customers were affected.
Owner: The on-call engineer owns the investigation and hot fix. I own the stakeholder comm and the merge plan. 
Air cover: The tests did their job by refusing this change. Take the time you need; I'm parking the site deploy review and will move today's check in if we need the time. I'm also holding all merges to main until its green.