# Practice Questions_ Set 2:
101. What does the `transaction` command do?
```
A. Groups a set of transactions based on time.
B. Creates a single event from a group of events.
C. Separates two events based on one or more values.
D. Returns the number of credit card transactions found in the event logs.
```
<details><summary> 
**Answer:** </summary>

```
B. Creates a single event from a group of events. 
```

</details>

102. Which SPL query generates a line chart comparing success vs skipped over time?
```
A. index=_internal sourcetype=SavedSplunker | fields sourcetype, status | transaction status maxspan=1d | stats count by status
B. index=_internal sourcetype=SavedSplunker | fields sourcetype, status | transaction status maxspan=1d | chart count OVER status by _time
C. index=_internal sourcetype=SavedSplunker | fields sourcetype, status | transaction status maxspan=1d | timechart count by status
D. None of these searches would generate a similar graph.
```
<details><summary> 
**Answer:** </summary>

```
C. index=_internal sourcetype=SavedSplunker | fields sourcetype, status | transaction status maxspan=1d | timechart count by status 
```

</details>

103. Which SPL command would you use to extract the domain from email addresses?
```
A. rex field=email "(?<domain>@.*)"
B. eval domain=replace(email, ".*@", "")
C. eval domain=split(email, "@")[1]
D. All of the above
```
<details><summary> 
**Answer:** </summary>

```
D. All of the above 
```

</details>

104. Which of the following is required when using `chart` with two fields?
```
A. OVER and BY clauses
B. BY clause only
C. index field defined
D. Search-time field extractions enabled
```
<details><summary> 
**Answer:** </summary>

```
A. OVER and BY clauses 
```

</details>

105. Which SPL command helps you count failed SSH logins from a secure log?
```
A. index=linux sourcetype=secure.log "Failed password" | stats count by user
B. index=secure_logs "success" | table user
C. index=ssh_logs "Password accepted" | dedup user
D. index=linux_logs "login failed" | rename user AS attacker
```
<details><summary> 
**Answer:** </summary>

```
A. index=linux sourcetype=secure.log "Failed password" | stats count by user 
```

</details>

106. Which SPL query returns the top 5 IP addresses by failed login attempts?
```
A. index=linux sourcetype=secure.log "Failed password" | top limit=5 src_ip
B. index=linux sourcetype=secure.log "Failed password" | stats count by user | head 5
C. index=linux_logs "Failed password" | dedup src_ip
D. index=secure.log | table ip | sort
```
<details><summary> 
**Answer:** </summary>

```
A. index=linux sourcetype=secure.log "Failed password" | top limit=5 src_ip 
```

</details>

107. What is the output of `eval flag=if(status>=400, "error", "ok")`?
```
A. Labels events as 'ok' or 'error' based on status code
B. Drops events below status 400
C. Creates a new sourcetype
D. Flags events for alerting only
```
<details><summary> 
**Answer:** </summary>

```
A. Labels events as 'ok' or 'error' based on status code 
```

</details>

108. How does `stats count by src_ip` differ from `top src_ip`?
```
A. Top adds count & percent by default
B. Stats is sorted by host field
C. Top ignores duplicates
D. They are identical
```
<details><summary> 
**Answer:** </summary>

```
A. Top adds count & percent by default 
```

</details>

109. Which query extracts usernames from failed SSH logs?
```
A. rex "Failed password for (?<user>\w+)"
B. eval user=lowercase(user)
C. table user
D. search user=*
```
<details><summary> 
**Answer:** </summary>

```
A. rex "Failed password for (?<user>\w+)" 
```

</details>

110. Which SPL query groups events by session based on user and time?
```
A. transaction user maxpause=30s
B. stats count by user
C. timechart span=5m count by user
D. join type=inner user
```
<details><summary> 
**Answer:** </summary>

```
A. transaction user maxpause=30s 
```

</details>

111. Which command is ideal for investigating multi-step transactions like checkout?
```
A. transaction
B. stats
C. append
D. table
```
<details><summary> 
**Answer:** </summary>

```
A. transaction 
```

</details>

112. Which SPL correctly identifies the most accessed URLs?
```
A. index=web | stats count by url | sort -count
B. index=web | top limit=5 url
C. index=web | table url
D. index=web | dedup url
```
<details><summary> 
**Answer:** </summary>

```
B. index=web | top limit=5 url 
```

</details>

113. Which SPL transforms a JSON payload field into extracted fields?
```
A. spath input=payload
B. rex field=_raw
C. eval json=parse(payload)
D. top field=payload
```
<details><summary> 
**Answer:** </summary>

```
A. spath input=payload 
```

</details>

114. In which scenario would `join` be preferred over `lookup`?
```
A. To combine two real-time search datasets
B. To enrich logs from static CSV
C. To fill nulls in fields
D. To normalize field names
```
<details><summary> 
**Answer:** </summary>

```
A. To combine two real-time search datasets 
```

</details>

115. Which command renames a field from `src_ip` to `attacker_ip`?
```
A. rename src_ip AS attacker_ip
B. eval attacker_ip=src_ip
C. fields attacker_ip
D. table src_ip AS attacker_ip
```
<details><summary> 
**Answer:** </summary>

```
A. rename src_ip AS attacker_ip 
```

</details>

116. How would you calculate total bytes transferred per host?
```
A. stats sum(bytes) by host
B. chart total(bytes) by host
C. eval bytes=total | stats count
D. top bytes host
```
<details><summary> 
**Answer:** </summary>

```
A. stats sum(bytes) by host 
```

</details>

117. Which SPL alerts you when login attempts exceed 20 from one IP?
```
A. stats count by src_ip | where count > 20
B. dedup src_ip > 20
C. lookup src_ip | alert if > 20
D. timechart by ip count
```
<details><summary> 
**Answer:** </summary>

```
A. stats count by src_ip | where count > 20 
```

</details>

118. What is the SPL to visualize user login activity hourly?
```
A. timechart span=1h count by user
B. chart user over 1h
C. stats by user hourly
D. transaction span=1h by user
```
<details><summary> 
**Answer:** </summary>

```
A. timechart span=1h count by user 
```

</details>

119. Which SPL counts HTTP status codes and shows trend over time?
```
A. timechart count by status
B. stats count by status
C. top status
D. eval count=status
```
<details><summary> 
**Answer:** </summary>

```
A. timechart count by status 
```

</details>

120. Which SPL lists top 3 errors in a log?
```
A. search error | top limit=3 _raw
B. search error | stats count by _raw
C. search error | dedup _raw | head 3
D. search error | table _raw
```
<details><summary> 
**Answer:** </summary>

```
A. search error | top limit=3 _raw 
```

</details>
