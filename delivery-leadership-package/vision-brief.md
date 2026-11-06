# Evergreen Quote: Vision Brief

> Copy this file into `delivery-leadership-package/vision-brief.md` in your repo and fill it in. Target length: 1 page (~300 words). Write for a Liberty Mutual VP who has 90 seconds.

## Product
**Name:** Evergreen Quote API (Phase 3 service delivery)
**Delivery week:** 3
**Delivery Lead:** Kristen Marturano
**Engineering team (represented by):** https://github.com/asc1-student06/evergreen-quote-api-delivery
**GitHub Project board:** https://github.com/users/asc1-student06/projects/7/views/1

## Who is the customer?
People shopping for auto, home, or life insurance on the Evergreen website who want an instant monthly premium estimate. A second adueince is partner sites that request quotes through GraphQL.

## What pain does Evergreen Quote remove?
Until now, quotes were calculated in the browser and never saved. The API gives every quote one trusted source: the same rates, the same validation, and a stored record, whether the request comes from our website (REST) or a partner (GraphQL).

## What does "good" look like at end of the week?
- The API answers over REST and GraphQL with data from MongoDB
- Bad input (for example, age 5 or type "boat") is rejected with a clear message
- The test suite is green, and CI checks it on every push
- It runs from a Docker image and is demonstrated as 3 replicas on a local Kubernetes cluster
- The service knows its official name, and the sponsor's rates are applied
- Everything is merged to main through a reviewed PR with green CI

## What are we explicitly NOT doing this week?
- Writing new features or refacoring the starter (assembly, not authoring)
- Connecting the marketing site to the API
- A live AWS/EKS deploy (unless the sponsor spporves a window)
- Logins, payments, or binding policies 

## How will we know if it worked?
- Tests: 7 of 7 passing in CI on main. Currently 0, tomorrow 6 of 7 should pass until fix goes in, target = 100% green on merge
- Correct premiums: 3 of 3 sample quotes match the sponsor's rate table. i.e., Auto coverage for agre 35, 50k, returns $450/month not .35.
- Resilience: 3 of 3 API replicas running on the local Kubernetes cluster, answering through one service with 0 manual steps to rebuild it from the k8s/ folder.
