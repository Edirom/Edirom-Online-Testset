# getHeader.xql -> meiHead2HTML.xsl
parameters:
```
$uri := request:get-parameter('uri', '')

$type := request:get-parameter('type', '')
```
## Dateiinformation
## Source Description
Title:
```
./titleStmt/title[1]/text()
```
Identifiers:
	node
	type
	
PropertyList:
```
./key | ./meter | ./perfMedium | ./castList | mei:componentGrp
```
Series:
```
./seriesStmt
```



