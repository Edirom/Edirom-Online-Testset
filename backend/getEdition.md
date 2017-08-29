# getEdition.xql
### Input parameters:
```
$uri := request:get-parameter('id', '')
```
### Import:
```
../xqm/edition.xqm
```
### Following steps are executed
```
edition:toJSON($uri)
```

#### in edition.xqm
get edition file:
```
$edition := doc($uri)/edirom:edition
```
return:
```
'id: "', $edition/string(@xml:id), '", ',
'doc: "', $uri, '", ',
'name: "', $edition/edirom:editionName, '"'
```
### Conditions
xml:id for edition and editionName in edition file are optional.

