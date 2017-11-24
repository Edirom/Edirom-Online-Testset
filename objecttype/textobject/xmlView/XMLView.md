# getXml.xql
parameters:
```
$uri := request:get-parameter('uri', '')

$internalId := request:get-parameter('internalId', '')
```
## XML Code
doc:
```
eutil:getDoc($uri)/root()
```
internal:
```
$doc/id($internalId)
```
xml:
```
 if(exists($internal))  then($internal)  else($doc)
```
## Example

[Example XML](../textView/test/TestXMLTextView.md)

[XML View Screenshot](test/XMLView.md)


