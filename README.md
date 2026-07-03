# det — the Deterministic CLI

`det` is the typed terminal client for [Deterministic](https://deterministic.sh)
— runtime verification for AI-generated science and engineering. Run
validations over the HTTP API, fetch receipts, and manage credentials:

```
det validate --bundle evidence.json --domain fluid_simulation
det get report <id>
det auth login | logout | whoami
```

Reference docs: [docs.deterministic.dev/cli](https://docs.deterministic.dev/cli/).

## Install

The npm package is `@deterministic-sh/cli`; it is **not published yet** — the
first release is tracked publicly. Until then, design partners receive the
preview build through their onboarding channel. Once published:

```bash
npm install -g @deterministic-sh/cli
det --version
```

Runtime: Node.js 22.14+. The CLI ships as a single-file ES-module bundle with
zero runtime dependencies.

## About this repository

This is a **distribution repo**, updated automatically from a private canonical
source (see `.github/mirror-manifest.json` for the source commit of the current
snapshot). `dist/cli.js` is the built artifact; development, issues triage, and
review happen upstream — issues are welcome here, but pull requests cannot be
merged into a mirror. Releases are cut here (signed `cli-v*` tags → the
Trusted-Publishers OIDC workflow in `.github/workflows/publish-cli.yml`), so npm
provenance attests exactly this repository and workflow.

## Security

- Credentials are stored at `~/.config/deterministic/credentials.json` with
  `0600` permissions; the key is never echoed or logged.
- The CLI talks only to the configured Deterministic host over HTTPS (loopback
  `http:` allowed for local development).
- Report vulnerabilities to security@deterministic.sh.

## License

See [LICENSE](./LICENSE).
