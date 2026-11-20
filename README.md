# Databricks App Spaces

A practical guide to Databricks App Spaces, with the **Sales & Finance Insights demo** as the central example. The demo documents App Space governance, application sharing, and Unity Catalog data authorization.

## Start here

- **[Sales & Finance Insights demo](AppSpacesDemo.md)** — the primary walkthrough, including the demo design, permission tests, authorization flow, and learnings.
- [What App Spaces are](docs/concepts/app-spaces.md) — concepts and scope.
- [Create an App Space](docs/setup/create-app-space.md) — UI, REST API, and Terraform entry points.
- [Permissions and API scopes](docs/setup/permissions.md) — App Space roles and user authorization scopes.
- [Unity Catalog access](docs/data/unity-catalog-access.md) — demo tables, grants, and access tests.
- [Sample datasets](docs/data/sample-datasets.md) — dataset schema and existing sample data.

## Suggested reading order

1. Read this overview to understand the repository.
2. Follow [AppSpacesDemo.md](AppSpacesDemo.md) for the end-to-end example.
3. Use the setup and data guides above when configuring a workspace.

## Repository structure

```text
.
├── README.md                         # Repository home and navigation
├── AppSpacesDemo.md                  # Primary end-to-end demo and test results
└── docs/
    ├── concepts/                     # App Space concepts
    ├── setup/                        # Creating spaces and configuring permissions
    └── data/                         # Unity Catalog data access and sample datasets
```

The original top-level reference files (`CreateAppSpaces.md`, `Permissions.md`, `UnityCatalogAccess.md`, and `Tables.md`) are retained for now as source material and backward-compatible links. The new `docs/` pages provide a navigable, topic-based entry point; the demo remains at the root by design.
