```
requests
| make-series count() default=0
on timestamp from datetime_add("hour",-72,now()) to now() step 1m 
| render timechart 
```
When rendering a timechart, missing values are poorly represented because the line becomes a straigth line from the last available value to the next, regardeless of their distance.  
`make-series` combined with `default=0` makes the representation of such missing values be zeros.
