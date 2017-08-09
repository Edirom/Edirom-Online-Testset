# getMeasurePage.xql
## Input parameters:
```
$id := request:get-parameter('id', '')

$measureIdName := request:get-parameter('measure', '')

$movementId := request:get-parameter('movementId', '')

$measureCount := request:get-parameter('measureCount', '1')
```
## Show following data informations
for measure with $measureIdName

1. measureId:
```
$measure/string(@xml:id)
```

2. zoneId:
```
substring-after($measure/string(@facs), '#')
```

3. pageId:
```
let $zoneId := substring-after($measure/string(@facs), '#')
let $zone := $mei/id($zoneId)
let $surface := $zone/parent::mei:surface
```
```
$surface/string(@xml:id)
```

4. path:
```
$surface/mei:graphic[@type='facsimile']/string(@target)
```

5. width:
```
$surface/mei:graphic[@type='facsimile']/string(@width)
```

6. height:
```
$surface/mei:graphic[@type='facsimile']/string(@height)
```

7. ulx:
```
$mei/id($zoneId)/string(@ulx)
```

8. uly:
```
$mei/id($zoneId)/string(@uly)
```

9. lrx:
```
$mei/id($zoneId)/string(@lrx)
```

10. lry:
```
$mei/id($zoneId)/string(@lry)
``` 

