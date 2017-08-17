# getiFameURL.xql
## Input parameters:
```
$uri := request:get-parameter('uri', '')
```
## Show following data informations
URL:
```
replace($uri, 
'xmldb:exist:///db/',
concat('http://', request:get-server-name(), ':', request:get-server-port(), '/exist/'))
```

