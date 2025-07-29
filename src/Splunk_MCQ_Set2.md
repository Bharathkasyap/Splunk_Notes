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

121. Which SPL function is best to calculate the unique number of users?
```
A. stats dc(user)
B. eval user=distinct()
C. top user
D. count(user)
```
<details><summary> 
**Answer:** </summary>

```
A. stats dc(user) 
```

</details>

122. Which search filters logs between two specific times?
```
A. earliest="07/01/2025:08:00:00" latest="07/01/2025:18:00:00"
B. time=07/01/2025 to 07/02/2025
C. range 08:00-18:00
D. timechart span=10h
```
<details><summary> 
**Answer:** </summary>

```
A. earliest="07/01/2025:08:00:00" latest="07/01/2025:18:00:00" 
```

</details>

123. Which SPL query detects brute force attacks using event count threshold?
```
A. index=linux_logs "Failed password" | stats count by user, src_ip | where count>10
B. index=brute_force | fillnull | dedup user
C. index=logs | stats by attack
D. index=linux | top failed_login
```
<details><summary> 
**Answer:** </summary>

```
A. index=linux_logs "Failed password" | stats count by user, src_ip | where count>10 
```

</details>

124. Which SPL would best chart average response time per API endpoint?
```
A. timechart avg(response_time) by endpoint
B. chart avg(endpoint) by time
C. stats sum(endpoint) by response_time
D. eval avg(endpoint)
```
<details><summary> 
**Answer:** </summary>

```
A. timechart avg(response_time) by endpoint 
```

</details>

125. How do you rename the field `clientip` to `ip_address`?
```
A. rename clientip AS ip_address
B. table clientip AS ip_address
C. eval ip_address=clientip
D. rex rename ip
```
<details><summary> 
**Answer:** </summary>

```
A. rename clientip AS ip_address 
```

</details>

126. Which command compares values in one search to another using common field?
```
A. join
B. lookup
C. appendcols
D. fillnull
```
<details><summary> 
**Answer:** </summary>

```
A. join 
```

</details>

127. Which SPL creates a column view of host, status, and count?
```
A. stats count by host, status
B. table host status count
C. top host, status
D. fields host status count
```
<details><summary> 
**Answer:** </summary>

```
B. table host status count 
```

</details>

128. What does `sort - count` do in a Splunk query?
```
A. Sorts in ascending order
B. Sorts by count descending
C. Sorts by time
D. Sorts by field name
```
<details><summary> 
**Answer:** </summary>

```
B. Sorts by count descending 
```

</details>

129. Which command enriches events with IP location from lookup?
```
A. lookup ip2geo ip OUTPUT city, country
B. inputlookup ip2geo.csv
C. rex field=ip
D. outputlookup
```
<details><summary> 
**Answer:** </summary>

```
A. lookup ip2geo ip OUTPUT city, country 
```

</details>

130. How would you extract port number from logs like 'port 22'?
```
A. rex "port (?<port>\d+)"
B. eval port=extract(port)
C. table port
D. spath port=field
```
<details><summary> 
**Answer:** </summary>

```
A. rex "port (?<port>\d+)" 
```

</details>

131. How to restrict search to logs only from a host called `webserver1`?
```
A. host=webserver1
B. source=webserver1
C. server=webserver1
D. hostname=webserver1
```
<details><summary> 
**Answer:** </summary>

```
A. host=webserver1 
```

</details>

132. What is the default format of _time field?
```
A. Epoch timestamp
B. ISO 8601
C. MM/DD/YYYY
D. Text
```
<details><summary> 
**Answer:** </summary>

```
A. Epoch timestamp 
```

</details>

133. Which SPL command formats results into a clean table layout?
```
A. table
B. fields
C. eval
D. sort
```
<details><summary> 
**Answer:** </summary>

```
A. table 
```

</details>

134. How can you find the error codes that appear most frequently?
```
A. top error_code
B. stats by error_code
C. eval error=count
D. join error_code
```
<details><summary> 
**Answer:** </summary>

```
A. top error_code 
```

</details>

135. What will this SPL do: `stats dc(user) by src_ip`?
```
A. Show number of distinct users per IP
B. Sort IPs
C. Dedup logs
D. Track errors
```
<details><summary> 
**Answer:** </summary>

```
A. Show number of distinct users per IP 
```

</details>

136. Which visualization is best for showing categorical data split by time?
```
A. Timechart
B. Pie Chart
C. Bar Chart
D. Single Value
```
<details><summary> 
**Answer:** </summary>

```
A. Timechart 
```

</details>

137. What is the best way to group events that share the same session id?
```
A. transaction session_id
B. eval session
C. rex field=session
D. dedup session_id
```
<details><summary> 
**Answer:** </summary>

```
A. transaction session_id 
```

</details>

138. Which command shows event count by host and limits result to top 3?
```
A. top limit=3 host
B. sort -count | head 3
C. dedup host | head 3
D. table host | top 3
```
<details><summary> 
**Answer:** </summary>

```
A. top limit=3 host 
```

</details>

139. What does `eval temp=celsius*9/5+32` do?
```
A. Converts Celsius to Fahrenheit
B. Converts time zone
C. Converts temperature to Kelvin
D. Extracts temp field
```
<details><summary> 
**Answer:** </summary>

```
A. Converts Celsius to Fahrenheit 
```

</details>

140. Which SPL gives you events without certain fields?
```
A. fields - unwanted_field
B. dedup fields
C. eval !field
D. table !field
```
<details><summary> 
**Answer:** </summary>

```
A. fields - unwanted_field 
```

</details>
