# Security Policy

This repository is a fork of [openclaw/clawrouter](https://github.com/openclaw/clawrouter). It carries no changes to ClawRouter's code. The only fork-specific files are pull request tooling under `.github/`.

## Reporting

- **Issues in ClawRouter itself:** report privately to OpenClaw at [security@openclaw.ai](mailto:security@openclaw.ai). Do not open a public issue or pull request that discloses an unpatched vulnerability, exploit path, secret, or security-sensitive proof of concept.
- **Issues in this fork's own files:** submit a private [GitHub Security Advisory](https://github.com/arcforgelabs/clawrouter/security/advisories/new) here.

## Scope

Only this fork's own files are in scope here: `.github/org-consistency/`, `.github/pull_request_template.md`, and the workflows that run them.

## Out of Scope

Everything in upstream ClawRouter, including its Worker, routing, credentials, budgets, retention, and deployment profiles. Report those to OpenClaw.
