# getParts.xql
## Input parameters:
```
$uri := request:get-parameter('uri', '')
```
## Show following data informations
For each part in mei:instrumentation/mei:instrVoice

1. Label:
```
$part/@label
```

2. ID:
```
$part/@xml:id
```

3. selectedByDefault: true

4. selected: true

## Example
### Parameter
![](media/15115265453053.jpg)

### XML
```
...
<perfMedium>
	<instrumentation>
		<instrVoice label="Score" xml:id="score"/>
		<instrVoice label="Duo Voces Articuli" xml:id="duoVoce"/>
	</instrumentation>
</perfMedium>
...
```
### result JSON
```
{label: "Score", id:"score", selectedByDefault:true, selected:true},{label: "Duo Voces Articuli", id:"duoVoce", selectedByDefault:true, selected:true}
```


