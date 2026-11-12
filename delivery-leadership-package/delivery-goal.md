# Delivery Goal: Evergreen Quote

> Copy this file into `delivery-leadership-package/delivery-goal.md`. One sentence. Read it back to yourself. Then to your pair. Then to someone who wasn't in the room. If they can repeat it, it's good.

## Goal

By Thursday EOD, the assembled Evergreen Quote API (REST + GraphQL, backed by MongoDB, with the sponsor's rates) is merged to main through a reviewed PR with green CI, and demonstrated running in a container and as 3 replicas on a local Kubernetes cluster.

## "Done" looks like

- The API answers every documented route: list, fetch by id, create with a computed premium.
- The same data answers through GraphQL, with the explorer at `/explorer`.
- `npm test` passes; the safety net holds.
- The containerized API serves the same answers as the dev server, and the CI run on the merge commit is **green**.
- The cluster demo shows three API pods behind one Service.
- A reviewed PR is merged, branch deleted.
- `delivery-leadership-package/` is complete and committed.

## Out of scope (this week)

- Writing new features or refactoring the starter (assembly, not authoring)
- Connecting the marketing site to the API
- A live AWS/EKS deploy (unless the sponsor approves a window)
- Logins, payments, or policy bindings
