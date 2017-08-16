# getMovementsFirstPage.xql
## Input parameters:
```
$uri := request:get-parameter('uri', '')
 $movementId := request:get-parameter('movementId', '')
```
## Show following data informations
mei:
```
doc($uri)/root()
```
zoneId:
```
($mei/id($movementId)//mei:measure)[1]/string(@facs)
 let $zoneId := if(starts-with($zoneId, '#'))
then(substring($zoneId, 2))
else($zoneId)
```
movements on first page:
```
$mei/id($zoneId)/parent::mei:surface/string(@xml:id)
```

