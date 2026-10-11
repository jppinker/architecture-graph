## Architecture Graph v0.3.0-rc2

**Understand your architecture. Before you change it.**

> **Draft publication notice:** The version-specific [Proprietary Evaluation License](https://github.com/jppinker/architecture-graph/blob/main/docs/PROPRIETARY_LICENSE-v0.3.0-rc2.md) is prepared for simultaneous publication with this release. No owner or legal approval, Publication Date, or effective license terms are asserted while this release remains a draft.
>
> _Before publication: complete the owner and legal approvals required by Section 15. Independent clean-room verification has passed 35/35 gates as recorded below._

v0.3.0-rc2 is the unchanged v0.2.0-rc2 product (Java/Spring, JPA, Kafka, PostgreSQL, HTTP, Kubernetes, Terraform, interactive graph) plus bounded, evidence-backed analysis of selected .NET, Go and Python dependencies and context-only Oracle, RabbitMQ and IBM MQ declarations, and **Copy for AI-agent** on every interactive graph page. Analysis is local and deterministic: no LLM calls, no network, no uploads, and the analyzed code is never run.

## What's new

### Copy for AI-agent

- **Where.** Every interactive graph page has a **Copy for AI-agent** button: Batch-10 pages (`batch10-report.html`) and Java/Spring pages (`report-graph-ai.html`).
- **What it copies.**
  - Click a fact to copy its identity, repository, file, relations (with direction and kind: `traversable` code dependency or `context` only) and evidence locations (file and line, no source excerpt), plus coverage and limits.
  - In **Show potential impact**, the same button copies the ranked review items, with their classes, hops and evidence-backed paths.
- **Only from the stored page.** Everything is copied from the stored page, only on your click. Nothing is sent anywhere.
- **Markdown-safe.** Every stored value is a Markdown code span, so repository, file and project names cannot become HTML, links or headings, and they read back exactly. Values with line breaks or invisible/bidirectional characters are JSON-escaped and marked.
- **Java/Spring results:** open **`report-graph-ai.html`**. `./archgraph graph <dir>/rc2` writes it next to the unchanged v0.2.0-rc2 `report-graph.html`, prints its path, and `--open` opens it.

### New technology coverage (unchanged from v0.3.0-rc1)

| Family | What is recognized | Status |
| --- | --- | --- |
| .NET | literal `ProjectReference` to an existing `.csproj` in the same repository | confirmed dependency, used for impact |
| Go | imports of packages inside the exact `go.mod` module | confirmed dependency, used for impact |
| Python | unambiguous static first-party imports | confirmed dependency, used for impact |
| Oracle SQL/PL-SQL | schema-qualified tables, packages, procedures, functions and same-repository calls | context only, **fixture-validated only** |
| RabbitMQ | Spring AMQP queue/exchange declarations and `@RabbitListener` | context only |
| IBM MQ | queue manager property and Spring JMS destinations | context only |
| Legacy (COBOL, JCL, WSDL, XSD, BPEL, IIB, Tuxedo) | file inventory | listed as unsupported, never analyzed |

Context-only relations are drawn dashed and copied as `context`. They are never impact paths, and no relation is ever inferred between repositories.

### Real-source validation

- **Public corpus.** 8 pinned public repositories (10 scopes), including dotnet/eShop, GoogleCloudPlatform/microservices-demo, pallets/itsdangerous and public RabbitMQ and IBM MQ samples:
  - 77 confirmed code dependencies;
  - 6 context-only relations;
  - 694 unsupported or unresolved sites, reported and never drawn as edges.
- **Independent inventory.** All 908 public result rows equal an independently written inventory of the same sources.
- **dotnet/eShop:** 28 projects and 46 `ProjectReference` dependencies, 46/46 equal to the frozen gold, each with its `.csproj` file and line.
- **Earlier behaviour unchanged.** The v0.2.0-rc2 Java/Spring behaviour is reproduced exactly: all 16 frozen v0.2.0-rc2 output commitments match.

### Interactive graph and impact analysis

- **Example:** in eShop, changing `src/EventBus/EventBus.csproj` returns 20 review items, of which 17 are genuine dependents along the reference direction.
- **Parity:** impact results equal an independent recomputation for all 62 public anchor files.

## Important limitations

- **Impact items are review candidates, not confirmed dependents.**
  - Only `direct_dependent` means a direct reference.
  - Over the 62 public anchors: 552 items, of which 119 are genuine dependents (all present) and 433 are other candidates.
  - Impact means review relevance, not guaranteed breakage. An absent edge is not evidence of safety.
- **Build-time code structure, not runtime service topology.**
  - Not modelled: MSBuild, NuGet, `go.work`, build tags, `sys.path`, dynamic imports, runtime DI, ASP.NET/Aspire hosting.
  - Not analyzed: gRPC/HTTP calls in .NET/Go/Python, and C#/Go/Python messaging clients.
- **Validation levels.**
  - Oracle, RabbitMQ bindings/publishing and the IBM MQ classic API/aliases are fixture-validated only.
  - Legacy files are inventory only.
- **Copy for AI-agent scope.**
  - It is on fact and impact panels, not on the relation (edge) panel or the script-free `report.html` pages.
  - For Java/Spring, `report-graph.html` stays the unchanged v0.2.0-rc2 page without the button.
- **Labels and rendering.**
  - Batch-10 pages label their output contract "development build" (`0.3.0-dev`).
  - Graphs with more than 12 repositories draw the extra ones in grey.
- **Platform.** Linux x86-64 with Node.js 22.x; graph pages tested in Chrome/Chromium.

## Verification

- **Reproducibility:** two builds are byte-identical, the release manifest (v4) validates, and the content scan is clean.
- **Clean-room rehearsal (development account):** 34/34 gates, from a fresh extraction, offline in an isolated namespace. Includes real-click Copy for AI-agent copies in Chrome checked against the stored graph data.
- **Independent clean-room verification:** **PASS, 35/35 gates** as `mvp1eval` through the separately authorized
  `pkexec` route. The fresh-extraction run was offline in an isolated namespace, exited 0 with empty stderr, removed
  its temporary tree, matched 24/24 frozen output commitments and 27/27 real-click Copy for AI-agent commitments,
  and recorded zero model calls. Chrome 152 clipboard checks used the real Clipboard API and passed for all 27 copies.

## Quick start

**Requirements:** Linux x86-64 and Node.js 22.x.

```bash
tar -xzf architecture-graph-mvp-0.3.0-rc2-linux-x64.tar.gz
cd architecture-graph-mvp
./archgraph doctor
./archgraph demo --no-open
```

Open `runs/demo-v2/analysis/report-graph-ai.html` (Java/Spring) or `runs/demo-v2/batch10/analysis/batch10-report.html` (.NET, Go, Python, RabbitMQ, Oracle) in Chrome or Chromium. Download the attached release asset, not GitHub's automatically generated source archive.

## Download integrity

**Archive:** `architecture-graph-mvp-0.3.0-rc2-linux-x64.tar.gz` (2,667,873 bytes)

**SHA-256:** `f5a76e09bdfd66ff1b4b0cadc5b919b692888084b62f26b621c7fff6b7e18607`

```bash
sha256sum architecture-graph-mvp-0.3.0-rc2-linux-x64.tar.gz
```

## License

Copyright © MENTORIX LLC (ООО «МЕНТОРИКС»). Proprietary evaluation software. Third-party components remain under their own licenses; their notices are included in the archive and under `LICENSES/`. The public demo graph is derived from [dotnet/eShop](https://github.com/dotnet/eShop) at commit `dc7ea499` (MIT, © .NET Foundation and Contributors). It contains project names, paths and line numbers only, with no eShop source code.

Earlier releases (v0.2.0-rc2, v0.1.1, v0.1.0) are unchanged.
