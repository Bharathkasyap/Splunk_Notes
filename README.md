# 📘 Splunk Core Certified Power User Notes

> Professionally organized notes for SPLK-1002 exam preparation.

---

<details>
<summary>📘 1. Introduction to Splunk</summary>

```
==============================
1. Introduction to Splunk
==============================

What is Splunk?
---------------
Splunk is a powerful platform for searching, monitoring, and analyzing machine-generated big data via a web-style interface. It stores, indexes, and correlates real-time data in a searchable repository from which it can generate graphs, reports, alerts, dashboards, and visualizations.

Why Use Splunk?
---------------
- Centralized log analysis
- Real-time monitoring
- Powerful dashboards
- Alerting and automation
- Extensible via apps and add-ons

Splunk Components:
------------------
1. **Universal Forwarder (UF)** – Lightweight agent that sends logs to Splunk Indexer.
2. **Indexer** – Parses and indexes the incoming data.
3. **Search Head (SH)** – Frontend used to run searches and build visualizations.
4. **Deployment Server** – Manages configurations for multiple Splunk instances.

Data Flow in Splunk:
--------------------
1. Log sources → UF → Indexer → SH
2. Raw data → Parsing → Indexing → Searching → Reporting

Indexes:
--------
- Logical data storage locations (like folders)
- Default index: `main`
- Custom indexes can be created

Example Log (from secure.log):
------------------------------
`Jun 08 18:20:24 sshd[4747]: Failed password for invalid user john from 10.0.0.4 port 22`

Basic Search:
-------------
```splunk
index=linux_logs sourcetype=secure.log "Failed password"
```

Exam Tips:
----------
📌 Understand each Splunk component and its role.
📌 Know the data flow and difference between UF, Indexer, and SH.
📌 Remember where parsing, indexing, and searching occur.

</details>

<details>
<summary>📘 2. Navigating the Splunk Interface</summary>

```
==============================
2. Navigating the Splunk Interface
==============================

Overview:
---------
Splunk's Web Interface (Search Head) is where analysts perform searches, build dashboards, create alerts, and view visualizations.

Main UI Components:
-------------------
1. Search Bar – Where SPL queries are written.
2. Time Range Picker – Choose time windows like "Last 24 hours" or custom time.
3. Sidebar Panel – Displays Datasets, Reports, Alerts, Apps, and Settings.
4. Fields Panel – Shows all indexed and extracted fields for each event.
5. Events Viewer – Displays event logs with field highlighting.

Time Range Picker:
------------------
This is critical to scope your searches correctly.

Search Modes:
-------------
1. Fast – Fastest, skips field discovery.
2. Smart – Default mode, balances speed and field discovery.
3. Verbose – Slower, discovers all fields.

Field Discovery:
----------------
Selected Fields: _time, host, source, sourcetype
Interesting Fields: Splunk's suggested fields

Example:
--------
```splunk
index=linux_logs sourcetype=secure.log "Failed password"
| stats count by user
```

Exam Tips:
----------
📌 Know what each UI panel is used for.
📌 Understand when to use Fast vs. Smart vs. Verbose search modes.
📌 The Time Picker greatly affects results — avoid forgetting to check it!

</details>


<details>
<summary>📘 3. Time Ranges in Splunk</summary>

```
==============================
3. Time Ranges in Splunk
==============================

Overview:
---------
Time range selection is one of the most critical aspects of Splunk searches.

Time Picker Presets:
--------------------
- Last 15 minutes
- Last 24 hours
- Last 7 days
- Yesterday
- Real-time

Relative Time:
--------------
- `-1h@h` = 1 hour ago aligned to hour
- `-15m@m` = 15 minutes ago, aligned to minute

Time Modifiers in SPL:
----------------------
```splunk
index=syslog earliest=-2h
index=syslog earliest="07/27/2025:08:00:00" latest="07/27/2025:10:00:00"
```

Real-Time Searches:
-------------------
- Live dashboarding
- Use with care (high system usage)

Example Query:
--------------
```splunk
index=linux_logs sourcetype=secure.log "Failed password"
| stats count by src_ip
| where count > 10
earliest=-1h
```

Exam Tips:
----------
📌 Set the right time range before running queries.
📌 Know real-time vs. historical tradeoffs.
📌 Understand time modifiers (`earliest`, `latest`).

</details>


<details>
<summary>📘 4. SPL Syntax and Search Pipeline</summary>

```
==============================
4. SPL Syntax and Search Pipeline
==============================

Overview:
---------
SPL (Search Processing Language) is how you query data in Splunk.

Structure:
----------
Each command is separated by a pipe (`|`) symbol.

Example:
--------
```splunk
index=web sourcetype=access_combined
| stats count by status
```

Command Types:
--------------
- Search: `index=main`
- Transforming: `stats`, `chart`, `timechart`
- Filtering: `where`, `fields`, `dedup`
- Eval: `eval`, `if`, `case`
- Format: `table`, `sort`

Example Query:
--------------
```splunk
index=web sourcetype=access_combined
| eval is_error=if(status>=400, "yes", "no")
| stats count by is_error
```

Real-World Example:
-------------------
```splunk
index=linux_logs sourcetype=secure.log "Failed password"
| eval day=strftime(_time, "%A")
| stats count by day, user
```

Exam Tips:
----------
📌 SPL syntax is case-sensitive.
📌 Don’t forget the `|` between commands.
📌 Understand the role of each command type in the pipeline.

</details>


<details>
<summary> 📘 5. Using Fields and Field Extraction</summary>

```
==============================
5. Using Fields and Field Extraction
==============================

Overview:
---------
Fields are key-value pairs extracted from event data. Splunk automatically extracts some fields and allows manual extractions.

Types of Fields:
----------------
- Default Fields: _time, host, source, sourcetype
- Indexed Fields: Extracted at index time (e.g., host)
- Search-time Fields: Extracted when a search is run (e.g., status)

Field Panels:
-------------
- Selected Fields: Always shown in UI
- Interesting Fields: Frequently occurring in current results

Field Extraction Methods:
-------------------------
1. Interactive Extraction – via UI (Settings > Fields > Field Extractions)
2. Using `rex` – Regular expression based extraction
3. Using `spath` – Extract fields from JSON logs

Example using `rex`:
---------------------
index=linux_logs sourcetype=secure.log
| rex "Failed password for (?<user>\w+) from (?<ip>\d+\.\d+\.\d+\.\d+)"

Example using `spath` (for JSON):
---------------------------------
index=api sourcetype=json_logs
| spath input=payload path=user.id output=user_id

Best Practices:
---------------
- Use `rex` for unstructured logs
- Use `spath` for JSON or XML
- Avoid extracting the same field multiple times

Exam Tips:
----------
📌 Understand difference between indexed vs search-time fields.
📌 Practice both `rex` and `spath` syntax.
📌 Know where to configure field extractions in the UI.
```
</details>


<details>
<summary>📘 6. Using Search Modes</summary>

```
==============================
6. Using Search Modes
==============================

Overview:
---------
Search Modes determine how much field discovery Splunk performs, which affects speed and detail.

Modes:
------
1. Fast – Minimal field extraction; fastest.
2. Smart – Balanced; default mode.
3. Verbose – Maximum field extraction; slowest.

When to Use:
------------
- Fast: For saved reports, known fields
- Smart: General searching
- Verbose: Exploratory searching

Comparison Table:
-----------------
Mode     | Field Discovery | Speed
---------|------------------|-------
Fast     | Minimal          | 🔥 Fast
Smart    | Conditional      | ⚖️ Balanced
Verbose  | Full             | 🐢 Slow

Exam Tips:
----------
📌 Know when to switch modes.
📌 Verbose is needed for field discovery.
📌 Smart adjusts based on pipeline usage.
```
</details>


<details>
<summary>📘 7. Transforming Commands</summary>

```
==============================
7. Transforming Commands
==============================

Overview:
---------
Transforming commands are used to calculate statistics and create charts or time-based trends.

Common Commands:
----------------
1. stats – Aggregates data
2. chart – Like stats but output in table format
3. timechart – Time-based trends

Examples:
---------
index=web sourcetype=access_combined
| stats count by status

index=web sourcetype=access_combined
| chart avg(bytes) over status by host

index=web
| timechart span=1h count by status

Transforming Functions:
-----------------------
- count
- avg
- sum
- min
- max
- dc (distinct count)
- values (list unique)

Best Practices:
---------------
- Use timechart when _time is needed
- Use dc(field) for distinct users/IPs
- Always verify fields exist before using them

Exam Tips:
----------
📌 Understand difference between stats, chart, and timechart.
📌 Know transforming functions (avg, dc, sum, etc.).
📌 Timechart requires _time field.
```
</details>


<details>
<summary>📘 8. Data Visualizations & Dashboards</summary>

```
==============================
8. Data Visualizations & Dashboards
==============================

Overview:
---------
Dashboards visualize search results using charts, tables, and gauges.

Common Visualization Types:
---------------------------
- Column and Bar charts
- Line and Area charts
- Pie and Scatter plots
- Single value, Gauge

Creating Dashboards:
--------------------
- Use "Save As > Dashboard Panel" after running a search.
- Combine multiple panels in one dashboard.

Modifying Panels:
-----------------
- Change chart type, title, color scheme
- Use tokens to pass values between inputs and panels

Best Practices:
---------------
- Use dropdown filters for interactivity
- Title each panel meaningfully
- Don’t overload with too many panels

Exam Tips:
----------
📌 You can save searches as dashboard panels.
📌 Know the types of visualizations.
📌 Use dynamic filters and inputs for reusability.
```
</details>


<details>
<summary>📘 9. Creating and Using Reports</summary>

```
==============================
9. Creating and Using Reports
==============================

Overview:
---------
Reports are saved searches that can be scheduled and shared.

Creating a Report:
------------------
- Run a search
- Click "Save As > Report"
- Set a title, description, permissions

Scheduling:
-----------
- You can schedule reports to run at set intervals
- Set actions like email, PDF export, alert trigger

Managing Reports:
-----------------
- Go to Settings > Searches, Reports, Alerts
- Modify permissions, owners, schedule

Difference from Dashboards:
---------------------------
Feature     | Report                  | Dashboard
------------|-------------------------|-------------------------
Purpose     | Scheduled results       | Interactive view
Output      | Table or chart          | Multiple visual panels
Scheduling  | Yes                     | No (but can refresh)

Exam Tips:
----------
📌 Reports are saved searches.
📌 You can schedule and share reports.
📌 Reports can send emails or trigger alerts.
```
</details>


<details>
<summary>📘 10. Alerts and Scheduled Searches</summary>

```
==============================
10. Alerts and Scheduled Searches
==============================

Overview:
---------
Alerts are saved searches with conditions that notify you when triggered.

Creating an Alert:
------------------
- Run a search
- Click “Save As > Alert”
- Set trigger condition (number of results, custom logic)
- Choose actions: email, webhook, script

Alert Types:
------------
- Real-time: Triggered as soon as condition met
- Scheduled: Runs at intervals and checks for match

Trigger Conditions:
-------------------
- Per-result (trigger for each event)
- Number of results (e.g. >100 errors)

Actions:
--------
- Send email
- Webhook
- Log to index
- Run script

Best Practices:
---------------
- Avoid real-time unless truly needed
- Use summary indexing for frequent alerts
- Include enough info in alert email

Exam Tips:
----------
📌 Know difference between real-time vs scheduled.
📌 Understand how to configure trigger conditions.
📌 Alerts are just scheduled searches with actions.
```
</details>


<details>
<summary>📘 11. Event Types and Tags</summary>

```
==============================
11. Event Types and Tags
==============================

Overview:
---------
Event types group similar events under a name, allowing easier reuse.

Creating Event Types:
---------------------
- Search for logs
- Click "Save As > Event Type"
- Provide a name and optional tag

Tags:
-----
- Labels applied to field values or event types
- Help categorize data (e.g., tag IPs as internal/external)

Example:
--------
`tag=authentication` could include event types like `login_success` and `login_failure`

Best Practices:
---------------
- Use consistent naming
- Combine tags with lookups for context

Exam Tips:
----------
📌 Event types are named saved searches.
📌 Tags help group events logically.
📌 Tags are useful for CIM and accelerated datasets.
```
</details>


<details>
<summary>📘 12. Lookups and Field Enrichment</summary>

```
==============================
12. Lookups and Field Enrichment
==============================

Overview:
---------
Lookups enrich event data by matching fields with external CSV or KV store.

Types of Lookups:
-----------------
1. **File-based (.csv)**
2. **External (scripts)**
3. **KV Store (indexed DB)**

Common Commands:
----------------
- inputlookup – view lookup contents
- lookup – enrich events
- outputlookup – write results

Example:
--------
index=web | lookup ip2location ip AS client_ip OUTPUT city, country

Automatic Lookups:
------------------
- Apply based on sourcetype
- Configured under Settings > Fields > Lookup Definitions

Best Practices:
---------------
- Use lookups to map codes, geo info, user info
- Keep lookup file updated

Exam Tips:
----------
📌 Understand inputlookup vs lookup vs outputlookup.
📌 Know where automatic lookups are defined.
📌 Know CSV formatting and matching fields.
```
</details>


<details>
<summary>📘 13. Calculated Fields, Aliases, and Field Extractions</summary>

```
==============================
13. Calculated Fields, Aliases, and Field Extractions
==============================

Overview:
---------
Splunk lets you create fields dynamically to simplify searches and improve performance.

Calculated Fields:
------------------
- Use eval expressions to define new fields
- Applied at search-time

Field Aliases:
--------------
- Rename fields without changing underlying data
- Example: rename clientip to ip_address

Field Extractions:
------------------
- Use regex or delimiters to define fields
- Created via UI or props.conf

Exam Tips:
----------
📌 Calculated fields use eval.
📌 Field aliases map one field name to another.
📌 Field extractions = making fields from raw logs.
```
</details>


<details>
<summary>📘 14. Splunk Knowledge Objects Summary</summary>

```
==============================
14. Splunk Knowledge Objects Summary
==============================

Overview:
---------
Knowledge Objects are reusable components that enhance Splunk functionality.

Key Objects:
------------
- Event Types
- Tags
- Lookups
- Reports
- Alerts
- Dashboards
- Data Models
- Field Extractions
- Saved Searches

Management:
-----------
- Settings > Knowledge
- Permissions control sharing (Private, App, Global)

Best Practices:
---------------
- Use naming conventions
- Tag and organize for reuse

Exam Tips:
----------
📌 Know which object is used where.
📌 Permissions and ownership impact usage.
📌 All objects are found in Settings > Knowledge.
```
</details>

---

<details>
<summary>📘 15. Combined Exam Tips (All Sections)</summary>

```
==============================
15. Combined Exam Tips (All Sections)
==============================

This section consolidates the most important exam tips scattered across all prior sections and lecture screenshots.

General Exam Tips:
------------------
✅ Understand the architecture – role of Indexer, Search Head, Universal Forwarder  
✅ Know the difference between real-time, scheduled, and historical searches  
✅ Use Time Picker wisely – avoid querying too much data  
✅ SPL is case-sensitive – especially field names  
✅ Syntax errors often stem from missing `|` or incorrect field references  
✅ Save time by knowing when to use Fast, Smart, or Verbose search modes  
✅ Pay attention to default vs. interesting fields in the Fields panel  
✅ Practice regex (`rex`) and JSON field extraction (`spath`)  
✅ Use `eval` to create dynamic fields and `stats` for summary views  
✅ `timechart` always needs `_time` field  
✅ Reports vs Dashboards: Reports are for static outputs, Dashboards are for interactive visualization  
✅ Alerts are scheduled searches with trigger conditions and actions  
✅ Lookup usage is critical – understand `inputlookup`, `lookup`, and `outputlookup`  
✅ Knowledge objects and their permissions (private, app, global) frequently appear in exams  

Pro Tips from Lecture:
----------------------
✅ Pivot allows visualization without writing SPL – good for business users  
✅ Accelerated Datasets enhance dashboard speed – ideal for scheduled panels  
✅ Use calculated fields instead of rewriting SPL every time  
✅ Don’t mix index-time and search-time field logic in same query  
✅ Tags and event types are critical for data model mapping and CIM compliance  
✅ Real-time alerts are costly – prefer scheduled unless justified  
✅ Field aliasing is useful when dealing with multiple sourcetypes  
✅ Use summary indexing to reduce computation for frequent reports/alerts  
✅ Use dropdowns and dynamic filters in dashboards to enhance usability  
✅ Use `dc()` for distinct count and `values()` to list unique items

Suggested Strategy for Exam:
----------------------------
🧠 Memorize SPL syntax and functions: `stats`, `eval`, `dedup`, `chart`, `table`, `sort`, `rename`  
🧪 Practice queries using provided sample logs (e.g., `secure.log`)  
🧩 Use scenario-based logic: Know what search should be used to troubleshoot login issues or network errors  
📊 Practice building dashboards from raw searches  
🗂️ Understand the difference between fields, tags, event types, and calculated fields  

Recommended Practice:
---------------------
- Write at least 50 SPL queries using transforming + filtering commands  
- Create a dashboard with at least 3 panels: timechart, bar, and single-value  
- Configure a scheduled alert with condition >10 failed login attempts in 1h  
- Perform a lookup join with external CSV data  
- Use `rex` to extract usernames from secure.log manually
```
</details>

✅ **Prepared for certification + real-world analyst usage**  
📝 Includes: Search commands, Dashboards, Alerts, Knowledge objects  
