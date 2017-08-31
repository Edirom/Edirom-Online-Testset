# getHeader.xql
## Input parameters:
```
$uri := request:get-parameter('uri', '')

$type := request:get-parameter('type', '')

$lang := request:get-parameter('lang', 'de')
```
## HTML Text
Tranform with teiHeader2HTML.xsl:
```
transform:transform($doc, concat($base, 'meiHead2HTML.xsl'), 
<parameters><param name="base" value="{$base}"/>
<param name="lang" value="{$lang}"/></parameters>)
```

