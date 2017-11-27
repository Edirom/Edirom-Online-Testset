# getOverlays.xql
## Input parameters:
```
$uri := request:get-parameter('uri', '')
```
## Show following data informations
### For each overlay in mei:annot[@type = 'overlay']:
1. ID:
```
$overlay/string(@xml:id)
```

2. Name:
```
$overlay/mei:title
```




 

