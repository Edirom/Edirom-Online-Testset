# getTargetLink.xql
## Input parameters:
```
$uri := request:get-parameter('uri', '')
```
## Show following data informations
### Object Type
work:
```
if(exists($doc//mei:mei) and exists($doc//mei:work))
```
source:
```
else if(exists($doc//mei:mei) and exists($doc//mei:source))
```
recording:
```
if(exists($doc//mei:mei) and exists($doc//mei:recording)
```
text:
```
if(exists($doc/tei:TEI)
```
html:
```
if(exists($doc/html)
```
### Title for object
work:
```
$doc//mei:work/mei:titleStmt)[1]/data(mei:title[1])
```
source
```
$doc//mei:fileDesc/mei:titleStmt[1]/data(mei:title[1])
```
recording
```
$doc//mei:fileDesc/mei:titleStmt[1]/data(mei:title[1])
```
text
```
$doc//tei:fileDesc/tei:titleStmt/data(tei:title[1]
```
html
```
$doc//head/data(title)
```
### Viewers for Objects
HeaderView
```
if($doc//mei:meiHead or $doc//tei:teiHeader)
```
SourceDescriptionView
```
 if($doc//mei:annot[@type='descLink'])
```
SourceView
```
if($doc//mei:facsimile//mei:graphic[@type='facsimile'])
```
AudioView
```
if($doc//mei:recording)
```
VerovioView
```
if($doc//mei:body//mei:measure and $doc//mei:body//mei:note)
```
TextView
```
if($doc//tei:body[matches(.//text(), '[^\s]+')])
```
SourceView
```
if($doc//tei:facsimile//tei:graphic)
```
TextFacsimileSplitView
```
if($doc//tei:facsimile//tei:graphic and $doc//tei:pb[@facs])
```
AnnotationView
```
if($doc//mei:annot[@type='editorialComment'])
```
iFrameView
```
if($type = 'html')
```
SourceDescriptionView
```
if($doc//mei:annot[@type=‚descLink'])
```
### Doc-uri with Parameters
InternalID:
```
if(contains($uri, ‚#‘))
if(contains($internalId, '?'))
```
Path:
```
if(contains($uriParams, ‚path='))
if(contains($path, '&amp;'))
```
Term:
```
if(contains($uriParams, ‚term='))
if(contains($term, '&amp;'))
```
InternalIdType:
```
if(exists($internal))
```

