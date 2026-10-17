# Tech Fleet landing page

A minimal landing page for Tech Fleet: a single accessible hero with a heading
and a one-paragraph intro. Static HTML and CSS, no build step.

Open `index.html` in a browser to view it.

## Engineering standards are enforced here

This repo was bootstrapped with the enterprise engineering-skills tooling
(`techfleetworks/enterprise-software-AI-skills` v1.1.0). See
[ADR-0001](docs/adr/0001-enforce-engineering-standards-via-enterprise-gates.md)
for the setup decision and its known limitations.

- **Gates (committed, portable):** the `enterprise-gates` CI check runs every
  gate in `gate-manifest.json` and blocks merges that fail. Run them locally:

  ```bash
  npm run gates
  ```

- **Pre-push pre-flight:** the armed hook in `.githooks/pre-push` is meant to run
  the offline gates before each push (armed automatically on `npm install` via
  the `prepare` script). Note: this hook currently runs zero gates on Windows
  (a path-separator bug in the upstream template, see ADR-0001); rely on CI as
  the real gate there. Run the gates yourself any time with `npm run gates`.

- **Directive (machine-local):** the always-on skills directive is installed at
  the user level (`esk-init --personal`), not committed, because its emitter
  lives in the external upstream repo. A fresh machine needs that one-time
  install; the committed gates block merges regardless.
