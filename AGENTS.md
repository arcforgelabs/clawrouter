# AGENTS.md

Telegraph style. Keep the data plane provider-neutral and the hot path small.

## Architecture

- TypeScript Worker modules own request classification, key checks, routing, budget preflight, provider transforms, and usage event construction.
- TypeScript owns the admin frontend, Cloudflare Access/GitHub glue, generated clients, and provisioning scripts.
- Provider support starts with `providers/<id>.provider.yaml`. Add a focused TypeScript adapter only when the manifest cannot express the provider safely.
- No upstream provider secrets in source, tests, fixtures, logs, screenshots, or docs.
- Do not log raw prompts or completions by default.
- Revocation and hard budget enforcement must stay faster and more authoritative than reporting/billing systems.

## Validation

- Run focused Worker and admin TypeScript tests for touched surfaces.
- Validate all bundled provider manifests after provider changes.
- Run autoreview before handoff for non-trivial code changes.

## Git

- Use focused commits.
- Keep `main` stable; feature work belongs on branches.
- PRs should include summary, verification, deployment status, and remaining risk.

<!-- arc-forge-org-consistency:start -->
## Pull requests

Use `.github/pull_request_template.md`. Keep these sections current in the pull request body:

- What Problem This Solves
- Why This Change Was Made
- User Impact
- Evidence

Evidence names the command, the commit, the result, and what was not run. A screenshot is the real product, with the viewport and whether the data was synthetic or live. If the proof could not be run, name the gap in Evidence. When a review asks for more proof, edit the body. Maintainer authorship does not skip the sections. A passing test is evidence about this source. Production activation is a separate record.

The org default procedure is `.github/org-consistency/skill/SKILL.md`. A stricter rule already in this file wins.
<!-- arc-forge-org-consistency:end -->
