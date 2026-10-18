

# Sales & Finance Insights Dashboard App (Built by Genie Code)

### Prompt:

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

1. **Header**
   - Title: Sales & Finance Insights
   - Subtitle: Secure, user-authorized analytics on Databricks
   - Display the signed-in user's identity if the platform provides it.

2. **Sales section**
   - Query `workspace.sales_demo.sales_data`.
   - Display a data table and useful summary metrics based on available columns.
   - Include relevant charts if the table has suitable numeric and categorical columns.

3. **Finance section**
   - Query `workspace.finance_demo.finance_data`.
   - Display a data table and useful summary metrics based on available columns.
   - Include relevant charts if the table has suitable numeric and categorical columns.

4. **Access-denied handling**
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


### App Snippet:

<img width="1440" height="791" alt="image" src="https://github.com/user-attachments/assets/37dad094-261d-47d8-b49a-64e159ab9459" />



# App Spaces Permissions


# READ ACCESS

siddharth.vishwanath is the account with admin permissions, and is managing the access for both the users (desaisiddharth and siddharthdesai)

<img width="725" height="509" alt="image" src="https://github.com/user-attachments/assets/ddde0c17-10d3-482c-bd7d-ce4ea6f0735f" />

<br/>
<br/>

desaisiddharth user is not granted create/manage app permissions, he can only read the app spaces (**can't manage permissions/authorizations, as visible, the buttons are disabled**), therefore he can:
<br/>
- Only Read the App Spaces


<img width="1431" height="794" alt="image" src="https://github.com/user-attachments/assets/50e719c2-2c6f-42c4-9bee-16393c104b8d" />


<img width="1440" height="900" alt="Screenshot 2026-10-19 at 12 11 56 AM" src="https://github.com/user-attachments/assets/fddb5223-07e8-444a-9996-576c977073f0" />


# MANAGE ACCESS

Here the user siddharthdesai, has the manage app spaces access, therefore he can:
- Create App
- Manage User Authorization & Permissions
- Can Deploy Application

<img width="1432" height="800" alt="image" src="https://github.com/user-attachments/assets/f8f20199-2609-491c-9a13-e6abb202d65b" />


# CREATE APP

Here the user desaisiddharth is granted can create app permissions, so he can:
- Can view app spaces
- Cannot manage app spaces (Edit Permissions, Delete App spaces, Manage Authorization, etc)


<img width="1439" height="759" alt="image" src="https://github.com/user-attachments/assets/05766553-a381-45c3-beb7-7b68ae0efb7e" />


<img width="1440" height="790" alt="image" src="https://github.com/user-attachments/assets/2259ccba-e228-4ae6-a091-afa2229f812c" />


<img width="1288" height="178" alt="image" src="https://github.com/user-attachments/assets/f6b5c2a1-f377-4053-8a3f-d264137c4bce" />

// Here we've stopped the application as we have already built an app from the other account(siddharth.vishwanath)
