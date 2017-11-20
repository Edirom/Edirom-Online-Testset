# getHeader.xql
## Input parameters:
```
$uri := request:get-parameter('uri', '')

$type := request:get-parameter('type', '')

$lang := request:get-parameter('lang', 'de')
```
## HTML Text
Tranform with [meiHeader2HTML](../../../transformations/getHeader/note/meiHead2HTML.md):
```
transform:transform($doc, concat($base, 'meiHead2HTML.xsl'), 
<parameters><param name="base" value="{$base}"/>
<param name="lang" value="{$lang}"/></parameters>)
```
## Example

[Example XML](test/TestXMLHeader.md)

[Generated HTML Result](test/TestXMLHeaderResult.md)

[Text View Screenshot](test/MetaDataView.md)

