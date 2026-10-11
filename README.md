# Architecture Graph

**Understand your architecture. Before you change it.**

**AI agents produce code quickly. Architecture Graph helps reviewers inspect evidence-backed dependencies and likely review impact before accepting a change.**

### [Try the v0.3.0-rc2 eShop demo](https://jppinker.github.io/architecture-graph/)

Explore a frozen analysis of [dotnet/eShop](https://github.com/dotnet/eShop) directly in Chrome or Chromium. The page is self-contained and makes no network requests.

**[Try eShop Demo](https://jppinker.github.io/architecture-graph/) · [Historical v0.2.0-rc2 Demo](https://jppinker.github.io/architecture-graph/v0.2.0-rc2/) · [v0.3.0-rc2 Release](https://github.com/jppinker/architecture-graph/releases/tag/v0.3.0-rc2)**

Architecture Graph discovers evidence-backed relationships in one or more repositories, renders them as an interactive graph, and shows the supported review impact of a file change. Analysis is local and deterministic: no LLM calls, API keys, source uploads, or application startup.

Architecture Graph is proprietary software. The product source is not published in this repository. The distributed archive contains bundled JavaScript that remains inspectable; that visibility is not an open-source license or a claim that the implementation is secret.

> **v0.3.0-rc2 release candidate** · Linux x86-64 · Node.js 22.x
> Independently verified in a clean room: 35/35 gates passed. Unsupported and unresolved patterns remain visible; a missing edge never means a change is safe.

## What is new in v0.3.0-rc2

- Bounded, evidence-backed analysis of literal .NET `ProjectReference` dependencies, Go imports inside the exact module, and unambiguous static first-party Python imports.
- Context-only Oracle, RabbitMQ, and IBM MQ declarations. These are never used as impact paths.
- Unsupported legacy files are inventoried without claiming analysis.
- **Copy for AI-agent** on interactive fact and impact panels. It copies stored identities, paths, relation direction and semantics, evidence locations, impact paths, and limitations as Markdown-safe text. It sends nothing and runs only after a click.
- The v0.2.0-rc2 Java/Spring behavior remains unchanged; all 16 frozen historical output commitments match.

The public eShop demo was generated from the frozen v0.3.0-rc2 archive at eShop commit `dc7ea499`. It contains 28 projects and 46 verified `ProjectReference` dependencies. The archive result equals the frozen independent inventory, and every relation retains its `.csproj` file and line. The previous public demo remains available at [`/v0.2.0-rc2/`](https://jppinker.github.io/architecture-graph/v0.2.0-rc2/).

## Download and quick start

> **Publication and license status:** The v0.3.0-rc2 release and its
> [version-specific Proprietary Evaluation License](docs/PROPRIETARY_LICENSE-v0.3.0-rc2.md)
> are publication drafts. No owner or legal approval is asserted, and the draft
> terms are not described as effective before the required Section 15 approvals
> and simultaneous publication with the release.

When the release is published, download `architecture-graph-mvp-0.3.0-rc2-linux-x64.tar.gz` from the [v0.3.0-rc2 release page](https://github.com/jppinker/architecture-graph/releases/tag/v0.3.0-rc2). Download the release asset, not GitHub's automatically generated source archive.

```sh
tar -xzf architecture-graph-mvp-0.3.0-rc2-linux-x64.tar.gz
cd architecture-graph-mvp
./archgraph doctor
./archgraph demo --no-open
```

The bundled demo writes the Java/Spring graph with Copy for AI-agent to `runs/demo-v2/analysis/report-graph-ai.html` and the heterogeneous graph to `runs/demo-v2/batch10/analysis/batch10-report.html`. Open either directly from disk in Chrome or Chromium; no server, CDN, font, or network is required.

Analyze repositories and inspect a change:

```sh
./archgraph analyze /path/to/repository [/path/to/another ...] --output runs/my-analysis
./archgraph impact --analysis runs/my-analysis --file <repo-id>:<relative-file> --intent modify --output runs/my-impact
./archgraph report runs/my-impact
./archgraph graph runs/my-analysis
```

The repository id is the directory name. Equal names alone never create a relationship, and no Batch-10 relation is inferred between repositories.

## Supported bounded subsets

| Family | Recognized subset | Result semantics |
| --- | --- | --- |
| Java/Spring and prior v0.2.0-rc2 families | Frozen Spring, JPA, Kafka, PostgreSQL, HTTP, Kubernetes, and Terraform behavior | Confirmed or context-only according to the existing rule |
| .NET | Literal `ProjectReference` to an existing `.csproj` in the same repository | Confirmed dependency, used for impact |
| Go | Imports of packages inside the exact `go.mod` module | Confirmed dependency, used for impact |
| Python | Unambiguous static first-party imports | Confirmed dependency, used for impact |
| Oracle SQL/PL-SQL | Schema-qualified declarations and same-repository calls | Context only; fixture-validated only |
| RabbitMQ | Bounded Spring AMQP declarations and listeners | Context only; binding/publishing subset fixture-validated only |
| IBM MQ | Queue-manager property and bounded Spring JMS destinations | Context only; classic API/aliases fixture-validated only |
| Legacy | COBOL, JCL, WSDL, XSD, BPEL, IIB, and Tuxedo file presence | Inventory only, never analyzed |

Every supported fact and relationship retains its canonical identity, repository-relative source location, rule, span, and evidence reference. Reports state partial, unsupported, unresolved, ambiguous, and truncated analysis explicitly.

## Explore and copy the graph

- Click a node for outgoing dependencies, incoming dependents, canonical identity, source file, and evidence.
- Choose **Show potential impact** to display the stored Layer-R result for that node's file. Nothing is traversed in the browser.
- Use **Copy for AI-agent** on a fact or impact panel to copy Markdown-safe context. The edge panel and script-free `report.html` do not have this control.
- Click an edge for its evidence. Search names, filter repositories or relation types, drag nodes, pan, zoom, fit, or reset.
- Solid edges are traversed by supported impact analysis. Dashed edges are verified architecture context only.

## Honest limitations

- Impact items are review candidates, not guaranteed breakage. Across 62 public anchors, all 119 genuine dependents are present, alongside 433 other review candidates. Only `direct_dependent` means a direct reference.
- This is bounded build-time static analysis, not runtime service topology or a general compiler/call graph.
- Not modeled for the new language families: MSBuild, NuGet, `go.work`, Go build tags, Python `sys.path` and dynamic imports, runtime dependency injection, ASP.NET/Aspire hosting, or gRPC/HTTP and messaging clients in .NET, Go, and Python.
- Oracle, RabbitMQ binding/publishing, and IBM MQ classic API/alias claims named above are fixture-validated only. Fixture validation is not production or broad real-world validation.
- Legacy files are inventory only. No cross-repository Batch-10 relationship is inferred.
- Batch-10 report pages truthfully retain the `0.3.0-dev` **development build** contract label inherited from the verified implementation.
- Graphs with more than 12 repositories draw additional repository nodes in grey. Graph rendering, counts, filtering, evidence, and self-test continue to work.
- Graph pages were tested in Chrome/Chromium. Impact is precomputed for at most 300 source files per page.
- Linux x86-64 with Node.js 22.x is the only supported release platform.

Unsupported technology or unresolved evidence can hide relationships. Absence of an edge is not evidence of safety.

## Privacy, provenance, and licensing

Analysis reads local repositories without modifying or executing them. It makes no network or model calls and uploads nothing. Reports use repository-relative paths, HTML-escape untrusted values, and use a content security policy that blocks remote resources.

- [v0.3.0-rc2 release identity and distribution boundary](docs/RELEASE.md)
- [v0.3.0-rc2 public release notes](docs/RELEASE_NOTES-v0.3.0-rc2.md)
- [v0.3.0-rc2 Proprietary Evaluation License draft](docs/PROPRIETARY_LICENSE-v0.3.0-rc2.md)
- [Historical v0.2.0-rc2 license](docs/PROPRIETARY_LICENSE.md)
- [Runtime dependency notices](LICENSES/THIRD_PARTY_NOTICES.md)
- [Product notice](LICENSES/NOTICE.md)
- [v0.2.0-rc2 historical release](https://github.com/jppinker/architecture-graph/releases/tag/v0.2.0-rc2)
- [Issues and feedback](https://github.com/jppinker/architecture-graph/issues)

Third-party components remain under their own licenses. The eShop-derived public demo contains project identities, paths, and line numbers only—no eShop source code—and is attributed under the eShop MIT license.

## Integrity

```text
f5a76e09bdfd66ff1b4b0cadc5b919b692888084b62f26b621c7fff6b7e18607  architecture-graph-mvp-0.3.0-rc2-linux-x64.tar.gz
```

The archive is distributed separately as a GitHub Release asset and is not stored in this repository. Use the release asset for installation; do not use GitHub's automatically generated source archives.
