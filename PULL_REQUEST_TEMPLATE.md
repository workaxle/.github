<!--
Your PR title becomes the squash commit on main — format: [WA-123] feat(scope): subject
Struggling to answer Deploy safety? That's usually two PRs — split it.
-->

## Description

## Added/updated tests?

- [ ] Yes
- [ ] No, and this is why: _please replace this line with details on why tests
      have not been included_

## Deploy safety

<!-- Rule: every merge must be deployable as-is. Anything that could degrade prod goes behind a flag.
     Tick exactly ONE box per question. Options with a colon need the answer filled in. -->

**Old & new together** — during deploy, the old and new versions run at the same time, sharing the DB, queues, and jobs.

- [ ] Nothing changed shape (DB, proto, events, GraphQL, job args)
- [ ] Something changed — it's safe because: <!-- one line, e.g. "new column, old code never reads it" -->

**Deploy order** — can this go out on its own, before or after any other repo?

- [ ] Yes, order doesn't matter
- [ ] No — order is in Jira: <!-- WA link --> — and wrong order degrades, doesn't break

**Who sees it** — what can a customer reach the moment this deploys?

- [ ] Everything here is finished and meant to be live
- [ ] Hidden behind off-by-default flag: `flag_name`
- [ ] Removing flag: `flag_name` — checked it's ON for all prod tenants
- [ ] Nothing — code isn't hooked up to any endpoint, consumer, or job

**Undo** — if this breaks prod, we get back to normal by:

- [ ] Turning off flag: `flag_name` — no deploy needed
- [ ] `git revert` + redeploy — acceptable; could a flag have made this instant?
- [ ] Neither works cleanly — plan B is: <!-- one line -->
