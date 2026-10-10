# Notices

Architecture Graph 0.2.0 release candidate 2 (Batch 9 with the graph view).

- `lib/batch9/src/`, `lib/batch9/docs/`, `lib/batch9/rc2/`, `lib/batch9/viz/src/`,
  `lib/batch8/`, `archgraph`, `README.md`, `templates/` and
  `examples/demo-multirepo-v2/` are original files of this product. The demo
  repositories are small synthetic examples written for this release; no
  third-party repository is bundled.
- `lib/batch4/`, `lib/batch5/`, `lib/batch6/src/`, `lib/batch6/docs/` and
  `lib/batch7/` are the unchanged frozen product core of this project.
- `lib/batch6/node_modules/`, `lib/batch9/node_modules/` and
  `lib/batch9/viz/node_modules/` contain unmodified third-party packages (for
  the last two, only the files loaded at run time). Their names, versions and
  licenses are listed in `THIRD_PARTY_NOTICES.md`, and each package's own
  license text is copied next to it in this directory.
- Every `report-graph.html` written by `./archgraph graph` or `./archgraph demo`
  embeds the unmodified Cytoscape.js bundle together with its MIT license text,
  so the page works offline and carries its own notice.

This notice does not grant any license beyond the terms published with the
release by its authors.
