# getInternalIdType.xql
## Input parameters:
```
$uri := request:get-parameter('uri', '')
```
## Show following data informations
internalId:
```
if(contains($uri, '#'))
then(substring-after($uri, '#'))
else()

if(contains($internalId, '?'))
then(substring-before($internalId, '?'))
else($internalId)
```

for internal following steps:
```
$internal := $doc/id($internalId)


$internal := if(exists($internal))
then($internal)
else(
	if(starts-with($internalId, 'measure_') and $doc//mei:parts)
	then( let $mdivId := functx:substring-before-last(substring-after($internalId, 'measure_'), '_')
		let $measureN := functx:substring-after-last($internalId, '_')
		return ($doc/id($mdivId)//mei:measure[@n eq $measureN])[1])
	else($internal))
	
	
local-name($internal)
```

