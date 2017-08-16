# getAnnotationsOnPage
## Input parameters:
```
$id := request:get-parameter('id', '')

$surfaceId := request:get-parameter('pageId', '')

For findAnnotations-funktion:
request:get-parameter('edition', '')
```
## Following steps are executed

1. Finds all annotations in all works.
```
for $id in $elemIds:
collection('edition'//mei:annot/@plist[tokenize(string(.), '\s+')  = concat($uri, '#', $id)]/..
```

2. Returns a JSON representation of all participants of an annotation
```
$participants := $elems[@xml:id = $plist]
```
	2.1 Reads the coordinates of an element
	find zone: 
	```
	if(name($participant) = 'measure' or name($participant) = 'staff')
```
then
```
$participant/root()/id(substring($participant/@facs, 2))
```
else
```
$participant
```
find coordinates:
```
(number($zone/@ulx), number($zone/@uly), number($zone/@lrx), number($zone/@lry))
```
2.2 Participants:
```
concat(
'{id:"', $annoId, '__', string($p/@xml:id), 
'",ulx:', $coord[1], 
',uly:', $coord[2], 
',lrx:', $coord[3], 
',lry:', $coord[4],'}'), ",")
 ```       

3. Returns a JSON representation of all svg's of an annotation:
```
annoId: $anno/string(@xml:id)
 figs: $anno//mei:graphic[@target = $surfaceUri]/..
 ```  
 ```   
  for $figs:
   concat(
'{id:"', $annoId, '__', string($fig/@xml:id), 
'",svg:"', replace(replace(util:serialize($fig/svg:svg, ()), '"', '\\"'), '\n', ''),'"}'), ",") 
```         

4. Return Annotations:
id:
```
$annotation/string(@xml:id)
``` 
plist: step 2

svgList: step 3

fn: 
```
loadLink(\"', $uri, '\")
``` 
uri: 
```
concat('xmldb:exist://', document-uri($annotation/root()), '#', $id)
```

priority: 
```
$annotation/mei:ptr[@type="priority"]/replace(@target, '#', '')
```

categories:
```
$annotation/mei:ptr[@type="categories"]/replace(@target, '#', '')
```


