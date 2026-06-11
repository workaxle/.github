<!--
Your PR title becomes the squash commit message — format: [WA-123] feat(scope): subject
Cherry-picking to production? Answer Deploy safety against the production branch, not main.
Hard to answer Deploy safety? That usually means this should be two PRs — split it.
-->

## Description

## Added/updated tests?

- [ ] Yes
- [ ] No, because: your_reason_here

## Deploy safety

<!-- Rule: every merge must be deployable as-is. Anything that could degrade prod goes behind a flag.
     Tick exactly ONE box per question. Replace placeholder tokens; keep answers on the same line as the box. -->

**Old & new together** <!-- q:compat --> — after this ships, old and new versions run at the same time (rolling pods, open browser tabs, cached bundles, old app installs) and share the same DB, queues, and APIs.

- [ ] Nothing changed format (DB, proto, events, GraphQL, job args or class names — anything saved or sent between processes)
- [ ] Format changed — it is safe because: your_reason_here

**Deploy order** <!-- q:order --> — can this deploy alone, before or after any other repo?

- [ ] Yes, order does not matter
- [ ] No — wrong order makes things slower or limited, but nothing breaks; order is in Jira: WA-XXXXX

**Who sees it** <!-- q:exposure --> — what can a customer reach the moment this deploys?

- [ ] Everything here is finished and meant to be live
- [ ] Hidden behind off-by-default flag: `YOUR_FLAG_NAME`
- [ ] Removing flag: `YOUR_FLAG_NAME` — I checked it is ON for all prod tenants in every cluster
- [ ] Nothing customers can reach — internal only (refactor, dependency bump, event plumbing, dead code)

**Manual steps** <!-- q:manual --> — must a human do anything beyond the normal release process (env vars, data task, infra)? Creating a default-off flag does not count; deleting or turning one on does.

- [ ] None — no human action needed
- [ ] Yes — steps are in Jira: WA-XXXXX

**Undo** <!-- q:undo --> — if this breaks prod, we get back to normal by:

- [ ] Turning off flag: `YOUR_FLAG_NAME` — no deploy needed
- [ ] `git revert` + redeploy — acceptable; could a flag have made this instant?
- [ ] Neither works — recovery plan: your_plan_here

<!-- deploy-safety:end -->
