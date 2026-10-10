# Security and privacy

Architecture Graph analyzes local source trees read-only. It does not start the target application, run Maven or Gradle, contact a cluster or cloud provider, run Terraform, upload source, or call an LLM.

Generated reports use repository-relative paths and withhold sensitive excerpts. Values are HTML-escaped. The interactive graph is self-contained and uses a content security policy that forbids network requests; its JavaScript and Cytoscape.js dependency are embedded with pinned hashes and license notices.

The public repository does not contain the product implementation source. Release archives contain inspectable bundled JavaScript; do not treat that inspectability as a security boundary or as an open-source license grant.

Do not analyze repositories containing secrets that should not be read by local tooling. Review generated output before sharing it: evidence excerpts are intentionally bounded and filtered, but any shared report is still derived from source code.

Report a suspected vulnerability through the repository owner's private GitHub security-reporting channel if enabled; otherwise open an issue without including secrets or private source.
