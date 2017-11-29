# getMeasureOnPage
## Input parameters:
```
$uri := request:get-parameter('uri', '')
 $surfaceId := request:get-parameter('pageId', '')
```
## Show following data informations

for 

```
$zone in $surface/mei:zone[@type='measure']
```

and
```
$measure := $mei//mei:measure[@facs=concat('#', $zone/@xml:id)]
```

1. zoneId:
```
$zone/string(@xml:id)
```

2. ulx:
```
$zone/string(@ulx)
```

3. uly:
```
$zone/string(@uly)
```

4. lrx:
```
$zone/string(@lrx)
```

5. lry:
```
$zone/string(@lry)
```

6. id:
```
$measure/string(@xml:id)
```

7. name:
```
$measure/string(@n)
```

8. type:
```
$measure/string(@type)
```

9. rest:
```
 if($measure//mei:mRest)
 then(string('1'))
 else 
 	if($measure//mei:multiRest)
 	then($measure//mei:multiRest/string(@num))
 	else(string('0'))
```

