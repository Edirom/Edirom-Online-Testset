# getEditionURI.xql
### Input parameters:
```
$uri := request:get-parameter('uri', '')
```
### Import:
```
../xqm/edition.xqm
```
### Get path for active edition

```
if(doc-available($uri))
then($uri)
else(edition:findEdition())
```

edition.xqm:

```
let $edition := (collection('/db/apps')//edirom:edition)[1]
return 'xmldb:exist://' 
	|| document-uri($edition/root())
```
### Examples for path definition:
return path same as $uri:
```
$uri :='xmldb:exist:///db/contents/testdata/edition.xml'
```
```
$uri :='/db/contents/testdata/edition.xml'
```
return path for first found edition file in database:
```
$uri :='db/contents/testdata/edition.xml'
```

```
$uri :=''
```



