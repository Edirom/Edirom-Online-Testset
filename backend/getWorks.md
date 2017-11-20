# getWorks.xql
### Conditions:
Only first title for work will be returned/shown.
### Input parameters:
```
$uri := request:get-parameter('id', '')
```
### Import:
```
../xqm/edition.xqm

../xqm/work.xqm
```
### Following steps are executed
```
$workUris := edition:getWorkUris($uri)
```
for each defined work:
```
for $workUri in $workUris
return work:toJSON($workUri)
```
#### in edition.xqm
get work file
```
doc($uri)//edirom:work/string(@xlink:href)
```
#### in work.xqm
get work informations:
```
$work := doc($uri)/mei:mei
```
return:
```
'id: "', $work/string(@xml:id), '", ',
'doc: "', $uri, '", ',
'title: "', $work//mei:workDesc/mei:work/mei:titleStmt/replace(mei:title[1], '"', '\\"'), '"'
```





