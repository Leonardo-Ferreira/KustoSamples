```
let roleName = "yourApplication";
let reqCount = requests
| where cloud_RoleName == roleName
| summarize count();
requests
| where cloud_RoleName == roleName
| where toint(resultCode) >= 500
| summarize todouble(count())/todouble(toscalar(reqCount))*100
```
The code above returns the percentage of failures (identified by the clause `resultCode >= 500`)
