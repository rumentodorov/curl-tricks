# How to measure the stats for HTTP request to endpoint with CURL

This help contains information how

## Create a text file curl-stats


```bash
    time_namelookup:  %{time_namelookup}\n
       time_connect:  %{time_connect}\n
    time_appconnect:  %{time_appconnect}\n
   time_pretransfer:  %{time_pretransfer}\n
      time_redirect:  %{time_redirect}\n
 time_starttransfer:  %{time_starttransfer}\n
                    ----------\n
         time_total:  %{time_total}\n
```

## Create a file named request-body and put your body there

```javascript
{
  "name":"Rumen Todorov"
  "department": "Dev"
}
```

## Make the exact CURL call

Depending of your request body use the following headers:
* Json - "Content-Type: application/json;charset=UTF-8"
* XML - "Content-Type:text/xml;charset=UTF-8"

```bash
curl -w "@curl-stats" -o /dev/null -X POST --header "Content-Type:text/xml;charset=UTF-8" -d @find-player http://<server>:<port>/endpoint
```
### Here is the result:

```bash
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   938  100   707  100   231  30888  10092 --:--:-- --:--:-- --:--:-- 32136
    time_namelookup:  0,005
       time_connect:  0,006
    time_appconnect:  0,000
   time_pretransfer:  0,006
      time_redirect:  0,000
 time_starttransfer:  0,023
                    ----------
         time_total:  0,023

```
Our response time is 23 ms