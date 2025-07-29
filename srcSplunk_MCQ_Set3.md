## Practice set 3:

201. Which of the following SPL queries correctly identifies the session duration for each user using transaction?
```
A. transaction user startswith="login" endswith="logout" | eval session_duration = duration
B. transaction user maxspan=30m | eval session=duration
C. stats by user | eval duration
D. join user duration
```
<details><summary> 
**Answer:** </summary>

```
A. transaction user startswith="login" endswith="logout" | eval session_duration = duration 
```

</details>

202. What is the main purpose of the `coalesce()` function in Splunk?
```
A. Returns the first non-null value among fields
B. Combines charts
C. Calculates correlation between fields
D. Converts field types
```
<details><summary> 
**Answer:** </summary>

```
A. Returns the first non-null value among fields 
```

</details>

203. Which SPL query detects multiple failed login attempts followed by a success within 5 minutes?
```
A. transaction user maxpause=5m | search event=success AND prior_event=fail
B. eventstats count by user | where count > 1
C. stats count by user | where fail > 1 AND success = 1
D. transaction user startswith="fail" endswith="success" maxspan=5m
```
<details><summary> 
**Answer:** </summary>

```
D. transaction user startswith="fail" endswith="success" maxspan=5m 
```

</details>

204. Which command can be used to create a summary index for performance improvement?
```
A. collect
B. outputlookup
C. lookup
D. join
```
<details><summary> 
**Answer:** </summary>

```
A. collect 
```

</details>

205. What will be the output of `eval status=if(like(uri,"%admin%"),"suspicious","normal")`?
```
A. Marks events with URI containing 'admin' as suspicious
B. Deletes 'admin' logs
C. Groups admin URIs only
D. Counts user logins
```
<details><summary> 
**Answer:** </summary>

```
A. Marks events with URI containing 'admin' as suspicious 
```

</details>

206. Which SPL query uses `spath` to extract nested field 'location.city' from a JSON payload?
```
A. spath input=payload path=location.city output=city
B. rex field=payload "location.city"
C. eval city=payload.location.city
D. table city from json
```
<details><summary> 
**Answer:** </summary>

```
A. spath input=payload path=location.city output=city 
```

</details>

207. How would you create a field that calculates time difference between two events per user?
```
A. streamstats earliest(_time) as start latest(_time) as end by user | eval diff=end-start
B. transaction user | eval diff=duration
C. eventstats diff by user
D. bin _time | diff
```
<details><summary> 
**Answer:** </summary>

```
A. streamstats earliest(_time) as start latest(_time) as end by user | eval diff=end-start 
```

</details>

208. What is the key difference between `eventstats` and `streamstats`?
```
A. streamstats calculates running totals, eventstats appends aggregate to all
B. eventstats is faster
C. streamstats only works on indexed fields
D. eventstats requires JSON logs
```
<details><summary> 
**Answer:** </summary>

```
A. streamstats calculates running totals, eventstats appends aggregate to all 
```

</details>

209. Which SPL returns only users whose last login was more than 30 days ago?
```
A. stats latest(_time) as last_seen by user | where last_seen < relative_time(now(), "-30d")
B. eventstats last_login by user | where last_login < today()
C. stats by user where duration > 30
D. join user | where time=-30d
```
<details><summary> 
**Answer:** </summary>

```
A. stats latest(_time) as last_seen by user | where last_seen < relative_time(now(), "-30d") 
```

</details>

210. Which field is required by `timechart` but not `chart`?
```
A. _time
B. host
C. status
D. source
```
<details><summary> 
**Answer:** </summary>

```
A. _time 
```

</details>

211. Which of the following SPL queries correctly identifies the session duration for each user using transaction?
```
A. transaction user startswith="login" endswith="logout" | eval session_duration = duration
B. transaction user maxspan=30m | eval session=duration
C. stats by user | eval duration
D. join user duration
```
<details><summary> 
**Answer:** </summary>

```
A. transaction user startswith="login" endswith="logout" | eval session_duration = duration 
```

</details>

212. What is the main purpose of the `coalesce()` function in Splunk?
```
A. Returns the first non-null value among fields
B. Combines charts
C. Calculates correlation between fields
D. Converts field types
```
<details><summary> 
**Answer:** </summary>

```
A. Returns the first non-null value among fields 
```

</details>

213. Which SPL query detects multiple failed login attempts followed by a success within 5 minutes?
```
A. transaction user maxpause=5m | search event=success AND prior_event=fail
B. eventstats count by user | where count > 1
C. stats count by user | where fail > 1 AND success = 1
D. transaction user startswith="fail" endswith="success" maxspan=5m
```
<details><summary> 
**Answer:** </summary>

```
D. transaction user startswith="fail" endswith="success" maxspan=5m 
```

</details>

214. Which command can be used to create a summary index for performance improvement?
```
A. collect
B. outputlookup
C. lookup
D. join
```
<details><summary> 
**Answer:** </summary>

```
A. collect 
```

</details>

215. What will be the output of `eval status=if(like(uri,"%admin%"),"suspicious","normal")`?
```
A. Marks events with URI containing 'admin' as suspicious
B. Deletes 'admin' logs
C. Groups admin URIs only
D. Counts user logins
```
<details><summary> 
**Answer:** </summary>

```
A. Marks events with URI containing 'admin' as suspicious 
```

</details>

216. Which SPL query uses `spath` to extract nested field 'location.city' from a JSON payload?
```
A. spath input=payload path=location.city output=city
B. rex field=payload "location.city"
C. eval city=payload.location.city
D. table city from json
```
<details><summary> 
**Answer:** </summary>

```
A. spath input=payload path=location.city output=city 
```

</details>

217. How would you create a field that calculates time difference between two events per user?
```
A. streamstats earliest(_time) as start latest(_time) as end by user | eval diff=end-start
B. transaction user | eval diff=duration
C. eventstats diff by user
D. bin _time | diff
```
<details><summary> 
**Answer:** </summary>

```
A. streamstats earliest(_time) as start latest(_time) as end by user | eval diff=end-start 
```

</details>

218. What is the key difference between `eventstats` and `streamstats`?
```
A. streamstats calculates running totals, eventstats appends aggregate to all
B. eventstats is faster
C. streamstats only works on indexed fields
D. eventstats requires JSON logs
```
<details><summary> 
**Answer:** </summary>

```
A. streamstats calculates running totals, eventstats appends aggregate to all 
```

</details>

219. Which SPL returns only users whose last login was more than 30 days ago?
```
A. stats latest(_time) as last_seen by user | where last_seen < relative_time(now(), "-30d")
B. eventstats last_login by user | where last_login < today()
C. stats by user where duration > 30
D. join user | where time=-30d
```
<details><summary> 
**Answer:** </summary>

```
A. stats latest(_time) as last_seen by user | where last_seen < relative_time(now(), "-30d") 
```

</details>

220. Which field is required by `timechart` but not `chart`?
```
A. _time
B. host
C. status
D. source
```
<details><summary> 
**Answer:** </summary>

```
A. _time 
```

</details>

221. Which of the following SPL queries correctly identifies the session duration for each user using transaction?
```
A. transaction user startswith="login" endswith="logout" | eval session_duration = duration
B. transaction user maxspan=30m | eval session=duration
C. stats by user | eval duration
D. join user duration
```
<details><summary> 
**Answer:** </summary>

```
A. transaction user startswith="login" endswith="logout" | eval session_duration = duration 
```

</details>

222. What is the main purpose of the `coalesce()` function in Splunk?
```
A. Returns the first non-null value among fields
B. Combines charts
C. Calculates correlation between fields
D. Converts field types
```
<details><summary> 
**Answer:** </summary>

```
A. Returns the first non-null value among fields 
```

</details>

223. Which SPL query detects multiple failed login attempts followed by a success within 5 minutes?
```
A. transaction user maxpause=5m | search event=success AND prior_event=fail
B. eventstats count by user | where count > 1
C. stats count by user | where fail > 1 AND success = 1
D. transaction user startswith="fail" endswith="success" maxspan=5m
```
<details><summary> 
**Answer:** </summary>

```
D. transaction user startswith="fail" endswith="success" maxspan=5m 
```

</details>

224. Which command can be used to create a summary index for performance improvement?
```
A. collect
B. outputlookup
C. lookup
D. join
```
<details><summary> 
**Answer:** </summary>

```
A. collect 
```

</details>

225. What will be the output of `eval status=if(like(uri,"%admin%"),"suspicious","normal")`?
```
A. Marks events with URI containing 'admin' as suspicious
B. Deletes 'admin' logs
C. Groups admin URIs only
D. Counts user logins
```
<details><summary> 
**Answer:** </summary>

```
A. Marks events with URI containing 'admin' as suspicious 
```

</details>

226. Which SPL query uses `spath` to extract nested field 'location.city' from a JSON payload?
```
A. spath input=payload path=location.city output=city
B. rex field=payload "location.city"
C. eval city=payload.location.city
D. table city from json
```
<details><summary> 
**Answer:** </summary>

```
A. spath input=payload path=location.city output=city 
```

</details>

227. How would you create a field that calculates time difference between two events per user?
```
A. streamstats earliest(_time) as start latest(_time) as end by user | eval diff=end-start
B. transaction user | eval diff=duration
C. eventstats diff by user
D. bin _time | diff
```
<details><summary> 
**Answer:** </summary>

```
A. streamstats earliest(_time) as start latest(_time) as end by user | eval diff=end-start 
```

</details>

228. What is the key difference between `eventstats` and `streamstats`?
```
A. streamstats calculates running totals, eventstats appends aggregate to all
B. eventstats is faster
C. streamstats only works on indexed fields
D. eventstats requires JSON logs
```
<details><summary> 
**Answer:** </summary>

```
A. streamstats calculates running totals, eventstats appends aggregate to all 
```

</details>

229. Which SPL returns only users whose last login was more than 30 days ago?
```
A. stats latest(_time) as last_seen by user | where last_seen < relative_time(now(), "-30d")
B. eventstats last_login by user | where last_login < today()
C. stats by user where duration > 30
D. join user | where time=-30d
```
<details><summary> 
**Answer:** </summary>

```
A. stats latest(_time) as last_seen by user | where last_seen < relative_time(now(), "-30d") 
```

</details>

230. Which field is required by `timechart` but not `chart`?
```
A. _time
B. host
C. status
D. source
```
<details><summary> 
**Answer:** </summary>

```
A. _time 
```

</details>

231. Which of the following SPL queries correctly identifies the session duration for each user using transaction?
```
A. transaction user startswith="login" endswith="logout" | eval session_duration = duration
B. transaction user maxspan=30m | eval session=duration
C. stats by user | eval duration
D. join user duration
```
<details><summary> 
**Answer:** </summary>

```
A. transaction user startswith="login" endswith="logout" | eval session_duration = duration 
```

</details>

232. What is the main purpose of the `coalesce()` function in Splunk?
```
A. Returns the first non-null value among fields
B. Combines charts
C. Calculates correlation between fields
D. Converts field types
```
<details><summary> 
**Answer:** </summary>

```
A. Returns the first non-null value among fields 
```

</details>

233. Which SPL query detects multiple failed login attempts followed by a success within 5 minutes?
```
A. transaction user maxpause=5m | search event=success AND prior_event=fail
B. eventstats count by user | where count > 1
C. stats count by user | where fail > 1 AND success = 1
D. transaction user startswith="fail" endswith="success" maxspan=5m
```
<details><summary> 
**Answer:** </summary>

```
D. transaction user startswith="fail" endswith="success" maxspan=5m 
```

</details>

234. Which command can be used to create a summary index for performance improvement?
```
A. collect
B. outputlookup
C. lookup
D. join
```
<details><summary> 
**Answer:** </summary>

```
A. collect 
```

</details>

235. What will be the output of `eval status=if(like(uri,"%admin%"),"suspicious","normal")`?
```
A. Marks events with URI containing 'admin' as suspicious
B. Deletes 'admin' logs
C. Groups admin URIs only
D. Counts user logins
```
<details><summary> 
**Answer:** </summary>

```
A. Marks events with URI containing 'admin' as suspicious 
```

</details>

236. Which SPL query uses `spath` to extract nested field 'location.city' from a JSON payload?
```
A. spath input=payload path=location.city output=city
B. rex field=payload "location.city"
C. eval city=payload.location.city
D. table city from json
```
<details><summary> 
**Answer:** </summary>

```
A. spath input=payload path=location.city output=city 
```

</details>

237. How would you create a field that calculates time difference between two events per user?
```
A. streamstats earliest(_time) as start latest(_time) as end by user | eval diff=end-start
B. transaction user | eval diff=duration
C. eventstats diff by user
D. bin _time | diff
```
<details><summary> 
**Answer:** </summary>

```
A. streamstats earliest(_time) as start latest(_time) as end by user | eval diff=end-start 
```

</details>

238. What is the key difference between `eventstats` and `streamstats`?
```
A. streamstats calculates running totals, eventstats appends aggregate to all
B. eventstats is faster
C. streamstats only works on indexed fields
D. eventstats requires JSON logs
```
<details><summary> 
**Answer:** </summary>

```
A. streamstats calculates running totals, eventstats appends aggregate to all 
```

</details>

239. Which SPL returns only users whose last login was more than 30 days ago?
```
A. stats latest(_time) as last_seen by user | where last_seen < relative_time(now(), "-30d")
B. eventstats last_login by user | where last_login < today()
C. stats by user where duration > 30
D. join user | where time=-30d
```
<details><summary> 
**Answer:** </summary>

```
A. stats latest(_time) as last_seen by user | where last_seen < relative_time(now(), "-30d") 
```

</details>

240. Which field is required by `timechart` but not `chart`?
```
A. _time
B. host
C. status
D. source
```
<details><summary> 
**Answer:** </summary>

```
A. _time 
```

</details>

241. Which of the following SPL queries correctly identifies the session duration for each user using transaction?
```
A. transaction user startswith="login" endswith="logout" | eval session_duration = duration
B. transaction user maxspan=30m | eval session=duration
C. stats by user | eval duration
D. join user duration
```
<details><summary> 
**Answer:** </summary>

```
A. transaction user startswith="login" endswith="logout" | eval session_duration = duration 
```

</details>

242. What is the main purpose of the `coalesce()` function in Splunk?
```
A. Returns the first non-null value among fields
B. Combines charts
C. Calculates correlation between fields
D. Converts field types
```
<details><summary> 
**Answer:** </summary>

```
A. Returns the first non-null value among fields 
```

</details>

243. Which SPL query detects multiple failed login attempts followed by a success within 5 minutes?
```
A. transaction user maxpause=5m | search event=success AND prior_event=fail
B. eventstats count by user | where count > 1
C. stats count by user | where fail > 1 AND success = 1
D. transaction user startswith="fail" endswith="success" maxspan=5m
```
<details><summary> 
**Answer:** </summary>

```
D. transaction user startswith="fail" endswith="success" maxspan=5m 
```

</details>

244. Which command can be used to create a summary index for performance improvement?
```
A. collect
B. outputlookup
C. lookup
D. join
```
<details><summary> 
**Answer:** </summary>

```
A. collect 
```

</details>

245. What will be the output of `eval status=if(like(uri,"%admin%"),"suspicious","normal")`?
```
A. Marks events with URI containing 'admin' as suspicious
B. Deletes 'admin' logs
C. Groups admin URIs only
D. Counts user logins
```
<details><summary> 
**Answer:** </summary>

```
A. Marks events with URI containing 'admin' as suspicious 
```

</details>

246. Which SPL query uses `spath` to extract nested field 'location.city' from a JSON payload?
```
A. spath input=payload path=location.city output=city
B. rex field=payload "location.city"
C. eval city=payload.location.city
D. table city from json
```
<details><summary> 
**Answer:** </summary>

```
A. spath input=payload path=location.city output=city 
```

</details>

247. How would you create a field that calculates time difference between two events per user?
```
A. streamstats earliest(_time) as start latest(_time) as end by user | eval diff=end-start
B. transaction user | eval diff=duration
C. eventstats diff by user
D. bin _time | diff
```
<details><summary> 
**Answer:** </summary>

```
A. streamstats earliest(_time) as start latest(_time) as end by user | eval diff=end-start 
```

</details>

248. What is the key difference between `eventstats` and `streamstats`?
```
A. streamstats calculates running totals, eventstats appends aggregate to all
B. eventstats is faster
C. streamstats only works on indexed fields
D. eventstats requires JSON logs
```
<details><summary> 
**Answer:** </summary>

```
A. streamstats calculates running totals, eventstats appends aggregate to all 
```

</details>

249. Which SPL returns only users whose last login was more than 30 days ago?
```
A. stats latest(_time) as last_seen by user | where last_seen < relative_time(now(), "-30d")
B. eventstats last_login by user | where last_login < today()
C. stats by user where duration > 30
D. join user | where time=-30d
```
<details><summary> 
**Answer:** </summary>

```
A. stats latest(_time) as last_seen by user | where last_seen < relative_time(now(), "-30d") 
```

</details>

250. Which field is required by `timechart` but not `chart`?
```
A. _time
B. host
C. status
D. source
```
<details><summary> 
**Answer:** </summary>

```
A. _time 
```

</details>
