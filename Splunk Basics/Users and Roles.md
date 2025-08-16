Splunk enterprise comes with out of the box roles that control what you can do:

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


Exam tips : 

Q : How many main roles do you have in Splunk ? 

A : 3
