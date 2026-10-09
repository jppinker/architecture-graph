# v0.2.0-rc2 release identity and distribution boundary

Architecture Graph is a public product with private source. This repository intentionally excludes the implementation, development history, internal tests, evaluation data, and the release archive itself. The frozen Linux archive is distributed separately as a GitHub Release asset.

## Frozen identity

- Release: `0.2.0-rc2`
- Platform: `linux-x64`
- Required Node.js: `22.x`
- Archive SHA-256: `51f79f3811730c147853c38205d33aa714bf9faa91c80c9da33226a978837d9a`
- Content commitment: `sha256:cc176908873519d91eeec35684a9d3acb381647d25f138dd96e63020fdd3bea8`
- Release manifest SHA-256: `0f906aa63e7611383717f63f152865ea91c931a03cb351dec79d82977c4c73ac`
- Final clean-room development commit: `62b05ca3af3e897e42b5c49d15b46eacaf8edb0f`

The archive was not rebuilt for publication preparation. The public snapshot excludes only files created after extraction under `runs/`; those files are analyzer output and are not archive members.

## Boundary

The public repository contains product documentation, genuine screenshots, a self-contained original demo, security guidance, proposed proprietary terms, and third-party notices. It contains no complete or partial release-source snapshot.

The separately distributed archive necessarily contains inspectable bundled JavaScript. The project does not describe those bytes as secret, and their inspectability does not make the product open source. The archive was not rebuilt or modified during publication preparation.

## Licensing

Third-party packages retain their upstream licenses and notices under [`LICENSES/`](../LICENSES/). The package notice grants no additional license for the original Architecture Graph files. Proposed Architecture Graph evaluation and distribution terms are available as an owner-approval draft in [`PROPRIETARY_TERMS_DRAFT.md`](PROPRIETARY_TERMS_DRAFT.md).
