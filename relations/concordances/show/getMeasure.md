# getMeasure.xql
## Input parameters:
```
$id := request:get-parameter('id', '')

$measureId := request:get-parameter('measureId', '')
```
## Show following data informations
measureId:
```
if(contains($measureId, '?'))
then(substring-before($measureId, '?'))
else($measureId)
```

movementId :
```
$mei := doc($id)/root()

$movementId := $mei/id($measureId)/ancestor::mei:mdiv[1]/@xml:id

$movementId := if(starts-with($measureId, 'measure_') and $mei//mei:parts)
then(functx:substring-before-last(substring-after($measureId, 'measure_'), '_'))
else($movementId)
```

measureCount:
```
if(contains($measureId, 'tstamp2='))
then(number(substring-before(substring-after($measureId, 'tstamp2='), 'm')) + 1)
else(1) ```


