# getWorkID.xql
### Input parameters:
```
$uri := request:get-parameter('uri', '')

$workId := request:get-parameter('workId', '')
```
### Import:
```
../xqm/work.xqm
```
### Get work id for defined work

```
if(doc($uri)//edirom:work[@xml:id = $workId])
then($workId)
else(work:findWorkID($uri))
```

work.xqm:

```
doc($uri)//edirom:work[1]/data(@xml:id)
```
###  Conditions

1. First defined work will be returned.
2. xml:id attribute is mandatory in work in edition file.



