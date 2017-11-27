# getMeasures.xql
## Input parameters:
```
$uri := request:get-parameter('uri', '')

$mdivID := request:get-parameter('mdiv', '')
```
## Show following data informations
### If mei:parts exists:
```
$mdiv := $mei/id($mdivID)
```
for each 
```
$measureN in distinct-values($mdiv//mei:measure/@n):
```

1. name:
```
$measureN
```

2. mdivs:
```
$mdiv/@xml:id
```

3. ID:
```
"measure_', $mdiv/@xml:id, '_', $measureN, '"
```

4. measures:
```
let $measureNNumber := number($measureN)
 let $measures := $mdiv//mei:measure[.//mei:multiRest][number(@n) lt $measureNNumber][.//mei:multiRest/number(@num) gt ($measureNNumber - number(@n))]             
let $measures := for $measure in $mdiv//mei:measure[@n = $measureN] | $measures
		return
			concat('{id:"', $measure/@xml:id, '", voice: "', $measure/ancestor::mei:part//mei:staffDef/@decls, '"}')
```

### Else:
```
for $measure in $mei/id($mdivID)//mei:measure
```

1. name:
```
$measure/@n
```

2. mdivs:
```
$measure/ancestor::mei:mdiv[1]/@xml:id
```

3. ID:
```
$measure/@xml:id
```

4. measures:
```
[{id:"', $measure/@xml:id, '", voice: "score"}]
```


