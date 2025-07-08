# Splunk Search Language: Essentials

Learn the core search features in Splunk: wildcards, case sensitivity, Boolean logic, operator precedence, and special character handling.

---

## Wildcards

Use an asterisk `*` to match **zero or more characters** in a word.

### Example:
Search for all words that start with `fail`:
```spl
fail*
```
Matches: `fail`, `failed`, `failure`, `failing`, etc.

---

## Case Sensitivity

Searches in Splunk are **not case-sensitive**.

### Example:
```spl
FAILURE
Failure
failure
```
All three will return the same results.

---

## Boolean Operators

Splunk supports these Boolean operators:

| Operator | Description                             | Example                        |
|----------|-----------------------------------------|--------------------------------|
| `OR`     | Match if **either** term exists         | `failed OR password`           |
| `AND`    | Match if **both** terms exist           | `failed AND password`          |
| `NOT`    | Exclude events containing the term      | `failed NOT password`          |

### Notes:
- If no operator is used between words, `AND` is implied.
```spl
failed password
```
This is the same as:
```spl
failed AND password
```

---

## 🔄 Boolean Evaluation Order

Splunk evaluates Boolean expressions in the following order:

1. `NOT`
2. `OR`
3. `AND`

Use **parentheses** to group and control logic flow.

### Example:
```spl
failed NOT (success OR accepted)
```
- `success OR accepted` is evaluated first
- Then `NOT` is applied
- Then `failed` is matched with the result

You can also use quotes to match an exact phrase:
```spl
"failed password"
```

---

## Special Character Escaping

Use the backslash `\` to escape special characters like quotes.

### Example:
Searching for this literal string:
```
info="user "Chris" NOT in database"
```

You need to escape the inner quotes:
```spl
info="user \"Chris\" NOT in database"
```

---

## Summary

- `*` = wildcard for matching patterns
- Splunk is **not case-sensitive**
- Use `AND`, `OR`, `NOT` for logic control
- `AND` is implied if no operator is written
- Operator precedence: `NOT` → `OR` → `AND`
- Use `()` to group expressions
- Use `\"` to escape quotes in string searches
