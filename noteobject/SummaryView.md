# getSummary.xql
parameters:
```
$uri := request:get-parameter('uri', '')

$type := request:get-parameter('type', '')
```
## Title
```
if($doc//mei:source/mei:titleStmt/mei:title[@type eq 'main'])
 then($doc//mei:source/mei:titleStmt/mei:title[@type eq 'main'][1]//text())
 else($doc//mei:source/mei:titleStmt/mei:title[1]//text())
```
## Identifiers
```
if($doc//mei:source//mei:identifier[@type eq 'siglum']) then(concat(' ', $doc//mei:source//mei:identifier[@type eq ‚siglum'][1]//text()))
```

## Extension
Zur Fassung "
```
{$expression}
```
" von
``` 
{$resp} 
```
„
```
{$title}
```
".
## Persons
```
for $name in $doc//mei:source/mei:titleStmt/mei:respStmt/mei:*[local-name() eq 'persName' or local-name() eq ‚name']
```
role:
```
if($name/@role) then($name/string(@role)) else(string(‚Responsible'))
```
name:
```
$name/text()
```
## Datas
```
for $date in $doc//mei:source/mei:pubStmt/mei:date | $doc//mei:source/mei:history/mei:creation/mei:date[1]
```
## Manuscripts
```
count($doc//mei:source/mei:itemList/mei:item) eq 1
```
manuscript:
```
$item/mei:physDesc/mei:repository[1]/text(), if($item/mei:physDesc/mei:physLoc) then(<br/>,$item/mei:physDesc/mei:physLoc[1]/text())
```
## Publisher
```
if($doc//mei:source/mei:pubStmt//mei:*[@role eq ‚publisher'])
```
name:
```
$doc//mei:source/mei:pubStmt//mei:*[@role eq ‚publisher'][1]/text()
```
## Plate Number
```
if($doc//mei:source/mei:physDesc/mei:plateNum)
```
number:
```
$doc//mei:source/mei:physDesc/mei:plateNum[1]/text()
```
## Facsimile Path
```
if($doc//mei:source//mei:titlePage/@facs)
```
oder
```
if($doc//mei:facsimile/mei:surface/mei:graphic)
```
path:
```
if(starts-with($uri, 'xmldb:exist'))
 then(   let $imagePath := doc($uri)/edirom_image:image/@file
     return concat($basePath, $imagePath, '?dw=', $width, '&amp;amp;mo=fit'))
else(concat($basePath, $uri, '?dw=', $width, '&amp;amp;mo=fit'))
```

