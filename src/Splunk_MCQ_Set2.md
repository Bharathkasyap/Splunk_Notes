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

141. Which SPL filters out events where the status field is 200?
```
A. search status!=200
B. eval status!=200
C. stats by status=200
D. where status!=200
```
<details><summary> 
**Answer:** </summary>

```
A. search status!=200 
```

</details>

142. What is the function of the `fillnull` command?
```
A. Replaces NULL values with default
B. Deletes NULL rows
C. Fills missing source values
D. Creates field aliases
```
<details><summary> 
**Answer:** </summary>

```
A. Replaces NULL values with default 
```

</details>

143. Which SPL generates a single row per user showing total and distinct IPs?
```
A. stats count, dc(src_ip) by user
B. table user, src_ip
C. top user by src_ip
D. dedup user
```
<details><summary> 
**Answer:** </summary>

```
A. stats count, dc(src_ip) by user 
```

</details>

144. What would `dedup user` do in a result set?
```
A. Keep first occurrence of each user
B. Remove all duplicate logs
C. Sort by user
D. Filter errors
```
<details><summary> 
**Answer:** </summary>

```
A. Keep first occurrence of each user 
```

</details>

145. How to rename a field inline while keeping both old and new names?
```
A. eval newfield=oldfield
B. rename oldfield AS newfield
C. fields oldfield, newfield
D. alias oldfield AS newfield
```
<details><summary> 
**Answer:** </summary>

```
A. eval newfield=oldfield 
```

</details>

146. Which SPL query would best identify the first login attempt per user?
```
A. sort _time | dedup user
B. stats by user
C. transaction first login
D. eval user_login
```
<details><summary> 
**Answer:** </summary>

```
A. sort _time | dedup user 
```

</details>

147. What does `stats count(eval(status=404)) AS not_found` return?
```
A. Number of 404s as 'not_found'
B. List of users
C. Table with status field
D. Percentage of failures
```
<details><summary> 
**Answer:** </summary>

```
A. Number of 404s as 'not_found' 
```

</details>

148. Which command helps to extract nested values from JSON logs?
```
A. spath
B. rex
C. join
D. table
```
<details><summary> 
**Answer:** </summary>

```
A. spath 
```

</details>

149. What does `rex field=_raw "user=(?<username>\w+)"` do?
```
A. Extract username field from raw logs
B. Remove raw events
C. Filter only usernames
D. Add field to lookup
```
<details><summary> 
**Answer:** </summary>

```
A. Extract username field from raw logs 
```

</details>

150. Which SPL returns number of events per host per day?
```
A. timechart span=1d count by host
B. chart count by host per day
C. stats by host | bin _time
D. top host | daily
```
<details><summary> 
**Answer:** </summary>

```
A. timechart span=1d count by host 
```

</details>

151. Which command can be used to create custom conditions like status range?
```
A. eval
B. where
C. sort
D. fillnull
```
<details><summary> 
**Answer:** </summary>

```
A. eval 
```

</details>

152. What is the effect of `search login error | top user`?
```
A. Shows top users with login error
B. Sorts by login
C. Filters only successful logins
D. Duplicates removed
```
<details><summary> 
**Answer:** </summary>

```
A. Shows top users with login error 
```

</details>

153. What is the main benefit of using `transaction` over `stats`?
```
A. Keeps raw events together as a group
B. Faster search time
C. More chart options
D. Used only for dashboards
```
<details><summary> 
**Answer:** </summary>

```
A. Keeps raw events together as a group 
```

</details>

154. Which of the following identifies login attempts within 60 seconds per user?
```
A. transaction user maxspan=60s
B. stats by user | span=60s
C. join type=user within 60s
D. chart user time
```
<details><summary> 
**Answer:** </summary>

```
A. transaction user maxspan=60s 
```

</details>

155. Which SPL provides count, average and distinct values in one table?
```
A. stats count avg(duration) dc(user)
B. table count avg dc
C. eval duration=avg | count
D. top duration user
```
<details><summary> 
**Answer:** </summary>

```
A. stats count avg(duration) dc(user) 
```

</details>

156. What’s the best way to visualize percentage of status codes?
```
A. stats count by status | eventstats sum(count) AS total | eval percent=(count/total)*100
B. top status
C. chart status by percent
D. lookup percent status
```
<details><summary> 
**Answer:** </summary>

```
A. stats count by status | eventstats sum(count) AS total | eval percent=(count/total)*100 
```

</details>

157. Which visualization best shows traffic distribution across categories?
```
A. Pie Chart
B. Line Chart
C. Single Value
D. Gauge
```
<details><summary> 
**Answer:** </summary>

```
A. Pie Chart 
```

</details>

158. Which SPL is most useful when tracking logins by user per hour?
```
A. timechart span=1h count by user
B. top user by hour
C. eval span=1h
D. stats by hour
```
<details><summary> 
**Answer:** </summary>

```
A. timechart span=1h count by user 
```

</details>

159. How to extract the domain from email addresses like 'admin@example.com'?
```
A. rex field=email "@(?<domain>.*)"
B. eval domain=replace(email,".*@","")
C. eval domain=split(email,"@")[1]
D. All of the above
```
<details><summary> 
**Answer:** </summary>

```
D. All of the above 
```

</details>

160. What happens if you omit `by _time` in timechart?
```
A. Search fails
B. Defaults to automatic time bucketing
C. Returns raw logs
D. Groups by host
```
<details><summary> 
**Answer:** </summary>

```
B. Defaults to automatic time bucketing 
```

</details>

161. What does the `eventstats` command do?
```
A. Adds aggregated data to each event
B. Deletes duplicate logs
C. Generates pie charts
D. Filters fields
```
<details><summary> 
**Answer:** </summary>

```
A. Adds aggregated data to each event 
```

</details>

162. Which SPL extracts and counts failed SSH login attempts by IP?
```
A. index=linux_logs "Failed password" | stats count by src_ip
B. search ssh error | stats by ip
C. eval login=fail | table ip
D. index=ssh_logs | dedup ip
```
<details><summary> 
**Answer:** </summary>

```
A. index=linux_logs "Failed password" | stats count by src_ip 
```

</details>

163. Which SPL query detects repeated errors by host?
```
A. index=errors | stats count by host | where count>5
B. index=errors | dedup host
C. search host error
D. stats error count
```
<details><summary> 
**Answer:** </summary>

```
A. index=errors | stats count by host | where count>5 
```

</details>

164. How do you search for events that do NOT contain the word 'success'?
```
A. search NOT success
B. search != success
C. where success=false
D. search success=0
```
<details><summary> 
**Answer:** </summary>

```
A. search NOT success 
```

</details>

165. Which SPL command combines all events into one per user session?
```
A. transaction user
B. dedup user
C. top user
D. append user
```
<details><summary> 
**Answer:** </summary>

```
A. transaction user 
```

</details>

166. Which SPL query extracts field `user` and groups by day of week?
```
A. eval day=strftime(_time,"%A") | stats count by day, user
B. eval day=dayofweek() | stats user
C. rex _time user day
D. timechart span=1d user
```
<details><summary> 
**Answer:** </summary>

```
A. eval day=strftime(_time,"%A") | stats count by day, user 
```

</details>

167. Which SPL query counts events over 10 minutes per host?
```
A. timechart span=10m count by host
B. chart host per 10min
C. stats count by host every 10m
D. eventstats 10m host
```
<details><summary> 
**Answer:** </summary>

```
A. timechart span=10m count by host 
```

</details>

168. Which SPL visualizes failed logins per source IP over 6 hours?
```
A. index=linux_logs "Failed password" | timechart span=6h count by src_ip
B. index=linux_logs | chart src_ip over 6h
C. stats by user 6h
D. timechart count by host
```
<details><summary> 
**Answer:** </summary>

```
A. index=linux_logs "Failed password" | timechart span=6h count by src_ip 
```

</details>

169. What is the purpose of `search source=*secure.log*`?
```
A. Filters logs from secure.log
B. Renames logs
C. Deletes secure logs
D. Creates index
```
<details><summary> 
**Answer:** </summary>

```
A. Filters logs from secure.log 
```

</details>

170. What will `stats values(status) by user` produce?
```
A. List of all status values per user
B. Counts status
C. Top 5 users
D. Deduplicates status
```
<details><summary> 
**Answer:** </summary>

```
A. List of all status values per user 
```

</details>

171. What is the effect of `chart avg(bytes) over user by _time`?
```
A. Plots average bytes per user over time
B. Summarizes bytes
C. Deduplicates users
D. Counts events
```
<details><summary> 
**Answer:** </summary>

```
A. Plots average bytes per user over time 
```

</details>

172. Which command is used to create a field from part of another field?
```
A. eval
B. rex
C. table
D. stats
```
<details><summary> 
**Answer:** </summary>

```
A. eval 
```

</details>

173. Which SPL returns all HTTP 500 errors grouped by URL?
```
A. search status=500 | stats count by url
B. stats by url
C. eval status=500 | table url
D. index=web | dedup url
```
<details><summary> 
**Answer:** </summary>

```
A. search status=500 | stats count by url 
```

</details>

174. Which SPL command helps remove specific fields from result?
```
A. fields - fieldname
B. eval field=null
C. dedup field
D. sort -field
```
<details><summary> 
**Answer:** </summary>

```
A. fields - fieldname 
```

</details>

175. How to convert `_time` to human-readable format?
```
A. eval readable_time=strftime(_time,"%Y-%m-%d %H:%M:%S")
B. table _time as readable
C. eval _time=convert()
D. convert _time to text
```
<details><summary> 
**Answer:** </summary>

```
A. eval readable_time=strftime(_time,"%Y-%m-%d %H:%M:%S") 
```

</details>

176. How to get the maximum `duration` by host?
```
A. stats max(duration) by host
B. chart duration host
C. table host duration
D. eval duration=max
```
<details><summary> 
**Answer:** </summary>

```
A. stats max(duration) by host 
```

</details>

177. Which SPL command returns a list of distinct users?
```
A. stats dc(user)
B. table user
C. top user
D. values(user)
```
<details><summary> 
**Answer:** </summary>

```
D. values(user) 
```

</details>

178. How to view field names available in events?
```
A. fields
B. table
C. rex
D. list
```
<details><summary> 
**Answer:** </summary>

```
A. fields 
```

</details>

179. Which visualization best shows user activity count grouped by department?
```
A. Bar Chart
B. Pie Chart
C. Line Chart
D. Single Value
```
<details><summary> 
**Answer:** </summary>

```
A. Bar Chart 
```

</details>

180. Which SPL query summarizes login attempts per hour, per user?
```
A. timechart span=1h count by user
B. chart login user per hour
C. stats user hourly
D. dedup user by hour
```
<details><summary> 
**Answer:** </summary>

```
A. timechart span=1h count by user 
```

</details>

181. What does `table` command do in SPL?
```
A. Displays fields in tabular format
B. Aggregates data
C. Generates charts
D. Deletes nulls
```
<details><summary> 
**Answer:** </summary>

```
A. Displays fields in tabular format 
```

</details>

182. How do you show both total and distinct user counts?
```
A. stats count, dc(user)
B. table user count
C. dedup user | stats count
D. top user
```
<details><summary> 
**Answer:** </summary>

```
A. stats count, dc(user) 
```

</details>

183. What does `stats avg(duration)` return?
```
A. Average value of duration field
B. Duration per event
C. Longest duration
D. Sum of duration
```
<details><summary> 
**Answer:** </summary>

```
A. Average value of duration field 
```

</details>

184. What does `search error OR fail` do?
```
A. Finds events with either 'error' or 'fail'
B. Searches exact phrase
C. Filters only error logs
D. Fails search if error exists
```
<details><summary> 
**Answer:** </summary>

```
A. Finds events with either 'error' or 'fail' 
```

</details>

185. Which SPL uses conditional evaluation to label errors?
```
A. eval status_type=if(status>=400, "error", "success")
B. stats if(status>400)
C. where status=error
D. lookup error status
```
<details><summary> 
**Answer:** </summary>

```
A. eval status_type=if(status>=400, "error", "success") 
```

</details>

186. How to rename 'status_code' to 'http_status'?
```
A. rename status_code AS http_status
B. eval http_status=status_code
C. table status_code
D. sort http_status
```
<details><summary> 
**Answer:** </summary>

```
A. rename status_code AS http_status 
```

</details>

187. How do you limit search to the last 2 hours?
```
A. earliest=-2h
B. latest=2h
C. span=2h
D. recent=2h
```
<details><summary> 
**Answer:** </summary>

```
A. earliest=-2h 
```

</details>

188. What command extracts fields using regex?
```
A. rex
B. spath
C. eval
D. table
```
<details><summary> 
**Answer:** </summary>

```
A. rex 
```

</details>

189. What is `_raw` in Splunk?
```
A. Original event data
B. Extracted field
C. Time format
D. IP field
```
<details><summary> 
**Answer:** </summary>

```
A. Original event data 
```

</details>

190. Which function provides sum of bytes transferred per host?
```
A. stats sum(bytes) by host
B. table bytes host
C. timechart host
D. eval bytes=sum
```
<details><summary> 
**Answer:** </summary>

```
A. stats sum(bytes) by host 
```

</details>

191. Which visualization is ideal for trend over time?
```
A. Line Chart
B. Pie Chart
C. Gauge
D. Single Value
```
<details><summary> 
**Answer:** </summary>

```
A. Line Chart 
```

</details>

192. How to track unique users logging in per day?
```
A. timechart span=1d dc(user)
B. chart user daily
C. dedup user | head
D. table user by date
```
<details><summary> 
**Answer:** </summary>

```
A. timechart span=1d dc(user) 
```

</details>

193. What command helps enrich data with usernames from a CSV?
```
A. lookup
B. join
C. eval
D. outputlookup
```
<details><summary> 
**Answer:** </summary>

```
A. lookup 
```

</details>

194. How to highlight failed login attempts from logs?
```
A. search "Failed password"
B. stats by login
C. rex user fail
D. fillnull fail
```
<details><summary> 
**Answer:** </summary>

```
A. search "Failed password" 
```

</details>

195. What is the function of `dc()` in SPL?
```
A. Counts distinct values
B. Deletes duplicates
C. Displays chart
D. Extracts time
```
<details><summary> 
**Answer:** </summary>

```
A. Counts distinct values 
```

</details>

196. What does `sort - count` imply?
```
A. Descending order by count
B. Group by count
C. Null sort
D. Show most recent only
```
<details><summary> 
**Answer:** </summary>

```
A. Descending order by count 
```

</details>

197. What is a benefit of `eventstats` over `stats`?
```
A. Preserves original events
B. Faster search
C. Used only in dashboards
D. Deduplicates results
```
<details><summary> 
**Answer:** </summary>

```
A. Preserves original events 
```

</details>

198. Which SPL returns top 3 error messages?
```
A. search error | top limit=3 _raw
B. table error | head 3
C. dedup error | tail 3
D. stats top error
```
<details><summary> 
**Answer:** </summary>

```
A. search error | top limit=3 _raw 
```

</details>

199. How to calculate login percentage per department?
```
A. stats count by department | eventstats sum(count) as total | eval percent=(count/total)*100
B. top department login
C. table department login
D. eval percent=login
```
<details><summary> 
**Answer:** </summary>

```
A. stats count by department | eventstats sum(count) as total | eval percent=(count/total)*100 
```

</details>

200. Which SPL command writes current search result to a lookup file?
```
A. outputlookup
B. inputlookup
C. lookup
D. fillnull
```
<details><summary> 
**Answer:** </summary>

```
A. outputlookup 
```

</details>
