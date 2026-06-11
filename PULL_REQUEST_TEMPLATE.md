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

**Old & new together** <!-- q:compat --> — during deploy, old and new code run at the same time. Is that safe here?

- [ ] Yes — nothing they share changed (data, contracts, messages)
- [ ] Something shared changed — still safe because: your_reason_here

**Deploy order** <!-- q:order --> — does this depend on another service or repo deploying first?

- [ ] No — this can deploy alone, in any order
- [ ] Yes — depends on: SERVICE_NAME, details in Jira: WA-XXXXX — wrong order makes things slower or limited, but nothing breaks

**Who sees it** <!-- q:exposure --> — what can a customer reach the moment this deploys?

- [ ] Everything here is finished and meant to be live
- [ ] Hidden behind off-by-default flag: `YOUR_FLAG_NAME`
- [ ] Removing flag: `YOUR_FLAG_NAME` — I checked it is ON for all prod tenants in every cluster
- [ ] Nothing customers can reach — internal only (refactor, dependency bump, event plumbing, dead code)

**Manual steps** <!-- q:manual --> — must a human do anything beyond the normal release process (env vars, data task, infra)? Creating a default-off flag does not count; deleting or turning one on does.

- [ ] None — no human action needed
- [ ] Yes — steps (write here or link Jira): your_steps_here

**Undo** <!-- q:undo --> — if this breaks prod, we get back to normal by:

- [ ] Turning off flag: `YOUR_FLAG_NAME` — no deploy needed
- [ ] `git revert` + redeploy — acceptable; could a flag have made this instant?
- [ ] Neither works — recovery plan: your_plan_here

<!-- deploy-safety:end -->
