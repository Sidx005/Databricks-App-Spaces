# Sales & Finance Insights Dashboard — Databricks App Spaces

## 1. Project Overview

**Application:** Sales & Finance Insights Dashboard  
**Built using:** Databricks Genie App Builder  
**App Space:** `Sales-Insights-Demo`  
**Objective:** Demonstrate App Space governance, app-sharing permissions, and Unity Catalog data access using On-Behalf-Of (OBO) authorization.

The application contains separate Sales and Finance dashboards. Each signed-in user should only be able to query datasets permitted by their Unity Catalog privileges.

### Data Sources

| Dataset | Unity Catalog Table |
|---|---|
| Sales | `workspace.sales_demo.sales_data` |
| Finance | `workspace.finance_demo.finance_data` |

### Application Preview

<img width="1440" height="791" alt="Sales and Finance Insights dashboard application" src="https://github.com/user-attachments/assets/37dad094-261d-47d8-b49a-64e159ab9459" />

<img width="939" height="794" alt="image" src="https://github.com/user-attachments/assets/03843a07-db39-4e0b-8f75-3545535b691b" />


---

## 2. Application Generation Prompt

The following prompt was used to build the application with Genie App Builder.

```md
Build a professional, interactive Streamlit-style data analytics application named **Sales & Finance Insights**.

### Objective
Demonstrate Databricks On-Behalf-Of (OBO) user authorization with Unity Catalog. Different signed-in users must see only the datasets they are authorized to access. The application must not bypass or override Unity Catalog permissions.

### Data sources
Use these existing Unity Catalog tables:
- Sales: `workspace.sales_demo.sales_data`
- Finance: `workspace.finance_demo.finance_data`

Do not create duplicate tables or modify the existing data.

### Application UI
Create a clean, modern analytics dashboard with:

1. Header
   - Title: Sales & Finance Insights
   - Subtitle: Secure, user-authorized analytics on Databricks
   - Display the signed-in user's identity if the platform provides it.

2. Sales section
   - Query `workspace.sales_demo.sales_data`.
   - Display a data table and useful summary metrics based on available columns.
   - Include relevant charts if the table has suitable numeric and categorical columns.

3. Finance section
   - Query `workspace.finance_demo.finance_data`.
   - Display a data table and useful summary metrics based on available columns.
   - Include relevant charts if the table has suitable numeric and categorical columns.

4. Access-denied handling
   - If the signed-in user lacks permission to access a table, show a friendly message such as:
     "You don't have permission to access this dataset. Contact your Databricks administrator."
   - Do not expose stack traces, access tokens, credentials, or internal authentication details.
   - If access to one table is denied, keep the other authorized section usable.

### Security requirements
- Use the current signed-in user's identity and the supported Databricks Apps user-authorization mechanism for data queries.
- Enforce authorization through the user's own permissions; do not use a shared administrator token or service principal to bypass data permissions.
- Do not store or display access tokens.
- Do not hardcode user email addresses to determine which datasets they can access.
- Do not simulate authorization in the UI. Let Databricks and Unity Catalog enforce actual permissions.
- Do not grant permissions, modify access controls, or change table ownership automatically.

### Expected behavior
- A user with access only to Sales can query Sales successfully and receives an access-denied message for Finance.
- A user with access only to Finance can query Finance successfully and receives an access-denied message for Sales.
- A user with permission to both tables can access both sections.
- The app must handle permission errors gracefully and must not display unauthorized data.

### Implementation constraints
Use only capabilities supported by Genie App Builder and the current App Space environment. Do not claim that OBO is configured unless the generated application actually supports and uses the signed-in user's authorization context. If direct OBO token forwarding or custom Python/Streamlit code is unsupported, clearly identify that limitation and explain what additional implementation is required.

Build the application and provide the steps required to configure its data access and deploy it within this App Space.
```

---

## 3. App Space Permissions

App Space permissions determine which users can view, create, or manage applications and authorization settings within the App Space.

The following tests were performed using three accounts:

- `siddharth.vishwanath` — administrator account
- `desaisiddharth` — read/create access test account
- `siddharthdesai` — management access test account

### 3.1 Read Access

The account `siddharth.vishwanath` manages access for the other test users.

The user `desaisiddharth` has read access to App Spaces but is not permitted to manage their permissions or authorization settings.

**Observed capabilities:**
- View App Spaces.
- Inspect available App Space information.
- Cannot edit App Space permissions.
- Cannot manage authorization settings or perform restricted administrative actions.

<img width="725" height="509" alt="App Space read access configuration" src="https://github.com/user-attachments/assets/ddde0c17-10d3-482c-bd7d-ce4ea6f0735f" />

<img width="1431" height="794" alt="App Space view with read-only permissions" src="https://github.com/user-attachments/assets/50e719c2-2c6f-42c4-9bee-16393c104b8d" />

<img width="1440" height="900" alt="Read-only App Space permissions" src="https://github.com/user-attachments/assets/fddb5223-07e8-444a-9996-576c977073f0" />

### 3.2 Manage Access

The user `siddharthdesai` was granted management access to App Spaces.

**Observed capabilities:**
- Create applications.
- Manage user authorization and permissions.
- Deploy applications.
- Perform App Space management actions permitted by the assigned role.

<img width="1432" height="800" alt="App Space management access configuration" src="https://github.com/user-attachments/assets/f8f20199-2609-491c-9a13-e6abb202d65b" />

### 3.3 Create App Access

The user `desaisiddharth` was also tested with app-creation permission without App Space management permission.

**Observed capabilities:**
- View App Spaces.
- Create an app where permitted by the assigned role and workflow.
- Cannot manage App Space permissions or delete App Spaces.
- Cannot manage authorization settings unless separately authorized.

<img width="1439" height="759" alt="Create app permission configuration" src="https://github.com/user-attachments/assets/05766553-a381-45c3-beb7-7b68ae0efb7e" />

<img width="1440" height="790" alt="App creation workflow" src="https://github.com/user-attachments/assets/2259ccba-e228-4ae6-a091-afa2229f812c" />

<img width="1288" height="178" alt="Application stopped after testing" src="https://github.com/user-attachments/assets/f6b5c2a1-f377-4053-8a3f-d264137c4bce" />

*Note: The application was stopped after testing because it had already been built using the `siddharth.vishwanath` account.*

---

## 4. Application-Sharing Permissions

App Space permissions and application-sharing permissions serve different purposes.

A user may be allowed to view an App Space but still be denied access to an individual application.

### 4.1 Initial Access Denied

When `siddharthdesai` attempted to open the application, the user received an **App permission denied** message because the application's sharing configuration did not grant the required access.

<img width="1440" height="744" alt="Application access denied before sharing permissions were granted" src="https://github.com/user-attachments/assets/a636d36c-6851-4820-9e9f-2b150bf1f4be" />

### 4.2 Granting CAN USE

The application owner subsequently granted `CAN USE` to `siddharthdesai` through the app's Share settings.

After this change, the user could open and use the application.

<img width="1095" height="535" alt="Application Share settings with CAN USE permission" src="https://github.com/user-attachments/assets/10b5f0bd-a4b9-47d7-ae6b-537eccebd155" />

**Key takeaway:** App Space access does not automatically grant access to every deployed application. The intended user must also have the appropriate application-sharing permission.

For ordinary users, `CAN USE` is generally sufficient; `CAN MANAGE` should be reserved for users who need to administer the application.

---

## 5. Unity Catalog Data Authorization

After application access was granted, the user's ability to query Sales and Finance was determined by Unity Catalog privileges.

The test user `siddharthdesai` belongs to the Finance group and has access to the Finance dataset but not the Sales dataset.

### 5.1 Sales Dashboard

The user attempted to access the Sales dashboard.

Because the user does not have the required Unity Catalog permissions for `workspace.sales_demo.sales_data`, the query should be denied.

<img width="1438" height="581" alt="Sales dashboard tested using the Finance-only user" src="https://github.com/user-attachments/assets/8016529a-edb8-4652-b365-3f590a50729b" />

### 5.2 Finance Dashboard

The user successfully accessed the Finance dashboard because the user's Unity Catalog group grants the necessary access to `workspace.finance_demo.finance_data`.

<img width="579" height="798" alt="image" src="https://github.com/user-attachments/assets/5f8352b8-b681-48cb-8227-9d3bde9d49a1" />

### 5.3 Expected Access Matrix

| User | Sales | Finance |
|---|---|---|
| `siddharth.vishwanath` — administrator/test account | Allowed | Allowed |
| `siddharthdesai` — Finance group | Denied | Allowed |
| Sales-only test user | Allowed | Denied |

The table describes the expected access based on the configured grants. Each result should be verified by querying the corresponding table as that user.

---

## 6. Understanding the Authorization Flow

The demo highlights three distinct authorization layers.

| Layer | Responsibility |
|---|---|
| App Space permissions | Control permitted App Space operations, such as viewing, creating, and managing apps. |
| Application-sharing permissions | Control who can open and use the deployed app. |
| Unity Catalog permissions | Control which underlying tables a user can query. |

### Authorization Flow

```text
User signs in
     |
     v
App Space permissions
     |
     v
Application sharing: CAN USE
     |
     v
Application uses supported user authorization context
     |
     v
Unity Catalog evaluates the user's privileges
     |
     +---- Sales: Allowed or Denied
     |
     +---- Finance: Allowed or Denied
```

The diagram represents the conceptual separation of responsibilities, rather than a strict sequence of internal API calls.

## 7. Key Learnings

1. **App Space permissions** govern app development and administration.
2. **App-sharing permissions** determine whether a user can open and use a deployed app.
3. **Unity Catalog** governs access to the underlying datasets.
4. **OBO authorization**, when supported and correctly configured, allows application queries to respect the signed-in user's permissions.
5. Creating an app, managing an App Space, using an app, and querying its data are different capabilities.
6. A successful application sign-in does not imply that the user can access every dataset.
7. Test users should receive the minimum permissions necessary for their tasks.
8. The application should handle denied queries gracefully without exposing access tokens, credentials, or internal error details.

## 8. Conclusion

The Sales & Finance Insights demo illustrates how Databricks separates App Space governance, application-level access, and data-level authorization.

Granting `CAN USE` allowed `siddharthdesai` to open the application. Unity Catalog then continued to enforce the user's Finance-only data privileges, preventing unauthorized access to Sales.

This demonstrates why secure Databricks applications need both appropriate application-sharing permissions and correctly configured data permissions. App Space management controls how applications are created and governed, while the application's authorization mechanism and Unity Catalog determine what data the signed-in user can access.
