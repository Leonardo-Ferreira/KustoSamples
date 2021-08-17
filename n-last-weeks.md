```
requests
| where timestamp > ago(90d)
| where dayofweek(timestamp) == dayofweek(now())
| summarize count() by bin(todatetime(strcat("20210101 ", format_datetime(timestamp,"HH:mm:ss"))),5m),tostring(week_of_year(timestamp))
| render timechart 
```
The query above compares the current say of the week against the same day of previous weeks
