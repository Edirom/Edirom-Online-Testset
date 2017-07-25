# getHeader.xql -> meiHead2HTML.xsl
parameters:
```
$uri := request:get-parameter('uri', '')

$type := request:get-parameter('type', '')
```
## Dateiinformation
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

