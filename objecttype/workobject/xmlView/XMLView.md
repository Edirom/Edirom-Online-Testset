# getXml.xql
### Input parameters:
```
$uri := request:get-parameter('uri', '')

$internalId := request:get-parameter('internalId', '')
```
### XML code for 'XML Quelle' view and 'XML Text' view 
$doc:
```
eutil:getDoc($uri)/root()
```
$internal:
```
$doc/id($internalId)
```
xml code:
```
 if(exists($internal))  then($internal)  else($doc)
```
## Example

[Example XML](../textView/test/TestXMLTextView.md)

[XML View Screenshot](../../textobject/xmlView/test/XMLView.md)


