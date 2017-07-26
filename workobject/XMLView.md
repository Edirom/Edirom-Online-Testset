# getXml.xql
input parameters:
```
$uri := request:get-parameter('uri', '')

$internalId := request:get-parameter('internalId', '')
```
## XML Code
$doc:
```
eutil:getDoc($uri)/root()
```
$internal:
```
$doc/id($internalId)
```
xml code:
```
 if(exists($internal))  then($internal)  else($doc)
```

