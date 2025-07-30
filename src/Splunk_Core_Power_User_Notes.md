
# Splunk Core Certified Power User Notes (Section 2 to Section 13)

---

## **Section 2: Transforming Commands for Visualizations**

### 2.1 Module Overview
Covers how to use transforming commands to create visualizations.

### 2.2 Visualization Data Structures
- Splunk organizes data into **events** and **fields**.
- Visualizations operate on **transformed data**, usually using commands like `stats`, `chart`, or `timechart`.

### 2.3 Types of Visualizations
- Tables
- Single value
- Bar, Column, Line, Area
- Pie charts
- Scatter charts
- Bubble charts
- Gauges
- Maps

### 2.4 Statistics Tables
- **Command**: `stats`
- **Purpose**: Aggregates events into a summary table
```spl
index=web sourcetype=access_combined | stats count by status
```

### 2.5 The `chart` Command - Single Series
- Converts search results into a tabular format for visualizations.
```spl
... | chart count over status
```

### 2.6 The `chart` Command - Multi-Series
```spl
... | chart count over date by status
```

### 2.7 The `timechart` Command - Single Series
- Visualizes trends over time.
```spl
... | timechart count
```

### 2.8 The `timechart` Command - Multi-Series
```spl
... | timechart count by status
```

### 2.9 Scatter & Bubble Charts
- Used to show relationships and distributions.
- Requires at least **two numerical fields**.

### 2.10 Formatting Statistics Tables
- Rename fields using `AS`
- Use `fieldformat`, `eval`, or dashboard formatting options.

### 2.11 Formatting Visualizations
- Add labels, legends, chart titles.
- Use `visualization` tab in Splunk UI.

---

## **Section 3: Advanced Visualizations**

### 3.1 Single Value Visualizations
```spl
... | stats count AS Total | fields Total
```

### 3.2 Maps
- Use `geostats` or `geom` commands with fields like `lat`, `lon`, `Country`, etc.

### 3.3 Creating a Trendline
- Use `predict` command
```spl
... | timechart count | predict count
```

---

## **Section 4: Filtering & Formatting Results**

### 4.1 Using `eval` Command
```spl
... | eval duration=logout_time - login_time
```

### 4.2 Calculating Fields
- `eval` can also be used for string, math, logical expressions.

### 4.3 Rounding Field Values
```spl
... | eval duration=round(duration, 2)
```

### 4.4 Converting Fields
```spl
... | eval status= tostring(status, "commas")
```

### 4.5 String Concatenation
```spl
... | eval fullName=firstname . " " . lastname
```

### 4.6 The `if` Function
```spl
... | eval alert=if(status > 500, "Yes", "No")
```

### 4.7 The `case` Function
```spl
... | eval type=case(status==200, "Success", status==404, "Not Found")
```

### 4.8 The `fillnull` Command
```spl
... | fillnull value="N/A"
```

### 4.9 Filtering Search Results
```spl
... search error OR failure
... | where status >= 400
```

---

## **Section 5: Correlating Events**

### 5.1 The `transaction` Command
```spl
... | transaction startswith="login" endswith="logout"
```

### 5.2 Filtering Transactions
```spl
... | transaction user | search duration>30
```

### 5.3 Transaction Constraints
- `maxspan`, `maxpause`, `maxevents`

### 5.4 Report on Transactions
- Combine `stats` or `chart` after `transaction`.

---

## **Section 6: Creating & Managing Fields**

### 6.1 Field Discovery (Auto-Extraction)
- Done at index time or search time

### 6.2 Field Extractions with Knowledge Objects
- **Settings → Fields → Field Extractions**

### 6.3 Delimiter Field Extractions
- Regex: `,`, `:`, `" "` etc.

### 6.4 RegEx Field Extraction
```regex
(?<status_code>\d{3})
```

---

## **Section 7: Field Aliases & Calculated Fields**

### 7.1 Field Aliases
- Maps multiple field names to the same logical field.
- Done via `Field aliases` configuration.

### 7.2 Calculated Fields
- Created using `eval`.
```spl
... | eval fullName=first . " " . last
```

---

## **Section 8: Tags & Event Types**

### 8.1 Tags
- Labels for field values.
- e.g., tag IP address `192.0.2.1` as “malicious”.

### 8.2 Event Types
- Saved search with a label
```spl
search index=web sourcetype=access_combined status=200
```

---

## **Section 9: Macros**

### 9.1 What is a Macro?
- Reusable search snippet.
- Accepts arguments.
```spl
`failed_login(user)`
```

### 9.2 Creating & Validating
- Go to `Settings → Advanced Search → Search Macros`

---

## **Section 10: Workflow Actions**

### 10.1 What is a Workflow Action?
- Used to run secondary searches or links on click.
- Supports GET/POST/search type.

---

## **Section 11: Creating Data Models**

### 11.1 Data Model Structure
- Root event dataset → child → constraints

### 11.2 Creating Fields in Data Models
- Auto-extracted
- Eval-based
- Lookup-based
- Regex

---

## **Section 12: CIM (Common Information Model)**

### 12.1 CIM Add-On
- Normalizes field names
- Enables compatibility with many apps

---

## **Section 13: Practice Tests**
- Apply all commands and configurations learned.
- Practice interpreting dashboards and output.
