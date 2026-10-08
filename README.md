# Architecture Graph

**Discover architecture dependencies across repositories and understand what to review when code changes.**

**AI-agents produce a lot of code and we need to monitor their impact on codebase.**

Architecture Graph analyzes supported Java/Spring, Kafka, and PostgreSQL relationships and generates evidence-backed HTML reports.

- Runs locally — no cloud account required.
- No LLM or API keys required.
- Supports analysis of multiple repositories.
- Shows source evidence for discovered relationships.
- Provides deterministic change-impact reports.

> **MVP v0.1.1** — Linux x64, Node.js 22.x required.
> Currently supports a limited Java/Spring + Kafka + PostgreSQL subset.

## Download

### [Download Architecture Graph v0.1.1](https://github.com/jppinker/architecture-graph/releases/tag/v0.1.1)

Download the file:

`architecture-graph-mvp-0.1.1-linux-x64.tar.gz`

**Important:** Download the release asset, not GitHub's automatically generated "Source code" archive.

## Quick Start

### 1. Download and extract

Download `architecture-graph-mvp-0.1.1-linux-x64.tar.gz` from the [latest release](https://github.com/jppinker/architecture-graph/releases/tag/v0.1.1).

Open a terminal in your Downloads directory and run:

```bash
mkdir architecture-graph
tar -xzf architecture-graph-mvp-0.1.1-linux-x64.tar.gz -C architecture-graph
cd architecture-graph/architecture-graph-mvp
```

### 2. Check prerequisites

```bash
./archgraph doctor
```

### 3. Try the demo

```bash
./archgraph demo --no-open
```

The demo analyzes example repositories and generates a local HTML architecture report.

Open the HTML file at the path printed in your terminal.

### 4. Analyze your own repositories

Single repository:

```bash
./archgraph analyze /path/to/your/repository
```

Multiple repositories:

```bash
./archgraph analyze /path/to/service-a /path/to/service-b
```

No manual configuration is necessary for an initial analysis.

For cross-repository Kafka/PostgreSQL relationships, verified resource identities may need to be supplied through the optional `--workspace` configuration.

### 5. Explore change impact

After analyzing your repositories:

```bash
./archgraph impact \
  --analysis <analysis-id-or-path> \
  --file <repo-id>:<relative-path> \
  --intent modify
```

Architecture Graph identifies:

- Direct dependencies
- Shared-resource peers
- Possible transitive impact
- Supporting source evidence
- Unsupported or unresolved relationships

A graph path indicates review relevance, not guaranteed runtime breakage.

## Supported Scope

Currently supported:

- Selected Java/Spring architecture constructs
- Kafka producers, consumers, and topics
- Supported PostgreSQL tables and relationships
- Evidence-backed cross-repository resource relationships
- Deterministic impact analysis

The MVP does not understand every Java framework or infrastructure technology.

Missing relationships do not imply that a change is safe.

## Privacy

All analysis runs locally.

- No source code is uploaded.
- No cloud service is required.
- No LLM calls are made.
- Analyzed repositories are not modified.

## Requirements

- Linux x64
- Node.js 22.x

I did not include macOS and native Windows in the current version of the product

## Feedback

This is an early MVP. Feedback from software engineers testing it on real repositories is especially valuable.

[Report an issue or suggest an improvement](https://github.com/jppinker/architecture-graph/issues)

## Release

[Architecture Graph v0.1.0 — Downloads and Release Notes](https://github.com/jppinker/architecture-graph/releases/tag/v0.1.0)
