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

41. Which command is best for evaluating conditional values in a field?
```
A. eval
B. stats
C. dedup
D. rex
```
<details><summary> 
**Answer:** </summary>

```
A. eval 
```

</details>

42. Which visualization displays a breakdown of categories as slices?
```
A. Bar Chart
B. Line Chart
C. Pie Chart
D. Single Value
```
<details><summary> 
**Answer:** </summary>

```
C. Pie Chart 
```

</details>

43. What is the correct SPL command to limit the search to last 24 hours?
```
A. latest=-24h
B. earliest=-24h
C. time=24h
D. set_time=24h
```
<details><summary> 
**Answer:** </summary>

```
B. earliest=-24h 
```

</details>

44. Which field stores the source file path of an event?
```
A. host
B. source
C. sourcetype
D. _raw
```
<details><summary> 
**Answer:** </summary>

```
B. source 
```

</details>

45. Which field tells you what format the data is in?
```
A. sourcetype
B. source
C. host
D. index
```
<details><summary> 
**Answer:** </summary>

```
A. sourcetype 
```

</details>

46. What type of search is triggered as soon as the condition is met?
```
A. Scheduled Search
B. Real-time Alert
C. Historical Alert
D. Conditional Lookup
```
<details><summary> 
**Answer:** </summary>

```
B. Real-time Alert 
```

</details>

47. Which function is used to list distinct field values?
```
A. sum()
B. dc()
C. avg()
D. values()
```
<details><summary> 
**Answer:** </summary>

```
D. values() 
```

</details>

48. Which object helps group similar events under a single name?
```
A. Alert
B. Report
C. Event Type
D. Tag
```
<details><summary> 
**Answer:** </summary>

```
C. Event Type 
```

</details>

49. What is the use of `fillnull` command?
```
A. Deletes NULLs
B. Fills NULL fields with default
C. Creates NULL fields
D. Sorts missing values
```
<details><summary> 
**Answer:** </summary>

```
B. Fills NULL fields with default 
```

</details>

50. Which Splunk component forwards data to the indexer?
```
A. Deployment Server
B. Universal Forwarder
C. Search Head
D. Heavy Forwarder
```
<details><summary> 
**Answer:** </summary>

```
B. Universal Forwarder 
```

</details>

51. Which command helps visualize data over time with different field values?
```
A. table
B. timechart
C. dedup
D. rex
```
<details><summary> 
**Answer:** </summary>

```
B. timechart 
```

</details>

52. Which lookup command is used to update or add to a CSV file?
```
A. lookup
B. inputlookup
C. outputlookup
D. dc()
```
<details><summary> 
**Answer:** </summary>

```
C. outputlookup 
```

</details>

53. What is the difference between `stats` and `chart`?
```
A. chart requires over/by and stats doesn’t
B. stats is only for tables
C. chart supports rex
D. stats needs JSON
```
<details><summary> 
**Answer:** </summary>

```
A. chart requires over/by and stats doesn’t 
```

</details>

54. Which field indicates which machine generated the log?
```
A. source
B. host
C. index
D. type
```
<details><summary> 
**Answer:** </summary>

```
B. host 
```

</details>

55. Which command would you use to hide certain fields from output?
```
A. fields -
B. remove
C. table
D. dedup
```
<details><summary> 
**Answer:** </summary>

```
A. fields - 
```

</details>

56. Which mode should you use to find new fields during log exploration?
```
A. Fast
B. Smart
C. Verbose
D. Minimal
```
<details><summary> 
**Answer:** </summary>

```
C. Verbose 
```

</details>

57. Which object is best used for scheduled emailing of search results?
```
A. Report
B. Dashboard
C. Transaction
D. Join
```
<details><summary> 
**Answer:** </summary>

```
A. Report 
```

</details>

58. How do you limit results to only 5 rows per unique user?
```
A. dedup 5 user
B. table user | head 5
C. sort user | head 5
D. dedup user
```
<details><summary> 
**Answer:** </summary>

```
A. dedup 5 user 
```

</details>

59. Which command allows conditional transformation of data?
```
A. case
B. stats
C. rex
D. search
```
<details><summary> 
**Answer:** </summary>

```
A. case 
```

</details>

60. What action does the `table` command perform?
```
A. Removes NULLs
B. Filters fields
C. Displays selected fields in column format
D. Creates time bins
```
<details><summary> 
**Answer:** </summary>

```
C. Displays selected fields in column format 
```

</details>
61. What does the `dc()` function do in Splunk?
```
A. Deletes content
B. Displays count
C. Distinct count of values
D. Draw chart
```
<details><summary> 
**Answer:** </summary>

```
C. Distinct count of values 
```

</details>

62. Which command removes duplicate events based on a field?
```
A. sort
B. dedup
C. filter
D. top
```
<details><summary> 
**Answer:** </summary>

```
B. dedup 
```

</details>

63. What is a key difference between reports and alerts?
```
A. Alerts support visualization
B. Reports are interactive
C. Alerts can be triggered
D. Reports can only be emailed
```
<details><summary> 
**Answer:** </summary>

```
C. Alerts can be triggered 
```

</details>

64. How is a Splunk 'tag' typically used?
```
A. Join datasets
B. Label field values
C. Create alerts
D. Configure indexes
```
<details><summary> 
**Answer:** </summary>

```
B. Label field values 
```

</details>

65. Which search mode balances performance and field discovery?
```
A. Fast
B. Smart
C. Verbose
D. Extended
```
<details><summary> 
**Answer:** </summary>

```
B. Smart 
```

</details>

66. Which function returns the total of a numeric field?
```
A. dc()
B. avg()
C. sum()
D. eval()
```
<details><summary> 
**Answer:** </summary>

```
C. sum() 
```

</details>

67. What is the result of the `sort - _time` command?
```
A. Random sort
B. Ascending by time
C. Descending by time
D. Oldest events first
```
<details><summary> 
**Answer:** </summary>

```
C. Descending by time 
```

</details>

68. Which UI element shows extracted fields in search results?
```
A. Time Picker
B. Fields Sidebar
C. Report Builder
D. Event Viewer
```
<details><summary> 
**Answer:** </summary>

```
B. Fields Sidebar 
```

</details>

69. Which command is used to match field values to a CSV?
```
A. outputlookup
B. rex
C. lookup
D. join
```
<details><summary> 
**Answer:** </summary>

```
C. lookup 
```

</details>

70. What is required for the `timechart` command to work?
```
A. Field alias
B. Indexed field
C. Field `_time`
D. JSON log
```
<details><summary> 
**Answer:** </summary>

```
C. Field `_time` 
```

</details>

71. What is the function of the `append` command?
```
A. Rename fields
B. Remove NULLs
C. Combine search results
D. Add rows to lookup
```
<details><summary> 
**Answer:** </summary>

```
C. Combine search results 
```

</details>

72. Which command is used to create new fields?
```
A. dedup
B. rex
C. eval
D. join
```
<details><summary> 
**Answer:** </summary>

```
C. eval 
```

</details>

73. Which search command lets you discover top N values for a field?
```
A. sort
B. table
C. top
D. eval
```
<details><summary> 
**Answer:** </summary>

```
C. top 
```

</details>

74. How do you view the raw logs in Splunk UI?
```
A. Chart view
B. Events tab
C. Dashboard panel
D. Report tab
```
<details><summary> 
**Answer:** </summary>

```
B. Events tab 
```

</details>

75. Which field tells Splunk what type of data it is processing?
```
A. source
B. host
C. sourcetype
D. index
```
<details><summary> 
**Answer:** </summary>

```
C. sourcetype 
```

</details>

76. How are permissions managed for Knowledge Objects?
```
A. Via Linux OS
B. Settings > Permissions
C. Stored in alert.conf
D. Cannot be set
```
<details><summary> 
**Answer:** </summary>

```
B. Settings > Permissions 
```

</details>

77. Which feature enriches logs with external location data?
```
A. Transaction
B. Lookup
C. Stats
D. Event Type
```
<details><summary> 
**Answer:** </summary>

```
B. Lookup 
```

</details>

78. Which eval function provides multiple conditional checks?
```
A. if()
B. case()
C. switch()
D. cond()
```
<details><summary> 
**Answer:** </summary>

```
B. case() 
```

</details>

79. What is the default index if none is specified?
```
A. system
B. main
C. default
D. audit
```
<details><summary> 
**Answer:** </summary>

```
B. main 
```

</details>

80. Which command would you use to format results into column display?
```
A. fields
B. table
C. top
D. eval
```
<details><summary> 
**Answer:** </summary>

```
B. table 
```

</details>

