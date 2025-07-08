# What Are Commands in SPL?

In Splunk, **SPL** (Search Processing Language) is composed of five key components:

1. **Search terms** – the foundation of your search queries.
2. **Commands** – define what you want Splunk to do with the results (e.g., charts, statistics, formatting).
3. **Functions** – describe how results should be computed or evaluated.
4. **Arguments** – parameters passed to functions for more control.
5. **Clauses** – define how results should be grouped or presented.

### Example:

![Search Language Structure](https://github.com/user-attachments/assets/2f3c27ee-690c-4e3c-aed8-055480f324cd)

**Note:** Always include the pipe `|`. It tells Splunk to pass the result set to the next component in the pipeline.

---

# Splunk Query Explanation

This document explains what the following Splunk SPL query does:

```spl
index=network sourcetype=cisco_wsa_squid usage=Violation
| stats count(usage) as Visits
```

---

## Query Breakdown

### `index=network`

Limits the search to events within the `network` index.

An **index** is like a database or storage location in Splunk for a specific category of data.

---

### `sourcetype=cisco_wsa_squid`

Narrows results to logs from Cisco Web Security Appliance (WSA) using Squid proxy log format.

The **sourcetype** tells Splunk how to parse and extract field values from those logs.

---

### `usage=Violation`

Filters to only include events where the `usage` field is equal to `Violation`, such as blocked or restricted web activity.

---

### Stats Command

```spl
| stats count(usage) as Visits
```

Performs statistical aggregation:

- `stats` generates a statistical summary.
- `count(usage)` counts the number of events where the `usage` field exists.
- `as Visits` renames the output field for clarity.

Since the search already filters for `usage=Violation`, this command effectively counts total **violations**.

---

## Summary

- Searches inside the `network` index.
- Filters only Cisco WSA logs where a violation occurred.
- Counts the number of those violations and renames the column `Visits`.

---

## Example: Grouping by Username

To show violations per user:

```spl
index=network sourcetype=cisco_wsa_squid usage=Violation
| stats count(usage) as Visits by cs_username
```

![Grouped by Username](https://github.com/user-attachments/assets/60154f97-c1f2-4003-a9b8-63b3259ea65a)

---

## Example: Filtering Users with Multiple Violations

```spl
index=network sourcetype=cisco_wsa_squid usage=Violation
| stats count(usage) as Visits by cs_username
| search Visits > 1
```

![Filtered Violations](https://github.com/user-attachments/assets/72ad30f6-e5b7-4c00-9001-950cd4de4d70)

---

# Case Sensitivity

- SPL keywords (commands, functions, arguments) are **not** case-sensitive.
- **Field values**, however, **are** case-sensitive.

### Example: Using `replace`

To modify specific hostnames using `replace`, case must match exactly:

```spl
... | replace "SERVER1" with "WebServer"
```

If case doesn’t match, replacement won’t work.

![Replace Example](https://github.com/user-attachments/assets/7927fc93-0b1b-4602-9957-5103f5edf915)

---

# Search Efficiency Tips

## 1. Use Time Range First

The most efficient way to narrow search results is by **restricting the time range**.

## 2. Use Default Fields

After time, prioritize these built-in fields for faster filtering:

- `index`
- `source`
- `host`
- `sourcetype`

---

## 3. Be Specific

The more precise your filters, the faster and more accurate the results.

---

## 4. Prefer Inclusion Over Exclusion

Instead of this (less efficient):

```spl
NOT "access granted"
```

Use this (more efficient):

```spl
"access denied"
```

---

## 5. Avoid Wildcards When Possible

Avoid leading or trailing wildcards like:

```spl
admin*
```

This is slower because it requires more pattern matching.

![Wildcard Example](https://github.com/user-attachments/assets/35a98fc4-3669-4d39-9f4d-8f03a89dbfd2)

---

## 6. Use Specific Sourcetypes

Avoid generic queries like:

```spl
sourcetype=*
```

Prefer a defined sourcetype to reduce event count and improve precision:

```spl
sourcetype=cisco_wsa_squid
```
