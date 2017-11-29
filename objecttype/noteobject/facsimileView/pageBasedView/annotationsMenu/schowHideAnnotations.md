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
## Example
XML:
```
... 
<annot type="editorialComment" xml:id="d1e518" plist="xmldb:exist:///db/contents/h-moll/neusatz.xml#measure-2-d4e27 xmldb:exist:///db/contents/h-moll/autograph.xml#edirom_measure_24f1c82e-43b8 xmldb:exist:///db/contents/h-moll/inselautograph.xml#edirom_measure_24f1c82e-43b8_insel">
 	<title>1. Kyrie I, m. 19, Fl I, II</title>
 	<p>
 		<rend rend="bold">A</rend>: with slur on 19/8–20/1
 	</p>
 	<ptr type="priority" target="#ediromAnnotPrio1"/>
 	<ptr type="categories" target="#SLA"/>
</annot> ...
``` 
JSON Result/Output: 

```            
{id: "d1e518", plist: [{id:"d1e518__edirom_measure_24f1c82e-43b8",ulx:285,uly:571,lrx:421,lry:1139}], svgList: [], fn: "loadLink(\"xmldb:exist:///db/contents/h-moll/work.xml#d1e518\")", uri: "xmldb:exist:///db/contents/h-moll/work.xml#d1e518", priority: "ediromAnnotPrio1", categories: "SLA"}
```



