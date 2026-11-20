# Databricks App Spaces

A practical guide to Databricks App Spaces, centered on the **Sales & Finance Insights** demo. The demo covers App Space governance, application sharing, and Unity Catalog data authorization.

## Start here

- **[Sales & Finance Insights demo](AppSpacesDemo.md)** — the primary walkthrough, permission tests, authorization flow, and learnings.
- [App Space concepts](docs/concepts/app-spaces.md)
- [Create an App Space](docs/setup/CreateAppSpaces.md)
- [Permissions and API scopes](docs/setup/Permissions.md)
- [Unity Catalog access](docs/data/unity-catalog-access.md)
- [Sample datasets and tables](docs/data/Tables.md)

## Repository structure

```text
.
├── README.md
├── AppSpacesDemo.md                  # Primary demo; intentionally kept at root
└── docs/
    ├── README.md
    ├── concepts/
    │   └── app-spaces.md
    ├── setup/
    │   ├── CreateAppSpaces.md         # App Space creation guide
    │   ├── Permissions.md             # Permissions and API scopes guide
    │   └── UnityCatalogAccess.md      # Detailed Unity Catalog setup and grants
    └── data/
        ├── Tables.md                  # Sample tables data and screenshots
        └── unity-catalog-access.md    # Summary overview of UC access
```

The `docs/setup/` and `docs/data/` directories organize setup guides and data documentation.

