# User Authorization

Define the permissions that apps have when acting on behalf of users (OBO).

- **RBAC (Role-Based Access Control)**
  1. **Any role:** Developers can share apps with any user. Users can choose their role when signing in to an app.
  2. **Only the selected role:** Restricts access to users who can assume the specified role. Developers can share apps in this space only with users who are eligible to assume that role.

- **API Scopes:** Restrict which Databricks APIs an app can use when acting on behalf of a signed-in user. Four configurations are available:
  1. **Data + AI (11 scopes):** Recommended option. Provides access to data, files, and AI capabilities.
  2. **Read only (4 scopes):** Allows viewing and analyzing data with a smaller set of API permissions.
  3. **Everything (16 scopes):** Allows all available API scopes, subject to the permissions of the authorizing user.
  4. **Custom:** Allows individual API scopes to be selected as needed.

  **Examples of API scopes:**
  - `sql:restricted-query` — Allows the app to execute read-only SQL queries on behalf of the user.
  - `sql` — Allows the app to execute SQL and manage SQL-related resources.
  - `genie` — Allows the app to access Databricks Genie.
  - `catalog.catalogs:read` — Allows reading Unity Catalog catalogs.
  - `catalog.schemas:read` — Allows reading Unity Catalog schemas.
  - `catalog.tables:read` — Allows reading Unity Catalog tables.
  - `catalog.connections` — Allows managing connections to external services and Lakehouse Federation.

  **Important:** API scopes control which API capabilities the app can use; they do not automatically grant access to all data or resources. The signed-in user's existing permissions still apply.


  # UI Snippets
  <img width="624" height="456" alt="image" src="https://github.com/user-attachments/assets/ed8e178e-34bb-4e9b-bd28-1adca43841b9" />

  <img width="604" height="755" alt="image" src="https://github.com/user-attachments/assets/47608d57-b48c-4df8-a811-c84348497287" />


<img width="706" height="434" alt="image" src="https://github.com/user-attachments/assets/3af613f6-9a7a-4230-afde-5a2b617cf596" />
