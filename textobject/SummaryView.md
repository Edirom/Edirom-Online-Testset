# getSummary.xql
## Title
```
$doc//tei:titleStmt/tei:title[1]/text()
```
oder
```
string-join($doc//tei:titleStmt/tei:title[@level eq 'a' or @level eq 'm']//text(),'. ‚
```
## Reihe
```
if($doc//tei:titleStmt/tei:title[@level eq ’s'])
```
value
```
$doc//tei:titleStmt/tei:title[@level eq ’s']//text()
```
## Herausgeber
```
if($doc//tei:titleStmt/tei:editor)
```
name
```
 $doc//tei:titleStmt/tei:title[@level eq ’s']//text()
```
## Persons
```
for $name at $i in $respStmt/tei:*[local-name() eq 'persName' or local-name() eq 'name' or local-name() eq ‚orgName']
```
## Publication Datas
```
for $date in $doc//tei:publicationStmt/tei:date
```
## Repository
```
$doc//tei:sourceDesc/tei:msDesc//tei:repository/text()
```
## Signatur
```
$doc//tei:sourceDesc/tei:msDesc//tei:idno/text()
```
## Publisher
```
$doc//tei:publicationStmt/tei:publisher[1]/text()
```

