# Permissions and API scopes

Databricks App Spaces govern both workspace roles and the API capabilities an app may request when acting on behalf of a signed-in user.

## RBAC options

- **Any role:** developers can share apps with users who select an eligible role when signing in.
- **Only the selected role:** limits access to users eligible to assume the configured role.

## API scope configurations

Available choices described in this repository include **Data + AI**, **Read only**, **Everything**, and **Custom**. Choose the narrowest scope set that supports the app. Examples include `sql:restricted-query`, `genie`, and Unity Catalog metadata read scopes.

Scopes limit API capabilities; they do not grant the user permission to data. The signed-in user's existing Unity Catalog privileges still apply. App Space permissions, app-sharing permissions, and data permissions should be tested separately.

See the original reference for scope descriptions and screenshots in [`Permissions.md`](../../Permissions.md), and the end-to-end results in [`AppSpacesDemo.md`](../../AppSpacesDemo.md).
