# getPages.xql
## Input parameters:
```
$uri := request:get-parameter('uri', '')
 $idPrefix := request:get-parameter('idPrefix', '') 
$term := request:get-parameter('term', '') 
$path := request:get-parameter('path', '') 
$page := request:get-parameter('page', '')
$imagePrefix := eutil:getPreference('image_prefix', request:get-parameter('edition', ''))
```




