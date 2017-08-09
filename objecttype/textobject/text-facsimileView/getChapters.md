# getChapters.xql
## Input parameters:
```
$uri := request:get-parameter('uri', '')
 $mode := request:get-parameter('mode', '')
```
## Show following data informations
### For Element of Type
tei:div[@type='chapter'] or
$tei//tei:div1 or
tei:milestone[@unit='number'] or
tei:div[@type='act']

#### name:
1. For elements 'div' and type 'chapter' or 'div1' concat
```
if($chapter/@n)then(concat($chapter/@n, ': '))else(''),
```
and:
```
let $label := if($chapter/tei:head)then($chapter/tei:head)else($chapter/text())
let $label := if(string-length($label) > 30)then(concat(substring($label, 1, 30), '…'))else($label)
)
```

2. For elements 'div' and type 'act'
```
let $numbers := $elem let $n := concat('No. ', $numbers/@n)
```

3. For elements 'milestone' and unit 'number'
```
let $label := local:changeFormat($act/@n)
let $label := $label || ' - ' || string-join(
	for $t in $scene/tei:head//text()
	return if(matches($t, '\w'))then($t)else(), '')
let $label := 
	if(string-length($label) > 40)
	then(concat(substring($label, 1, 40), '…'))
	else($label)
```

#### id:
1. For elements 'div' and type 'chapter' or 'div1'
string(@xml:id) von element

2. For elements 'div' and type 'act'
string(@xml:id) von element

3. For elements 'milestone' and unit 'number':
for $scene in element of tei:div[@type='scene']
```
$scene/string(@xml:id)
```

#### pageID:
1. For elements 'div' and type 'chapter' or 'div1'
```
if($mode = 'pageMode')
then(substring-after($elem/preceding::tei:pb[1]/@facs, '#'))
else('-1')
```

2. For elements 'div' and type 'act'
```
if($mode = 'pageMode')
then(substring-after($elem/preceding::tei:pb[1]/@facs, '#'))
else('-1')
```

3. For elements 'milestone' and unit 'number'
```
if($mode = 'pageMode')then(substring-after($scene/preceding::tei:pb[1]/@facs, '#'))else('-1')
```





