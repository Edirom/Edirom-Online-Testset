# getSummary.xql
parameters:
```
$uri := request:get-parameter('uri', '')

$type := request:get-parameter('type', '')
```
## Persons
```
for $resp in $doc//mei:work/mei:titleStmt/mei:respStmt/mei:*[not(local-name() eq 'resp') and @role]
```
role:
```
concat(upper-case(substring($resp/@role 1,1)),substring($resp/@role, 2))
```
name:
```
$resp/text()
```
## Title
```
if($doc//mei:work/mei:titleStmt/mei:title[@type eq 'main'])
 then($doc//mei:work/mei:titleStmt/mei:title[@type eq 'main'][1]//text())
 else($doc//mei:work/mei:titleStmt/mei:title[1]//text())
```
## Identifiers
```
for $ident in $doc//mei:work/mei:identifier
```
## Expressions
```
for $expression in $doc//mei:work/mei:expressionList/mei:expression
```
label:
```
$expression/string(@label)
```
manifestations:
```			 
for $source in //mei:relation[@target = $target and @rel =‚isEmbodimentOf']/root()
```
manifestation:
```		
$source//mei:source/mei:titleStmt/mei:title[1]/text()
```

