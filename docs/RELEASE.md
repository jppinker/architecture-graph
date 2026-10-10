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

The public repository contains product documentation, genuine screenshots, a self-contained original demo, security guidance, a publish-ready proprietary evaluation license draft, and third-party notices. It contains no complete or partial release-source snapshot.

The separately distributed archive necessarily contains inspectable bundled JavaScript. The project does not describe those bytes as secret, and their inspectability does not make the product open source. The archive was not rebuilt or modified during publication preparation.

## Licensing

Third-party packages retain their upstream licenses and notices under [`LICENSES/`](../LICENSES/). The package notice grants no additional license for the original Architecture Graph files. The Architecture Graph proprietary evaluation license prepared for owner approval is available in [`PROPRIETARY_LICENSE.md`](PROPRIETARY_LICENSE.md).

The draft identifies the licensed subject as the exact `v0.2.0-rc2` Linux
x86-64 archive and provides a free, worldwide, nonexclusive evaluation license
for 90 days from first installation or execution. It permits unmodified copies
for internal evaluation, testing, internal demonstrations, authorized-user
sharing within the same organization, and reasonable backups. It prohibits
production and commercial use, external redistribution, sublicensing,
transfers, and modification except where applicable law requires otherwise.

### Presentation and acceptance before use

Publication must use the following flow without rebuilding or modifying the
frozen archive:

1. Complete every owner/legal approval in Section 15 of the draft and record
   the authorized Publication Date.
2. Put a conspicuous link to the complete license in the GitHub release notes,
   above the asset instructions, together with this notice: **"Architecture
   Graph v0.2.0-rc2 is offered only under its Proprietary Evaluation License.
   Review the license before use. Installing or executing the software accepts
   the license and starts the evaluating organization's 90-day period."**
3. Keep the equivalent notice and license link above the README download and
   quick-start commands so a user is presented with the terms before the first
   instructed execution.
4. Publish the license document and release notes at the same time. Do not
   describe the license as effective or the asset as available under it before
   that publication.

Downloading alone is not defined as acceptance. First installation or
execution after the user has an opportunity to review the electronic terms is
the defined acceptance act. For an organization, the first such act by an
authorized employee or officer starts one organization-wide 90-day period.
This electronic first-use flow is intended to use the simplified procedure for
computer-program licenses under Article 1286(5) of the Civil Code of the
Russian Federation; its sufficiency for the intended distribution and user
territories remains an express owner/legal approval requirement.

### Russian-law drafting review

The draft is structured to state the matters required or contemplated by
Articles 1235 and 1286 of the Civil Code of the Russian Federation: the specific
computer program/release, expressly permitted methods of use, worldwide
territory, a 90-day term, free consideration, and a simple (nonexclusive)
license. It also defines electronic presentation and the act that constitutes
acceptance. This is a documentation consistency review, not a legal opinion.

ООО «МЕНТОРИКС» (MENTORIX LLC), INN 9715521135, OGRN 1257700586483, must not
approve publication until qualified Russian legal counsel has confirmed those
provisions, the supplied company identifiers, and the complete license. A
registered address and legal-notice contact have not been supplied. Ownership
and authority to license the original Software have also not been verified.
The liability language contains no monetary cap and requires specific
owner/legal approval.
