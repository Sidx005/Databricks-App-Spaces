# App spaces

An **App Space** is a governance boudary introduced by Databricks that allows workspace administrators to manage data access, security guidelines,
and spending policies for groups of applications and developers simultaneously.



## Story Behind introducing App Spaces

Due to rise of AI assistants and "Vibe-coding" , building data-drivn applications has become easier. Databricks introduced App Spaces to allow non-technical business users and "citizen developers" to build
applictions rapidly via tools like ** Genie App Builder ** without compromising enterprise security or budget.



## Provlem Solved

Before App Spaces , governing internal tooling was highly inefficient. IT directly solves the following enterprise bottlenecks:

- **Per-App Administrative Overhead** : Instead of forcing IT or  platform teams to manually review , configure identities , and provision data permissions for. every individual application, admins can configure a single App Space once.
   Every App deployed in that space automatically inherits those pre-approved rules.

- **Security & Permission Leakage** : Non tech builders are mostly not security experts. App Spaces prevents apps from proxying unauthorized permissions by restricting data access strictly to the predefined guardrails set by the administrator.
- **Uncapped Compute Costs** : It aggregates operations tracking, enabling admins to apply strict spend limits and cost policies across thousands of multi-app environments.



  ## Core Concepts
  - **Purpose:** Governance boundary for managing groups of custom applications and their developers.
  - **Managed OBjects**: Used to manage access for Custom applications, developer group pemrissions, API Scopes, and compute spending policies. Unlike unity catalog that manages Schemas, tables, views, files/volumes, AI Models, Storage Credntials.
  - **Target Audience**: App Developers, Software Engineeers, and Non-Technical Business Builders.
  - **Scope of Control**: Environemnt constraints(network egress, compute scaling, "on-behalf-of-user" authentication scopes
 



## What are Dtabricks Apps?

**Databricks Apps** is a serverless runtime framework that lets developers build, hopst, and govern secure data and AI applications(like chatbots and interactive dashbaords) directly within the Databricks ecosystems.

**Examples of Databricks Apps**

Applications built on Databricks typically utlize popular open-source Python or front-end Javascript frameworks. Common examples are:

1. **AI Chatbots & RAG Applications :** Using frameworks like Gradio or Streamlit alongside Mosaic AI Vector Search and LLMs to create conversational assistnats that securely reference internal documentation.
2. **Interactive Data Dashboards**: Building Dash or Shiny Applications thst pull live telemetry, time-metrics or operational KPIs from Databricks SQL Warehouses.
3. **Custom Machine Learning Tools :** Internal Tools for expert data-labelling tasks, operaional dashboards for processing specialized health data, or demand forecasting visualizers.
<a href="https://hiflylabs.com/blog/2024/10/9/databricks-apps-first-look">
  <img width="1158" height="1040" alt="Click here" src="https://github.com/user-attachments/assets/e7e56aae-e259-4de1-8bef-8e2e60039b0c">
</a>

<p style={width:'100%'; text-align:'center'}>Sample Databricks App Architecure [Source: hippylabs.com]</p>
