1. What is the purpose of the 'index' keyword in a Splunk search?
```
A. Specifies the type of visualization to use
B. Filters data by source type
C. Identifies the data repository to search in
D. Assigns events to fields
```
<details><summary> 
**Answer:** </summary>

```
C. Identifies the data repository to search in 
```

</details>

2. Which Splunk component is responsible for parsing and indexing data?
```
A. Universal Forwarder
B. Deployment Server
C. Indexer
D. Search Head
```
<details><summary> 
**Answer:** </summary>

```
C. Indexer 
```

</details>

3. Which command is used to group events that start with 'login' and end with 'logout'?
```
A. join
B. transaction
C. stats
D. eval
```
<details><summary> 
**Answer:** </summary>

```
B. transaction 
```

</details>

4. Which command aggregates data such as count, avg, min, and max?
```
A. eval
B. where
C. stats
D. rex
```
<details><summary> 
**Answer:** </summary>

```
C. stats 
```

</details>

5. Which command is required to create a time-based trend in Splunk?
```
A. table
B. chart
C. timechart
D. fillnull
```
<details><summary> 
**Answer:** </summary>

```
C. timechart 
```

</details>

6. What command is used to extract fields using regular expressions?
```
A. spath
B. rex
C. eval
D. top
```
<details><summary> 
**Answer:** </summary>

```
B. rex 
```

</details>

7. Which command should be used to remove duplicates based on a field?
```
A. sort
B. dedup
C. table
D. rename
```
<details><summary> 
**Answer:** </summary>

```
B. dedup 
```

</details>

8. Which visualization is best for displaying percentage-based breakdowns?
```
A. Line chart
B. Pie chart
C. Single value
D. Timechart
```
<details><summary> 
**Answer:** </summary>

```
B. Pie chart 
```

</details>

9. What type of field is 'sourcetype' in Splunk?
```
A. Search-time Field
B. Event Type
C. Indexed Field
D. Calculated Field
```
<details><summary> 
**Answer:** </summary>

```
C. Indexed Field 
```

</details>

10. Which search mode discovers the most fields but is slowest?
```
A. Fast
B. Smart
C. Verbose
D. Custom
```
<details><summary> 
**Answer:** </summary>

```
C. Verbose 
```

</details>

11. Which Splunk feature lets you enrich events using a CSV file?
```
A. Tags
B. Lookup
C. Transaction
D. Rex
```
<details><summary> 
**Answer:** </summary>

```
B. Lookup 
```

</details>

12. Which Splunk role allows you to run searches but not create alerts or reports?
```
A. Power
B. Admin
C. User
D. Viewer
```
<details><summary> 
**Answer:** </summary>

```
C. User 
```

</details>

13. Which function shows unique values in a field?
```
A. dc()
B. sum()
C. values()
D. avg()
```
<details><summary> 
**Answer:** </summary>

```
C. values() 
```

</details>

14. Which command is used to read data from a lookup file?
```
A. inputlookup
B. lookup
C. outputlookup
D. eval
```
<details><summary> 
**Answer:** </summary>

```
A. inputlookup 
```

</details>

15. What does the 'eval' command do?
```
A. Performs statistical analysis
B. Filters events
C. Creates or modifies fields
D. Joins two datasets
```
<details><summary> 
**Answer:** </summary>

```
C. Creates or modifies fields 
```

</details>

16. Which command outputs a clean table of selected fields?
```
A. table
B. stats
C. sort
D. fields
```
<details><summary> 
**Answer:** </summary>

```
A. table 
```

</details>

17. What is the default number of events shown per page in Splunk Web?
```
A. 10
B. 20
C. 100
D. 50
```
<details><summary> 
**Answer:** </summary>

```
C. 100 
```

</details>

18. Which component handles user dashboards and visualizations?
```
A. Indexer
B. Search Head
C. Deployment Server
D. Universal Forwarder
```
<details><summary> 
**Answer:** </summary>

```
B. Search Head 
```

</details>

19. What is the main benefit of using 'timechart' over 'stats'?
```
A. More rows
B. Better color options
C. Time-series output
D. Faster results
```
<details><summary> 
**Answer:** </summary>

```
C. Time-series output 
```

</details>

20. Which command is useful for joining two datasets in Splunk?
```
A. append
B. transaction
C. join
D. eval
```
<details><summary> 
**Answer:** </summary>

```
C. join 
```

</details>

21. Which function returns the number of unique values in a field?
```
A. sum()
B. values()
C. dc()
D. count()
```
<details><summary> 
**Answer:** </summary>

```
C. dc() 
```

</details>

22. What command would you use to rename a field in results?
```
A. eval
B. rename
C. table
D. rex
```
<details><summary> 
**Answer:** </summary>

```
B. rename 
```

</details>

23. Which Splunk command helps read JSON logs and extract nested fields?
```
A. spath
B. rex
C. eval
D. fields
```
<details><summary> 
**Answer:** </summary>

```
A. spath 
```

</details>

24. How do you create a new field based on conditional logic?
```
A. eval
B. table
C. dedup
D. sort
```
<details><summary> 
**Answer:** </summary>

```
A. eval 
```

</details>

25. Which of the following is a knowledge object in Splunk?
```
A. transaction
B. field
C. event type
D. rex
```
<details><summary> 
**Answer:** </summary>

```
C. event type 
```

</details>

26. Which mode discovers all fields but is slowest?
```
A. Fast
B. Smart
C. Verbose
D. None
```
<details><summary> 
**Answer:** </summary>

```
C. Verbose 
```

</details>

27. Which command writes search results to a lookup file?
```
A. outputlookup
B. inputlookup
C. lookup
D. eval
```
<details><summary> 
**Answer:** </summary>

```
A. outputlookup 
```

</details>

28. What does the 'rex' command require to extract fields?
```
A. JSON path
B. Regex pattern
C. Stats function
D. Lookup table
```
<details><summary> 
**Answer:** </summary>

```
B. Regex pattern 
```

</details>

29. Which of the following can be scheduled?
```
A. Dashboard
B. Saved Search
C. Report
D. Alert
```
<details><summary> 
**Answer:** </summary>

```
C. Report 
```

</details>

30. What role does the Deployment Server play?
```
A. Stores dashboards
B. Distributes configurations
C. Parses logs
D. Performs indexing
```
<details><summary> 
**Answer:** </summary>

```
B. Distributes configurations 
```

</details>

31. What is the default field that represents time in Splunk?
```
A. timestamp
B. log_time
C. _time
D. event_time
```
<details><summary> 
**Answer:** </summary>

```
C. _time 
```

</details>

32. Which function would calculate average bytes transferred?
```
A. avg(bytes)
B. count(bytes)
C. sum(bytes)
D. dc(bytes)
```
<details><summary> 
**Answer:** </summary>

```
A. avg(bytes) 
```

</details>

33. What type of chart is best for showing time-based trends?
```
A. Pie Chart
B. Timechart
C. Bar Chart
D. Single Value
```
<details><summary> 
**Answer:** </summary>

```
B. Timechart 
```

</details>

34. Which command combines results from two different searches?
```
A. append
B. eval
C. join
D. stats
```
<details><summary> 
**Answer:** </summary>

```
A. append 
```

</details>

35. In Splunk, what is a 'sourcetype'?
```
A. A field extraction
B. Data format identifier
C. Index name
D. Search role
```
<details><summary> 
**Answer:** </summary>

```
B. Data format identifier 
```

</details>

36. Which component allows users to create alerts and dashboards?
```
A. Indexer
B. Search Head
C. Universal Forwarder
D. Deployment Server
```
<details><summary> 
**Answer:** </summary>

```
B. Search Head 
```

</details>

37. Which command would remove duplicate usernames?
```
A. dedup user
B. sort user
C. fields user
D. table user
```
<details><summary> 
**Answer:** </summary>

```
A. dedup user 
```

</details>

38. What visualization is best for showing overall status at a glance?
```
A. Pie Chart
B. Single Value
C. Bar Chart
D. Scatter Plot
```
<details><summary> 
**Answer:** </summary>

```
B. Single Value 
```

</details>

39. What does the 'inputlookup' command do?
```
A. Fetches logs from files
B. Displays field names
C. Reads data from lookup file
D. Exports logs to CSV
```
<details><summary> 
**Answer:** </summary>

```
C. Reads data from lookup file 
```

</details>

40. Which type of field is created during indexing?
```
A. Calculated Field
B. Search-time Field
C. Indexed Field
D. Tag
```
<details><summary> 
**Answer:** </summary>

```
C. Indexed Field 
```

</details>

