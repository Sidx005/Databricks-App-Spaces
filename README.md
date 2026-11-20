# Databricks App Spaces

A practical guide to Databricks App Spaces, centered on the **Sales & Finance Insights** demo. The demo covers App Space governance, application sharing, and Unity Catalog data authorization.

## Start here

- **[Sales & Finance Insights demo](AppSpacesDemo.md)** — the primary walkthrough, permission tests, authorization flow, and learnings.
- [App Space concepts](docs/concepts/app-spaces.md)
- [Create an App Space](docs/setup/create-app-space.md)
- [Permissions and API scopes](docs/setup/permissions.md)
- [Unity Catalog access](docs/data/unity-catalog-access.md)
- [Sample datasets](docs/data/sample-datasets.md)

## Repository structure

```text
.
├── README.md
├── AppSpacesDemo.md                  # Primary demo; intentionally kept at root
└── docs/
    ├── README.md
    ├── concepts/
    ├── setup/
    ├── data/
    ├── CreateAppSpaces.md             # Original detailed guide
    ├── Permissions.md                 # Original detailed guide
    ├── Tables.md                      # Original sample tables and screenshots
    └── UnityCatalogAccess.md          # Original detailed guide
```

The `docs/setup/` and `docs/data/` pages are the organized navigation/reference pages. Original detailed guides remain under `docs/` for now; links from the organized pages point to their current locations.
