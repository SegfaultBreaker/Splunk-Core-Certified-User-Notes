# What Is an App in Splunk?

![image](https://github.com/user-attachments/assets/f78e642f-8be6-4013-b5db-397cdab85282)

An **App** in Splunk is a preconfigured environment that extends the core functionality of your Splunk instance. Apps include dashboards, reports, alerts, field extractions, and configuration files tailored to specific use cases or data sources.

Think of an App as a **workspace** designed to solve a particular problem or to support a particular domain (e.g., security, networking, application monitoring).

> 🧠 Apps enhance Splunk’s built-in knowledge and capabilities, allowing users to analyze specific data types more efficiently.

---

## App Visibility

The apps visible to a user depend on:

- The user's **assigned role**
- The app's **permissions and sharing settings**
- Whether the app has been made globally visible or kept private

In general, **only administrators** (or users with sufficient capabilities) can manage app visibility and access.

---

## Roles in Splunk

Roles define what a user can **see**, **do**, and **interact with** in Splunk. Each role comes with a set of capabilities that control access to features, apps, and data.

---

### Default Predefined Roles in Splunk Enterprise

| Role          | Description                                                                 |
|---------------|-----------------------------------------------------------------------------|
| **Administrator** | Full access. Can install apps, configure settings, ingest data, and create knowledge objects for all users. |
| **Power**         | Can create and share knowledge objects with other users of an app, and perform real-time searches. |
| **User**          | Limited access. Can view their own knowledge objects and those shared with them. |

---

### Roles in Splunk Cloud

Splunk Cloud provides similar roles with slight naming differences:

| Splunk Enterprise | Splunk Cloud |
|-------------------|--------------|
| Administrator     | `sc_admin`   |
| Power             | `Power`      |
| User              | `User`       |

Additionally, Splunk Cloud introduces some cloud-specific roles:

- `can_delete`: Can delete indexed data
- `token_auth`: Manages authentication tokens
- `apps`: Manages installed cloud apps

---

## Installing Apps and Adding Data

Users with the appropriate capabilities (usually administrators) can:

- Install apps from **Splunkbase** (https://splunkbase.splunk.com/)
- Add new **data inputs**
- Configure **indexing**, **parsing**, and **permissions**

> 🏠 In your own Splunk instance ("home"), admins or users with elevated permissions can customize the environment by adding new apps and connecting new data sources.

![{2A3B9FA7-0DB2-4D38-A914-C15BE66EDCB5}](https://github.com/user-attachments/assets/dbc45251-5d04-4603-9eff-afebb5183437)
![image](https://github.com/user-attachments/assets/b43b321d-9ffd-4c9c-bbb1-2156ee739a57)

---

### Basic Tour of the Splunk search and Dashboards

![image](https://github.com/user-attachments/assets/331ea94d-6440-4f5c-91ac-3ab3882dae86)

1) It's for switching throught your all apps (others than search and dashboard) that you can find on the left part from the Splunk home
2) It's for editing your account
3) To see system level messaging
4) Manage and edit your Splunk configuration
5) Monitoring the progress of your searches (inside jobs)
6) Find help
7) Search bar for using searches
8) The Search history : can be used for seeing all your previous searches
9) Time range picker : used for retrieving events from a specific time period
10) Data Summary : displays a breakdown of the data indexed by hosts, sources and sourcetypes
    ![{DFA0E474-B5CA-4B13-B5AC-1E92BCB7DACE}](https://github.com/user-attachments/assets/4a6d2a7a-53e7-4222-b082-e0eb24f45abd)

   - Sourcetype : classification of the data
   - Sources : the file or the directory path, network port or script from which the event originated
   - Host : hostname or ip address or the FQDN, of the machine from which the event originated

## Summary

- **Apps** provide a tailored experience for specific data types or tasks.
- **Visibility** and **access** to apps depend on roles and permissions.
- **Roles** control what users can do, from viewing data to configuring the system.
- Splunk **Cloud and Enterprise** share the same basic role structure, with some differences.


