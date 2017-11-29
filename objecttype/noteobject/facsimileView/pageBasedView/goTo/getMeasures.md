# getMeasures.xql
## Input parameters:
```
$uri := request:get-parameter('uri', '')

$mdivID := request:get-parameter('mdiv', '')
```
## Show following data informations
if($mei//mei:parts)
```
'id: "measure_', $mdiv/@xml:id, '_', $measureN, '", ',
'measures: [', string-join($measures, ','), '], ',
'mdivs: ["', $mdiv/@xml:id, '"], ', 
'name: "', $measureN, '"'
```
else
```
'id: "', $measure/@xml:id, '", ',
'measures: [{id:"', $measure/@xml:id, '", voice: "score"}], ',
'mdivs: ["', $measure/ancestor::mei:mdiv[1]/@xml:id, '"], ',
'name: "', $measure/@n, '"'
```
## Example
### Parameter
![](../../../../workobject/facsimileView/pageBasedView/goTo/media/15115276855744.jpg)

### XML
```
...
<mdiv xml:id="edirom_mdiv_ac05b317-fb5b" label="1. Kyrie I">
<staffDef decls="#score"/>
<measure xml:id="edirom_measure_8ed5a31e-5f94" n="1" facs="#edirom_zone_d557a0e0-ce2c"/>
...
```
### Result JSON
```
{id: "measure_edirom_mdiv_ac05b317-fb5b_1", measures: [{id:"edirom_measure_8ed5a31e-5f94", voice: "#score"}], mdivs: ["edirom_mdiv_ac05b317-fb5b"], name: "1"}
...
```






