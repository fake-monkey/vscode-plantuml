# Custom build

- Base: Marketplace version 2.18.1, upstream master commit
  `7bc1758ed73dc269f5721d78c6c6c01f461d7cb0`. Upstream has no v2.18.1
  tag or GitHub Release; the latest upstream tag is v2.18.0.
- Feature branch: `feat/server-env-vars` (no upstream PR).
- Integration branch: `custom`.
- Custom version and local tag: `2.18.1+custom.1` and `v2.18.1+custom.1`.
- Fork remote: `fork` (`git@github.com:fake-monkey/vscode-plantuml.git`).
  The existing `origin` remote continues to point to upstream.

`plantuml.server` supports `${env:NAME}` placeholders. See README.md for usage.

Validation: `node --experimental-strip-types --test test/serverUrl.test.mjs`
passes all five tests with the existing Node 22.15.1 installation.
`git diff --check` passes. `npm run compile` cannot run because project
dependencies (including TypeScript) are absent. No dependencies were installed.
Full extension compilation, VSIX packaging (including acceptance of SemVer build
metadata), and rendering inside VS Code remain unverified. The custom version
metadata does not provide automatic update ordering.

Branches and tag were created locally; no push, release, or installation was
performed. No backup worktrees or temporary processes were created.
