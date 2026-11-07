# AGENTS.md

Telegraph style. Keep the data plane provider-neutral and the hot path small.

The shared rules are referenced below; this repo's own rules are in Router safeguards, at the end.

<!-- arc-forge-org-consistency:start -->
Read the shared Arc Forge instructions before work:
https://github.com/arcforgelabs/tools/blob/main/docs/AGENTS.shared.md

Optional local source: ~/repos/tools/docs/AGENTS.shared.md.
Verify that the local checkout has the origin arcforgelabs/tools before use.
Do not copy the shared rules here.
Keep repository-specific safeguards and document references outside this block.

Common agent workflows: https://github.com/openclaw/agent-skills.
Product repositories own their product-specific skills.
Reusable release workflows: https://github.com/openclaw/release-workflows.
<!-- arc-forge-org-consistency:end -->

## Router safeguards

### Architecture

- TypeScript Worker modules own request classification, key checks, routing, budget preflight, provider transforms, and usage event construction.
- TypeScript owns the admin frontend, Cloudflare Access/GitHub glue, generated clients, and provisioning scripts.
- Provider support starts with `providers/<id>.provider.yaml`. Add a focused TypeScript adapter only when the manifest cannot express the provider safely.
- No upstream provider secrets in source, tests, fixtures, logs, screenshots, or docs.
- Do not log raw prompts or completions by default.
- Revocation and hard budget enforcement must stay faster and more authoritative than reporting/billing systems.

### Validation

- Run focused Worker and admin TypeScript tests for touched surfaces.
- Validate all bundled provider manifests after provider changes.
- Run autoreview before handoff for non-trivial code changes.

### Git

- Use focused commits.
- Keep `main` stable; feature work belongs on branches.
- Pull request Evidence also names the deployment status and the remaining risk.
