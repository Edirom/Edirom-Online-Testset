# getText.xql
## Input parameters:
```
$uri := request:get-parameter('uri', '')
 $idPrefix := request:get-parameter('idPrefix', '') 
$term := request:get-parameter('term', '') 
$path := request:get-parameter('path', '') 
$page := request:get-parameter('page', '')
$imagePrefix := eutil:getPreference('image_prefix', request:get-parameter('edition', ''))
```

## Following steps are executed:
1. overwrite $doc with [reduceToPage](../../../transformations/getText/text/reduceToPage.md):
```
if($page eq '')
then($doc)
else(
	let $pb1 := $doc//tei:pb[@facs eq '#' || $page]/@n
	let $pb2 := ($doc//tei:pb[@facs eq '#' || $page] following::tei:pb)[1]/@n
	return
	transform:transform($doc, doc('../xslt/reduceToPage.xsl'), <parameters><param name="pb1" value="{$pb1}"/><param name="pb2" value="{$pb2}"/></parameters>) )
```

2. $xslInstruction:
```
$doc//processing-instruction(xml-stylesheet)
```
```
for $i in util:serialize($xslInstruction, ())
return
	if(matches($i, 'type="text/xsl"'))
	then(substring-before(substring-after($i, 'href="'), '"'))
	else()
```
3. $xsl depend from \$xslInstruction, trasform with [teiBody2HTML](../../../transformations/getText/text/teiBody2HTML.md):
```
if($xslInstruction)then($xslInstruction)else('../xslt/teiBody2HTML.xsl')
```
4. transform \$doc depend from $xslInstruction:
```
if($xslInstruction)
then(transform:transform($doc, doc($xsl), <parameters>{$params}</parameters>))
else(transform:transform($doc, doc($xsl), <parameters>{$params}<param name="graphicsPrefix" value="{$imagePrefix}"/></parameters>))
```
5. transform doc with  [edirom_idPrefix](../../../transformations/getText/text/edirom_idPrefix.md):
```
transform:transform($doc, doc('../xslt/edirom_idPrefix.xsl'), <parameters><param name="idPrefix" value="{$idPrefix}"/></parameters>) ```


