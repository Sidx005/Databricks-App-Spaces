# App Spaces

An App Space is a Databricks governance boundary for managing applications and developers together. It provides controls for app creation and management, user authorization scopes, and compute policies.

## How the boundaries differ

- **App Space permissions** govern who can view, create, or manage apps in the space.
- **Application sharing** controls who can use an individual deployed app.
- **Unity Catalog permissions** govern which underlying data a user's identity can read.

An app being visible or usable does not by itself grant access to its datasets. The [Sales & Finance demo](../../AppSpacesDemo.md) illustrates these distinct layers.

## Common use

App Spaces are useful when a team wants a common governance boundary for multiple apps and their builders, rather than configuring every app environment independently. Administrators can constrain capabilities and access while Unity Catalog continues to enforce data privileges.

For setup details, see [Create an App Space](../setup/create-app-space.md) and [Permissions and API scopes](../setup/permissions.md).
