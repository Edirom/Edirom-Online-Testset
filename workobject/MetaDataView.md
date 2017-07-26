# getHeader.xql -> meiHead2HTML.xsl
input parameters:
```
$uri := request:get-parameter('uri', '')

$type := request:get-parameter('type', '')
```
## Datainformation
```
mei:titleStmt
```
## Workdetails
## Title
```
./titleStmt/title[1]/text()
```
## Additional Meta Data
```
mei:langUsage | mei:editionStmt
```
## Annotations

