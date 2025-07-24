# Overview of Splunk Components

Splunk can be installed on a variety of hosts:
- Physical Machine
- Virtual Machine
- Containers

Once installed, each machine becomes a **Splunk instance**. Instances can be configured to perform one or more roles, depending on deployment needs.

> In small deployments, all roles may exist on one instance. In distributed environments, roles are separated for performance and scalability.

---

## Splunk Component Types

### **Processing Components**
- **Forwarders**: Collect and send data to indexers.
- **Indexers**: Parse, index, and store data.
- **Search Heads**: Search, analyze, and visualize data.

### **Management Components**
- **Deployment Server**: Manages configurations for forwarders.
- **Indexer Cluster Manager**: Manages indexer clusters.
- **Search Head Cluster Deployer**: Manages search head clusters.
- **License Manager**: Enforces licensing and usage.
- **Monitoring Console**: Monitors Splunk health and performance.

> Each Splunk instance can be configured as one or more component types.

---

## Basic Splunk Architecture

- **Three Core Components**:
  1. Forwarder
  2. Indexer
  3. Search Head

---

## Splunk Forwarders

Forwarders are installed on machines where data originates. They collect and send data to Splunk indexers.

### Types of Forwarders

- **Universal Forwarder (UF)**:
  - Lightweight agent with minimal resource usage.
  - Cannot parse or index data.
  - Used for efficient data forwarding.
  - Typically used on endpoints.

- **Heavy Forwarder (HF)**:
  - Full Splunk Enterprise instance configured to forward data.
  - Can parse, transform, and route data before indexing.
  - Useful for filtering or masking sensitive data before indexing.

> The **primary method** to get data into Splunk is via forwarders. Other input methods include HEC, scripts, APIs, and manual uploads.

###  Sample Exam Questions

- **Q:** Which component resides on machines where data originates?  
  **A:** Forwarders

- **Q:** Which component can perform log filtering or parsing?  
  **A:** Heavy Forwarders

---

## Splunk Indexers

Indexers handle:
1. **Parsing**: Breaks incoming data into individual events.
2. **Indexing**: Adds metadata (`host`, `source`, `sourcetype`, timestamp).
3. **Storing**: Writes events to disk as indexes.
4. **Searching**: Responds to search queries from Search Heads.

### Indexes
- **Main**: Default index for data if not specified.
- **_internal**: Internal Splunk logs (e.g. errors, resource usage).
- **Custom Indexes**: User-defined for better organization.

### Index Buckets (Data Lifecycle)

Buckets are directories containing indexed data.

- **Hot**: Actively written to.
- **Warm**: Rolled over from hot; still searchable.
- **Cold**: Older data on slower storage; searchable.
- **Frozen**: Past retention policy. Can be deleted or archived.
- **Thawed**: Archived frozen data restored for future searches.

> Searches can access hot, warm, cold, and thawed data. Only hot buckets are writable.

### Index Clustering

- Used for data redundancy and high availability.
- **Indexer Cluster**: Group of indexers replicating data.
- **Cluster Manager**: Manages replication and indexer health.

> Indexer 1 replicates to Indexer 2 & 3 for fault tolerance.

### Sample Exam Questions

- **Q:** Which Splunk component transforms raw data into events and indexes them?  
  **A:** Indexer

- **Q:** Which component stores data?  
  **A:** Indexer

---

## Splunk Search Head

The **Search Head (SH)** allows users to:
- Write and execute SPL queries.
- Create dashboards, alerts, reports.
- Visualize indexed data.

### Key Functions
- Distributes search queries to indexers.
- Merges results and presents them to the user.
- Stores knowledge objects (alerts, reports, macros, etc.).

### Search Head Clustering
- Multiple SHs with identical configurations.
- Uses a **Cluster Captain** (a SH node that manages the group).
- **Search Head Deployer** pushes apps/configs to all SHs.

> Searches are load-balanced across SH members.

### Sample Exam Question

- **Q:** Which component allows you to run SPL queries?  
  **A:** Search Head

---

## Deployment Server

Used to **distribute apps and configurations** to:
- Universal Forwarders
- Non-clustered indexers or search heads

### Features
- Uses **deployment apps** to manage content.
- Clients are called **deployment clients**.
- Primarily used in large-scale environments with thousands of forwarders.

> Not used to manage clustered indexers or SH clusters.

---

## Licensing in Splunk

### License Models
1. **Ingest Volume-based**: Based on daily indexing volume.
2. **Infrastructure-based**: Based on vCPUs or other compute resources (mostly for Splunk Cloud).
3. **Feature-based**: For premium apps/features (e.g. ITSI).

### License Manager
- Central server managing license pools.
- Other components are **license peers**.
- Tracks data ingestion and triggers license violations.

> Violations may disable searching temporarily.

---

## Monitoring Console

Built-in tool for monitoring your Splunk environment.

### Key Uses
- Monitor Splunk internal logs (from `_internal` index).
- Visualize deployment health.
- Troubleshoot performance issues.

> Includes dashboards for forwarders, indexing, licensing, and more.

<img width="500" height="424" alt="image" src="https://github.com/user-attachments/assets/fe66e2a3-8a2c-428a-ac54-748d540993e1" />

---


##  Exam Tip Summary

| Concept | Know This |
|--------|------------|
| Forwarders | UF (lightweight), HF (can parse/filter) |
| Indexers | Parse, assign metadata, write to index |
| Buckets | Hot (write), Warm, Cold, Frozen, Thawed |
| Search Heads | SPL queries, dashboards, clusters |
| Deployment Server | Distribute apps/configs to UFs |
| Licensing | Volume-based, license peers, violations |
| Monitoring Console | Health, performance, topology |
| Knowledge Objects | Alerts, macros, saved searches |
| Data Inputs | Files, scripts, HEC, etc. |

