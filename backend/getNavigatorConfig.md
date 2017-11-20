# getNavigatorConfig.xql
### Conditions
Show items so than they ordered in edition file, no @sortNo attribute is used.
### Input parameters:
```
$editionId := request:get-parameter('editionId', '')

$workId := request:get-parameter('workId', '')
```

### Get following information as HTML, show items so than they ordered in edition file
get navigator definition from edition file:
```
$edition := doc($editionId)/root()
$work := $edition/id($workId)
$navConfig := $work/edirom:navigatorDefinition
```
For each element in $navConfig get
navigatorItem:
```
let $target := $item/replace(@targets, 
let $cfg := concat('{', replace(substring-before($item/substring-after(@targets, '['), ']'), '=', ':'), '}')
```
  
```
<div class="navigatorItem{
	if($depth lt 2)
	then()
	else($depth)}" 
	id="{$item/@xml:id}"
	onclick="loadLink('{$target}', 	{$cfg})">
	{ $item//edirom:name[1]/node() }
</div>
```

navigatorSeparator:
```
<div class="navigatorSeparator"></div>
```

navigatorCategory:
```
<div class="navigatorCategory{if($depth = 1)then()else($depth)}" id="{$category/@xml:id}">
```

```
<div class="navigatorCategoryTitle{if($depth = 1)then()else($depth)}">
{
	if($depth = 1)
	then($category/edirom:names/edirom:name[1]/text()})
	else(
		<span id="{$category/@xml:id}-title" onclick="..." class="folded">{$category/edirom:names/edirom:name[1]/text()}
			<i class="fa fa-caret-right fa-fw"></i>
		</span>
	)
</div>

<div id="{$category/@xml:id}-items" class="">
{
	for $elem in $category/edirom:navigatorItem 
	| $category/edirom:navigatorCategory
	
	return
		if(local-name($elem) eq 'navigatorItem')
		then(local:getItem($elem, $depth))
		else 
			if(local-name($elem) eq 'navigatorSeparator')
			then(local:getSeparator())
			else 
				if(local-name($elem) eq 'navigatorCategory')
				then(local:getCategory($elem, $depth + 1))
				else()
}
</div>
```



