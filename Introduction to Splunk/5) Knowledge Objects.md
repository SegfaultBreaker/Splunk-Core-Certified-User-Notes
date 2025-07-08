# What Are Knowledge Objects in Splunk?

**Knowledge objects** in Splunk are reusable tools that enhance data discovery, classification, and analysis. They are created from your indexed data and provide structure and context to make searching, reporting, and visualizing data more efficient.

> Think of knowledge objects as the *custom intelligence layer* you and your users build on top of raw data to extract meaningful insights.

---

## Categories of Knowledge Objects

Knowledge objects are grouped into **five functional categories**:

1. **Data Interpretation**
2. **Data Classification**
3. **Data Enrichment**
4. **Data Normalization**
5. **Data Models**

---

## Why Use Knowledge Objects?

Knowledge objects offer powerful benefits in a Splunk deployment:

- **Reusable**: Once created, they can be reused across searches, reports, and dashboards.
- **Sharable**: Objects can be shared with others based on permission settings.
- **Search-Enhanced**: They make searches more efficient, intuitive, and context-rich.
- **App-Scalable**: Can be packaged into apps for deployment across teams and environments.

---

## Knowledge Manager Responsibilities

In large deployments, a **knowledge manager** is responsible for:

1. Overseeing knowledge object creation and usage
2. Defining naming conventions and best practices
3. Normalizing event data across sources
4. Building **data models** to support Pivot and accelerated reporting

---

## 1. Data Interpretation

![Data Interpretation](https://github.com/user-attachments/assets/f148d9e5-c6dc-401a-8d86-648bccc65583)

- **Field Extractions**: Fields are automatically extracted based on sourcetype, but additional fields can be manually created for deeper insights.
- **Calculated Fields**: Dynamic fields created at search time using SPL to perform calculations on existing values.

---

## 2. Data Classification

![Data Classification](https://github.com/user-attachments/assets/42a710e2-cd1c-4bbe-8977-836c2ceeea53)

- **Event Types**: Categorize events based on search criteria (e.g., all login failures).
- **Transactions**: Group conceptually related events that span a period of time into a single logical event.

---

## 3. Data Enrichment

![Data Enrichment](https://github.com/user-attachments/assets/d7db7792-4392-470b-b0a6-0551fd3c96ba)

- **Lookups**: Augment event data by adding fields from external sources like CSVs or KV stores (e.g., mapping IPs to locations).
- **Workflow Actions**: Add UI actions to events that link to external systems or refined searches (e.g., open a ticket, drill into logs).

---

## 4. Data Normalization

![Data Normalization](https://github.com/user-attachments/assets/cab011f0-7235-4e82-a2a4-e2a67f9f1bcf)

- **Tags**: Assign human-readable labels to field values for simplified searching (e.g., tag `src_ip=10.0.0.1` as `malicious_ip`).
- **Field Aliases**: Normalize data by giving different fields from different sources a shared alias (e.g., `user`, `username`, and `usr` all become `user`).

---

## 5. Data Models

![Data Models](https://github.com/user-attachments/assets/97c6508c-93be-474e-bad4-e89c20a74197)

- **Data Models**: Hierarchical structures built on datasets, used for Pivot-based exploration or to accelerate reports.
  - Composed of events, transactions, and searches
  - Foundation of **Splunk Enterprise Security** and **ITSI** apps

---

> Summary: Knowledge objects are key to unlocking the full analytical power of Splunk. They help teams collaborate, scale, and get to insights faster using reusable, structured intelligence built right into your data layer.

