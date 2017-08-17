# getMovements.xql
## Input parameters:
```
$uri := request:get-parameter('uri', '')
```
## Show following data informations
### For each movement in mei:mdiv:
1. ID:
```
$movement/string(@xml:id)
```

2. Name:
```
$movement/string(@label)
```


