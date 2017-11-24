# getMovements.xql
## Input parameters:
```
$uri := request:get-parameter('uri', '')
```
## Show following data informations
For each movement in mei:mdiv:
1. ID:
```
$movement/string(@xml:id)
```

2. Name:
```
$movement/string(@label)
```

## Example
XML:
``` 
...
 <mdiv xml:id="edirom_mdiv_ac05b317-fb5b" label="1. Kyrie I">
 ...
``` 
JSON Result/Output: 
```            
{id: "edirom_mdiv_ac05b317-fb5b", name: "1. Kyrie I"}
```

