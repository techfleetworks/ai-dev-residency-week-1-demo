# 1. Enforce engineering standards via the enterprise gates (bootstrap-v2)

- Status: accepted
- Date: 2026-10-17
- Deciders: mdenner

## Context

This repository hosts a small Tech Fleet landing page. It must enforce the
organization's engineering standards on every change, using the local
engineering-skills repository's own tooling at
`C:\Users\morga\Documents\enterprise-software-AI-skills` (the upstream,
`techfleetworks/enterprise-software-AI-skills`, version 1.1.0).

The upstream ships two installers (see its `bootstrap` skill):

- `esk-init` installs the always-on directive hook, which makes an agent *load*
  the skills while it works (honor system, per session, bypassable).
- `esk-genesis` installs the CI gates, which make a change *unable to merge*
  unless it passes (server-side required check, fail-closed), plus a local
  pre-push pre-flight.

A fully protected repo wants both. The question was how to apply each one here
without creating a hook that is dead on other machines.

## Decision

1. Run `esk-genesis` to install the committed, portable enforcement: the three
   manifest gates (`skill-gate-parity`, `manifest-provenance`,
   `bootstrap-presence`), the aggregator (`run-manifest-gates.mjs`), the single
   required check workflow (`enterprise-gates.yml`), and the armed pre-push hook
   (`core.hooksPath=.githooks`, auto-armed on `npm install` via the `prepare`
   script).
2. Do **not** commit a per-repo directive hook. The directive emitter lives in
   the external upstream repo, so a committed hook pointing at an absolute path
   would be dead on every other machine; `esk-init` refuses this by design. The
   machine already has the `--personal` (user-level) directive hook installed
   and emitting (verified: `esk-init --personal --check` exits 0), which already
   covers every session rooted in this repo on this machine.

## Consequences

- Enforcement that travels with the repo: the `enterprise-gates` required check
  (once an admin marks it required) blocks any merge that fails the gates, and
  the pre-push hook catches the offline gates in seconds before a push.
- The directive layer is machine-local, not committed. A teammate on a fresh
  machine needs the one-time `esk-init --personal` install to get the directive;
  the committed gates still block their merges regardless.

## Known limitations (evidence-stated)

- `manifest-provenance` is a network/CI-only gate. It passes only when a
  published upstream GitHub release `v1.1.0` carries a matching
  `gate-manifest.json`. Locally the pre-push hook skips it by design; in CI it
  fails closed if no such release is published. Whether that release exists is
  **not-assessed** here (no network check was run). Source to re-run: the
  `enterprise-gates` workflow's "Fetch upstream manifest for provenance" step.
- The gate self-tests copied into `test/` by `esk-genesis` resolve each gate at
  the upstream path `.claude/skills/judge-arch/scripts/check-*.mjs`, which does
  not exist in a consumer (genesis places the gates under `scripts/ci/`). So
  `node --test` fails wholesale here. This is **observed** (re-run: `node
  --test`). It does not block merge (the required check runs the aggregator, not
  these tests), but it means the gates' own discrimination tests do not execute
  in this repo. The fix belongs upstream in `esk-genesis` (rewrite the test's
  gate path to `scripts/ci/` on copy, or drive it by the `GATE_DIR` env), not in
  hand-edits to the vendored files here.
