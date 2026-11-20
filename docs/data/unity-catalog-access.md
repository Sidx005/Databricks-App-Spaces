# Unity Catalog access

The demo uses two tables in the `workspace` catalog:

- Sales: `workspace.sales_demo.sales_data`
- Finance: `workspace.finance_demo.finance_data`

The intended authorization test is that Sales users can read Sales but not Finance, and Finance users can read Finance but not Sales. Both user groups need catalog usage; each group should receive schema usage and table `SELECT` only for its permitted dataset.

The original [`UnityCatalogAccess.md`](../../UnityCatalogAccess.md) includes example SQL grants and screenshots. Review grants in the target workspace and validate each dataset as the relevant test identity. Do not rely on UI visibility as proof of data authorization.

For the broader application and sharing test flow, see [`AppSpacesDemo.md`](../../AppSpacesDemo.md).
